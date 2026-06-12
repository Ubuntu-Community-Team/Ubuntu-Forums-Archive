---
title: "Deleting kernels?"
date: 2009-04-29
forum: General Help
---

### Post by NFblaze on 2009-04-29
So I notice that on power up GRUB has like the old kernels listed into it. 

Im sure I dont need no more than the current version and the last version.

How would I go about deleting the old kernels... do I just delete the selections from GRUB or is there much more to it.

---

### Post by wsonar on 2009-04-29
You can edit the /boot/grub/menu.list file and rem out the old ones with a #

You can also rename the title to something more human like ubuntu 9.04

---

### Post by NFblaze on 2009-04-29
Yea, but that doesnt sound like  that actually deletes the old kernels  themselves...?

---

### Post by plucky on 2009-04-30
> **NFblaze said:**
> Yea, but that doesnt sound like  that actually deletes the old kernels  themselves...?

Open Synaptic package manager and search for **linux-image** and mark the versions you want removed.Make sure you don't remove the latest kernel.

This will also update the grub menu.

It is recommended you keep at least one spare working kernel,just to use as a troubleshooting tool if the latest kernel develops a problem.


Good Luck

---

### Post by bladeswords on 2009-04-30
Just a little addition, you can find out your current kernel version by running 
```
uname -a
``` from the terminal.  Mine is currently 2.6.28-11-generic.

---

### Post by NFblaze on 2009-04-30
Alright, Thanks guys I will definitley try this out today... I was busy playin Unreal Tournament 3 all day yesterday...lol

---

