---
title: "how can I format my second hard drive to Linux?"
date: 2006-09-09
forum: Desktop Environments
---

### Post by eighthate on 2006-09-09
Some1 help me, i know i can use gparted but i dont know how to use it!
some1 help pls!!

---

### Post by someguyouknow on 2006-09-09
gparted is fairly simple to use.
open it up
in the top right corner should be a list of the harddrives installed on your computer. assuming you only have two it will prolly be hdb
choose how you want it to be formatted and then format.

my second harddrive is XFS but the favorite seems to be ext3.

---

### Post by aysiu on 2006-09-10
Make sure your drive is unmounted before you try to reformat it.

GParted's homepage has some screenshots that may help you understand how to use it:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

### Post by eighthate on 2006-09-10
how can i open it up, I'm noob at this, i installed it using synaptic, but i cant find it anywhere. Thanks.

---

### Post by arkangel on 2006-09-10
should be in System>>administration>>Gnome Partition Editor

if not open a terminal and type
> sudo gparted

---

### Post by eighthate on 2006-09-10
Oh great thanks a bunch!

---

### Post by eighthate on 2006-09-10
Some1 wanna give me more support, it doesnt seems to format to linux, when i wanna open my newly formated Hard drive it says its still in windows, when i reboot it stills asks me if i wanna boot in windows..

(error: device /dev/hdc1 does not exist

error: could not execute pmount)

---

### Post by dwasifar on 2006-09-10
> **eighthate said:**
> Some1 wanna give me more support, it doesnt seems to format to linux, when i wanna open my newly formated Hard drive it says its still in windows, when i reboot it stills asks me if i wanna boot in windows..
I had that happen once.  Try installing the drive in a Windows machine and delete the partitions using Windows.  Then take it back to Linux and repartition it.  That worked for me.  YMMV.

---

### Post by arkangel on 2006-09-11
you can try with cfdisk,  it is quite reliable

sudo cfdisk

---

