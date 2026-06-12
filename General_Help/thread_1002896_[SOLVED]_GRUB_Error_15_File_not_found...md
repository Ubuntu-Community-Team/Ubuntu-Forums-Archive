---
title: "[SOLVED] GRUB Error 15: File not found.."
date: 2008-12-05
forum: General Help
---

### Post by tonybeccar on 2008-12-05
Hello, i recently installed ubuntu on my computer. I have two hard drives, one is a ntfs drive that i use only for storage, and the other had 2 partitions, one for windows and the other for ubuntu 8.04, everything worked fine then. As I was saying, i recently upgraded to Ubuntu 8.10. I formatted the linux partition from the live cd in the installation wizard, everything seemed fine. The weird thing is that when the installation was finished, i rebooted my computer and windows xp booted automatically, odd. Well, so i inserted my super grub disc and tried to fix it. It's really strange what happens here, when i try to fix my linux partition, i get an error 15, the SGD cannot find the file /boot/grub/stage1. BUT, when i go to the option "Boot from master boot record" and i select the linux hard drive, it boots perfectly! I don't know what happens here, i'll show you my menu.lst and a fdisk -l command to see what the hard drives are. My ubuntu partition is at (hd1,1) although when i go to the grub from the ubuntu command line it says it's in (hd0,1). I also tried the command: root (hd0,1) ; setup (hd0). Anyway, please someone could look at it and see what is happening here? Thank you very much!

---

### Post by caljohnsmith on 2008-12-05
Do you know which drive you boot on start up? How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```

sudo xxd  -l  2 -p /dev/sda
sudo xxd -s 1049 -l 2 -p /dev/sda
sudo xxd  -l  2 -p /dev/sdb
sudo xxd -s 1049 -l 2 -p /dev/sdb
```
Note that "-l" is a lowercase L, not a one. That should help clarify your booting issues.

---

### Post by tonybeccar on 2008-12-05
Hi caljohnsmith, thanks for the fast answer! Look, i CAN use my ubuntu, i simply use the sgd every time i start up, so i did the commands you told me from my ubuntu not from the live cd if that is what you meant. Here is my output:

sudo xxd  -l  2 -p /dev/sda = eb48

sudo xxd -s 1049 -l 2 -p /dev/sda = 01ff

sudo xxd  -l  2 -p /dev/sdb = 33c0

sudo xxd -s 1049 -l 2 -p /dev/sdb = 0181

Now what do I have to do with this?

Thank you very much!

---

### Post by caljohnsmith on 2008-12-05
OK, that helps alot :); according to those commands, you have Grub properly installed to the sda drive, while the sdb drive has a Windows MBR. That means if you boot directly into Windows on start up, you must be booting the sdb drive; also, that means your Windows boot files must be on the sdb drive in the sdb1 NTFS data partition. Usually Windows only puts its boot files on another drive if the drive you install Windows to is the slave drive, and the other drive Windows puts its boot files on is the master drive. Is the sdb drive by chance set as the master drive? 

