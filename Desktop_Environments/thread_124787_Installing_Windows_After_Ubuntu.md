---
title: "Installing Windows After Ubuntu"
date: 2006-02-02
forum: Desktop Environments
---

### Post by nami on 2006-02-02
Hope someone can help me.

I have 3 partitions on my harddrive, 1 = win2k, 2 = winxp, 3 = ubuntu.

After installing ubuntu my winxp stopped working, apparently a file is missing or corrupted and I have tried replacing it from with windows cd but does not make any difference.

So my quesiton is, if I format my winxp partition and then re-install winxp, will my win2k and ubuntu partitions still work?

Please help

---

### Post by taurus on 2006-02-02
Yes, they still work but you can't get back into Ubuntu again since that crappy you call Windows XP will take over the bootloader...  Therefore, you need to re-install GRUB again so you can boot Windows 2000, Windows XP, and Ubuntu!

---

### Post by nami on 2006-02-02
IC!

So how would I install grub again after re-installing windows xp?

Thanks for the advice.

---

### Post by midwinter on 2006-02-02
Here you go:

[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

Good luck :)

---

### Post by nami on 2006-02-02
I'm gonna need the luck!  Thanks! :D

---

### Post by taurus on 2006-02-02
[QUOTE=nami]I'm gonna need the luck!  Thanks! :D[/QUOTE]
You don't need luck.  Just follow the instruction from the link above and you should be fine.  On the other hand, you will need a lot of luck everytime you boot up XP!!!  :twisted:

---

### Post by nami on 2006-02-03
I followed the instructions on that link and I got to a screen where I am supposed to select a partition.  I have no idea which partition Breezy is on?  How do I find out?

---

### Post by finalzero on 2006-02-03
Which OS would normally boot first, Windows 2000 or Windows XP (or better yet, which one did you install first)?

How many partitions does win2k have, how many does winXP have? total those up, then add one more which should be Ubuntu but the best method is to stick the Ubuntu CD in, boot of this and run the setup as normal, when you get to the disk partition bit choose manual partition and you should now see al list of the available partitions.

Good luck,

Fz

---

### Post by Herman on 2006-02-03
> I followed the instructions on that link and I got to a screen where I am supposed to select a partition. I have no idea which partition Breezy is on? How do I find out?If you are still on that screen, you might want to select 'Go Back', and on the Ubuntu Installer Main Menu, scroll down to 'Abort the Installation', you can always exit the installer that way. it will warn you your system might be left in an unusable state, but ignore that. 
Then use some method to find out about your partition numbers. One suggestion would be to boot the Install CD again, and pretend you are doing a regular install, press 'enter', let the installer detect your hardware, and when you get to '[!!] partition disks' make a note (on a peice of paper) what your partitions are. Then choose 'Go Back', and exit through the Ubuntu Installer Main Menu once again.
Another way is to use a live CD of some kind with a utility for looking at your partitions, such as GParted on the 'Breezy' Live CD, or something like that. 
Then try again when ready.
That 'Unofficial Linux Super Grub Disk' under where you were looking on that Wiki page looks interesting.     :-D (Herman)

---

### Post by nami on 2006-02-03
On the partition screen it gaves options like

part0disk0
part1disk0
part2disk0
.
.
part0disk1

I have the following screenshot from PartitionMagic

[[IMG]http://img52.imageshack.us/img52/8640/partitions0lr.th.jpg[/IMG]](http://img52.imageshack.us/img52/8640/partitions0lr.jpg)

But I don't know how to workout the partXdiskX from that screenshot?

---

### Post by Ramses de Norre on 2006-02-03
From the partitionMagic screen I'd say ubuntu is at part1disk0 (second partition of the first disc, and they seem to count from 0). But I'm not totally sure about the extended part, I don't think it's counted as a partition.
correct me if I'm wrong:)

---

