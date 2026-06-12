---
title: "Unable to Dual Boot Xubuntu 16.04.1 with Windows 7 using EasyBCD.."
date: 2017-02-04
forum: Desktop Environments
---

### Post by anxiouslelimo on 2017-02-04
**kernel panic-not syncing: VFS: unable to mount root fs on unknown block(0,0). I get this error trying to boot.**

Since MBR is used instead of grub, I don't know if that is the issue. But I guess, it's not. Because after adding EasyBCD entry I'm able to get into grub. When I select Ubuntu or Advanced Options for Ubuntu first it came up with cannot read or write outside of hd(0). I've installed ubuntu /boot partition on sda9 and selected it as boot loader location while installing. sda10 is swap and sda11 is /root. 
If I press enter it goes back to grub menu and upon selecting Ubuntu again........ kernel panic- not syncing: VFS: unable to mount root fs on unknown block(0,0)... error is shown. 

Its a 10 year old desktop with BIOS support.

Please Help. :(

---

### Post by oldfred on 2017-02-04
EasyBCD uses the very old grub4dos which is based on grub legacy, not grub2.
And that may be the issue.

Do you have AHCI on in BIOS? That can be an issue as old IDE setting emulates IDE. And some IDE did not boot anything on a drive beyond 137GB. 
But should not be an issue with newer systems that have AHCI.

If you install grub to MBR does system boot ok?

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Also grub2 does not recommend installs to PBR partition boot sector. It has to convert to blocklists which are unreliable.
EasyBCD's grub4dos requires chainloading to Ubuntu's grub2 in PBR to work.

---

### Post by anxiouslelimo on 2017-02-05
I got it working. I still dont know if this got it working. Before creating livecd I formatted usb to fat32 and used Universal USB Installer to create live cd. previously I tried Rufus. May be a bad block sector error in USB created the problem.

---

### Post by anxiouslelimo on 2017-02-05
Thank You for the reply oldfred. I will mark this solved

---

