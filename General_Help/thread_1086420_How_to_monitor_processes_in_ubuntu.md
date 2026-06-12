---
title: "How to monitor processes in ubuntu"
date: 2009-03-04
forum: General Help
---

### Post by joshaman on 2009-03-04
How do I monitor the actions of processes in unbuntu?  

e.g. something like ProcessMonitor for windows.

---

### Post by lykwydchykyn on 2009-03-04
I don't know of a completely analogous program, but you can get pretty similar information using the strace command.  It has a lot of switches to filter or adjust the output, but the basic command is:
```

strace -p pid#

```
where pid# is a process id number.

---

### Post by Kobalt on 2009-03-04
The built-in System Monitor (System > Admin. > System Monitor) allows for simple process monitoring, right-clicking on any running process in the list. 
Is that tool sufficient for you ?

---

### Post by joshaman on 2009-03-04
Thanks for the tip, lykwydchykyn.  I sure wish there was something with a GUI..  

System monitor is not what I'm looking for, but thanks for replying, Kobalt.

---

### Post by jonallport on 2009-03-04
top

---

### Post by bodhi.zazen on 2009-03-04
moved to general help ;)

---

### Post by emarkay on 2009-03-04
Interesting - surely there's something - I sort of wondered that myself.

---

