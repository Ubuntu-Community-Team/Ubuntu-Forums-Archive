---
title: "Reinstalling Ubuntu - Partition"
date: 2009-02-04
forum: General Help
---

### Post by draxz on 2009-02-04
Hello,

I had initially installed linux as my main OS by automatically allocating harddisk space for XP (6.5GB). But I logged in to XP for some reason to find free space available for XP is 246MB of 6.5Gb.

I want to reinstall Ubuntu so I can allocate more space for XP (i will use Ubuntu as my primary OS)

Can I boot the live Ubuntu cd and click install and allocate more space for Ubuntu(I dont have any personal data on Ub.)

---

### Post by redilyn on 2009-02-04
Kinda,

Boot from the livecd and then look under System -> Administration for gparted or Partition editor.

From there you can resize - shrink ubuntu and expand the xp partition to whatever size you need.

You should have a backup before attempting such an operation though

---

### Post by draxz on 2009-02-04
> **redilyn said:**
> Kinda,

Boot from the livecd and then look under System -> Administration for gparted or Partition editor.

From there you can resize - shrink ubuntu and expand the xp partition to whatever size you need.

You should have a backup before attempting such an operation though

I am confused now
So I should just run Ubuntu like always then pop in the cd and use gparted or should I restart my laptop with the cd press F12 (if I do this it will show install Ubuntu, check, update etc)

---

### Post by 7mkgw7q on 2009-02-04
Just boot from the cd. When you are in the live version on the cd, use the instructions above. That is probably the best way to do it. Does that make sense?

---

### Post by redilyn on 2009-02-04
You need to restart your computer and boot from the cd.

The ubuntu cd boot menu should have an option to "Try ubuntu with installing". This is the option you want.

From there you can use the partition editor to resize the partition.

---

### Post by draxz on 2009-02-04
I already have UB. installed, I just want to give more space for XP but still partition my OS have linux as my primary OS also keeping XP with minimum space.

Can I booth from CD click install Ubuntu(not try it) and partition it again even though Ubuntu is ready installed

---

### Post by 7mkgw7q on 2009-02-04
You could do that I suppose, but it would be much easier to just tinker with the partitions the way redilyn said. It would take less time and you would not have to start over configuring Unbuntu.

---

### Post by arepaking on 2009-02-04
> **draxz said:**
> I already have UB. installed, I just want to give more space for XP but still partition my OS have linux as my primary OS also keeping XP with minimum space.

Can I booth from CD click install Ubuntu(not try it) and partition it again even though Ubuntu is ready installed

Yes you can. Like our fellas said.

a) Run the LiveCD. When the desktop appears
b) Go to System->Administration->Partition Editor
c) Make your changes
e) Reboot.

---

### Post by draxz on 2009-02-04
A big problem.  I booted from CD and went into desktop and used the editor.

I first reduced the size for linux from 49GB to 46Gb, and i clicked continue and it was does. The 3 GB got created as another parition. So now I have unallocated partition, the linux and Xp
How can I add the unallocated partition to XP and what will happen if I delete the unallocated partition

---

### Post by dox_drum on 2009-02-04
> **draxz said:**
> A big problem.  I booted from CD and went into desktop and used the editor.

I first reduced the size for linux from 49GB to 46Gb, and i clicked continue and it was does. The 3 GB got created as another parition. So now I have unallocated partition, the linux and Xp
How can I add the unallocated partition to XP and what will happen if I delete the unallocated partition

In Windows (if you want it), you can modify  the partition... to be a data backup, or whatever you want. Perhaps you can manage it better, you know, is Windows.

Enjoy!

---

### Post by draxz on 2009-02-04
What happens to the partition I deleted, will the space be added back

---

### Post by 7mkgw7q on 2009-02-04
You can incorporate that into another partition if you want, by growing the partition on the other side of it from Ubuntu. Does that make sense?

---

### Post by draxz on 2009-02-04
It does'nt I am totally new to this. 

How can I add back the unallocated partition to XP or linux

---

### Post by 7mkgw7q on 2009-02-04
Will you pull up the partition editer and upload a screenshot so I can see where the partitions are? I will be able to help you more easily if I can see what I am working with.

---

### Post by draxz on 2009-02-04
here it is , you can see unallocated 1.13GB

The first is the XP and followed by Linux

---

### Post by 7mkgw7q on 2009-02-04
Ok, so tell me what all you have done at this point. I apologize for taking so long to get back with you.

---

### Post by Elfy on 2009-02-05
As it stands you need to do a couple of things in order.

Boot the livecd - start the partition editor and turn off the swap. At the moment your free space is inside the extended partition.

You need to resize the extended partition so that the free space is outside.

Then you need to move the extended partition to the right.

