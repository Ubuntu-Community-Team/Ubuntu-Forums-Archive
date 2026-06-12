---
title: "Grub issue"
date: 2008-12-31
forum: General Help
---

### Post by Intrepid Ibex on 2008-12-31
:(,

I wanted to have gfx-grub, so therefore I followed these instructions (which are currently the up-to-date ones. The first message isn't up-to date):

[http://ubuntuforums.org/showthread.php?t=208855&page=66](http://ubuntuforums.org/showthread.php?t=208855&page=66)
> **ryukent said:**
> 
..
sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)

Obviously you need to change the X and Ys.

sudo grub-install /dev/sdaX

This was very important. Didn't work without it. Note the X is not the same number as the x or y in the previous section as grub uses different numbers. You need to look up the correct hard disk to use. It should be the one are booting to.
...

So I did all the other things, but at that part I accidentally selected Windows C: partition at 
sudo grub: grub> root
and sudo grub-install /dev/sda!

So how do I undo the changes?

- currently I can't boot to Windows (Vista)

ps. I need to fix this as quick as possible:
Thanks forehand for the helpers! Thank you really much!

---

### Post by Intrepid Ibex on 2008-12-31
Bump! Anyone :)?

---

### Post by caljohnsmith on 2008-12-31
Sounds like you may have accidentally overwritten your Windows boot sector with Grub. In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by Intrepid Ibex on 2008-12-31
It's pretty big.. I posted it in here: [http://pastebin.com/m46625da](http://pastebin.com/m46625da)

---

### Post by caljohnsmith on 2008-12-31
Actually you posted the contents of the bash script and not the results; please post the contents of the "[COLOR="Blue"]RESULTS.txt[/COLOR]" file. :)

---

### Post by Intrepid Ibex on 2008-12-31
OH :D!

Sorry, here it is:
```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for its boot files.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Mounting failed:
mount: you must specify the filesystem type

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Mounting failed:
mount: you must specify the filesystem type

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda4: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3ffb046e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   181984319    90992128+   7  HPFS/NTFS
/dev/sda2   *   299162430   312576704     6707137+   7  HPFS/NTFS
/dev/sda3       181984320   221247179    19631430   83  Linux
/dev/sda4       221247180   299162429    38957625    5  Extended
/dev/sda5       221247243   299162429    38957593+  83  Linux

Partition table entries are not in disk order

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda3: UUID="dcfa8068-b3a8-4645-bfcf-cc8dcffedac8" TYPE="ext3" 
/dev/sda5: UUID="16a57d37-35a7-41b6-bf8f-bc376b65311e" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda5 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/linuxpro/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=linuxpro)

=========================== sda3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
....................
....................
# savedefault=false

## ## End Default Options ##

title        Ubuntu 8.10, kernel 2.6.27-11-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=dcfa8068-b3a8-4645-bfcf-cc8dcffedac8 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=dcfa8068-b3a8-4645-bfcf-cc8dcffedac8 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-9-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=dcfa8068-b3a8-4645-bfcf-cc8dcffedac8 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=dcfa8068-b3a8-4645-bfcf-cc8dcffedac8 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=dcfa8068-b3a8-4645-bfcf-cc8dcffedac8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=16a57d37-35a7-41b6-bf8f-bc376b65311e /home           ext3    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda3/boot: ==================================

total 24640
drwxr-xr-x  3 root root    4096 2008-12-29 10:26 .
drwxr-xr-x 20 root root    4096 2008-12-29 19:27 ..
-rw-r--r--  1 root root  508385 2008-12-19 19:57 abi-2.6.27-11-generic
-rw-r--r--  1 root root  507665 2008-11-21 01:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91358 2008-12-19 19:57 config-2.6.27-11-generic
-rw-r--r--  1 root root   91364 2008-11-21 01:46 config-2.6.27-9-generic
drwxr-xr-x  3 root root    4096 2008-12-31 21:50 grub
-rw-r--r--  1 root root 8621630 2008-12-24 18:09 initrd.img-2.6.27-11-generic
-rw-r--r--  1 root root 8619552 2008-12-15 14:31 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 23:11 memtest86+.bin
-rw-r--r--  1 root root 1031799 2008-12-19 19:57 System.map-2.6.27-11-generic
-rw-r--r--  1 root root 1029585 2008-11-21 01:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1074 2008-12-19 19:58 vmcoreinfo-2.6.27-11-generic
-rw-r--r--  1 root root    1073 2008-11-21 01:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2248912 2008-12-19 19:57 vmlinuz-2.6.27-11-generic
-rw-r--r--  1 root root 2244304 2008-11-21 01:46 vmlinuz-2.6.27-9-generic

=============================== sda3/boot/grub: ===============================

total 252
drwxr-xr-x 3 root root   4096 2008-12-31 21:50 .
drwxr-xr-x 3 root root   4096 2008-12-29 10:26 ..
-rw-r--r-- 1 root root    197 2008-12-31 21:35 default
-rw-r--r-- 1 root root     15 2008-10-04 23:10 device.map
-rw-r--r-- 1 root root   8108 2008-12-31 21:35 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-31 21:35 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-31 21:35 installed-version
-rw-r--r-- 1 root root   8712 2008-12-31 21:35 jfs_stage1_5
-rw-r--r-- 1 root root   5012 2008-10-04 18:30 menu (copy).lst
-rw-r--r-- 1 root root   5117 2008-12-31 21:50 menu.lst
-rw-r--r-- 1 root root   5143 2008-12-31 21:50 menu.lst~
-rw-r--r-- 1 root root   5259 2008-12-31 21:25 menu.lst.backup
-rw-r--r-- 1 root root   5259 2008-12-31 21:20 menu.lst.backup~
-rw-r--r-- 1 root root   7352 2008-12-31 21:35 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-31 21:35 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-11-13 14:04 splashimages
-rw-r--r-- 1 root root    512 2008-12-31 21:35 stage1
-rw-r--r-- 1 root root 121460 2008-12-31 21:35 stage2
-rw-r--r-- 1 root root   9556 2008-12-31 21:35 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sda1: unknown volume type
/dev/sda2: unknown volume type
```

---

### Post by caljohnsmith on 2008-12-31
Unfortunately it looks like you did accidentally install Grub to the boot sector of both your NTFS partitions (sda1 and sda2); to fix it, how about booting your Vista Install CD, go to the command line, and run:
```
diskpart
```
And at the diskpart prompt do:
```
list volumes
exit
```
And find the drive letters for both of your NTFS partitions and do:
```
E:\boot\bootsect.exe /nt60 X:
```
But replace E with the drive letter of the Vista CD if it is different, and also replace X with the drive letter of each of your NTFS partitions. How about giving that a shot and let me know how it goes.

---

### Post by Intrepid Ibex on 2008-12-31
Yeah, yeah.

nice...

I have 2 Vista disks. I put the first one in, there came this window, where I pressed next and next, and (of course!!) it started installing Windows after that..
And before it installs Windows, it of course formats the whole disk..

So now I have no OS on my computer... hehe...

**E:** this message written with my old PC which has Xubuntu

Thanks anyway :( ..

---