Anyway, I think the most ideal solution for your situation is to change your BIOS to boot your Ubuntu drive, and then you can boot either Windows or Ubuntu from the Grub menu. If that sounds good to you, then you will first need to correct your Grub's menu.lst, so open it up with:
```
gksudo gedit /boot/grub/menu.lst
```
Delete the "root (hd1,1)" line in all the Ubuntu entries so that they look similar to:
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		2a64dce2-afa6-4b21-8d5b-bb593c101691
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2a64dce2-afa6-4b21-8d5b-bb593c101691 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```
In other words, if you have a "uuid" line to specify the correct partition for Ubuntu, you don't have to use a "root (hdX,Y)" line; you only need to use one or the other, not both. Also, your Windows entry in the Ubuntu menu.lst should work fine to boot Windows the way you have it now with Windows' boot files in sdb1, but I would recommend moving the Windows boot files back to the Windows partition so you can boot Windows directly from its partition, and not from your sdb data drive. If you want help with that, then please post the following:
```
sudo mkdir /mnt/sda1 /mnt/sdb1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb1 /mnt/sdb1
ls -l /mnt/sda1 /mnt/sdb1
cat /mnt/sda1/boot.ini /mnt/sdb1/boot.ini
```
And we can work from there if you want. :)

---

### Post by tonybeccar on 2008-12-05
Oh my god man, it worked like a charm! You are a genius man, i really thank you. I had my BIOS booting from my sdb and i changed it to sda. Windows boots perfectly. Lots of thanks and good luck!!:)

---

### Post by caljohnsmith on 2008-12-05
> **tonybeccar said:**
> Oh my god man, it worked like a charm! You are a genius man, i really thank you. I had my BIOS booting from my sdb and i changed it to sda. Windows boots perfectly. Lots of thanks and good luck!!:)
Glad to hear it worked OK; cheers and have fun with Ubuntu. :)

---

### Post by gizzacroggy on 2009-12-05
Hi C

I have the same problem as tonnybeccar - recently installed ubuntu and for few days was running a dual booting with Ubuntu 9.10 and Windows Vista running on the same hard drive. Then I turned it on yesterday morning to find that Grub is playing up. 

I am now emerging myself in a crashcourse in Linux and code trying to solve this. I used the Subergrub disc but same error as tonny - error 15.

I ran the tests that you gave him and here are my results. 

sudo xxd  -l  2 -p /dev/sda         = eb63
sudo xxd -s 1049 -l 2 -p /dev/sda   = ffff
sudo xxd  -l  2 -p /dev/sdb         = no medium found
sudo xxd -s 1049 -l 2 -p /dev/sdb   = no medium found

I would  love any assistance you can give in understanding what is going on and learning how to fix it. 
 
Thanks

G x

Here is my fdisc information in case useful.
gizzacroggy@gizzacroggy-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a7c51dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1918       23354   172183732    7  HPFS/NTFS
/dev/sda4           23355       30401    56605027+   5  Extended
/dev/sda5           23355       30107    54243441   83  Linux
/dev/sda6           30108       30401     2361523+  82  Linux swap / Solaris

---

### Post by oldfred on 2009-12-05
They have improved the way we look at boot issues with this script.

Boot Info Script 0.37 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
Instructions
  louieb's 
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 [http://ubuntuforums.org/showthread.php?p=8279056#1](http://ubuntuforums.org/showthread.php?p=8279056#1)
  caljohnsmith
 [http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3) 
cd to directory saved to: 
chmod 755 boot_info_script037.sh 
sudo ./boot_info_script037.sh 
or as example if on desktop from liveCD download 
sudo bash ~/Desktop/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.


Also is the problem after you booted into Vista. Grub2 is larger than grub legacy and windows MBR and some windows software likes to hide things in the MBR and now corrupts grub2.

HP ProtectTools and Dell Recovery Tool write into MBR
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)
[http://ubuntuforums.org/showthread.php?p=8433673](http://ubuntuforums.org/showthread.php?p=8433673)

Also I have not looked at supergrub lately but it was not yet updated for grub2.

---

### Post by gizzacroggy on 2009-12-07
Here are my results.

The mount output look svery different to the examples posted in the links you shared with me.


```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sda5 and 
                       looks at sector 376389137 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #5 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1a7c51dd

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3    *     30,801,920   375,169,383   344,367,464   7 HPFS/NTFS
/dev/sda4         375,182,010   488,392,064   113,210,055   5 Extended
/dev/sda5         375,182,073   483,668,954   108,486,882  83 Linux
/dev/sda6         483,669,018   488,392,064     4,723,047  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: UUID="9E98822C9882034F" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="EE94845794842465" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="315caa64-ddbe-4f7e-8dfc-eb0b23f5d405" TYPE="ext4" 
/dev/sda6: UUID="357af9e8-2c9d-40bb-a1bd-3e82feb3c024" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 315caa64-ddbe-4f7e-8dfc-eb0b23f5d405
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 315caa64-ddbe-4f7e-8dfc-eb0b23f5d405
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=315caa64-ddbe-4f7e-8dfc-eb0b23f5d405 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 315caa64-ddbe-4f7e-8dfc-eb0b23f5d405
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=315caa64-ddbe-4f7e-8dfc-eb0b23f5d405 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set ee94845794842465
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=315caa64-ddbe-4f7e-8dfc-eb0b23f5d405 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=357af9e8-2c9d-40bb-a1bd-3e82feb3c024 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 192.0GB: boot/grub/grub.cfg
 192.0GB: boot/initrd.img-2.6.31-14-generic
 192.0GB: boot/vmlinuz-2.6.31-14-generic
 192.0GB: initrd.img
 192.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by oldfred on 2009-12-07
Unless your media direct has corrupted grub2 it says it is installed correctly. The eb63 and ffff from the old commands also match mine which are the beginning & end of the boot sector. eb63 means it is grub2. The script just prints out in words what the old commands translated said.

Supposedly error 15 is because you have old grub in the MBR but are booting new grub so there are file mismatches.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
scroll down about half way for errors
**File Not Found (Error 15)**
This error is the result of a GRUB 2 installation to /boot but a Master Boot Record ( MBR ) which still contains Grub legacy.

It says to reinstall grub2 which I would try first.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by gizzacroggy on 2009-12-08
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I tried this - it says succesfully installed but when I reboot it gives me the same message - no bootable devices.


[https://help.ubuntu.com/community/Gr...0from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

I followed this. It went smoothly telling me succesfully installed but when I reboot the same as above happens

Any suggestions for what to try next?

G

---

### Post by oldfred on 2009-12-08
I did not realize you had your own thread. See my post in your thread.

---

