---
title: "Hello All from ubuntu gnubie"
date: 2006-01-02
forum: Desktop Environments
---

### Post by edwardcating on 2006-01-02
I have been prowling the posts for a few days, and have to say that the overall level of civility on ubuntu forums is gratifying.

Please bear with me while I explain my problem:

I have installed ubuntu on a Toshiba Satellite laptop and a Sony Vaio (P3, 512MB Ram, Nvidia) without any hitches whatsoever. The experience proved the worth of the slogan "it just works". I am dual-booting on both machines with WinXP in separate partitions on the same HD. I am locked into dual-boot because I require Photoshop CS2 for high-end raw file editing (Gimp is still 8-bit, unfortunately) and I run an Epson Stylus Pro 4800 printer for which there is no gimp-print/cups solution, yet. This is at work, where second hard drives and partitioning software availability is not an issue.

However, I have run into a problem on a new family computer at home. Since I often work on projects there, I need the Photoshop capability. My daughter is using Dreamweaver for a class in school. Unfortunately, the new Dell machine we got does not have OS disks or even the ability to make a backup set! After an hour and a half with Dell tech support, I finally got them to send out WinXP install CDs. But I am still not sure that even a clean XP install will give me the option to partition the disk in a way that will be very useful for running XP and ubuntu in a dual boot configuration. I don't own a copy of Partition Magic and I don't want to shell out the bucks to buy it, either. I would really prefer not to have to buy a second hard drive. Money is tight.

Can anyone tell me where to get a freeware partitoning utility that will operate on the primary partition on which the OS is installed? So far all I have found have a limitation in this regard or else they won't downsize a NTFS partition. If I can simply repartition the drive, ubuntu is a go, if not, I'm not going to be able to use it at home.

Any help on this would be VERY much appreciated.

I hope everyone had a happy New Year and that 2006 brings good things to all!

---

### Post by dcstar on 2006-01-02
[QUOTE=edwardcating]
....... But I am still not sure that even a clean XP install will give me the option to partition the disk in a way that will be very useful for running XP and ubuntu in a dual boot configuration. I don't own a copy of Partition Magic and I don't want to shell out the bucks to buy it, either. I would really prefer not to have to buy a second hard drive. Money is tight.
.......[/QUOTE]
You should be able to re-install XP and specify the partition sizes you want, but I would suggest the following (since you are looking at re-installing XP anyway):

[LIST=1]
[*]Save all of your existing XP data.
[*]Install Ubuntu and wipe out the existing XP disk - but manually reserve space on the disk for XP.
[*]Install XP on the reserved space after Ubuntu is installed and running.
[*]Edit the Ubuntu Grub boot manager to give you the XP boot option.
[/LIST]
I suggest installing Ubuntu first because any boot manager needs to be at the start of your disk, and if you install XP first that area may not be available for the boot manager.

---

### Post by JamesNorris on 2006-01-02
You shouldn't need to intall xp before you can parition the drive. Your ubuntu CD will partition the hard drive as one of the stages of install. If the non-gui-ness of it scares you (like it used to scare me) one option, that I always used until recently, was to keep a copy of Mandrake Linux on CD with me, and use DiskDrak (I think) which would partiton your drive before the installation, and just quit before you get to the installation. It's a bit convoluted, but I don;t know of any other graphical partitioning method without buying Partition Magic.

Unless you format your HDD as FAT32 before you install XP and then resize that one later? XP will install on FAt32, and it makes filehsaring between the two OSes easier, too.

---

### Post by Lord Illidan on 2006-01-02
Install XP first. Otherwise, you will run into a whole set of problems which might be hard to solve.

If XP is already installed, then use the Ubuntu or Mandriva Installer to resize the NTFS partition (make sure you defragment and preferably make a backup beforehand.)
Then install Ubuntu.

This should work. I have done it on 3 computers on the same harddisk with different distros, and no problems as yet. Just take it easy.. and make sure the right options are selected before pressing ok.

---

### Post by edwardcating on 2006-01-02
[QUOTE=Lord Illidan]Install XP first. Otherwise, you will run into a whole set of problems which might be hard to solve.

If XP is already installed, then use the Ubuntu or Mandriva Installer to resize the NTFS partition (make sure you defragment and preferably make a backup beforehand.)
Then install Ubuntu.

This should work. I have done it on 3 computers on the same harddisk with different distros, and no problems as yet. Just take it easy.. and make sure the right options are selected before pressing ok.[/QUOTE]


Thank you for the reply; it gives me hope. I did not realize that the ubuntu installer could resize the NTFS partition. I only recall there being options to erase and install on HDA (or LVM) and then there is the manual option, but I thought that would erase the entire disk. I'll give it a second go - maybe it's all under the hood, after all. Thank you.

---

### Post by Lord Illidan on 2006-01-02
Yes, it is under the manual option.
Good luck!

---

### Post by sawjew on 2006-01-02
There is another option which I have used if you prefer to use a gui partitioner.  If you have the Ubuntu live cd just boot from that and use Gparted to change your partitions in whatever way you prefer.  Just make sure you backup any data on your hard drive and defragment Windows first.  

Good luck.

---

