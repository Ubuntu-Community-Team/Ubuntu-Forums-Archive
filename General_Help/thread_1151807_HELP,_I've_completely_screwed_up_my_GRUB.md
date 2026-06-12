---
title: "HELP, I've completely screwed up my GRUB"
date: 2009-05-07
forum: General Help
---

### Post by Lorenzo1985 on 2009-05-07
Essentually I wanted to delete some old partitions, and upgrade my root partition to ext4 (yes I'm aware of the risks, i'm not particulary concerned about the data in that partition)

Anyway grub-install didnt appear to work, i tried allot of things last night from various tutorials with limited success. However I'd say it would be best to presume everything in /boot is written off. it doesnt help that most of the tutorials do not cater for people with a seperate /boot partition 

I am able to get to a grub prompt by installing grub to (hd0)
but no menu, and I havent quite worked out how to boot from the prompt

my partitions are as follows (as far as I can tell)
Device         grub device     Normal mount point
/dev/sda4     (hd0,3)          /
/dev/sda6      (hd0,5)         /boot
/dev/sda7       ?              /home

If I were to start again with /boot how would you go about it?
How can i get grub installed on my hard drive and get an auto generated menu.lst to work.

Points of note:
I can access a Jaunty live CD

If I try to do setup (hd0,5) i get errors similar to the following
Running "embed /grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)

I tried following this turorial with the addition of mounting 
/dev/sda6 at /mnt/system/boot
i get an error something like:
Could not find device for /boot or not a block device.


Any ideas of how i would go about sorting this out from scratch?

Many thanks for any help provided....

---

### Post by Lorenzo1985 on 2009-05-07
Apologies the bump, but does anyone have an idea how to do this with a seperate /boot partition

---

### Post by caljohnsmith on 2009-05-07
Lorenzo1985, please observe the [Forum Do's and Don'ts]("http://ubuntuforums.org/showthread.php?t=885580") and don't bump your thread sooner than every 24 hours. :)

About your Grub problems, a good place to start is to download the **Boot Info Script** to your Ubuntu desktop (can be your Live CD):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by Lorenzo1985 on 2009-05-07
Apologies for the poor conduct. It''s amazing how quickly this forum moves. Just show how popular Ubuntu is I suppose. 

Anyways....

Here is the output of the script you asked me to run.

One point to note is that I think the comments in my /etc/fstab are wrong. When I deleted partion /dev/sda6 all the other moved down.So sda7 became sda6 etc. I dont believe this is a problem because I don't thing the UUIDs will have changed. I have mounted the partitions and I'm prety sure whats in the first post is correct with reguard to which partition is which.

```
============================= Boot Info Summary: =============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda6 and 
                       looks at sector 195255506 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
mount: /dev/sdc1 already mounted or sdc1 busy

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed53ed53

Partition  Boot         Start           End          Size  Id System

/dev/sda3         156,151,800   586,067,264   429,915,465   5 Extended
/dev/sda5         583,047,108   586,067,264     3,020,157  82 Linux swap / Solaris
/dev/sda6         195,238,008   195,430,724       192,717  83 Linux
/dev/sda7         195,430,788   583,047,044   387,616,257  83 Linux
/dev/sda4          97,562,745   156,151,799    58,589,055  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00059e06

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002  8e Linux LVM


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 522 MB, 522452992 bytes
2 heads, 63 sectors/track, 8098 cylinders, total 1020416 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00b28a2d

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     1,020,415     1,020,384   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda4: LABEL="/" UUID="07184754-cad1-4997-b495-322471bc4122" TYPE="ext4" 
/dev/sda5: TYPE="swap" UUID="369bdc82-7ab6-4a9b-9aba-4dd089366b04" 
/dev/sda6: LABEL="/boot" UUID="ab314c00-0f68-423a-82b1-a9bb6d593ffc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="/home" UUID="52e661bd-dbf9-4b2e-9408-7a17ce609bc8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: LABEL="media" UUID="29363817-1c7a-47eb-a9ba-377ca189793a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="002F-A9D2" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


============================= sda6/grub/menu.lst: =============================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=07184754-cad1-4997-b495-322471bc4122 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=07184754-cad1-4997-b495-322471bc4122

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, memtest86+
uuid		07184754-cad1-4997-b495-322471bc4122
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sda6: Location of files loaded by Grub: ===================


  99.9GB: grub/menu.lst
  99.9GB: grub/stage2

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=07184754-cad1-4997-b495-322471bc4122 /               ext4    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=ab314c00-0f68-423a-82b1-a9bb6d593ffc /boot           ext3    relatime        0       2
# /dev/sda8
UUID=52e661bd-dbf9-4b2e-9408-7a17ce609bc8 /home           ext3    relatime        0       2
# /dev/sda5
UUID=369bdc82-7ab6-4a9b-9aba-4dd089366b04 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1       /media/media    ext3        defaults,rw,noatime,nodiratime        0       0
```

