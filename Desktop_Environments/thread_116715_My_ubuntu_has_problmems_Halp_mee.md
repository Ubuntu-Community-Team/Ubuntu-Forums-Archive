---
title: "My ubuntu has problmems Halp mee"
date: 2006-01-13
forum: Desktop Environments
---

### Post by iraklirost on 2006-01-13
:o when My Ubuntu is rebooting It has some problems:

* starting RAID devices ...
* starting hardware event demoun ....
* Creating Initial dvices nodes ....
*Cheking Roo file system
  /containing a file sistem with errors check forced
Inode 677 ... has imagic flag set

/:UNEXPECTED INCONSISTENCY; Run fsck manually
   (i.e. without -a or -p prtion)


*fsk faild. Pease repari manually and reboot.
*that rhe root file system is currently mounted ready-only. To remount  it read-write.

* #mount  -n -o remount, rw /
 *Contlo-D will exit from the shell and reboot the system

bash. lesspipe: command not found
bhash : dircolors: command not found

root@(none)


*

---

### Post by Xumbi on 2006-01-13
I think we will need more information to help you with this.

* What version of Ubuntu are you running?
* What kind of hardware do you have?  You mentioned RAID, what RAID level are you running, and on how many disks?
* Have you tried running the Ubuntu live CD?

Let us know more so we can help.  :D

---

### Post by iraklirost on 2006-01-13
I have ubuuntu 5.10.6.12
I have ntfs on hda1, and ubuntu one Hda2 and swat on hda5
My hard drive is 20 gb

---

### Post by southernman on 2006-01-13
type in "fsck" enter. (without the quotes)

Just follow along with it and answer "y" each time your prompted, should fix those errors.

---

### Post by iraklirost on 2006-01-14
i wrote command

fsck -y but now I have other problems (Ubuntu still isnot going in the system)


Failed to start X server (your Graphical Interface)

Fatal server error
(cannot open log file "/var/log/Xorg.0.log

---

