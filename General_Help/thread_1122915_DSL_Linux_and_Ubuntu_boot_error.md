---
title: "DSL Linux and Ubuntu boot error"
date: 2009-04-11
forum: General Help
---

### Post by tm222 on 2009-04-11
I have done an Install of DSL on a partition, and GRUB cannot boot it. It says that the kernel is too old. I know this, because DSL uses 2.4 instead of 2.6 is it possible to boot DSL?


Acer Travelmate 529TXV (I know it's old) 
800 MHz, 512 MB of RAM, Triple Boot Ubuntu Jaunty, Arch Linux, and soon DSL.

---

### Post by tommcd on 2009-04-11
When you install DSL, doesn't it give you the option of installing grub? If so, does it give you the option where you want grub installed?
If it gives you the option where you want to install grub, choose to install DSL's grub to the DSL partition. Then add this to Ubuntu's grub:
```

title DSL
configfile (hdX,Y)/bootgrub/menu.lst
savedefault

```
Replace X,Y with the partition # for DSL. Rememver grub counts from zero. Also, verify that DSL installs the menu.lst to /boot/grub/menu.lst. For most distros this is the case.

---

### Post by nrballard on 2009-04-12
DSL uses Lilo.

You'd have to boot from the DSL LiveCD, create a file /etc/lilo.conf in one of your drive partitions, and run:

lilo -r /dev/sda1 (or wherever the lilo.conf file is located)

---

### Post by tm222 on 2009-04-12
Thanks for the configfile thing, I should of figured that out after playing with Arch Linux, it uses those commands all the time, so I'll try that now.

---

### Post by tm222 on 2009-04-12
Ok, I tried the configfile thing and the boot gets farther in the process, but after it scanned the partitons or something, it still said
"FATAL: Kernel too old" and said something like Kernel Panic

---

