---
title: "Set system to read only"
date: 2009-06-15
forum: General Help
---

### Post by yogg on 2009-06-15
Hi

Is it possible to make an already running Ubuntu installation read only like an live CD? Has maybe someone a good link or a google search string to this theme for me?

---

### Post by ultratwo on 2009-06-15
You might be able to with your home partition (if you have separate root and home partitions) simply by changing /etc/fstab, however if you do that with your root the inability of the system to save files will cause problems (in to save .Xauthority file will prevent you from running graphical programs as root.

It is possible to save files on a Live CD, they are just stored in memory and disappear when you shutdown.

One question, why do you want to do this?

---

### Post by yogg on 2009-06-15
Memory sticks have limited write cycles. I would install a system on a memory stick, but if I do this on the normal way the system writes log files and many other things. So the stick reaches his limitations in a very short time.

I need something like an live CD. New files and programs are stored in an ramdrive and disappear on reboot. But for some other reasons the system must be installed first on the normal way.

---

### Post by yogg on 2009-06-15
In 5h on side 5

Needs some push up :P

---

