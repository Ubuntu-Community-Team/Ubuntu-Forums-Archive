---
title: "windows has corrupted ubuntu!?"
date: 2009-04-06
forum: General Help
---

### Post by Hellstudios on 2009-04-06
I just recently made a windows XP pro CD, made a 25GB partition for it to run on, installed it, then, wondering why a menu didn't come out to ask which OS I wanted to boot from(went automatically to XP) I started to get worried, after installing Steam and download TF2 I popped in my ubuntu live CD, rebooted from my CD drive, then went into gparted and checked to see if my 50GB partition of ubuntu is still there, it was, so I edited it's flag to "boot", took out the live CD, rebooted, then this error came up

"error loading operating system"

I tried going into gparted with my live CD and scanning for problems but it says there is none. now I ask of you, is it possible to get all my programs, pictures, mozilla preferences i.e. passwords bookmarks, and other stuff from it or is it completely gone????

Thanks for your time,
Hellstudios

---

### Post by Hellstudios on 2009-04-06
Sorry for the double post but this is what happened when I did "sudo fdisk -l"


Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6361    51094701   83  Linux
/dev/sdb2   *        6375        9566    25639740    7  HPFS/NTFS
/dev/sdb3            9567        9729     1309297+   5  Extended
/dev/sdb5            9567        9729     1309266   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System

---

### Post by Hendronicus on 2009-04-06
You can use your Ubuntu Live CD to restore GRUB and it should pick up your new Windows partition as well. Here's the link:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by ryanhaigh on 2009-04-06
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

EDIT: too slow, boo for me, yay for ubuntuforums

---

### Post by Hellstudios on 2009-04-06
oh my god thank you! I wish I could pay you! :D


I'll bump if this works. rebooting now.

---

