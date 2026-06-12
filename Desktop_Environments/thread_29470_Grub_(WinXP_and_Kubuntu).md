---
title: "Grub (WinXP and Kubuntu)"
date: 2005-04-24
forum: Desktop Environments
---

### Post by Coollie on 2005-04-24
Hi all,

I've got the following problem. I have 2 HD's (80 Gbyte - Master on IDE and 20 Gbyte - Slave on IDE). I used Fdisk (Win95) to create 2 partitions (FAT32) on the 80 Gb HD and installed WinXP on the 20Gb HD (NTFS). Windows starts with no problem. All HD's are seen in XP. The next step was to install Kubuntu on the first partition on the 80 Gb HD. I installed Kubuntu on the first partition of this HD with no problem except when i reboot i don't get an option to start WinXP in the GRUB menu. So i tried to manually insert the command lines in de menu.lst. This works but when I tell GRUB to start Windows XP I get the following error:

root (hd0,1) (Linux uses the first HD (hd0,0) and WinXP the second drive)

Filesystem type unknown, partition type 0xf

makeactive

Error 12: Invalid device requested

My own analisis:

As I can imagen, Linux overwrittes the MBR of the first HD. Windows uses the MBR of the first HD to point at the second drive (i think) and so starting WinXP. I've already tried changing the booting order in my Bios with no succes.

Still to try:

Making slave HD into bus Master. Booting from a floppy (Win95) and executing the following command in DOS: Fdisk /MBR. This wil create a new Master Boot Record on the HD. Afterwards switching back the previous situation and boot from linux HD.

Question:

Is ther any other way to correct this?

Greetinz  and thnx in advance :-?

Linux Newbe  :grin:

---

### Post by nad on 2005-04-24
There are several threads here currently discussing issues similar to yours.

Please search and respond to an existing thread that you and others will more easily find and benefit from the total of the community knowledge.

Thank you.

---

### Post by Coollie on 2005-04-24
[QUOTE=nad]There are several threads here currently discussing issues similar to yours.

Please search and respond to an existing thread that you and others will more easily find and benefit from the total of the community knowledge.

Thank you.[/QUOTE]
 Dan,

Thnx for your fast reply. I've checked many other threads on this forum and many other on the net but i've not once encountered similar problems.
Do you have a tread in mind?

Greetinx!

---

### Post by nad on 2005-04-24
Just within the past two days!

[http://www.ubuntuforums.org/showthread.php?t=15934&highlight=xp+grub](http://www.ubuntuforums.org/showthread.php?t=15934&highlight=xp+grub)
[http://www.ubuntuforums.org/showthread.php?t=28669&highlight=xp+grub](http://www.ubuntuforums.org/showthread.php?t=28669&highlight=xp+grub)
[http://www.ubuntuforums.org/showthread.php?t=29401&highlight=xp+grub](http://www.ubuntuforums.org/showthread.php?t=29401&highlight=xp+grub)
[http://www.ubuntuforums.org/showthread.php?t=28776&highlight=xp+grub](http://www.ubuntuforums.org/showthread.php?t=28776&highlight=xp+grub)
[http://www.ubuntuforums.org/showthread.php?t=29274&highlight=xp+grub](http://www.ubuntuforums.org/showthread.php?t=29274&highlight=xp+grub)

---

### Post by dermotti on 2005-04-24
add 

map (hd1)  (hd0)

to the xp boot

---

### Post by Coollie on 2005-04-25
[QUOTE=nad]Just within the past two days!

[http://www.ubuntuforums.org/showthread.php?t=15934&highlight=xp+grub](http://www.ubuntuforums.org/showthread.php?t=15934&highlight=xp+grub)
[http://www.ubuntuforums.org/showthread.php?t=28669&highlight=xp+grub](http://www.ubuntuforums.org/showthread.php?t=28669&highlight=xp+grub)
[http://www.ubuntuforums.org/showthread.php?t=29401&highlight=xp+grub](http://www.ubuntuforums.org/showthread.php?t=29401&highlight=xp+grub)
[http://www.ubuntuforums.org/showthread.php?t=28776&highlight=xp+grub](http://www.ubuntuforums.org/showthread.php?t=28776&highlight=xp+grub)
[http://www.ubuntuforums.org/showthread.php?t=29274&highlight=xp+grub](http://www.ubuntuforums.org/showthread.php?t=29274&highlight=xp+grub)[/QUOTE]
 Dan ... U R the man ...
Thnx for the info. Was looking in the wrong direction!

Greetinx!

Coollie

---

