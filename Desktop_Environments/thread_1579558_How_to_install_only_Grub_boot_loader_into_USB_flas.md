---
title: "How to install only Grub boot loader into USB flashdisk?"
date: 2010-09-22
forum: Desktop Environments
---

### Post by rudysuryanto on 2010-09-22
Dear all, I want to install only Grub boot loader into USB flashdisk, and I want to boot ISO file bootable from USB external harddisk, use grub boot loader from USB flashdisk, how to do it? Thank's.

---

### Post by sikander3786 on 2010-09-22
See these links.

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Which ISO you want to boot by using Grub? Are you sure Grub will be able to boot it?

---

### Post by rudysuryanto on 2010-09-22
I read at this:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

that grub 2 can booting ISO from harddisk, but I want to use external harddisk to boot ISO file backup of Ubuntu that have been made by remastersys,

---

### Post by LinuxPhreak on 2010-09-22
> **rudysuryanto said:**
> I read at this:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

that grub 2 can booting ISO from harddisk, but I want to use external harddisk to boot ISO file backup of Ubuntu that have been made by remastersys,

```

menuentry "Try MyRemix 32-bit" {
set isofile="/boot/myremix/myremix-1.0.iso"
loopback loop /boot/myremix/myremix-1.0.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/myremix/myremix-1.0.iso --
initrd (loop)/casper/initrd.gz
}

##Notice that in the following section I added the only-ubiquity part. This will only boot 
##ubiquity. You can't make a KIOSK of other programs like this though.

menuentry "Install MyRemix 32-bit" {
set isofile="/boot/myremix/myremix-1.0.iso"
loopback loop /boot/myremix/myremix-1.0.iso
linux (loop)/casper/vmlinuz boot=casper only-ubiquity iso-scan/filename=/boot/myremix/myremix-1.0.iso --
initrd (loop)/casper/initrd.gz
}

```
If your initrd file is has lz extension replace that. However I noticed you said your using remastersys which use the gz. 

It is worth mentionong a few things. According to the Grub community GRUB2 doesn't support all ISO images. They even state this on their freenode IRC channel. However alot of Debian baseds distros GRUB2 does support. 

Another thing to mention is that if you need support for GRUB the GRUB community has stopped giving support for older versions of GRUB and only offer support for GRUB2.

---

