---
title: "Disk boot failure, ubuntu, windows 7 related"
date: 2009-05-12
forum: General Help
---

### Post by superarmy on 2009-05-12
I tried installing Windows 7 to a 50Gb partition on my main Hard Drive. After install and now every time I try and boot up my computer (using live CD currently) I receive a boot drive failure. I'm having a hard time pin-pointing the problem, though it seems it cannot be attributed to grub as reinstalling it did not help, any ideas? Using 9.04 if that helps.

---

### Post by lindsay7 on 2009-05-12
I you are using the Ubuntu cd so forget my first response.  Did you install Ubuntu yet or are you just using it to access the internet now?

---

### Post by elliotn on 2009-05-12
It might be your corrupt hard disk, yes u may need to reformat that partition, u cant format it with windows cd, Well I couldnt so I used ubuntu cd to format it and then used xp

---

### Post by superarmy on 2009-05-13
Important note: Both OS's are fully installed. Ubuntu has been installed for a year prior.

Ubuntu Live Cd access show me both partitions obtain all appropriate files needed to run each OS.

---

### Post by lindsay7 on 2009-05-13
Ok, I copied this from another post, this will tell what is going on with your drive and what is installed in terms of the mbr and what is in the grub file. This should tell us what is missing and what needs to be done.


Please download this and place it on your Desktop in Ubuntu:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

You will have you run it, so that we can gather more information about your hard drive setup and boot process to troubleshoot the problem more clearly.

After you download it to the Desktop, right-click it and click Properties, then click the Permissions tab and check the box at the bottom of the window that 'allows executing'.

Then click the Applications menu at the top right of your screen, followed by the Accessories menu and then click Terminal. A black window will come up, in it type the following commands, ending each line with a press of the Enter key:

Code:

cd ~/Desktop
sudo ./boot*.sh

Please remember that in Linux, everything is case sensitive. Therefore, a lowercase 'd' is different than an uppercase 'D'. Also, you will be prompted for the password you gave when you installed Ubuntu whenever you use the 'sudo' command. The 'sudo' command escalates privileges and in this case is needed to properly view the hard drives and boot process.

After you have done this, it should place a Results.txt file on your desktop. Double-click that file and select Edit->Copy. Then return here and start a new reply message. In this message, click the # sign at the top of the message editor box and this will give you CODE tags; click between these tags ({code]here[/code}) and paste the contents that you copied from the Results.txt file.

---

### Post by superarmy on 2009-05-13
Thanks for helping, here are the results

```
=> Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ddd13

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   512,007,614   512,007,552  83 Linux
/dev/sda2    *    512,007,615   614,582,639   102,575,025   7 HPFS/NTFS
/dev/sda3         614,582,640   625,137,344    10,554,705   5 Extended
/dev/sda5         614,582,703   625,137,344    10,554,642  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f9c798a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,064   488,392,002   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="60faa73a-f8e5-4997-9cb3-4ddd92eb9713" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="B2E08C31E08BFA3D" TYPE="ntfs" 
/dev/sda5: UUID="9389281a-b185-4d86-96d5-5348ef8e7f98" TYPE="swap" 
/dev/sdb1: LABEL="M-)M-PM-jM-V4M-YM-2M-2M-(M-4M-X" UUID="486F-035C" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 

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
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


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
# kopt=root=UUID=60faa73a-f8e5-4997-9cb3-4ddd92eb9713 ro

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

title		Ubuntu 9.04, kernel 2.6.28-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=60faa73a-f8e5-4997-9cb3-4ddd92eb9713 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=60faa73a-f8e5-4997-9cb3-4ddd92eb9713 ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=60faa73a-f8e5-4997-9cb3-4ddd92eb9713 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=60faa73a-f8e5-4997-9cb3-4ddd92eb9713 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=60faa73a-f8e5-4997-9cb3-4ddd92eb9713 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=60faa73a-f8e5-4997-9cb3-4ddd92eb9713 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=60faa73a-f8e5-4997-9cb3-4ddd92eb9713 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=60faa73a-f8e5-4997-9cb3-4ddd92eb9713 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, kernel 2.6.27-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=60faa73a-f8e5-4997-9cb3-4ddd92eb9713 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=60faa73a-f8e5-4997-9cb3-4ddd92eb9713 ro  single
initrd		/boot/initrd.img-2.6.27-10-generic

title		Ubuntu 9.04, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=60faa73a-f8e5-4997-9cb3-4ddd92eb9713 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=60faa73a-f8e5-4997-9cb3-4ddd92eb9713 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title           Windows 7
root            (hd0,1)

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=60faa73a-f8e5-4997-9cb3-4ddd92eb9713 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9389281a-b185-4d86-96d5-5348ef8e7f98 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 151.8GB: boot/grub/menu.lst
 151.8GB: boot/grub/stage2
 170.0GB: boot/initrd.img-2.6.27-10-generic
 202.3GB: boot/initrd.img-2.6.27-11-generic
 162.2GB: boot/initrd.img-2.6.27-14-generic
 186.0GB: boot/initrd.img-2.6.27-7-generic
 151.8GB: boot/initrd.img-2.6.28-11-generic
 187.7GB: boot/initrd.img-2.6.28-12-generic
  81.7GB: boot/vmlinuz-2.6.27-10-generic
 202.3GB: boot/vmlinuz-2.6.27-11-generic
 193.2GB: boot/vmlinuz-2.6.27-14-generic
 124.6GB: boot/vmlinuz-2.6.27-7-generic
  56.3GB: boot/vmlinuz-2.6.28-11-generic
 209.4GB: boot/vmlinuz-2.6.28-12-generic
 187.7GB: initrd.img
 151.8GB: initrd.img.old
 209.4GB: vmlinuz
  56.3GB: vmlinuz.old
```

---

### Post by superarmy on 2009-05-13
Problem isolated. I'll run this through. I used gparted to format the Windows drive and from there I went to the bios and reassigned top priority to the OS driver as 7 had switched it. When I tried installing again this time, my boot devices have be turned into slave drives and my slave drive has become a master drive.....

This is weird....

---

### Post by lindsay7 on 2009-05-13
Let's try to edit you grub menu

in the terminal type "sudo gedit boot/grub/menu.lst"

then add the lines to the end of the file so that it looks like this

title           Windows 7
root            (hd0,1)
savedefault
makeactive
chainloader     +1

the save the file

Then lets make sure that the grub is correct so do this with the live cd

"sudo grub"

"find /boot/grub/stage2"

this will give you a result like (hdx,y), use the result that you get in the following

"root (hdx,y)"
"setup (hd0)"
"quit"

Reboot your computer without the live cd. Note you should have your bios set to boot off of the drive that is hd0 which is where windows and Ubuntu are located.

There is some stuff in you grub file that I do not completely understand so I am not sure if this will fix it.  If this does not do the trick, I woud run the boot script again so that it is updated with the changes that we will do and start a new post asking for help to fix this. You should get some more attention that way.


_**P.S.  This is very important.**_  I just noticed that your windows boot instructions are above the line that reads 
"### END DEBIAN AUTOMAGIC KERNELS LIST"  You must delete the lines that are above that line the now read
"title           Windows 7
root            (hd0,1)"

Add the whole stanza
"title           Windows 7
root            (hd0,1)
savedefault
makeactive
chainloader     +1"

below that line and save the file as pointed out above.

---

