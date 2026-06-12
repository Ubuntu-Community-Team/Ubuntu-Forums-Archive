---
title: "Help moving root partition"
date: 2009-01-05
forum: General Help
---

### Post by WelterPelter on 2009-01-05
Hi -
I have my root partition on one drive and my home partition on another. 
Now the drive holding the root partition is getting sketchy, do I'd like to move everything over to the drive with /home on it. 

I've been using Linux for a few years now, and have made enough mistakes to know that this operation should be done with great caution (at least in my case ;)). 

So my question is, how would you recommend I do this? 

My guess is that it's something like: 

Boot from Live CD.
Make new root partition on second drive.
Copy the contents of old root to new root. (Will it screw things up to have two root partitions?)
Fix fstab to reflect new configuration.
Unplug old drive and reboot system to see if new root works. 

Any corrections, additional information, or hints would be very welcome. I'd like to not have to install everything from scratch again, if possible. 

Thanks.

---

### Post by bodhi.zazen on 2009-01-05
Moving your root partition should be fairly easy.

You can move it using a live CD. After moving the partition you will need to update both 

/etc/fstab

and 

/boot/grub/menu.lst

You can not run two root partitions at the same time (ie when booting from hard drive).

here is a how-to that may help you :

[How to run bleeding edge - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=316237")

---

### Post by WelterPelter on 2009-01-05
I think I get it. 
One question. 
What about the extended and swap partitions? 
Do I need to create and copy these too?

---

### Post by bodhi.zazen on 2009-01-05
Well, an extended partition allows you to get around the limitation of 4 primary partitions.

You instead make 1 extended partition which then can contain logical partitions.

You do not need to move swap. With a live CD make a new swap partition with gparted and update /etc/fstab with the new UUID of the new swap partition.

See also

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

---

### Post by WelterPelter on 2009-01-07
Well, this ended up only partially going well.

Moving the partitions worked as advertised.

It took me a while to figure out how to then copy the data over. 

```
cp -ax /mnt/old/* /mnt/new 
``` worked. Doing this from the root gparted directory, and including the * was key.

So everything got copied over, but there were huge problems with booting. Beavered away for a few hours (configure, configure, configure) without success. Finally just reinstalled the entire system. Brutal but effective. 

Thank you bodhi.zazen for your help.

---

### Post by bodhi.zazen on 2009-01-07
OUCH

The cp command is not the best approach (as you can see).

Use something like tar or dd or gparted will copy / paste partitions or partimage or well you  get the idea, a better tool.

---

### Post by WelterPelter on 2009-01-07
Perhaps it would be helpful to unpack the line "copy the drive" in your "bleeding edge" thread to explain the best ways to copy.

I ended up googling endless linux how-to sites that claimed that cp -ax was the most trouble-free way to go.

I did attempt to cut and paste the partition with gparted, btw, but it only made a shallow copy, as far as I could tell. 

Anyway, this is all postmortem, of course.

---

