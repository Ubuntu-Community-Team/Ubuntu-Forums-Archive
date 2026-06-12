---
title: "does not recognize floppy"
date: 2006-01-19
forum: General Help
---

### Post by marcostt on 2006-01-19
I have installed Kubuntu in tree differents computers... and in all of them I get the same bug: can not read fllopy disk: when I try to mount disk, just try to read it, and show me an error message: 

> Can not mount device. Please check that the device is plugged correctly

Some idea?

---

### Post by Xandor on 2006-01-20
What kernel are you using, and did you compile it yourself. If so, check your configuration, there is an option that, for some kernels, is defaulted to off, this option allows support for floppy disks. I am not able to recall the name of the option but if you run xconfig or menuconfig you should be able to find it, I beleive it's under the file system section.
Also, when your computer boots up and tries to access your floppy drive for booting does your floppy drive make any noise or the light come on, the power cord could have been knocked loose.

---

### Post by marcostt on 2006-01-21
Sorry, I am new at linux... I dont know how to run xconfig...

Anyway, the kernel is the one that comes with kubuntu 5.10 breezy. And it is not a problem of my computer: I have just installed yesterday kubuntu in other two computers with the same problem with floppy.

---

### Post by mo_x on 2006-01-21
Have you tried other disks?
Are you sure the drive is ok?

---

### Post by marcostt on 2006-01-21
[QUOTE=mo_x]Have you tried other disks?
Are you sure the drive is ok?[/QUOTE]

Yes, I have tried other disks... and sometimes in my computer mount the disk with some and not with others... but in the computers of my friends where I have install kubuntu, occurs the same, dont work the disks, or not with all the diskettes

---

### Post by mo_x on 2006-01-21
Are it alsways the same disks that are not working? Then I suspect the problems are with the disks. Otherwise maybe just keep trying.

---

