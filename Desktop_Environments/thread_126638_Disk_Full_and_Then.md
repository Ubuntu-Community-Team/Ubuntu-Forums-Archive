---
title: "Disk Full and Then?"
date: 2006-02-07
forum: Desktop Environments
---

### Post by firingstone on 2006-02-07
After doing some apt-get install and a reboot.I found myself outside the desktop
could only see the GDM interface and input my login and password,but got a warning when hit the 'enter' key. And warning says about something like, it cannnot write some GDM stuff,since the disk is full or the home dirctory is locked,and advice me to ask administrator for help. Well, I guess the first reason  should fit my situation. Then what shall I do? no help even I do some apt-get remove and I am not using a LVM. Really need help here.
Thank you in advance

---

### Post by jasmuz on 2006-02-07
First go to a console: ctrl + alt + f1, login  and type this

$ sudo apt-get clean  
(this will clean everything you file downloaded, but wont interfere with your install)

Then check how full the disks are:

$ df -h


Hope this helps

---

### Post by kaamos on 2006-02-07
You could try to boot in recovery mode (can be chosen in grubs menu) and use the command
```
df -h
```
to see the status of your disk space. If its full, remove some stuff. Doing
```
apt-get clean
```could help for starters.

EDIT: too slow.

---

### Post by firingstone on 2006-02-07
That is cool and simple solution! Thank you!! :) 
And yes it was 100% usage, but now I can jump in my ubuntu again:) 
By the way is there a easy way to resize the partition?

---

### Post by nanotube on 2006-02-07
use the gparted partition editor (install package gparted).?

---

### Post by firingstone on 2006-02-07
[QUOTE=nanotube]use the gparted partition editor (install package gparted).?[/QUOTE]
Well, installed that but options are all in grey, not available
Even if I choose applications--system tools --Run as different user --
and type gparted and choose root, still the same.

---

### Post by kaamos on 2006-02-07
You can't resize mounted partitions, thats probably why they are greyed out.

---

### Post by firingstone on 2006-02-07
yeah, you are right, I forgot to umount the partition. 
The problem is I can not umount the / partition which I am trying to enlarge.

---

### Post by nanotube on 2006-02-07
you would have to boot from livecd to resize that one...

---

