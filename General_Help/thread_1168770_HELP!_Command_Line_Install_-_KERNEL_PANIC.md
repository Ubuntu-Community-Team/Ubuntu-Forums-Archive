---
title: "HELP! Command Line Install - KERNEL PANIC"
date: 2009-05-24
forum: General Help
---

### Post by abyrne on 2009-05-24
Hi,

    I have a big problem. I have repeatedly tried to install a command-line ubuntu using the cli option on the Ubuntu 8.10 Minimal (netboot) CD. I installed it along with Xubuntu 9.04 and a Gparted Live image on the same hard drive. But when I try to boot it up for the first time I get the normal boot-up messages and then I get this

```
[   0.744248] VFS: Cannot open root device "<NULL>" or unknown-block(104,1)
[   0.744302] Please append a correct "root=" boot option; here are the available partitions:
[   0.744371] Kernel Panic - not syncing: VFS: unable to mount root fs on unknown-block(104,1) 
```

And the Caps Lock and Scroll Lock lights on my keyboard start flashing, the system becomes unresponsive, and I have to force shutdown.

This is getting annoying as I have installed and reinstalled 3 times and have gotten the same result.

I'm pretty familiar with Linux and Ubuntu but I've never seen anything like this. If anyone knows anything about this please help!

Thanks

---

### Post by cariboo on 2009-05-24
From the error message it looks like you don't have a / partition defined.

---

### Post by abyrne on 2009-05-24
> From the error message it looks like you don't have a / partition defined. 

I'm pretty sure I do. The installation wouldn't have worked if I didn't.

---

### Post by abyrne on 2009-05-24
bump

---

### Post by Super TWiT on 2009-05-24
Two things, 1. have you checked your install disk for errors? 2. Did you format the partition before installation?
Weird error...

---

