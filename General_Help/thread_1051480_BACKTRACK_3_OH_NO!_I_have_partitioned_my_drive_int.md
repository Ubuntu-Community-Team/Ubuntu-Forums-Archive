---
title: "BACKTRACK 3 OH NO! I have partitioned my drive into two pieces and now..."
date: 2009-01-26
forum: General Help
---

### Post by Epidemic_HardyBoy on 2009-01-26
It cannot read the full amount! (1g) it only reads 700+mb.
Anyone know how to fix this? As in make it one full partition of 1g?
Thanks all

:P

---

### Post by Epidemic_HardyBoy on 2009-01-26
Anyone know this problem?
This is when I tried making Knoppix install on the Flash Drive
from Pendrivelinux website.
I want to get my Fast Track on there but there is now two "pieces" of the Flash drive, one being "700+" and the other being "240+"

PLEASE

---

### Post by 5BallJuggler on 2009-01-26
how important is the data on the drive? 
if it's not so important, use gparted from the liveCD to rebuild the partition, also, by using this it does not definately mean that the data will be lost anyway..


...unless you format it too.

---

### Post by e1mer on 2009-01-26
Well, good news and bad news.

The good news is it's easy to fix if you don't care about
the data.

Just boot from the live CD and delete both partitions.
Then make a new one and install.

The bad news is that if you care about your data you're going
to have to learn some commands.

Let's assume 2, and assume /dev/sda. Change below accordingly.

First, get a sudo su command prompt.
Then use fdisk to delete the bogus partition.
WARNING: Don't delete your swap partition!!!!
```
sudo su -
fdisk /dev/sda

```
Here you need to print, then delete, then write and quit.
Each command is followed by 'return'  YOU MUST PICK THE RIGHT
PARTITION TO DELETE!!!
Remember which file system type you use for the good partition.
I would guess that you're deleting partition 3 (swap, /, then bogus.)

Next you have to use either resize2fs or resize_reiserfs to
change the size of your good partition.

Use ```
man resize2fs
``` if it said ext2fs or ext3fs above.

Good luck.

---

### Post by gigaferz on 2009-01-26
hey, im not a real pro or anything, but, what are you trying to do??

It could be simple, just plug your flash drive into any computer and, erase/delete partitions and create one.

Like when you install ubuntu. (gparted)

 Then again, Im not sure about your problem.

---

### Post by Epidemic_HardyBoy on 2009-01-26
> how important is the data on the drive?
if it's not so important, use gparted from the liveCD to rebuild the partition, also, by using this it does not definately mean that the data will be lost anyway..


...unless you format it too.

I tried using gparted and it said I cannot compile the two into 1 full 1g partition.

The data is useless.

---

### Post by Epidemic_HardyBoy on 2009-01-26
I hopped on Windows a couple of minutes back.

[IMG]http://i306.photobucket.com/albums/nn266/epidemic_gfx/omfgfff.png[/IMG]

This is what I am dealing with. The "blank" partition of the Flash is 235
I want to compile that into the other 721

---

### Post by Epidemic_HardyBoy on 2009-01-26
I've hopped on BT3 Live.. I opened up QTParted (SLAX gparted counterpart?) and was able to delete one of the partitions (721mb one) but the 235mb one is still standing there, I will try to get a screenshot up in a moment.

---

### Post by cariboo on 2009-01-26
Now that you have deleted the one partition can you not use gparted to increase the size of the original partition?

Jim

---

### Post by dagnabit dang doohickey on 2009-01-26
If unsuccessful at getting this done in Linux, there's a utility by HP that will easily reformat the whole USB stick. You can get it [here]("http://files.extremeoverclocking.com/file.php?f=197") [extremeoverclocking.com].

---

### Post by Epidemic_HardyBoy on 2009-01-26
thank you!

---

