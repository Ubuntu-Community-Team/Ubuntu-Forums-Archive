---
title: "grub rescue after deleting Ubuntu partition through Windows 8"
date: 2014-04-17
forum: Debian
---

### Post by Cameron_Kidman on 2014-04-17
Hey all, I'm kinda stuck. I know what I did, I just don't know how to fix it. I've dug around a little and tried the automatic settings with boot-repair and it gave me this file:  [http://paste.ubuntu.com/7272556/](http://paste.ubuntu.com/7272556/)

I deleted the ubuntu partition (or what I thought was the ubuntu partition) and it seems to have taken the Windows rescue partition with it... I don't want to pay Acer $50 for the OEM install files if I can avoid it, so I'm trying to fix my issue here. 

After running the boot-rescue, now when I start up (using the Windows Boot Manager as the boot device and UEFI enabled), it just sits on the "acer" screen and spins, can't really tell if anything is happening. 

Looking to sell the computer tomorrow to a windows user, so I would love to get some help! :(

---

### Post by oldfred on 2014-04-17
Moved to Other OS since just Windows issue.

UEFI computers boot from the efi partition. 
BIOS computers boot from MBR or first sector of hard drive, and then with a Windows type boot loader it searches for the NTFS partition with the boot flag to find a bootable system.

But it looks like you have an UEFI system, but have boot flag on the main Windows partition, more like a BIOS boot.

Use gparted or Windows tools to move boot flag to the real efi partition or sda2 from sda4. You can only have one efi partition per hard drive. (or with BIOS one primary partition with boot flag).

Then you should be able to choose the Windows boot loader in the UEFI to boot Windows.

---

