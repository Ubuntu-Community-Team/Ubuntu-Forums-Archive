---
title: "Needs to ship with a graphica partition manager"
date: 2010-12-02
forum: Desktop Environments
---

### Post by yyyc186 on 2010-12-02
I was royally burned by this today.  The KUbuntu live-CDs don't ship with a graphical partition manager, either KDE Partition manager or GParted.  I had to scrounge around and deal with an icky nasty Gnome interface today when moving to a 1.5TB drive.

---

### Post by a-user on 2010-12-02
so you actually HAD a graphical partition manager? then what's the fuzz all about?

---

### Post by mardukvmbc on 2010-12-02
Had the same issue... you have to install gparted or something similar. Unfortunate that they weren't included, I second including them. If you're trying to repair a system quite often it's not on-line.

---

### Post by oldfred on 2010-12-02
The default install is just / and swap. You cannot use gparted on the partition you are running from so you cannot use gparted on the default install. 

But I do not have a default install so one of the first things I download is gparted. Even if I just want to view my mounted partitions I like to have gparted installed. 

But gparted is just one of many apps that I want and a CD can only hold so much, so not everything is on the install CD. Since I do clean installs, I created a small bash file with the apt-get install lines to install several additional apps that I always want to install.

I also have gparted, system rescue and several other emergency type ISO set up to loop mount from a USB drive and some times now copy to a CD. I used to just use CDs but found the flash allows me to stay more current without having to use so many CDs.

---

### Post by efflandt on 2010-12-02
A simple solution is System > Administration > Startup Disk Creator to create a bootable iso on USB memory stick (or any flash memory like SD or even microSD on a USB card reader).  If you include persistent data (which is a loop mounted casper-rw file) you can add programs.  Just do not try installing video drivers or updates for anything related to booting (kernels, etc.) because that is fixed in a squashfs file system that runs before persistent data is mounted.

Or a regular install to USB flash or hard drive can come in handy.  When a Win program stepped on grub2 in my mbr I used grub2 on a USB hard to boot Ubuntu on my internal hard drive, which made it easy to install grub to a primary Linux partition instead of the mbr.  Then I used a Windows disk to repair the mbr, then gparted to mark the partition with grub as the boot partition.  No more worries about Windows programs storing data in what they "think" is an unused part of the mbr.

---

