---
title: "Linux Installed, I Want To Create a External HDD From This"
date: 2012-12-14
forum: Desktop Environments
---

### Post by TheBeginning on 2012-12-14
Hi,

I have Linux installed on one of my hard drives.
But I have to work for a few weeks by somebody that is just a tiny bit known with MS, from Linux he has never heard of.

So I was thinking to get me an external hdd case for about 20 bucks,
and just boot from the external hdd when I need. 

Do I need to buy anything more, or are any special steps required ?

Due to warantee/garanty at the desktop, I rather plug in my Linux hdd extern, then open the case from this person and he might get problems because of this.

I'd hope some one can give me some rough pointers.

Thanks per advance.

~TheBeginning,

---

### Post by ibjsb4 on 2012-12-14
May be easier to just make a bootable usb flash drive and not deal with an hdd.

---

### Post by TheBeginning on 2012-12-14
> **ibjsb4 said:**
> May be easier to just make a bootable usb flash drive and not deal with an hdd.

Thanks, but I do not have any clue on this, how to achieve that.
And if I will create a bootable usb flash drive, how I will be able to working from the original Linux Distro ?

I mean, I have all my files located already on this Linux hdd, 

Any help is appreciated.

~Renaldo,

---

### Post by ibjsb4 on 2012-12-14
You would need to build a persistent flash drive big enough to hold your files.

[https://www.google.com/search?client=ubuntu&channel=fs&q=persistent+usb+flash+drive+ubuntu&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=persistent+usb+flash+drive+ubuntu&ie=utf-8&oe=utf-8)

If you do this with an external HDD you need to make it bootable.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=make+external+HDD+boot&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=make+external+HDD+boot&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by oldfred on 2012-12-14
If you have a larger flash drive you can do a full install to the flash drive. Not quite as speedy as a hard drive, but functional especially if you change settings to reduce writes and have a fair amount of RAM.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

    
If you do a full install, you can just copy your /home over which has all your user configuration files & your data.

Some do copy entire system but then have major issues with duplicate UUIDs, and have to reinstall grub, edit fstab and change a few other settings to house clean duplicates issues.

Install to external device is like any install, but you have to use Something Else or manual install to get the option to install the grub2 boot loader to the MBR of the external or second drive.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

    
       Full install of 12.04 to 64GB USB device C.S.Cameron post #3
[http://ubuntuforums.org/showthread.php?t=2092077](http://ubuntuforums.org/showthread.php?t=2092077)
Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

    
       With SSD or Flash drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.
change to noop i/o scheduler

---

