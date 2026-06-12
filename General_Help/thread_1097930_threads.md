---
title: "threads"
date: 2009-03-16
forum: General Help
---

### Post by cybo on 2009-03-16
this is a generic question related to software threads.

i'm trying to learn this topic and understand what software threads are. but the more i read the more confused i get.

can anyone explain what a thread is and what are
1. kernel threads
2. native threads
3. user threads
4. POSIX threads
5. what is the difference between those kinds of threads
6. what is a user space
7. what is a kernel space
8. what is the difference between them

any help is greatly appreciated

---

### Post by markitect on 2009-03-16
Let me answer out of order:
Kernel/User Space are a logical separation of different memory, threads and other resources based on how much privilege they have.

Kernel Space has all of the kernel related memory and code, this space has unlimited permission to do what they want with whatever they want.

User Space is where everything else runs, and has to depend on the kernel for system calls.  This is where almost everything runs.

Kernel vs User Threads are threads in the corresponding space.  For the most part you do not care about this at all, but drivers and things like that often have some threads inside the kernel and some inside the user space.  By limiting the amount of code run with no restrictions you reduce the risk of thinks from system instability to vulnerability.

POSIX is a handy toolkit for programmers to use.  It provides standard calls for creating and manipulating threads, as well as many other things.  POSIX is a standard that operates on many different operating systems, and is for the most part what a programmer is concerned with.

---

### Post by cybo on 2009-03-17
thanks for the help. is there any good reading you can recommend about threads for a beginner?

---

### Post by markitect on 2009-03-17
Check out this book, it's a good all around Linux programming book, and will get you started with threads, as well as processes and the ways to communicate between them (ch 11 -14).

[http://books.google.com/books?id=-Krh_QqpuG0C](http://books.google.com/books?id=-Krh_QqpuG0C)

---

### Post by cybo on 2009-03-17
thanks

---

