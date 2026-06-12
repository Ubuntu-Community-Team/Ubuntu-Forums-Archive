---
title: "Grub error 17, deleted partition table and reinstalled grub"
date: 2009-05-03
forum: General Help
---

### Post by megajosh2 on 2009-05-03
I had various reasons to remove my partition table, and after I did so I reinstalled grub on /dev/sdb1 (before it was on /dev/sdb), and I get Grub error 17 immediately after I go to grub. Does anyone know how I could fix this?

---

### Post by Mr Fredrick on 2009-05-03
Hi megajosh2,

I had a similar problem and I got great help from the "How to Install Grub from a Live CD" thread over in the "Tips and Tutorial" forum.

I think the following is a link to it:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by megajosh2 on 2009-05-03
Thanks for the help but I've already tried reinstalling grub running this command:
```

# grub-install --root=/mnt/sdb1 /dev/sdb1 --recheck

```
/mnt/sdb1 is of course where I mounted /dev/sdb1.

---

### Post by caljohnsmith on 2009-05-03
If you deleted your partition table as you said in your original post, I'm just wondering how then you are going to reinstall Grub if the drive has no partition table? But if the drive does still have a partition table, it would help to get a clearer picture of your setup (including the current partitions on that drive), so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

And do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

Regards,
John

---

### Post by megajosh2 on 2009-05-03
No, I repartitioned my drive. Here's the boot info:
```

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 1228863 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b36bdea

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *      8,835,750   321,669,494   312,833,745   7 HPFS/NTFS
/dev/sda2                  63     8,835,749     8,835,687   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8d399bc0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     4,096,574     4,096,512  83 Linux
/dev/sdb2           4,096,575     9,269,504     5,172,930  82 Linux swap / Solaris
/dev/sdb3           9,269,505   214,066,124   204,796,620  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="4CF41666F4165316" TYPE="ntfs" 
/dev/sda2: UUID="423B-2BDF" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="8917e6cd-bac7-4aa3-ab20-2e276206ad47" TYPE="ext2" 
/dev/sdb2: UUID="c9a90e30-51a9-4538-95da-ec1dbc564805" TYPE="swap" 
/dev/sdb3: LABEL="Arch Linux" UUID="e0938d94-4650-4474-8ba6-2fcc246567af" TYPE="ext3" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb3 on /media/Arch Linux type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sdb1/boot/grub/menu.lst: ===========================

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd1,0)
kernel /arch/vmlinuz26 root=/dev/sda3 rw vga=773
initrd /arch/kernel26.img

# (1) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1

=================== sdb1: Location of files loaded by Grub: ===================


    .6GB: boot/grub/menu.lst
    .6GB: boot/grub/stage2

=========================== sdb3/boot/grub/menu.lst: ===========================

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd1,0)
kernel /boot/vmlinuz26 root=/dev/sda3 rw vga=773
initrd /boot/kernel26.img

# (1) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1

=============================== sdb3/etc/fstab: ===============================

# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
none                   /dev/pts      devpts    defaults            0      0
none                   /dev/shm      tmpfs     defaults            0      0

/dev/cdrom             /media/cd   auto    ro,user,noauto,unhide   0      0
/dev/dvd               /media/dvd  auto    ro,user,noauto,unhide   0      0
/dev/fd0               /media/fl   auto    user,noauto             0      0

# root, swap, boot
/dev/sdb3             /            ext3        defaults            0      0
/dev/sdb1             /boot        ext2        defaults            0      0
/dev/sdb2             swap         swap        defaults            0      0


=================== sdb3: Location of files loaded by Grub: ===================


  19.6GB: boot/grub/menu.lst
  19.6GB: boot/kernel26-fallback.img
  19.7GB: boot/kernel26.img
  19.6GB: boot/vmlinuz26
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

---

### Post by caljohnsmith on 2009-05-03
Just out of curiosity, but why did you post in the Ubuntu forums when you are trying to install Grub for Arch Linux? :) Anyway, I can still try to help you with your Grub problem if you want. According to your Arch's /etc/fstab, sdb1 is supposed to be a /boot partition, yet all of Arch's boot files are still in the main Arch partition, sdb3. Do you still want to use sdb1 as a boot partition, or do you want to just leave everything where it is in your root Arch sdb3 partition? The easiest of course would be to leave things as they are in sdb3, but let me know what you want to do.

John

---

### Post by megajosh2 on 2009-05-03
I was using the Ubuntu LiveCD to do all this, and I guess I just thought to come here. :D Doesn't make a lot of sense now that I think about it.

Yeah, I still wanted to use sdb1. I copied all of Arch's boot files into /arch on sdb1 (I'm planning on using multiple systems so I wanted to organize it).

---

### Post by caljohnsmith on 2009-05-03
OK, if you want to keep sdb1 as your /boot partition, you will first need to move your Grub boot files; because you installed Grub to sdb1 using "grub-install" in the way you did, grub-install put the Grub files in the /boot/grub directory in that partition when it should just be the /grub directory since Arch mounts that partition on /boot. So to fix that, how about doing:
```
sudo mount /dev/sdb1 /mnt
sudo mkdir /mnt/grub
sudo mv /mnt/boot/grub/* /mnt/grub
sudo rm -fr /mnt/boot/grub
gksudo gedit /mnt/grub/menu.lst
```
The last command should pull up your menu.lst, and change the Arch entry to use (hd0,0) instead of (hd1,0):
```
title  Arch Linux
root   [COLOR="Red"](hd0,0)[/COLOR]
kernel /arch/vmlinuz26 root=/dev/sda3 rw vga=773
initrd /arch/kernel26.img
```
Then you will need to unmount sdb1 before running the following Grub commands:
```
sudo umount /dev/sdb1
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
Then reboot, make sure your sdb drive is set to boot first in your BIOS boot order, and you should get the Grub menu on start up. Let me know if you can successfully boot Arch at that point, or if you run into problems.

John

---

### Post by megajosh2 on 2009-05-03
Thanks a lot, it worked! I just have problems with Arch though, I'll head to their forums to try and solve them.

---

### Post by caljohnsmith on 2009-05-03
> **megajosh2 said:**
> Thanks a lot, it worked! I just have problems with Arch though, I'll head to their forums to try and solve them.
Glad to hear that worked OK. Good luck resolving your Arch issues. :)

John

---

