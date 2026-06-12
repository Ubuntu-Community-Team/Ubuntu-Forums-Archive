---
title: "Samba thread (yet another)"
date: 2006-08-15
forum: Desktop Environments
---

### Post by hegleran on 2006-08-15
Well I've spent the past couple of hours reading and playing with Samba in xubuntu and I'm stumped.  My network consists of my xubuntu machine, an xp pro machine, and an xp home machine.  I can browse files between the two xp machines no prob - from pro to home, and from home to pro.  I can browse the share on the home pc from the ubuntu box with no problem.  I cannot browse the pro machine from the ubuntu box.  I don't care about browsing files on the ubuntu machine from an xp machine.  I basically want to be able to browse files located on the pro machine on the ubuntu machine, and can't.  When I open xfsamba4 and double click on my workgroup (yes all machines are on the same workgroup), it queries and finds the home machine only.  I've tried disabling the computer browser service on the pro machine as outlined in a previous thread and that did nothing.  I've got no password on the pro machine, and both the pro machine and the ubuntu machine have the same username, obviously different hostnames.  Both XP machines are NTFS.

So long story short:
why can I browse xp home's files on ubuntu, but not even see the pro machine in xfsamba4, let alone browse it?  I've checked file sharing in pro, and I have a directory on my d drive shared as read only.

Also, when I do a sudo smbclient -U (username) -L (hostname of pro machine)I can see the share listed with the folder name, type DISK, comment (none)


Any help would be greatly appreciated.

-Andy

---

### Post by maniacmusician on 2006-08-15
why don't you just mount them using fstab? though i recommend using cifs instead of samba, as it is the up and coming transfer protocol, and is slowly replacing smbfs. people are finding it more efficient: [http://ubuntuforums.org/showthread.php?t=148519](http://ubuntuforums.org/showthread.php?t=148519)

heres's a howto:
[http://ubuntuforums.org/showthread.php?t=128873](http://ubuntuforums.org/showthread.php?t=128873)

---

### Post by hegleran on 2006-08-15
Well I was able to manually mount the filesystem so now I'll just add the mount to fstab so I can have it mount upon boot.  That definitely solves my problem, thanks.  I still find it strange though I can browse my xp home share but not my xp pro share via xfsamba4 - definately more than one way to skin a cat though.

---

