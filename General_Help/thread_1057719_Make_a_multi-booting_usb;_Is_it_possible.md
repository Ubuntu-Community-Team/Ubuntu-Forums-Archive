---
title: "Make a multi-booting usb; Is it possible?"
date: 2009-02-02
forum: General Help
---

### Post by arkticcool on 2009-02-02
I have had quite a bit of success creating LiveUSBs, with a variety of tools, and tutorials which have included Unetbootin, and the LiveUSB creator (Intrepid).

However I've never been able to create a USB with more then one distribution. This thought was kept out of mind for the last few months, until I bought a 16GB usb.

Now that I have the space for multiple OS's (Mostly LiveCDS, but maybe one customized system), I've been wondering how to make a multi-booting USB, with grub/lilo as the manager (or any other, I'm not picky).

Is it possible, and how can it be done?

---

### Post by Neural oD on 2009-02-02
I'm sure i've seen it done before - have you googled it yet?

---

### Post by zwygart on 2009-02-02
Sure it is possible. I have Puppy4.00, UbuntuLiveCD 8.10, UBCD and SystemRescueCD working now on my 16G USB flash drive. I will now add gentooLiveCD wich I suppressed a while ago due to not having enough space. For your info I tried to boot without success : ArchLinux, Slax, ophcrack, backtrack, all stopping with kernel panic. Mint has some trouble to. 

You have made some bootable drives so no need to explain howto. I sugesst GRUB. It is easy to add entries. I also suggest to make a partition for each OS. Most ISO/OS boot with isolinux, so check out the isolinux.cfg or syslinux.cfg file and traduce the content for GRUB in the menu.lst. 
A while ago (and I will reput it on), I had multi bootloader. GRUB is able to access more than it's own partition so it is the first one. Then I passed the control to the syslinux installed on the partition wich booted his OS. Syslinux can only boot his partition. For any question please post. We can work togheter.

---

### Post by Gizenshya on 2009-02-02
16gb usb... you mean a 16gb usb flash drive?

if I were you, I'd just have a 2.5" hdd.  lots more space, and easier to work with.  Just install your OS's like normal, and stick it in a case and boot from usb.

---

### Post by zwygart on 2009-02-02
> 16gb usb... you mean a 16gb usb flash drive?

if I were you, I'd just have a 2.5" hdd. lots more space, and easier to work with. Just install your OS's like normal, and stick it in a case and boot from usb.
I know, now I would prefer a HD, but a HD is bigger physically. So a flash drive is easier to bring with you anywhere. Next thing I would buy is a external HD.

---

### Post by arkticcool on 2009-02-03
> **zwygart said:**
> Sure it is possible. I have Puppy4.00, UbuntuLiveCD 8.10, UBCD and SystemRescueCD working now on my 16G USB flash drive. I will now add gentooLiveCD wich I suppressed a while ago due to not having enough space. For your info I tried to boot without success : ArchLinux, Slax, ophcrack, backtrack, all stopping with kernel panic. Mint has some trouble to. 

You have made some bootable drives so no need to explain howto. I sugesst GRUB. It is easy to add entries. I also suggest to make a partition for each OS. Most ISO/OS boot with isolinux, so check out the isolinux.cfg or syslinux.cfg file and traduce the content for GRUB in the menu.lst. 
A while ago (and I will reput it on), I had multi bootloader. GRUB is able to access more than it's own partition so it is the first one. Then I passed the control to the syslinux installed on the partition wich booted his OS. Syslinux can only boot his partition. For any question please post. We can work togheter.

So what your saying is that I install multiple partitions on my disk for each system, install them using Unetbootin etc. etc.to each partition, then install grub and copy paste the entries of syslinux.cfg/isolinux.cfg.

Ok if all goes through I'll make a python script to automate the process of format/install/copy.

Unless you've done it differently, in fact, could you tell me the exact set up of your 16GB usb.

---

### Post by zwygart on 2009-02-03
I don't used Unetbootin, I only copy the content of the ISO in the partitions. If I want to install, I install without the bootloader and setted it up manually after. This way is safer to not screw up the host computer.

Yes install GRUB.

Until here you where right, and it will be easy to do this in a programme. (I don't know how you partition with python).

You cannot only copy the content of the isolinux.cfg. Isolinux and grub don't have the same syntax. You may only use the isolinux.cfg if you install isolinux on the partition (not the disk).
Here some important differences between grub and isolinux/syslinux :
Grub begins with title instead of label
initrd is not present on isolinux. It is added with the append command
append is not present on grub. The options are pasted after the kernel line.
isolinux include a configfile with include
grub use configfile, with some differences.
These are some differences.


I don't remeber all the changes. 
To install grub copy the files in boot/grub on the drive, then run these commands in a grub shell
```
find /boot/grub/menu.lst
root (hdX,Y)
setup (hdX,3)
```
replace the X and Y with the number returned by find. Be carefull to not take the one of your computer.
Yes, it worked by installing on the 4 partition , even if I don't have 4 primaire partition on the disk. I found it on a thread that flash drive don't have MBR and that the bootloader could be installed on there. It worked for me. And even if I installed syslinux after grub, it don't replaced grub. :)   By the way I installed superGrub (it is GRUB with more options)
So here is the important entries of my USB menu.lst
```
title Puppy 400
kernel $(grub_device)/vmlinuzPuppy lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
initrd $(grub_device)/initrd

title live
root (hd0,5)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper
initrd /casper/initrd.gz quiet splash --

title live-install
root (hd0,5)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity
initrd /casper/initrd.gz quiet splash --

title check
root (hd0,5)
kernel /casper/vmlinuz boot=casper integrity-check 
initrd /casper/initrd.gz quiet splash --

title SystemRescueCD
root (hd0,6)
kernel /isolinux_SRCD/rescuecd init=/sbin/init
initrd /isolinux_SRCD/initram.igz
boot
```
Also the fdisk -l if you want to see it:
```
Disk /dev/sdb: 16.1 GB, 16173236224 bytes
64 heads, 32 sectors/track, 15424 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00080570

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        8462     8665072    b  W95 FAT32
/dev/sdb2           10650       14431     3872768   83  Linux
/dev/sdb3            8463       10649     2239488    5  Extended
/dev/sdb4           14432       15424     1016832    b  W95 FAT32
/dev/sdb5            9254        9945      708608    b  W95 FAT32
/dev/sdb6            8463        9253      809952    b  W95 FAT32
/dev/sdb7            9946       10649      720880    b  W95 FAT32

```
There are some partition with none working oses.

If you need more infos please post, I'm open to help you doing these.

---

### Post by arkticcool on 2009-02-04
I've made a multi-booting usb with tty, DSL, SLAX and otg linux. You must have used mk-boot-usb perl script displayed on this site.

[http://people.ofset.org/~ckhung/p/mk-boot-usb/](http://people.ofset.org/~ckhung/p/mk-boot-usb/)

It partitions the usb and installs grub, tty/otg linux for you. Then it easily shows you how to install other live installations from their LiveCD isos.

I will make a tutorial on how to make a multi-booting LiveUSB.

---

### Post by zwygart on 2009-02-04
Sorry, never seen this page. I never used perl to. DSL I ran it only from a emulator on XP. But it is interesting anyway Thanks :)
As I said I copied the grub files, then installed grub manually from a Linux environnement. After I copied ISO's like it says in your linked site. I know this may be not easy to explain. 
I searched a lot some mounts ago to find a tutorial wich worked for me.
It's a very good idea to make a tutorial. I will help you where you want. If you want to traduce it I can do it for French and German. I know french and german better than english (I think my english is not so bad).
;)

---

### Post by arkticcool on 2009-02-05
Created a multi-booting USB tutorial at [http://ubuntuforums.org/showthread.php?p=6680003#post6680003](http://ubuntuforums.org/showthread.php?p=6680003#post6680003).

Visit it to create your own. zwygart I would be glad if you followed the tutorial and translated it, or even better created your own on how you made yours.

---

