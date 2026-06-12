---
title: "/boot/grub/i386-pc/normal.mod not found. Disk moved from old computer"
date: 2015-11-05
forum: Desktop Environments
---

### Post by dlublink2 on 2015-11-05
Hello,

I just spent a few hours trying to get Ubuntu Mate to run on my "new" i5 Dell Optiplex 990 with UEFI.

The disk I installed in the computer is from an older computer ( don't ask why ). After multiple attempts to reinstall, using various combinations, I always got the message "/boot/grub/i386-pc/normal.mod not found".

After some testing, I discovered that the bios in the machine was a UEFI. The disk had an old dos style partition table. When the Ubuntu installer repartitioned the disk, it kept the dos partition table because that's what was already there.

To work around the problem, I erased EVERYTHING using dd, and the installer succesfully installed Ubuntu and it boots fine now.


WARNING !!!!! The following command will cause loss of data!!! :

1. I booted using a live USB key
2. I opened a terminal and ran mount to see the name of the usb device and used dmesg and ls /dev and disk/dev/sdX to find my hard drive.
3. I ran this command : sudo dd if=/dev/zero of=/dev/sdX bs=1024 count=$((1024*1024))
4. I rebooted
5. I booted the live USB key 
6. I ran the installer.
7. in the UEFI/BIOS screen , I selected 'ubuntu' as the preferred OS to boot
7. Rebooted, the computer works perfectly!

I posted this in case someone else runs into the same issue.

[https://xkcd.com/979/](https://xkcd.com/979/)

---

