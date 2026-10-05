# Software_Engineering_Project_Management-SEPM-
# RIDHIKANTA SARKAR SUMIT
**ID:** IT24045

---

## Class 2
**Date:** 3-10-26

---

## Files Included

| File | Description |
|------|-------------|
| `Main2.java` | Instance variable vs. object behavior (`Student` class) |
| `ThreadMain.java` | Multithreading using `start()` |
| `ThreadMain1.java` | Calling `run()` directly (no new thread) |
| `Main2.class`, `Student.class` | Compiled bytecode of `Main2.java` |

---

## 1. Main2.java — Instance Field

`Student` has an **instance field** `count` initialized to `0`. The constructor increments it. Since every object gets its **own copy** of `count`, each new `Student` starts from `0` and becomes `1`.

**Output:**
```
1
1
1
```

**Note:** To share one counter across all objects, declare it as `static int count = 0;`. The output would then be `3 3 3`.

---

## 2. ThreadMain.java — Using `start()`

`CookingTask` extends `Thread` and overrides `run()`. Calling `start()` creates a **new thread** for each task, so they run concurrently with `main`.

**Possible output (order may vary):**
```
All tasks started...
Thread-0 - Running: Cooking
Thread-1 - Running: Washing
```

The order is **not guaranteed**, because the threads are scheduled by the JVM.

---

## 3. ThreadMain1.java — Using `run()`

Here `run()` is called directly instead of `start()`. This is just a normal method call, so **no new thread is created**; everything runs on the `main` thread, one after another.

**Output (always the same):**
```
main - Running: Cooking
main - Running: Washing
All tasks started...
```

---

## Key Takeaway

| | `start()` | `run()` |
|---|-----------|---------|
| Creates new thread | Yes | No |
| Thread name shown | `Thread-0`, `Thread-1` | `main` |
| Execution order | Not guaranteed | Sequential |

---

## How to Compile and Run

```bash
javac Main2.java
java Main2

javac ThreadMain.java
java ThreadMain

javac ThreadMain1.java
java ThreadMain1
```

> **Note:** `ThreadMain.java` and `ThreadMain1.java` both define a class named `CookingTask`. Compile and run them in separate folders, or compile one at a time, to avoid class conflicts.
