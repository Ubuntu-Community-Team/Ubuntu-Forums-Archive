---
title: "Does segmentation fault lead to memory leakage?"
date: 2009-01-15
forum: General Help
---

### Post by prick.i.am on 2009-01-15
I am workin on "lp_solver" which is a linear program solver, trying to optimise it using openmp. It was leading to segmentation faults when i use a large number of variables and constraints. How do i overcome this? Does it lead to memory leakage which may affect the performance of the system?

---

### Post by heindsight on 2009-01-15
A memory leak is when a process allocates memory and then fails to release it back to the OS again. In sever cases (where a process keeps allocating more and more memory) it can impact performance of other processes, but as soon as the offending process terminates (either voluntarily or because of an error or because it gets killed) the memory it allocated is freed up again.

A segmentation fault is an error which occurs when a process tries to access memory it's not allowed to access (i.e. memory not allocated to it). 

So no, it doesn't lead to memory leakage - in fact, any memory leakage that may be occurring in your process is stopped when the process dies because of the segfault.

---

### Post by prick.i.am on 2009-01-15
> **heindsight said:**
> A memory leak is when a process allocates memory and then fails to release it back to the OS again. In sever cases (where a process keeps allocating more and more memory) it can impact performance of other processes, but as soon as the offending process terminates (either voluntarily or because of an error or because it gets killed) the memory it allocated is freed up again.

A segmentation fault is an error which occurs when a process tries to access memory it's not allowed to access (i.e. memory not allocated to it). 

So no, it doesn't lead to memory leakage - in fact, any memory leakage that may be occurring in your process is stopped when the process dies because of the segfault.



Thx...
How can i protect my program from segmentation faults?
Because this seems to occur only when i parallelize a piece of code with large no of variables or iterations. FYI, i am using openmp on lp-solver.

---

### Post by heindsight on 2009-01-15
To avoid segfaults, you just have to be careful about how you allocate and use memory in your code. If you're using dynamic arrays, be sure that you allocate enough memory for the array before using it, remember the length of the array you've allocated and don't try to read and write beyond the end of the array. For pointers, make sure that the pointer points to something before you try to dereference it.

---

### Post by prick.i.am on 2009-01-15
> **heindsight said:**
> To avoid segfaults, you just have to be careful about how you allocate and use memory in your code. If you're using dynamic arrays, be sure that you allocate enough memory for the array before using it, remember the length of the array you've allocated and don't try to read and write beyond the end of the array. For pointers, make sure that the pointer points to something before you try to dereference it.

Thank you.
My concern is if a linear program with 100 variables and 200 constraints  can be parallelized, why cant the same work with 1000 variables and 2000 constraints???

---

