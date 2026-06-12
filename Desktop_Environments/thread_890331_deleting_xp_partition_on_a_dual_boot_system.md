---
title: "deleting xp partition on a dual boot system"
date: 2008-08-14
forum: Desktop Environments
---

### Post by jmsgz on 2008-08-14
Re: Deleting Windows Partition
yeah have been watching this discussion and would like to know the following: ,,,because i would like to give the BOOT to XP "no pun intended"!!!!!! [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

am i understanding you folks correcting by paraphrasing that the general procedure for getting rid of the xp portion of a dual boot system is to either

1.) resize the existing ubuntu partition -or-
2.) deleting the existing xp partition - or-
3.) formating the xp partition to linux file type and using it with
the ubuntu system. (is about 20 gig) -or-
4.) if all else fails just reinstall using entire hd???
(doing all of this from live CD, because you cannot
do it while hd is mounted.))????

also where does the dual boot program reside? on the xp or ubuntu side or neither??????? Do i have to worry about it if performing the above less option 4?

thanks in advance jmsgz

data & programs on xp partition are of no further use therefore caution is not required, however, to learn the system more i can mess with it some instead of deleting but was worrying about the boot situation?

---

### Post by jpkotta on 2008-08-15
I would just reformat the XP partition with ext3, add a line to fstab to mount it at boot, and that's it.  IIRC, Windows needs to be on the first partition, and you can only grow the end of a partition (same for an ext3 filesystem), so it's probably not possible to grow the ubuntu partition to make use of the free space.

The boot loader is grub.  It has a small piece that goes in the boot sector, which initializes the HD and finds the menu.lst file in /boot.  That file tells grub what it can boot and how to do it.  So it's mostly on the Linux side.  You don't need to touch grub, but maybe you want to edit /boot/grub/menu.lst and remove the Windows stuff.

---