The unallocated space will now be next to the xp partition so you can now resize the xp partition.

Do each of these seperately - use apply after each stage.

This is likely to take a long time to complete - especially the move.

If it was a brand new install with no real work done on it I would thing carefully about that and maybe look at just reinstalling.

Backup any data you can't afford to lose, unless of course you already do :)

---

### Post by draxz on 2009-02-05
Ok this is wht I have done.

I shrink sda5 from the left and shrink sda2 from the left it took 1 hour 30 min for the first one and 2 hours for the second one. Then on sda1 I added the space by moving it to the right. 

Now I have unallocated space of 7 GB 

on my boot screen I see

Ubuntu 8.10, Kernel 2.6.27-11 Generic
Ubuntu 8.10, Kernel 2.6.27-11 Generic - recovery mode

Ubuntu 8.10, Kernel 2.6.27-7 Generic
Ubuntu 8.10, Kernel 2.6.27-7 Generic- recovery mode
ubuntu 8.10 Memtest
other operating system
XP

Is the unallocated space normal and why is it showing other OS

---

### Post by redilyn on 2009-02-05
Okay now resize sda5 to use the extra 7Gb

Its not actually showing another OS but rather Ubuntu 8.10 with a new and older kernel.

The other two are memtest and Windows XP

---

### Post by Elfy on 2009-02-05
> **draxz said:**
> Ok this is wht I have done.

I shrink sda5 from the left and shrink sda2 from the left it took 1 hour 30 min for the first one and 2 hours for the second one. Then on sda1 I added the space by moving it to the right. 

Now I have unallocated space of 7 GB 

on my boot screen I see

Ubuntu 8.10, Kernel 2.6.27-11 Generic
Ubuntu 8.10, Kernel 2.6.27-11 Generic - recovery mode

Ubuntu 8.10, Kernel 2.6.27-7 Generic
Ubuntu 8.10, Kernel 2.6.27-7 Generic- recovery mode
ubuntu 8.10 Memtest
other operating system
XP

Is the unallocated space normal and why is it showing other OS

You have 7Mb unallocated not 7Gb ;)

If by other os you mean

[COLOR="Blue"]other operating system[/COLOR]
XP

then that is fairly normal as XP is just another os to everyone but MS :D

You can lose that from your menu list if you so wish by editing the file 

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
``` to backup and 

```
gksudo gedit boot/grub/menu.lst
``` to edit it - at the bottom you'll see similar to

title 		---Other OS List---
root
 delete both lines

---

### Post by draxz on 2009-02-05
NO. 

it says other operating system    
and then Windows XP
So an extra operating system..

let me add using the livecd. Will post after that

---

### Post by redilyn on 2009-02-05
Other Operating System is just a heading its not actually an operating system

---

### Post by Elfy on 2009-02-05
Xp is the other operating system

the bit that says other operating system is a title

---

### Post by draxz on 2009-02-05
so I dont have to do any thing now. I dont know why the partition editor is not showing up. Guess I will use the gparted live cd to add the addition 7gb to linux or Xp.


so after this am I all set to linux?

---

### Post by Elfy on 2009-02-05
If the gparted screenshot is correct it is 7Mb only - I don't know why you keep saying 7Gb?

But I would say that as it si you have no swap partition.

It should certainly boot now though, might be worth adding a swap partition - use the livecd if you want to do that.

---

### Post by draxz on 2009-02-05
Sorry , I dont know why I kept saying GB.

Do I really need a SWAP partition....

---

### Post by Elfy on 2009-02-05
It's as well to have one - how much RAM do you have?

You could instead create a swap file


Edit - [https://help.ubuntu.com/community/SwapFaq#How](https://help.ubuntu.com/community/SwapFaq#How) do I add more swap?

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by draxz on 2009-02-05
I have a 1GB ram

---

### Post by Elfy on 2009-02-05
Well I have 1.3Gb and swap - often it's untouched - but I have needed it.

I would be inclined to create one - either a partition or a swap file - unless you wnat to hibernate then a partition at least the same size as RAM. 

If you want a prtition then you'll need to do a small resize - I would suggest sda5, resized from left to right then you can use the 7Mb as part of the swap.

Then once you've rebooted you need to add it to fstab so it get's used properly.

---

### Post by draxz on 2009-02-05
If I have a 1 GB ram how much should I create as SWAP.

Most of the time I hibernate, I dont shut down my laptop

---

### Post by Elfy on 2009-02-06
Well if you'd looked at the links you were given you would have seen

> The hibernation feature (suspend-to-disk) writes out the contents of the memory to the swap partition before turning off the machine. Therefore, your swap partition should be _at least_ as big as your RAM size. So a bit more than 1Gb and you'll be fine.

---