---

### Post by caljohnsmith on 2009-05-07
It looks like you might have more problems than just with Grub; you don't seem to have any of Ubuntu's boot files, i.e. kernels and initrd images, in your sda6 boot partition. Also, your Grub's menu.lst doesn't even include any entries for booting Ubuntu--the only entry is for running "memtest". Before upgrading Ubuntu to an ext4 file system, were you able to boot Ubuntu OK? Do you have any idea how you might have uninstalled/deleted your Ubuntu boot files? How about posting the output of the following commands from your Live CD:
```
sudo mkdir /mnt/sda6 /mnt/sda4
sudo mount /dev/sda6 /mnt/sda6 && ls -lR /mnt/sda6
sudo mount /dev/sda4 /mnt/sda4 && ls -l /mnt/sda4/boot
sudo mount --bind /dev /mnt/sda4/dev
sudo mount --bind /proc /mnt/sda4/proc
sudo chroot /mnt/sda4 /bin/bash
dpkg --get-selections linux*
exit
```
And we can work from there.

John

---

### Post by Lorenzo1985 on 2009-05-07
Wow, your really good!! Thankyou very much for your help!

As mentioned last night lots and lots of things were tried, many of them probably were not wise. one of them definetly included copying from the live CD's filesystems /boot. I believe the menu.lst was created by chroot'ing to the mounted drive and running update-grub

```

ubuntu@ubuntu:~$ sudo mkdir /mnt/sda6 /mnt/sda4
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt/sda6 && ls -lR /mnt/sda6
/mnt/sda6:
total 2574
-rw-r--r-- 1 root root  525592 2009-05-06 22:40 abi-2.6.28-11-generic
-rw-r--r-- 1 root root   90584 2009-05-06 22:40 config-2.6.28-11-generic
drwxr-xr-x 2 root root    1024 2009-05-06 22:52 grub
-rw-r--r-- 1 root root  128796 2009-05-06 22:40 memtest86+.bin
-rw-r--r-- 1 root root 1871601 2009-05-06 22:40 System.map-2.6.28-11-generic
-rw-r--r-- 1 root root    1170 2009-05-06 22:40 vmcoreinfo-2.6.28-11-generic

/mnt/sda6/grub:
total 301
-rw-r--r-- 1 root root    191 2009-05-06 22:39 default
-rw-r--r-- 1 root root     60 2009-05-06 22:39 device.map
-rw-r--r-- 1 root root   8288 2009-05-06 22:39 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-05-06 22:39 fat_stage1_5
-rw-r--r-- 1 root root   8712 2009-05-06 22:39 jfs_stage1_5
-rw-r--r-- 1 root root   4049 2009-05-06 22:51 menu.lst
-rw-r--r-- 1 root root   7352 2009-05-06 22:39 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-05-06 22:39 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-05-06 22:39 stage1
-rw-r--r-- 1 root root 121740 2009-05-06 22:39 stage2
-rw-r--r-- 1 root root 121740 2009-05-06 22:39 stage2_eltorito
-rw-r--r-- 1 root root   9556 2009-05-06 22:39 xfs_stage1_5
ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt/sda4 && ls -l /mnt/sda4/boot
total 0
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/sda4/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/sda4/proc
ubuntu@ubuntu:~$ sudo chroot /mnt/sda4 /bin/bash
root@ubuntu:/# dpkg --get-selections linux*
linux-firmware					install
linux-generic					install
linux-headers-2.6.27-11				purge
linux-headers-2.6.27-11-generic			purge
linux-headers-2.6.27-12				purge
linux-headers-2.6.27-12-generic			purge
linux-headers-2.6.27-13				purge
linux-headers-2.6.27-13-generic			purge
linux-headers-2.6.27-14				purge
linux-headers-2.6.27-14-generic			purge
linux-headers-2.6.27-7				purge
linux-headers-2.6.27-7-generic			purge
linux-headers-2.6.28-11				install
linux-headers-2.6.28-11-generic			install
linux-headers-generic				install
linux-image-2.6.27-11-generic			deinstall
linux-image-2.6.27-12-generic			deinstall
linux-image-2.6.27-13-generic			deinstall
linux-image-2.6.27-14-generic			deinstall
linux-image-2.6.27-7-generic			deinstall
linux-image-2.6.28-11-generic			install
linux-image-generic				install
linux-libc-dev					install
linux-restricted-modules-2.6.27-11-generic	deinstall
linux-restricted-modules-2.6.27-12-generic	deinstall
linux-restricted-modules-2.6.27-13-generic	deinstall
linux-restricted-modules-2.6.27-14-generic	deinstall
linux-restricted-modules-2.6.27-7-generic	deinstall
linux-restricted-modules-2.6.28-11-generic	install
linux-restricted-modules-common			install
linux-restricted-modules-generic		install
linux-sound-base				install
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ 


```

