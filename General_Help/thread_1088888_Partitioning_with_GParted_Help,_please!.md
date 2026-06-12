---
title: "Partitioning with GParted? Help, please!"
date: 2009-03-06
forum: General Help
---

### Post by inspirations365 on 2009-03-06
Almost there, guys. Almost there.

The LAST thing I'll need help with, now that I finally got my laptop speakers working in Ubuntu 8.10 is to add SWAP and /home partitions.

Here's my hard drive setup and allocation:
9 GB Recovery Partition - primary
30 GB Windows 7 x64 Beta - primary
154 GB Windows Vista x32 - primary
30 GB 8.10 Ubuntu x64 - primary

If possible, I would like to divide the Ubuntu partition into:
2 GB SWAP - I have 4 GB RAM in my system.
18 GB /home
10 GB /root

Can anyone help me? I'm not too familiar with how partitioning works, but I know I cannot make another primary partition, and Ubuntu won't let me resize it's partition. Is what I want to do even possible?

THANK YOU!

---

### Post by taurus on 2009-03-06
Nope.  You already have 4 primary partitions so you need to make one of those into extended partition first.  Then, you can create logical partitions under that extended partition.  As of right now, there is nothing you can do unless you 

1.  trash windows 7,
2.  trash windows vista,
3.  or trash Ubuntu and start it over again.

---

### Post by inspirations365 on 2009-03-06
Let's say I was willing to start Ubutnu all over again. How would I go about accomplishing my goal with this?

---

### Post by taurus on 2009-03-06
Assuming Ubuntu used to be on /dev/sda4 (4th primary).  You need to convert that into extended partition.  Then, create 3 logical partitions: /dev/sda5 (2GB), /dev/sda6 (10GB), & /dev/sda7 (whatever left).  

Then, format /dev/sda5 as swap and both /dev/sda6 & /dev/sda6 as ext3.  You can do all that with gparted from Ubuntu LiveCD.

Then, reinstall Ubuntu and when you get to the partition screen, pick Manual option and mount /dev/sda6 to / and /dev/sda7 to /home.  Format those partitions if you wish.  Don't think you have to do anything with swap partition, /dev/sda5, since the installer should know how to handle it.  Otherwise, mount /dev/sda5 as swap.

---

### Post by inspirations365 on 2009-03-06
So lemme get this right before I go messing up everything I just (!!) got fixed.

I need to:
-Reformat the (current) Ubuntu partition(?)

-Run the LiveCD and convert the 4th partition into an extended partition.
-Make the three seperate partitions.

Okay, question. I had to install Ubuntu from the alternate install CD because the normal one wouldn't work. Can I do this from that one too? And if so, how?

---

### Post by emarkay on 2009-03-06
There's a limit to amount of partitions that can't be changed in PC's that's why there are extended ones.

Using Gparted (make sure you have the latest version ) is the best way to prepare - make sure when installing Ubunutu you remember where you want it.

Why does not the normal install work - are you doing it from the live install of from the initial menu?

---

### Post by inspirations365 on 2009-03-06
I don't know why the LiveCD (nor the GParted Live CD) will work normall on my system. They do not see the partitions for some reason, but the alternate install CD does, so that's what I must use. Is it possible to convert the partition into an extended partition using the alternate install CD? If so, how?

---

### Post by bodhi.zazen on 2009-03-06
> **inspirations365 said:**
> I don't know why the LiveCD (nor the GParted Live CD) will work normall on my system. They do not see the partitions for some reason, but the alternate install CD does, so that's what I must use. Is it possible to convert the partition into an extended partition using the alternate install CD? If so, how?

The alternate CD has an option for manually partitioning. Simply delete partitions then re-create what you are needing. Deleting a partition == lose all data on the partition ;)

---

### Post by taurus on 2009-03-06
Or if you want to use gparted, try the GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

---

### Post by inspirations365 on 2009-03-06
Okay, I almost have all of my questions answered. So I'm trying to convert my Ubuntu partition into an extended one. Will this show up in the installer as a logical drive and not a primary one? I want GRUB to control my OS'es. Where do I install that to?

---

