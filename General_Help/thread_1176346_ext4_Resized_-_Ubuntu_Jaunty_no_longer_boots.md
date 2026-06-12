---
title: "ext4 Resized - Ubuntu Jaunty no longer boots"
date: 2009-06-02
forum: General Help
---

### Post by Pooven on 2009-06-02
Hi there,

I've run into a very painful problem that I can't seem to resolve via online support: my machine dual boots between Vista and Ubuntu. I noticed that if Ubuntu access the Windows partition, then Vista no longer boots so I decided to create another partition to store files usable by both Windows and Ubuntu - oh if someone knows how to access Vista via Ubuntu safely, I'd really like to know :)

Anyway, I resized my ext4 partition that stores Ubuntu using a LiveCD (Ubuntu Jaunty). It resized without errors but on reboot Ubuntu no longer boots. A guy had a similar problem: [http://ubuntuforums.org/showthread.php?t=1155907](http://ubuntuforums.org/showthread.php?t=1155907). I tried the suggested steps but to no avail.

The error I get:

> mount: mounting /dev/disk/by-uuid/(a hexadecimal sequence) on root failed: Invalid argument
mount: mounting /dev on root/dev failed: No such file or directory
mount: mounting /sys on root/sys failed: No such file or directory
mount: mounting /proc on root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg

The prompt that comes up has: *(initramfs)*

I also found the site: [https://bugs.launchpad.net/ubuntu/+source/klibc/+bug/309762](https://bugs.launchpad.net/ubuntu/+source/klibc/+bug/309762) but I'm unsure how to proceed based on the information there.

I have no idea what to do, please help :frown:

---

### Post by dcstar on 2009-06-03
> **Pooven said:**
> Hi there,

I've run into a very painful problem that I can't seem to resolve via online support: my machine dual boots between Vista and Ubuntu. I noticed that if Ubuntu access the Windows partition, then Vista no longer boots so I decided to create another partition to store files usable by both Windows and Ubuntu - oh if someone knows how to access Vista via Ubuntu safely, I'd really like to know :)

Anyway, I resized my ext4 partition that stores Ubuntu using a LiveCD (Ubuntu Jaunty). It resized without errors but on reboot Ubuntu no longer boots.
........

From the 9.04 release notes ([http://www.ubuntu.com/getubuntu/releasenotes/904):](http://www.ubuntu.com/getubuntu/releasenotes/904):)

[I][SIZE="4"]Possible data-loss problems resizing ext4[/SIZE]

The resize2fs tool may cause data loss when growing or shrinking ext4 filesystems off-line. [See this mail from the upstream maintainer for more details]("http://article.gmane.org/gmane.comp.file-systems.ext4/12763"). Unfortunately we became aware of this too late to fix it in Ubuntu 9.04. If you wish to resize an ext4 filesystem using the tools in Ubuntu 9.04, you may be able to work around these problems by first disabling the flex_bg and uninit_bg features (do not attempt this on a mounted filesystem!):

tune2fs -O ^flex_bg,^uninit_bg /dev/DEVICE_NAME
e2fsck /dev/DEVICE_NAME

However, we still strongly recommend taking significantly more care with backups than usual before attempting to resize an ext4 filesystem.[/I]

---

### Post by Pooven on 2009-06-03
So it's quite possible that I've indeed incurred data loss? I really should have read the release notes! I just noticed that gparted supported resizing ext4 and thought I'd give it a go - oh well. Thank you for your reply :)

So I should basically reinstall Ubuntu?

---

### Post by Yellow Pasque on 2009-06-03
IIRC, resizing your partition changes the UUID. Did you change the UUID in /etc/fstab and /boot/grub/menu.lst ?

Use a LiveCD, mount your root partiton, and use the following command to get the new UUID:
```
blkid
```

Copy and paste into the aforementioned files.

---

### Post by Pooven on 2009-06-03
I was thinking that perhaps the UUID had to be changed but I had no idea how to do such a thing! So thank you for my alternative to re-installation!! However, the troubling part is that I cannot mount my installed ext4 file system (sda6) while using the LiveCD.

I get the error:
> mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I tried to check the partition for errors using:
> e2fsck -f -y -v /dev/sda6
But I get:
> e2fsck: Group descriptors look bad... trying backup blocks...
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda6: Invalid argument while reading block 8945664

/dev/sda6: Invalid argument reading journal superblock

e2fsck: Invalid argument while checking ext3 journal for /dev/sda6 

I noticed that *e2fsck* identifies the partition as ext3 however *gparted* notices that sda6 (my Ubuntu installation is on this) is ext4, but says that it cannot read the contents of the partition.

So I'm assuming that I'd need to modify the fstab and menu.lst on the actual sda6 file system? Using the LiveCD, won't /boot/grub/menu.lst point to the mounted LiveCD file system?

Your replies that far are really appreciated :)

---

### Post by dr_y on 2009-07-08
I am having the very same problem after having resized ext4 partition. Does anybody know any solutions?

---

### Post by friasa on 2009-11-05
Does anyone know if this problem still exists on Ubuntu 9.10 Live CD?

---

### Post by jchedstrom on 2010-01-11
I can confirm that using gparted to resize ext4 partitions works on the 9.10 64bit live cd. 

Not only that, it successfully allowed me to completely remove my swap partition, shrink and move my home directory which is encrypted, and then grow my root partition into the freed space. Honestly I was expecting the worst but was pleasantly surprised that it worked flawlessly.

Note: I recommend running 'sudo apt-get install gparted' before you try this. That should assure that you are running the most up to date gparted regardless of what's on your live cd.

---

### Post by Joshua Hublar on 2010-02-10
Confirmed operational x86 9.10 LiveCD.

---

