---
title: "Issues after using boot repair"
date: 2011-12-28
forum: Desktop Environments
---

### Post by avimanyu786 on 2011-12-28
Acer laptop had windows xp and ubuntu. The windows partition was reformatted and reinstalled due to which the grub loader was lost and windows was the only OS that booted.

To restore the grub loader, I used the live ubuntu cd and installed & ran boot repair([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair))

Boot repair automatically created the following URL for future reference:

[http://paste.ubuntu.com/777523](http://paste.ubuntu.com/777523)

The grub bootloader was restored.

But some new issues arose:

1. After selecting ubuntu in the grub menu the following error was displayed:

resume:  libgcrypt  Version 1.2.3
resume:  Could not stat the resume device file
resume:  Please type in the file name and try again
               or press Enter to boot the system

Pressing enter boots the system.

Wrong entry found in fstab(swap should be /dev/sda5 and not as /dev/sda6) - changed.

Uninstalled uswususp and reinstalled it. Issue fixed.

2. Other partitions do not get automounted. 

     Installed pysdm to reconfigure other 2 partitions (1.ntfs-windows and 2.ntfs-containing files) to append /etc/fstab

     Issue fixed.

3. Usb drives and cd/dvd rom do not automount when inserted.They can be manually mounted.

tried gconf-editor in nautilus preferences - automount options are already checked.

Is there any rule missing in udev? 

How to fix the 3rd issue? Please help!

---

