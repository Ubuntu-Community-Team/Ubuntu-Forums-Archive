---
title: "Installing windows xp after installing ubuntu"
date: 2008-12-05
forum: General Help
---

### Post by siuchi on 2008-12-05
I have ubuntu 8.04 installed on my machine.  And i want to install windows XP in the same machine for some reason.  I dun want to use VM to install the windows.

How can i do so? Any how-to or step by step can help?

Thanks,

---

### Post by taurus on 2008-12-05
You need to boot your machine with the LiveCD.  Then, use gparted in System -> Administration and resize your harddrive, leaving room at the beginning for windows.  Now, create a partition (it has to be a primary since windows doesn't work well with a logical partition) with that unallocated space and format that to ntfs filesystem.  Then, reboot with windows CD in the drive and install it on that new partition. 

And of course, windows will overwrite GRUB from MBR so you won't be able to boot Ubuntu again so you need to reinstall GRUB after you've finished installing windows.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

p.s.  ALWAYS backup important files first before you do any resizing.

---

### Post by singedwings on 2008-12-05
A simple way to do this is to have a separate hard disk. Unplug the ubuntu hd, install win to new hd. Plug in the ubuntu hd, point you bios to boot from the ubuntu hd. Edit  /boot/grub/menu.lst to add the windows drive.

---

### Post by siuchi on 2008-12-06
> **taurus said:**
> You need to boot your machine with the LiveCD.  Then, use gparted in System -> Administration and resize your harddrive, leaving room at the beginning for windows.  Now, create a partition (it has to be a primary since windows doesn't work well with a logical partition) with that unallocated space and format that to ntfs filesystem.  Then, reboot with windows CD in the drive and install it on that new partition. 

And of course, windows will overwrite GRUB from MBR so you won't be able to boot Ubuntu again so you need to reinstall GRUB after you've finished installing windows.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

p.s.  ALWAYS backup important files first before you do any resizing.

Is there any guild for me to following on partitioning the hard disk for my purpose?

Singedwings: Its a laptop, so i can't install another hard disk on it

Thanks

---

