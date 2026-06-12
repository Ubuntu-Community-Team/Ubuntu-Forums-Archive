---
title: "NTFS Partition Gone - help!"
date: 2006-01-07
forum: General Help
---

### Post by M4v3R on 2006-01-07
Hello all,
I tried to install Ubuntu a few weeks ago. I made a 5 Gig partition for it and everything was fine. So now I tried to resize my NTFS Partition (Which was 65 Gig large, it was 2nd NTFS Partition on this drive only for my data, first was main Windows partition, 5 Gig). And this is where my problems started. I booted up 5.10 Live CD, run GParted and told it to resize NTFS Data Partition to 20 Gig and make new linux Ext3 partition. I hit apply and some warning popped that changes was made on a busy device and now I have to reboot system. But something strange happened - the whole graph of my disk just dissapeared and it was all 'Unformatted'. When I rebooted machine, my Data partition was gone. It was there, but it says 'Unformatted'. I tried various ways to rescue it, with no luck. It seems that the partition table is corrupted. I have many very important things there and I don't feel loosing this 20 Gigs of data. 

Here's a little diagram of my disk:

- NTFS System Partition (5 Gig, /dev/sda1)
- Unknown (20 Gig, my data partition, /dev/sda7) <-- corrupted one, was ntfs
- Linux (5 Gig, /dev/sda3)
- Unknown (40 Gig, meant to be linux, /dev/sda6)
- Linux Swap (267 Mb, /dev/sda5)

Anyone can help me with this ?

---

### Post by le_jawa on 2006-01-07
Ouch.
To the best of my knowledge, your options are pretty limited, but you do have some.

1.)  If you have access to Partition Magic, use its partition table editor to directly edit your partition and redefine the system on it.  If that partition ever had it's own filesystem built, that should resurrect it.  Just be careful with that program; it can be dangerous.

2.) Buy some recovery software and recover your data.  There are lots of good packages for NTFS recoveries.

3.)  Send your drive off to a data recovery service.

I'm afraid that's all I see, though someone else here may have some additional thoughts.  In any case, good luck!

---

### Post by aysiu on 2006-01-07
Well, it's either one of two things: 1. GParted is displaying your partition table incorrectly. 2. You somehow accidentally reformatted your entire hard drive.

Can you boot the live CD and open a terminal and then post the output of ```
sudo fdisk -l
```?

---

### Post by M4v3R on 2006-01-07
Now I did even worse. In order to do anything I tried a program called "TestDisk". It found something, even restored label ("Data") from my partition. But when I rebooted the system...

> 
GRUB loading, please wait...

Error 17

---

### Post by Sef on 2006-01-08
This is taken from the Gentoo site:

> Grub Error 17

Situation

Code Listing 5.1: Grub Output

root (hd0,0)
filesystem type unknown partition type 0x7

Error 17 : Cannot mount selected partition

Solution

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

Be sure to check your root(x,y) settings in your grub.conf. 

Also, if you are trying to boot Windows, make sure that your grub.conf file has the root (hdX,Y) (or rootnoverify (hdX,Y)) and chainloader (hdX,Y)+1 in it.

[http://www.gentoo.org/doc/en/grub-error-guide.xml]("http://www.gentoo.org/doc/en/grub-error-guide.xml")

---

### Post by slux on 2006-01-08
Testdisk probably got your NTFS back then but you somehow broke the Linux one. Possibly because you restored the original full-size windows partition and the two overlap? Then you need to either make them coexist again or backup one of them somewhere else and repartition that one.

---

