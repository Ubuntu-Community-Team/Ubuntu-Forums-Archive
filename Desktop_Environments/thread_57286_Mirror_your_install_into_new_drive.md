---
title: "Mirror your install into new drive?"
date: 2005-08-15
forum: Desktop Environments
---

### Post by autocrosser on 2005-08-15
Ok--I'm going to move into Ubuntu full-time. I installed 5.04 into a smallish spare drive on my system & now would like to move all of it into one of the main drives. I've cleared 90G on a 120G (I do webdesign & artwork-so I like room)-the remainder is a OSX install.

So, is it going to be as easy as (as root) copy the directories after formatting how I want? I know I'll need to edit fstab-yaboot (mac grub) & run a prebind?

What am I missing? Thoughts--ways of doing--apps--???

I'm going to turn the "old" install into Breezy & want a LARGE comfee space for my work (& seperate the wife's user--too long to go into here:neutral:--not a computer user:?)

---

### Post by danns on 2005-08-16
I've done stuff like this before, but only on x86.   Unless you really, really have a pressing need to keep your current setup, I'd recommend doing a fresh install.  You can always copy over the entire contents of your home directory into the new install.

One of the ways I did this in the past was using cp -a source destination.  It helps if you use a boot disc of some sort (maybe the ubuntu ppc install cd); mount the source and destination; then run cp -a.

You do not want to copy over what is in /dev or /proc, but you want to make sure those directories exist off of /.  You'll have to change your /etc/fstab settings and then configure yaboot.

---

### Post by autocrosser on 2005-08-16
Well, I'm dial-up & have downloaded a large amount of things-(read games-keeps wife happy:?) --not looking forward to re-downloading it all with a fresh install--but if that is the better way, I'll go there......after all, it will be worth it in the end.:grin:

---

### Post by danns on 2005-08-16
Well, since you are on dial-up, if you don't mind spending a few hours playing around; give it a shot.  The worst you can do is fill up that new partition with some data.  If it doesn't work you still have your original partition you can boot from.  

This is what I would try:

Boot from the ubuntu install cd and exit out of the installer or switch to another console.

Create two mount points:  Source and destination

Copy the entire structure of the source to the destination:  cp -a source/* destination 

At this point you can mess around with chroot to change / to your working partition and configure yaboot.conf, but if you are not sure about this I would reboot into your working system.

Create a new image in the yaboot.conf file using your existing kernel but set the root to your new partition.  Bless the bootsector and reboot.

You should now be able to get into your new system as if it was your old.  If everything is working, edit the yaboot.conf file in the new system and make the necessary changes; then rebless the disk.

I'm a bit rusty on my yaboot configuration so you will want to read over some howtos or man pages to get the commands and syntax correct.

---

### Post by autocrosser on 2005-08-16
I've got a "rescue" disc based on Gentoo (a prior distro I tried-VERY use to using it:-P )--Have both disks partitioned the same (same directory mount points)--Am using /--/home--/tmp--/usr--/opt. So what I think I'm going to do---boot the Gentoo rescue disc, mount both of every partition, then cp -a source/* destination for each one. After this is done make sure that fstab agrees with the "new" partition mount points & correct yaboot--Then chroot into the "new" system from Gentoo and ybin -v to "bless" it (got a "crib" sheet from Gentoo on how to do it).
 
I've booted with the <option> key down many times to screen into open firmware, so I guess I'll be using that to cross between the various OS's on the system--
 
Sound like the plan?

---

