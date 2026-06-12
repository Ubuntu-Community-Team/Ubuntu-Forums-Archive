---
title: "Can't Grow a Logical Partition"
date: 2009-05-29
forum: General Help
---

### Post by trench.me on 2009-05-29
On one of my machines I've a 320GB internal HD. I formatted it quite awhile back and miffed the partitions a bit. I've a boot partition, swap partition, system partition, and home partition. Approximately half the drive was left unallocated  because I planned on installing another OS. Now I've decided I'd just like to grow my home partition to fill up the drive. 

GParted, from a live disc, will not let me grow the volume. And further, I can't create a new partition in the unallocated space because "I have too many logical partitions". :/

What's the best way to resolve this with minimal impact on my current setup?

```
$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000227fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13         620     4883760   82  Linux swap / Solaris
/dev/sda3             621        3052    19535040   83  Linux
/dev/sda4            3053       20676   141564780   83  Linux
```***EDIT: Replace all instances of LOGICAL that occur here with PRIMARY. I'm an idiot, it's late, and my xanax says hai. Ugh.***

---

### Post by plucky on 2009-05-29
> **trench.me said:**
> On one of my machines I've a 320GB internal HD. I formatted it quite awhile back and miffed the partitions a bit. I've a boot partition, swap partition, system partition, and home partition. Approximately half the drive was left unallocated  because I planned on installing another OS. Now I've decided I'd just like to grow my home partition to fill up the drive. 

GParted, from a live disc, will not let me grow the volume. And further, I can't create a new partition in the unallocated space because "I have too many logical partitions". :/

What's the best way to resolve this with minimal impact on my current setup?

```
$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000227fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13         620     4883760   82  Linux swap / Solaris
/dev/sda3             621        3052    19535040   83  Linux
/dev/sda4            3053       20676   141564780   83  Linux
```

***EDIT: Replace all instances of LOGICAL that occur here with PRIMARY. I'm an idiot, it's late, and my xanax says hai. Ugh.***

You have 4 **Primary** partitions which is the maximum allowed on one disk.Thus gparted will not allow you to create another partition.It should however allow you to extend a partition into the allocated space,provided the un-allocated space is adjacent to the rear of the partition you are extending.

[color=blue]Take a screen shot and post to the forums so we can see how your disk is setup.[/color]

Alternatively:

You could unmount and delete the swap partition and create an extended partition (which counts as a primary partition) in the un-allocated space and re-create the swap as a logical partition and the rest of the un-allocated space as logical partitions.
If you do this,the UUID of the swap partition will change and you have to change it in **/etc/fstab** file or you swap partition will not mount.

Good Luck

---

### Post by trench.me on 2009-05-29
The unallocated space is indeed adjacent to the rear of the partition I'd like extended. Here's a screenshot.

[_[IMG]http://trench.me/ubuntuforums/images/GParted.jpg[/IMG]_]("http://trench.me/ubuntuforums/images/GParted.jpg")

So I guess the question becomes how do I extend /dev/sda4 (aka /home)? I've tried un-mounting and resizing but I get a "failed to resize" error.

I was using Knoppix so I tried GParted as well as QtParted. Neither wished to comply. If possible, I'd much rather go with your first method than the alternative (not because of the UUID/fstab thing, rather just because I'd like to extend my current /home/ partition if at all possible, you know?). I'll try again and take screenshots of the errors I'm receiving.

And mucho thanks for the help.

---

### Post by Soul-Sing on 2009-05-29
You can addit. use the newest gparted iso, which runs as a live-cd.
It has more options as gparted.

---

### Post by fuzzyworbles on 2009-05-29
i can't see why you wouldn't be able to grow sda4. in your screenshot the partition is mounted. make sure you've unmounted it (perhaps via the a console and not through gparted) before attempting to grow.

---

### Post by Soul-Sing on 2009-05-29
> **fuzzyworbles said:**
> i can't see why you wouldn't be able to grow sda4. in your screenshot the partition is mounted. make sure you've unmounted it (perhaps via the a console and not through gparted) before attempting to grow.

That is the reason to use the gparted live-cd.

---

### Post by trench.me on 2009-05-29
I just returned from Knoppix and GParted worked  smooth-as-silk. No clue what provoked the errors yesterday, I did everything exactly the same as I did during today's successful attempt.

Odd.. but yay, nonetheless, because it's fine now.

Side-note: I can't use the GParted LiveCD on the machine due to the giant red warning seen on [this page]("http://gparted.sourceforge.net/livecd.php"), pointing to the unresolved wtf-bug found [here]("http://bugzilla.gnome.org/show_bug.cgi?id=579000") (which should probably be expanded from a GParted bug and introduced as a Debian[?] bug). 

Thanks for the responses & help all!

---

