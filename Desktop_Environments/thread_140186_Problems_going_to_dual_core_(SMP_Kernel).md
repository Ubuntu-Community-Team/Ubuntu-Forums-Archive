---
title: "Problems going to dual core (SMP Kernel)?"
date: 2006-03-05
forum: Desktop Environments
---

### Post by Bokonon on 2006-03-05
I have Ubuntu (32bit) working pretty much the way I want to, but I am thinking about upgrading my CPU to an AMDX2 chip.  Other than the CPU, I am ready for the jump hardware wise.

My question is when I switch to the SMP kernel, will I pretty much have to do a reinstall?  I would like to keep everything the way it is, but take advantage of the dual core processor.

---

### Post by o_fortuna on 2006-03-05
[QUOTE=Bokonon]I have Ubuntu (32bit) working pretty much the way I want to, but I am thinking about upgrading my CPU to an AMDX2 chip.  Other than the CPU, I am ready for the jump hardware wise.

My question is when I switch to the SMP kernel, will I pretty much have to do a reinstall?  I would like to keep everything the way it is, but take advantage of the dual core processor.[/QUOTE]
No need for a reinstall (in fact, that wouldn't even do anything.) Just
```
sudo apt-get install linux-k7-smp
sudo update-grub
```
Will do it for you (and add a line to GRUB).
You may want to remove the old kernel, which is linux-386, because it's basically a waste of space (just make sure that the SMP kernel works first -- just to be safe!)

---

### Post by Bokonon on 2006-03-06
Fortuna, thanks for the information.  I did not realize the smp kernel was not on the CD.  (stuck in Fedora thinking I guess).

It worked great on my HT laptop, so I anticipate no problems going to dual core AMDX2 on the desktop.

Edit:  No problem on the desktop either.  New 4400+ works great and is clocked to 4800+ levels.  No problems running anything with the new kernel and everything runs a LOT better.  I dumped the old kernel.  Thanks again Fortuna!

---

