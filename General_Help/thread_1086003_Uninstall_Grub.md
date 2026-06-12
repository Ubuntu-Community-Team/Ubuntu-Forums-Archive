---
title: "Uninstall Grub"
date: 2009-03-03
forum: General Help
---

### Post by Berri82 on 2009-03-03
Hello,

I always get error on Stage 1.5 read error, I'm new on Linux. How do I do to completely uninstall Grub?

I tried to reinstall Grub in order to fix the error but with no success although the installation worked fine. I know I have some bad sectors on HD so I'm assuming it has something to do with this. I'm currently using Ubuntu Live CD and installed ubuntu on the disc but each time I reboot the computer Grub error appears as always.

Thanks for any comment/help on this issue,

---

### Post by woodenbrick on 2009-03-03
You don't want to uninstall grub, this is your bootloader, which loads up linux/other operating system's at startup.  

It's not 100% clear from your question, but is Ubuntu installed on your hard drive?  If so boot from the live disc (not hard drive) and follow these instructions:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Berri82 on 2009-03-04
I don't want to have 2 OS, I only want to have Ubuntu running on the system. 
I installed Ubuntu on my hard drive but when I reboot it doesn't load well and gives the Stage 1.5 read error ALWAYS. So I decided to install Windows XP to see if I could at least use windows but it doesn't format the hard drive because of the bad sectors I mentioned earlier, and thereby setup fails. What should I do? I can only access the computer through the Live CD thus far.

Thank you for your time again,

---

### Post by Berri82 on 2009-03-04
I know a solution is buying a new hard drive but that's not going to happen soon so I'm trying to fix this Grub error thing since ubuntu installation supposedly worked well (until i reboot that is).

---

### Post by Berri82 on 2009-03-04
Any suggestions?

---

### Post by woodenbrick on 2009-03-05
Does it give a more detailed error message than that? Like an error number?  

