---
title: "Windows won't boot, says &quot;NTLDR is missing&quot;"
date: 2008-01-06
forum: Desktop Environments
---

### Post by jhvillegas2 on 2008-01-06
I am getting the message "NTLDR is missing".  I have a dual configuration of WinXP Home and Ubuntu 7.10.  What could be causing this?  Your help is greatly appreciated.

jhvillegas2

---

### Post by logos34 on 2008-01-06
Sounds like you get to the grub menu and choose to boot XP and then get the error message.  Right?  Did it just stop working?  

Post the following:

sudo fdisk -l

cat /boot/grub/menu.lst
(just the windows entry at bottom)

---

### Post by jhvillegas2 on 2008-01-06
Here it is.

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29d429d3

	Device 		Boot	Start	End	Blocks		Id	System
	/dev/sda1	*	1	4711	37841076	7	HPFS/NTFS
	/dev/sda2		4712	9729	40307085	f	W95 Ext'd (LBA)
	/dev/sda5		4712	9364	37375191	83	Linux
	/dev/sda6		9365	9729	2931831		82	Linux swap / Solaris

Disk /dev/sdb:  250.0 GB, 250059350016
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

	Device		Boot	Start	End	Blocks		Id	System
	/dev/sdb1		1	15339	123210486	7	HPFS/NTFS
	/dev/sdb2		15340	30401	120985515	f	W95 Ext'd (LBA)
	/dev/sdb5		15340	30481	120985483*	83	Linux
jhvillegas2@jhvillegas2-desktop:~$cat /boot/grub/menu.lst
.
.
.
#This entry automatically added by the Debian installer for a non-linux OS
#on /dev/sda1
title			Microsoft Windows XP Home Edition
root			(hd0.0)
savedefault
makeactive
chainloader		+1

---

### Post by jhvillegas2 on 2008-01-06
You are correct with the process of generating the error.  I don't think I have tried to run the Windows on that box since I installed Ubuntu about a week ago.  For all I know, Ubuntu may have had something to do with it messing up.

Thanks again for your help.

---

### Post by logos34 on 2008-01-07
that root line in windows entry looks funny.  

> root (hd0.0)

Should be a comma separating zeros, not a period.

Do this:

gksudo gedit /boot/grub/menu.lst

Replace the period with a comma.

> root (hd0[COLOR="Red"]**,**[/COLOR]0)

---

### Post by c0met on 2008-01-07
If you go to the below web page and scroll down, you'll find lots of links about GRUB, This guy is especially helpful when it comes to explaining how to set it up. I also suggest that it might be a good idea to get the ISO for SUPERGRUB and burn yourself a bootable CD. That will also help.

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by jhvillegas2 on 2008-01-07
I hate to break this to you, c0met, but the website you listed says very little about the NTLDR.  That is where I am having the problem.  Thanks for the effort.  Do you have any other ideas?

---

### Post by jhvillegas2 on 2008-01-07
Logos34, the period was a typo.  I should have typed the comma instead, as it appears on the screen after the command.  Any other ideas, please?

---

### Post by logos34 on 2008-01-07
if you have xp install cd try booting into recovery console and running **chkdisk /r** and **fixboot**.

[http://www.kellys-korner-xp.com/win_xp_rec.htm](http://www.kellys-korner-xp.com/win_xp_rec.htm)
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixboot.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixboot.mspx)

The problem is on the windows side.  Grub is trying to hand off/chainload the boot process to windows but can't find ntldr.  Hopefully chkdsk will straighten things out (it normally runs first boot into windows after resizing, but you said you didn't).  But it could be anu number of things

---

### Post by logos34 on 2008-01-07
What's on sdb1?  Just an ntfs windows data dump?

---

### Post by c0met on 2008-01-07
Hi jhvillegas2. You must have followed a different link from the one that I took. As mentioned, SuperGRUB looks like it could be useful. Here is the direct URL to that page at the site I gave before.

[[COLOR="RoyalBlue"]**http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html**[/COLOR]]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

If you do a "search" of the page, you'll find a number of references to NTLDR. For example, I have copied the below from about half-way down the page.

> [Super]GRUB helps you
boot your Linux OS,
restore GRUB in a MBR (you can choose which hard disk's MBR too),
install GRUB's IPL to a partition (boot sector),
or
restore NTLDR's IPL in a MBR.

Please read through the page before rushing in an using SuperGRUB, though. There's an ISO of a bootable version of SuperGRUB somewhere at this site. You need to burn a CD of this program and boot from it. Then you can go about restoring what you want to restore. This little program has rescued me a couple of times.

---

### Post by jhvillegas2 on 2008-01-07
sdb1 is just a storage partition

---

### Post by jhvillegas2 on 2008-01-07
the two solution provided above don't work......anything else i could try?

---

