---
title: "In desperate need of an expert! - &quot;Error 29: Disk write error&quot;"
date: 2007-08-08
forum: Dell  Ubuntu Support
---

### Post by Kemrin on 2007-08-08
Hello, and welcome to completely broken theater. Today I'll be telling you the tale of the little laptop that couldn't.

I am working on a Dell Insperon E1505. It is a Dual Boot with Ubuntu 7.04 and Windows XP Home second edition. It comes up to the grub menu, but when you select any option but Ubuntu recovery mode it gives "Error 29: Disk write error" If you enter the recovery mode, it goes through a long drawn out process were it lists hundreds of processes, but ultimately still fails to start. I went to the build in Diagnostic's program, and it gives me a Failed on the "DTS short test" but passes everything else. I dont know how the laptop got this way, it was brought to me by a friend who wants me to fix it... but I dont really even know what it's problem is! Please help.

---

### Post by MikeEvans on 2007-08-08
from **[http://ubuntuforums.org/showthread.php?t=417908]("http://ubuntuforums.org/showthread.php?t=417908")**

> I got the same problem (ERROR 29: Disk write error) after I installed ubuntu feisty to dual boot with Windows XP Professional. I tried all advice from above but nothing worked. After a lot of work I finally made it work!!!

Here is how:

Find out on WHICH hd and WHICH partition windows is installed on (usually hd0,0) then edit the /boot/grub/menu.lst file by using sudo gedit /boot/grub/menu.lst

find the part were it says (or equivalent) :

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional

and then enter the following:

rootnoverify (hd0,0)
chainloader +1

NOTE : REPLACE the number of the windows partition at rootnoverify (hd0,0). For example if your windows is installed on hd1,0 change it to rootnoverify (hd1,0).
Normally grub would find the correct partition but put root (hd"correct partition for windows") so you only really need to change it from root to rootnoverify

DO NOT!!! leave the makeactive command. That is the main reason we get the error! Linux tries to write on the disk to set is as active but it cannot write on an NTFS disk (M$ sucks...)

Also after you boot in windows it might run chdisk leave it run until it finishes. It only runs once don't worry nothing important just windows being a smart ***

HOPE it works for you 

Any help?

---

### Post by Kemrin on 2007-08-08
I can't use Sudo Gedit, because I can't get into Ubuntu, or linux at all. All I can get into is the grub command prompt, and when I use the find function to seek that file, it says that file doesn't exist. Am I missing something? Is there a way to gedit from the grub menu?

---

### Post by Pinkydead on 2007-08-08
Have you tried booting with a Ubuntu install CD.

That's what I'd do if I had a problem like that - at least you would be able to check if the disk was physically OK.

I also find, using an external USB drive for my OS, that using UIDs to identify disks is a whole lot more effective - as the references don't change later on.

---

### Post by Kemrin on 2007-08-08
Thank you all for trying. I have consulted dell with the stats from the diagnostics failure, and the error message means the hard disk is physically dead. These are the symtoms of a dead hard drive. My only question: Why is the grub still functional? Isn't the grub menu held in the hard drive too? If someone could shed some light on this, I'd be greatful. Thanks.

---

### Post by igor54 on 2007-08-09
If grub still works, the HDD is NOT dead!
Use a Live CD from a magazine or wherever (one that loads into memory, rather than the hard drive. This will (should) mount the other partitions (Win and Linux). Start Gedit on the Lie CD. Find the Linux partition, and navigate to /boot/grub/menu.lst
Carry out MikeEvans' suggestion above, reboot (without the live CD), and all should be sweet!

---

### Post by Kemrin on 2007-08-13
I used a damn small linux live play CD toram, but when I went to mount the hard drives, they all gave error messages. Any more suggestions?

---