---

### Post by caljohnsmith on 2009-05-07
OK, I'm not sure if you will be running from the same Live CD session by the time you see this post, so I'm repeating some of the commands just in case; please post the output of all the following commands:
```

sudo umount /dev/sda6
sudo mkdir /mnt/sda4
sudo mount /dev/sda4 /mnt/sda4
sudo mount --bind /dev /mnt/sda4/dev
sudo mount --bind /proc /mnt/sda4/proc
sudo cp /etc/resolv.conf /mnt/sda4/etc/resolv.conf
sudo mount /dev/sda6 /mnt/sda4/boot
sudo chroot /mnt/sda4 /bin/bash
apt-get --reinstall install linux-image-2.6.28-11-generic
ls -l /boot
gedit /boot/grub/menu.lst &
```
After pulling up Grub's menu.lst file with that last command, add the following Ubuntu entries to it:
```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		ab314c00-0f68-423a-82b1-a9bb6d593ffc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=07184754-cad1-4997-b495-322471bc4122 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		ab314c00-0f68-423a-82b1-a9bb6d593ffc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=07184754-cad1-4997-b495-322471bc4122 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic
```
Next exit the chroot environment and run some Grub commands:
```
exit
sudo umount /dev/sda6
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
And please post the output of the commands prior to typing "quit". If all the commands seem to go well, go ahead and reboot to your HDD, and let me know how far you get. We can work from there. :)

John

---

### Post by Lorenzo1985 on 2009-05-07
first posting before quit and or reboot.

Thanks again for the help.

Points of note, menu.lst seemed to already have the entrees mentioned but I added the ones you gave anyway.

gedit command didn't seem to work very well so I used vi instead.

here goes...

```
ubuntu@ubuntu:~$ sudo umount /dev/sda6
ubuntu@ubuntu:~$ sudo mkdir /mnt/sda4
mkdir: cannot create directory `/mnt/sda4': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt/sda4
mount: /dev/sda4 already mounted or /mnt/sda4 busy
mount: according to mtab, /dev/sda4 is already mounted on /mnt/sda4
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/sda4/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/sda4/proc
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/sda4/etc/resolv.conf
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt/sda4/boot
ubuntu@ubuntu:~$ sudo chroot /mnt/sda4 /bin/bash
root@ubuntu:/# apt-get --reinstall install linux-image-2.6.28-11-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/24.3MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 179346 files and directories currently installed.)
Preparing to replace linux-image-2.6.28-11-generic 2.6.28-11.42 (using .../linux-image-2.6.28-11-generic_2.6.28-11.42_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.28-11-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.28-11-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up linux-image-2.6.28-11-generic (2.6.28-11.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.28-11.42 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.28-11.42 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.28-11-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.28-11-generic          
 *  nvidia (180.44)...                                                          nvidia (180.44): Already installed on this kernel.
                                                                         [ OK ]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

root@ubuntu:/# ls -l /boot/
total 13830
-rw-r--r-- 1 root root  525592 2009-04-17 04:34 abi-2.6.28-11-generic
-rw-r--r-- 1 root root   90584 2009-04-17 04:34 config-2.6.28-11-generic
drwxr-xr-x 2 root root    1024 2009-05-07 20:24 grub
-rw-r--r-- 1 root root 7954892 2009-05-07 20:24 initrd.img-2.6.28-11-generic
-rw-r--r-- 1 root root  128796 2009-05-06 23:40 memtest86+.bin
-rw-r--r-- 1 root root 1871601 2009-04-17 04:34 System.map-2.6.28-11-generic
-rw-r--r-- 1 root root    1170 2009-04-17 04:39 vmcoreinfo-2.6.28-11-generic
-rw-r--r-- 1 root root 3522336 2009-04-17 04:34 vmlinuz-2.6.28-11-generic
root@ubuntu:/# gedit /boot/grub/menu.lst &
[1] 15661
root@ubuntu:/# No protocol specified

(gedit:15661): Gtk-WARNING **: cannot open display: :0.0

[1]+  Exit 1                  gedit /boot/grub/menu.lst
root@ubuntu:/# vi /boot/grub/menu.lst
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ sudo umount /dev/sda6
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,5)
root (hd0,5)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/grub/stage2 /grub/menu.lst"... succeeded
Done.
grub> 


```

