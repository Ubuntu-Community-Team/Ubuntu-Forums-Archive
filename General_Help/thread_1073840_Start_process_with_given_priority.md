---
title: "Start process with given priority"
date: 2009-02-18
forum: General Help
---

### Post by Zipi on 2009-02-18
Hi,
how can i start a process with a given priority (if possible)?

I am aware of the "nice" command,but it seems it changes the niceness of a process,not the actual priority....

---

### Post by heindsight on 2009-02-18
The kernel's process scheduling algorithms assign priorities to processes. The only aspect of the actual scheduling priority you as a user can control is the niceness. So from a user perspective niceness is priority.

You may want to read this: [http://oreilly.com/catalog/linuxkernel/chapter/ch10.html](http://oreilly.com/catalog/linuxkernel/chapter/ch10.html) if you want to understand the gory details of process scheduling and priorities in the kernel

---

### Post by Zipi on 2009-02-18
Thanks!
I have read the part about system calls,noticing,in particular,the nice() system call.
It seems a bit different from the "nice" shell command,since the "nice" shell command lets me start a process with a given niceness,while the system call lets me change it after the process creation.
Is there some way to actually set the niceness since the process start?

---

### Post by heindsight on 2009-02-18
The nice() system call is for a process to set it's own niceness.
you can use the renice command to change the niceness of a process. As a normal user, you can only renice processes that you own and you can only increase the niceness of a process. As root on the other hand, you can  increase or decrease the niceness of any process.

A word of warning though, if you set the niceness of some process too low, your system may become so unresponsive (because that process will have much higher scheduling priority than any others) that it can become hard to reverse the process by increasing the niceness again. If you want to decrease the niceness of a process, I'd recommend doing it by small amounts at a time.

You should probably read the manual:
```
man renice
```

---

### Post by Zipi on 2009-02-18
Ok :) Thanks again!

---

