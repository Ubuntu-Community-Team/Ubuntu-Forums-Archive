---
title: "GRUB install failure on Dell XPS 8300 Raid 0"
date: 2012-06-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by webgeeze on 2012-06-12
Hi guys/gals

a bit of help please, from the knowledgeable community would save me pulling even more clumps of hair out .....

I have a Dell XPS 8300 running windows 7 (64 bit) and it's configured with Raid 0 on 2 x 1GB drives. It's fast on windows 7 which i prefer to all the other versions of windows, but I have ubuntu on many other machines and want it to dual boot on this one. Problem is, the RAID partition.

I have attempted install from USB drive and it fails when installing the boot loader. I know this is to do with GRUB loader assuming it's not raid and i have seen another post on here to install grub on the raid partition. Trouble is, it's not clear what's what.

ls /dev/mapper shows this

ubuntu@ubuntu:~$ ls /dev/mapper
control                  isw_dgjhgdjdjd_ARRAY0p2  isw_dgjhgdjdjd_ARRAY0p5
isw_dgjhgdjdjd_ARRAY0    isw_dgjhgdjdjd_ARRAY0p3  isw_dgjhgdjdjd_ARRAY0p6
isw_dgjhgdjdjd_ARRAY0p1  isw_dgjhgdjdjd_ARRAY0p4
ubuntu@ubuntu:~$ ^C

in gparted i have

/dev/mapper/isw_dgjhgdjdjd_ARRAY0 = 1.82 TiB

/dev/mapper/isw_dgjhgdjdjd_ARRAY0p3 = 940.81 GiB
/dev/mapper/isw_dgjhgdjdjd_ARRAY0p6 = 903.81 GiB

/dev/mapper/isw_dgjhgdjdjd_ARRAY0p1 (fat16) DellUtility 170mb used
/dev/mapper/isw_dgjhgdjdjd_ARRAY0p2 (ntfs) RECOVERY
/dev/mapper/isw_dgjhgdjdjd_ARRAY0p3 (ntfs) OS (windows 7)
/dev/mapper/isw_dgjhgdjdjd_ARRAY0p4 (extended) 
/dev/mapper/isw_dgjhgdjdjd_ARRAY0p6 (ext4) 
/dev/mapper/isw_dgjhgdjdjd_ARRAY0p5 (linux-swap)

can you some kind person with a few minutes spare, give me some instructions on hoe to install this without blowing up my windows 7 installing please :-)

regards
justin

---

### Post by webgeeze on 2012-06-12
Update:

[http://paste.ubuntu.com/1036985/](http://paste.ubuntu.com/1036985/)

seems my problem is to do with 

/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.

---

### Post by VorobejPapa on 2012-06-15
The host is OK
 I have like 3 forums running on it and one site. No Problems 
I dont think this error can come from permissions?

---

### Post by YannBuntu on 2012-07-04
> **webgeeze said:**
> Update:

[http://paste.ubuntu.com/1036985/](http://paste.ubuntu.com/1036985/)

seems my problem is to do with 

/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.

Hello
Did you manage to solve your problem?

---

### Post by masuch on 2012-10-14
I have solved it by:

[http://ubuntuforums.org/showthread.php?t=1661254]("http://ubuntuforums.org/showthread.php?t=1661254")

OR 

use gdisk advance options to rewrite MBR (which I am using preferably)

where did you get flexnet ? From Adobe installed software on windows (even trial version), like me ?

---