---

### Post by Lorenzo1985 on 2009-05-07
Unfortunately that wasn't entirely sucessful, however, this is what happened. 

rebooted, it got to the loading grub bit then the screen cleared and the following appeared
```
Boot from (hd0,3) ext4 07184754-cad1-4997-b495-322471bc4122

Error 15: File no found

Press any key to continue...
```

pressed any key and a grub menu came up. Now I'm guessing here that the second set of ubuntu 9.04s is the one I pasted from you, so I'll try that.

That results in the quoted text occurring again, as does the first entry.

---

### Post by jobeirne on 2009-05-07
Hey guys, I'm in the same boat as Lorenzo. I've followed the steps specified by John analogously up to this point.

Although I think my problem was rooted in removing the wrong packages in Jaunty -- at some point I ran a "sudo apt-get remove cups*" and there were some pretty heavy-handed removals before that.

Strangely, the last thing I saw before rebooting into a memtest was a messaged displayed at chroot... Something to the effect of apt-get saying "hey, I've got these two packages you can remove 'cause they're unowned: grub and grub-common". I'm not so sure it was actually "grub-common", but it was something to that effect.

---

### Post by caljohnsmith on 2009-05-07
OK, we're at least making some progress. I realized I made a mistake in those Grub entries I gave you to put in your menu.lst (sorry about that), because there should be no /boot directory in the kernel/initrd lines:
```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		ab314c00-0f68-423a-82b1-a9bb6d593ffc
kernel		/vmlinuz-2.6.28-11-generic root=UUID=07184754-cad1-4997-b495-322471bc4122 ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		ab314c00-0f68-423a-82b1-a9bb6d593ffc
kernel		/vmlinuz-2.6.28-11-generic root=UUID=07184754-cad1-4997-b495-322471bc4122 ro  single
initrd		/initrd.img-2.6.28-11-generic
```
Also, I would recommend changing the "hiddenmenu" line in your menu.lst to "#hiddenmenu" so you will see the Grub menu by default on start up. After you've done that, go ahead and reboot and let me know if you make it any further this time when you select Ubuntu from your Grub menu. We can work from there.

John

---

### Post by jobeirne on 2009-05-07
No dice.
Still stuck with a "file not found" error.

---

### Post by caljohnsmith on 2009-05-07
OK, just to double-check things, how about posting your full menu.lst again, and also please post:
```

sudo umount /dev/sda6
sudo mount /dev/sda6 /mnt && ls -l /mnt
```
Next, go ahead and reboot, and when you get the Grub menu on start up, press "c" to get the Grub command line, and then do:
```
grub> root (hd0,3)
```
Then type the following command **without pressing enter**:
```
grub> null /
```
And instead press TAB for tab-completion; you should see a directory listing of your sda4's root directory if that works. Let me know if that works or not. 

John

---

### Post by Lorenzo1985 on 2009-05-07
ok, going to reboot now

```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ ls -l /mnt
total 13830
-rw-r--r-- 1 root root  525592 2009-04-17 03:34 abi-2.6.28-11-generic
-rw-r--r-- 1 root root   90584 2009-04-17 03:34 config-2.6.28-11-generic
drwxr-xr-x 2 root root    1024 2009-05-07 19:27 grub
-rw-r--r-- 1 root root 7954892 2009-05-07 19:24 initrd.img-2.6.28-11-generic
-rw-r--r-- 1 root root  128796 2009-05-06 22:40 memtest86+.bin
-rw-r--r-- 1 root root 1871601 2009-04-17 03:34 System.map-2.6.28-11-generic
-rw-r--r-- 1 root root    1170 2009-04-17 03:39 vmcoreinfo-2.6.28-11-generic
-rw-r--r-- 1 root root 3522336 2009-04-17 03:34 vmlinuz-2.6.28-11-generic

```

---

### Post by Lorenzo1985 on 2009-05-07
before this idiot rudely interrupted....

Bingo, successful boot. Thankyou very much!!

removing the /boot from the entries you gave me solved the issue.

Thanks loads

---

### Post by caljohnsmith on 2009-05-07
That's great news, glad to hear you can now boot Ubuntu again. Cheers and enjoy Ubuntu. :)

John

---

