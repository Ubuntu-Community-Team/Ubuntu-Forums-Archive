---
title: "Not able to hide a partition with gparted"
date: 2009-03-08
forum: General Help
---

### Post by WebBuddha on 2009-03-08
Hi There,

I want to install Vista in some free space on my harddisk, so I want to hide my ubuntu partition with an live-cd and gparted.
I've selected the partition and tried to set is as hidden, but this will not be recognized.
What could be the problem?

Thanks in advance
WebBuddha

---

### Post by hexanol on 2009-03-08
Well, there's no problem of installing Vista if Ubuntu is already installed. No need to "hide" your Ubuntu partition. And normally, the only thing "hiding" does is it changes the partition type. This works only on some partition type.

---

### Post by WebBuddha on 2009-03-08
well the "hide" option is not working on my ext partition.
If I installed vista, without to hide the partition, on the free space, the ubuntu partition will not be recognized as extended any more.

sorry for my bad english ;-)

---

### Post by taurus on 2009-03-08
Windows will never recognize ext3 (or anything that is not fat32/ntfs filesystem) so who cares.

Just install windows on that free space and of course, you will not be able to boot Ubuntu anymore since windows will overwrite your GRUB on MBR.  Therefore, you need to reinstall GRUB to MBR if you want to boot both Ubuntu and windows.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by hexanol on 2009-03-08
Hum... well, Vista normally doesn't mess with your other partitions when you install it, so I'm not sure to understand what you mean. There's no need to "hide" anything. Just create a primary partition for Vista from gparted, then install Vista in this partition and everything will be fine (note that Vista will rewrite your MBR, but that's another (easy to solve) story).

---

### Post by WebBuddha on 2009-03-08
ok, I will give it a try again.

---

### Post by WebBuddha on 2009-03-08
ok, after installing vista and booting the ubuntu live-cd, I've startet gparted and my ubuntu partition is shown as unallocated.
So something went wrong, right?

---

### Post by meierfra. on 2009-03-08
Sometimes Windows  messes up the partition table slightly. Boot from the  Ubuntu LiveCD, open a terminal and post the output of

```
sudo fdisk -lu
sudo sfdisk -d
```

---

### Post by WebBuddha on 2009-03-09
that's exactly what it looks like.
I solved the problem other way ;-)
I did an Acronis backup and restored the Ubuntu partition after the Vista installation.
One more entry in the menu.lst and both works.
Thanks for all your help.

Regards
WebBuddha

---

### Post by meierfra. on 2009-03-09
> I solved the problem other way

Good news. Have fun  with Ubuntu and Vista.

---