Something you could try (can't promise it will work)

Load up your ubuntu live cd.  Mount your hard drive (you can usually do this just by pressing Places -> Name of Drive).  I assume it mounts the hard drive in /media/disk though you will need to check this.  Run the following commands from a terminal:
  
cd /media/disk/boot/grub
mkdir ./backupstage1_5
mv *stage1_5 ./backupstage1_5
grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit 

reboot and see if this worked.

---

### Post by Berri82 on 2009-03-05
No, it just says "Grub Stage 1.5 read error".

```
ubuntu@ubuntu:/media/disk/boot/grub$ mv *stage1_5 ./backupstage1_5
mv: cannot move `backupstage1_5' to a subdirectory of itself, `./backupstage1_5/backupstage1_5'
mv: cannot move `e2fs_stage1_5' to `./backupstage1_5/e2fs_stage1_5': Permission denied
mv: cannot move `fat_stage1_5' to `./backupstage1_5/fat_stage1_5': Permission denied
mv: cannot move `jfs_stage1_5' to `./backupstage1_5/jfs_stage1_5': Permission denied
mv: cannot move `minix_stage1_5' to `./backupstage1_5/minix_stage1_5': Permission denied
mv: cannot move `reiserfs_stage1_5' to `./backupstage1_5/reiserfs_stage1_5': Permission denied
mv: cannot move `xfs_stage1_5' to `./backupstage1_5/xfs_stage1_5': Permission denied
```

Should't I be using the sudo command thing to get access?

---

### Post by Berri82 on 2009-03-05
I rebooted and tried again:

```
ubuntu@ubuntu:~$ cd /media/disk/boot/grub
ubuntu@ubuntu:/media/disk/boot/grub$ sudo mkdir ./backupstage1_5
mkdir: cannot create directory `./backupstage1_5': File exists
ubuntu@ubuntu:/media/disk/boot/grub$ sudo mv *stage1_5 ./backupstage1_5
mv: cannot move `backupstage1_5' to a subdirectory of itself, `./backupstage1_5/backupstage1_5'
```

:(

---

### Post by woodenbrick on 2009-03-05
sorry that was a stupid thing to name the backup folder, but it should have copied them all in anyway. (apart from itself!)
To check:
cd /media/disk/boot/grub/backupstage1_5
ls should give you a list of files that were moved.
If so, continue with the rest of my instructions

Edit: and yes, use sudo

---

### Post by Berri82 on 2009-03-07
Ok, files were moved properly but when I execute Grub it goes as follows:

```
grub> root (hd0,0)

Error 21: Selected disk does not exist

grub> root (hd0,1)

Error 21: Selected disk does not exist

grub> root (hd1,0)

Error 21: Selected disk does not exist

grub> 
```

What should I now?

EDIT: I forgot to use sudo, am going to reboot to see if it worked.

---

### Post by woodenbrick on 2009-03-07
if you type:
root (hd
then hit tab, grub should give you a list of hard drives available, or complete it fully.

---

### Post by Berri82 on 2009-03-07
Grub loading... Stage2 read error. Nothing else is said.

Help? :)

---

### Post by woodenbrick on 2009-03-08
I'm not sure what else to suggest, it looks as though maybe the first sector of your hard drive where the Master Boot Record sits is corrupted, which might not be fixable.

The only other ideas I have are to do a full reinstall of Ubuntu (unlikely to work, but you never know) or have your /boot directory on a separate flash drive. Your computer would boot off this then use the hard drive as its root directory. I have never done this though, don't know exactly how to set it up.

---

### Post by meierfra. on 2009-03-08
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by Berri82 on 2009-03-08
Results are as follows:

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks at sector 215611799 
    of the same hard drive for the stage2 file. A stage2 file is at this 
    location on /dev/sda. Stage2 looks on partition #1 for /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd55a5eab

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   231,480,584   231,480,522  83 Linux
/dev/sda2         231,480,585   234,436,544     2,955,960   5 Extended
/dev/sda5         231,480,648   234,436,544     2,955,897  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="48e03c6f-093c-4a12-8344-ea3c5f0c08e6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="6dcd8317-6204-4489-b03b-63eda2f46c30" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /media/disk type ext3 (rw,nosuid,nodev)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=48e03c6f-093c-4a12-8344-ea3c5f0c08e6 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=48e03c6f-093c-4a12-8344-ea3c5f0c08e6 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=48e03c6f-093c-4a12-8344-ea3c5f0c08e6 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=48e03c6f-093c-4a12-8344-ea3c5f0c08e6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=6dcd8317-6204-4489-b03b-63eda2f46c30 none            swap    sw              0       0
/dev/scd2       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

=================== sda1: Location of files loaded by Grub: ===================


 110.3GB: boot/grub/menu.lst
 110.3GB: boot/grub/stage2
 110.3GB: boot/initrd.img-2.6.22-14-generic
 110.4GB: boot/initrd.img-2.6.22-14-generic.bak
 110.4GB: boot/vmlinuz-2.6.22-14-generic
 110.3GB: initrd.img
 110.4GB: vmlinuz
```

Anything wrong with them?

---

### Post by meierfra. on 2009-03-08
Grub is configured correctly. Given your problems with  bad sectors, I suggest  to run a file system check.

Boot from the Ubuntu live CD, open a terminal and type: 

```

sudo umount /dev/sda1
sudo e2fsck -yvc /dev/sda1
```

(you can ignore any "/dev/sda1 not mounted" error message from the first command) 

If "e2fsck" fixes some errors, run it again.

---

### Post by Berri82 on 2009-03-09
```
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda1: clean, 101022/14483456 files, 995276/28935065 blocks
```

I guess it didn't help much. What else should I do?

---

### Post by meierfra. on 2009-03-09
Try 

```

sudo umount /dev/sda1
sudo e2fsck -fyvc /dev/sda1
```
("the  "-f" makes sure that  the file sytem check is run, even if "e2fsck" thinks that the file system is clean)

If this does not help, try purging the grub stage files and then reinstall grub:

```

sudo mount /dev/sda1 /mnt
sudo cp  /etc/resolv.conf /mnt/etc/resolv.conf
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc //mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt /bin/bash
apt-get install --purge grub
grub-install /dev/sda
exit

```

---

### Post by Berri82 on 2009-03-11
File system check took a lot of time but finally came to an end:

```
ubuntu@ubuntu:~$ sudo e2fsck -fyvc /dev/sda1
e2fsck 1.40.2 (12-Jul-2007)
Checking for bad blocks (read-only test): done                                
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

  101022 inodes used (0.70%)
     105 non-contiguous inodes (0.1%)
         # of inodes with ind/dind/tind blocks: 4407/33/0
  995280 blocks used (3.44%)
       4 bad blocks
       1 large file

   77476 regular files
   10779 directories
     132 character device files
      26 block device files
       2 fifos
       0 links
   12598 symbolic links (11564 fast symbolic links)
       0 sockets
--------
  101013 files
ubuntu@ubuntu:~$
```

I'll check in the morning if that solved Grub error when the computer will be turned back on. Hopefully it will fix although I have a feeling it don't. If not i'll follow your other instructions and cross my fingers that will be the final solution to this imbroglio.

---

### Post by Berri82 on 2009-03-12
```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc //mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# apt-get install --purge grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 253 not upgraded.
root@ubuntu:/# grub-install /dev/sda
rm: cannot remove `/boot/grub/backupstage1_5': Is a directory
root@ubuntu:/# 

```
:-k What now? Thank you in advance for your time

---

### Post by meierfra. on 2009-03-12
Sorry, I messed up the instruction. After "sudo chroot /mnt /bin/bash" it should be


```
apt-get purge grub
apt-get install grub
grub-install /dev/sda

```

(You might also run "sudo e2fsck -fyvc /dev/sda1"
one more time before you try this. )

Even if this works, the bad blocks are a sign that your hard drive is failing. So you should back up all your important data and consider getting a new hard drive.

---

### Post by Berri82 on 2009-03-12
I know, I am only trying to see if I can fix this error in the meantime. I'll post the results here when file system check and grub reinstall are done.

---

### Post by Berri82 on 2009-03-12
Everything went ok except the last command where supposedly grub is installed:

```
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# apt-get purge grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub*
0 upgraded, 0 newly installed, 1 to remove and 253 not upgraded.
Need to get 0B of archives.
After unpacking 827kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 88931 files and directories currently installed.)
Removing grub ...
root@ubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 0 to remove and 253 not upgraded.
Need to get 0B/375kB of archives.
After unpacking 827kB of additional disk space will be used.
Selecting previously deselected package grub.
(Reading database ... 88885 files and directories currently installed.)
Unpacking grub (from .../grub_0.97-29ubuntu4_i386.deb) ...
Setting up grub (0.97-29ubuntu4) ...

root@ubuntu:/# grub-install /dev/sda
rm: cannot remove `/boot/grub/backupstage1_5': Is a directory
root@ubuntu:/# 
```

What happen if I don't install Grub back on the computer? And what should I do to install it again then, since the installation with these instructions didn't work. Thank you again for your time and patience,

---

### Post by meierfra. on 2009-03-12
> rm: cannot remove `/boot/grub/backupstage1_5': Is a directory


It seems that grub-install got confused by the "backupstage1_5" directory you created. 

Try this

```
sudo mount /dev/sda1 /mnt 
sudo rm -r /mnt/boot/grub/backupstage1_5
sudo grub-install --root-directory=/mnt --recheck /dev/sda
```

---

### Post by Berri82 on 2009-03-13
```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt 
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo rm -r /mnt/boot/grub/backupstage1_5
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt --recheck /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/sda
ubuntu@ubuntu:~$ 
```

How to check if device map, whatever that is, is correct or not?

---

### Post by meierfra. on 2009-03-13
Your device map is ok. Just reboot and hope for the best.

---

### Post by Berri82 on 2009-03-14
It retreated to Stage 1.5. So I guess I've pretty much tried all possibilities available to overcome Grub error, no? Thank you all for your help and time! 
If anyone sees any other options available to surpass this error let me know by posting here. :popcorn:

---

### Post by meierfra. on 2009-03-14
Let's see what happens if grub is installed to the first sector of the Ubuntu partition instead of the MBR:


Boot from the LiveCD, open a terminal, install grub to (hd0,0):

```
sudo grub
root (hd0,0)
setup (hd0,0)
quit
```

and install a windows type mbr:

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Then try to boot into Ubuntu.

---

### Post by Berri82 on 2009-03-19
Because it is the first time lilo is installed on this computer, it said after setup was done it would be imperative to do liloconfig(8) and something else /*/*/ which I didn't do any of those.

I'm rebooting now and see if it worked.

---

### Post by Berri82 on 2009-03-19
Stage2 Read Error..

What else should I do?

---

### Post by meierfra. on 2009-03-19
Lets see whether SuperGrub is able to boot your Ubuntu.

Get the SuperGrubDisk iso from  [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/index.php?pid=5")
Burn the iso to a CD.
 Boot from the CD.
At the first screen choose

!Linux! (1)  Auto

If you are lucky this will boot you into Ubuntu. The SuperGrub CD comes with its own stage files, so hopefully this avoids the problems you have with your own stage files.

This is not  permanent solution, but at least we will know whether it is possible to boot into your Ubuntu partition and we can work from there.

---

### Post by Trigsu on 2009-03-20
I'll lend this topic for a bit. I have dualboot system. XP and Ubuntu. My Ubuntu HD is cracking up, and I need to send it to warranty repairs/change. Meanwhile I'll be using Windows XP (long time no seen).

**How to I completely remove GRUB from my original "C:" (Windows system) - drive?**

When I get new HD in return some day, I'll install fresh Ubuntu in there.

Edit:
Searching for more:
"I can confirm that:
FIXMBR
DID WORK"

---

### Post by Berri82 on 2009-03-22
bzip2-100-x86-win32.exe 	
sgd_0.9588.iso 	
sgd_0.9588.iso.gz 	
sgd_0.9590.iso 	
sgd_0.9590.iso.gz 	
sgd_0.9598.iso 	
sgd_0.9598.iso.bz2 	
sgd_0.9642.iso 	
sgd_0.9642.iso.bz2 	
sgd_0.9662.iso 	
sgd_0.9662.iso.bz2 	
sgd_0.9662.iso.zip 	
sgd_0.9667.iso 	
sgd_0.9667.iso.bz2 	
sgd_0.9667.iso.gz 	
sgd_0.9667.iso.zip 	
sgd_0.9670.iso 	
sgd_0.9670.iso.bz2 	
sgd_0.9670.iso.gz 	
sgd_0.9670.iso.zip 	
super_grub_disk_0.9689.iso 	
super_grub_disk_0.9701.iso 	
super_grub_disk_0.9701.iso.bz2 	
super_grub_disk_0.9710.iso 	
super_grub_disk_0.9711.iso 	
super_grub_disk_0.9716.iso 	
super_grub_disk_0.9718.iso 	
super_grub_disk_0.9722.iso 	
super_grub_disk_0.9725.iso 	
super_grub_disk_0.9726.iso 	
super_grub_disk_0.9763.iso 	
super_grub_disk_0.9770.iso 	
supergrubdisk_0.9677.iso 	
supergrubdisk_0.9677.iso.bz2 	
supergrubdisk_0.9677.iso.gz 	
supergrubdisk_0.9677.iso.zip 	

Which one of those should I burn? I downloaded super_grub_disk_0.9770.iso file but am having difficulties to make a boot disc because burn process fails. Later on I will try again to burn the iso and report here afterwards.

---

### Post by pheonixdragon on 2009-03-22
Try this:

fdisk /mbr

This will overwrite grub bootloader and install Microsoft bootloader. If you want Ubuntu back then you have to reinstall again.:KS

---

### Post by meierfra. on 2009-03-22
> I downloaded super_grub_disk_0.9770.iso 

That should be fine. But if you have problems, Mirror0 has a slightly newer version:

[http://forjamari.linex.org/frs/download.php/1133/super_grub_disk_0.9774.iso](http://forjamari.linex.org/frs/download.php/1133/super_grub_disk_0.9774.iso)

---

