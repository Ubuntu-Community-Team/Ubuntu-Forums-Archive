---
title: "Problems with Seagate FreeAgent external hard drive"
date: 2008-12-31
forum: General Help
---

### Post by choicefresh on 2008-12-31
A month or so ago, I accidentally caught a virus on Windows. At the time, I was dual-booting Ubuntu 8.04 Hardy Heron and Windows XP Pro SP3.

After a while, my Windows stopped booting up, and I could only get into Ubuntu. Soon after, my GRUB got messed up, so I couldn't get into Ubuntu.

I wanted to backup my things before reinstalling Windows, so I bought a Seagate 1TB external hard drive and booted into an Ubuntu 8.10 Intrepid Ibex LiveCD. After a little bit of fiddling, I moved some files onto the drive. However, when testing to make sure it worked on a different computer running Windows, it said that it was not formatted, so since I still hadn't reinstalled, I formatted it to NTFS using Windows. However, when plugging it in through USB, GParted doesn't assign a partition to it, so I can't mount it. Can someone help me with this?

Thank you,
Choicefresh

---

### Post by bumanie on 2008-12-31
It is likely that your windows drive can be made bootable again and grub should be able to be fixed. Can you post the output of > sudo fdisk -l off a live cd

---

### Post by choicefresh on 2008-12-31
In case your curious, [this is where I was asking for help about the virus.]("http://forums.techguy.org/malware-removal-hijackthis-logs/777972-easydecrypter-trojan-dnschanger.html")

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           8        7743    62139420    7  HPFS/NTFS


I believe that is my Windows partition.

---

### Post by bumanie on 2008-12-31
Just wanted to check your partitions. You are right that is windows. Was the usb external drive plugged in when you did sudo fdisk -l? After formatting, did you remove the drive via 'safely remove device' or just unplug it? If you just unplugged it, any linux based system will see the drive as active, although usually it will still give a partition designation with a trinagle and exclamation symbol indocating the drivev/filesystem is still active.

PS:If you are not aware gparted names drives differently than windows does - your internal drive would probably be /dev/sda and the external /dev/sdb - just in case you were expecting to see c:\ or d:\

---

### Post by choicefresh on 2008-12-31
It was plugged in. While I tried to find a place where I could safely eject the external hard drive, there was no "eject" on the right-click menu or anything, so I just unplugged it.

---

### Post by choicefresh on 2009-01-02
Do you have any suggestions, or should I just FTP the backup to a different computer, and then reformat and work on it?

---

