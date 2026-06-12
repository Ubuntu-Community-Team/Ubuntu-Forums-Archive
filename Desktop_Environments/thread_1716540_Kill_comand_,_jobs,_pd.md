---
title: "Kill comand , jobs, pd"
date: 2011-03-28
forum: Desktop Environments
---

### Post by 71GA on 2011-03-28
Hello!

I am learning terminal and i want to kill a process. There are 2 ways to do it i ve heard. 1st way is to type following in terminal:
```
jobs
[1]+  Running                 xload &
kill %1
```
2nd way is to type:
```
ps 
  PID TTY          TIME CMD
 1668 pts/0    00:00:00 bash
 5042 pts/0    00:00:00 xload
 5043 pts/0    00:00:00 ps
kill 5043
```

1st example is working, but 2nd isnt. What am i missing? 

TY

---

### Post by jwcalla on 2011-03-28
> **71GA said:**
> Hello!

I am learning terminal and i want to kill a process. There are 2 ways to do it i ve heard. 1st way is to type following in terminal:
```
jobs
[1]+  Running                 xload &
kill %1
```2nd way is to type:
```
ps 
  PID TTY          TIME CMD
 1668 pts/0    00:00:00 bash
 5042 pts/0    00:00:00 xload
 5043 pts/0    00:00:00 ps
kill 5043
```1st example is working, but 2nd isnt. What am i missing? 

TY

You had a typo... you wanted to kill process id 5042.

---

### Post by 71GA on 2011-03-28
> **jwcalla said:**
> You had a typo... you wanted to kill process id 5042.

Thank you.

---

