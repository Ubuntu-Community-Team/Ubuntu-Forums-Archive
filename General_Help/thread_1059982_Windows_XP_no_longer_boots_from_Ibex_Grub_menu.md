---
title: "Windows XP no longer boots from Ibex Grub menu"
date: 2009-02-04
forum: General Help
---

### Post by ubalderdash on 2009-02-04
Choosing Windows XP in my Grub window no longer works. Much to my regret I do still need Windows sometimes. 
Can anyone help me please?

---

### Post by caljohnsmith on 2009-02-04
How about opening a terminal (Applications > Accessories > Terminal) and posting::
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
And please identify your Windows partition. We can work from there if you want.

---

### Post by ubalderdash on 2009-02-04
Is this the information you require?

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd1aad1aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   253296854   126648396    7  HPFS/NTFS
/dev/sda2       253296855   625137344   185920245    5  Extended
/dev/sda5       253296918   609971984   178337533+  83  Linux
/dev/sda6       609972048   625137344     7582648+  82  Linux swap / Solaris


Thanks for responding!

---

### Post by caljohnsmith on 2009-02-04
How about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And at the very end of the file add:
```
title Windows 
root (hd0,0)
chainloader +1
```
Reboot, choose Windows from Grub, and let me know how far you get. We can work from there if necessary.

---

### Post by ubalderdash on 2009-02-04
That new link to "Windows" from the Grub menu gave me the same result as before>

That is...

"A disk error occured
Press Ctrl-Alt-Del to restart"

---

### Post by caljohnsmith on 2009-02-04
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by ubalderdash on 2009-02-04
As per your instructions...


```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
Record 6 has no FILE magic (0x0)
Failed to open inode FILE_Bitmap: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
Record 6 has no FILE magic (0x0)
Failed to open inode FILE_Bitmap: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd1aad1aa

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   253,296,854   253,296,792   7 HPFS/NTFS
/dev/sda2         253,296,855   625,137,344   371,840,490   5 Extended
/dev/sda5         253,296,918   609,971,984   356,675,067  83 Linux
/dev/sda6         609,972,048   625,137,344    15,165,297  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="748451068450CC6C" TYPE="ntfs" 
/dev/sda5: UUID="8654b7a6-e7b3-416c-8874-0c5549cfcaa1" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="f0aa2a0f-d0eb-425d-982e-40d50ac1468a" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/icare/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=icare)

=========================== sda5/boot/grub/menu.lst: ===========================

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=8654b7a6-e7b3-416c-8874-0c5549cfcaa1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8654b7a6-e7b3-416c-8874-0c5549cfcaa1

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		8654b7a6-e7b3-416c-8874-0c5549cfcaa1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8654b7a6-e7b3-416c-8874-0c5549cfcaa1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		8654b7a6-e7b3-416c-8874-0c5549cfcaa1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8654b7a6-e7b3-416c-8874-0c5549cfcaa1 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		8654b7a6-e7b3-416c-8874-0c5549cfcaa1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8654b7a6-e7b3-416c-8874-0c5549cfcaa1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8654b7a6-e7b3-416c-8874-0c5549cfcaa1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8654b7a6-e7b3-416c-8874-0c5549cfcaa1 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8654b7a6-e7b3-416c-8874-0c5549cfcaa1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title Windows 
root (hd0,0)
chainloader +1








=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8654b7a6-e7b3-416c-8874-0c5549cfcaa1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=f0aa2a0f-d0eb-425d-982e-40d50ac1468a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 294.5GB: boot/grub/menu.lst
 294.5GB: boot/grub/stage2
 294.5GB: boot/initrd.img-2.6.27-11-generic
 294.5GB: boot/initrd.img-2.6.27-7-generic
 294.5GB: boot/vmlinuz-2.6.27-11-generic
 294.5GB: boot/vmlinuz-2.6.27-7-generic
 294.5GB: initrd.img
 294.5GB: initrd.img.old
 294.5GB: vmlinuz
 294.5GB: vmlinuz.old

```

---

### Post by caljohnsmith on 2009-02-04
It looks like there's something wrong with your Windows file system, because the Windows partition is not even mountable right now. How about booting your Windows Install CD, go to the "recovery console" and do:
```
chkdsk /r
```
And run that as many times as it takes until it reports no errors. Then reboot, and let me know how far you get booting Windows from Grub.

---

### Post by ubalderdash on 2009-02-04
I have run the "chkdsk /r" command twice and rebooted as instructed but a new message is now telling me that the System32/hal.dll file is either missing or corrupted...

---

### Post by caljohnsmith on 2009-02-04
OK, how about posting:
```
sudo mount /dev/sda1 /mnt && ls -l /mnt && cat /mnt/boot.ini
```

---

### Post by ubalderdash on 2009-02-04
Results

```
total 2096117
-rwxrwxrwx 1 root root          0 2008-11-21 17:21 AUTOEXEC.BAT
-rwxrwxrwx 1 root root     507766 2009-02-04 19:19 bootex.log
-rwxrwxrwx 1 root root        211 2008-11-23 19:08 boot.ini
-rwxrwxrwx 1 root root          0 2008-11-21 17:21 CONFIG.SYS
drwxrwxrwx 1 root root       4096 2008-11-21 18:18 Documents and Settings
drwxrwxrwx 1 root root      12288 2009-02-04 18:55 found.000
-rwxrwxrwx 1 root root          0 2008-11-21 17:21 IO.SYS
-rwxrwxrwx 1 root root          0 2008-11-21 17:21 MSDOS.SYS
-rwxrwxrwx 1 root root      47564 2008-04-14 10:00 NTDETECT.COM
-rwxrwxrwx 1 root root     250048 2008-04-14 10:00 ntldr
-rwxrwxrwx 1 root root 2145386496 2009-01-24 13:25 pagefile.sys
drwxrwxrwx 1 root root      12288 2009-01-24 12:38 Program Files
drwxrwxrwx 1 root root          0 2008-11-21 22:03 RECYCLER
-rwxrwxrwx 2 root root      14574 2008-11-25 18:26 st330AdaptorMgr.log
-rwxrwxrwx 2 root root     175760 2008-11-25 18:28 stInstall.log
drwxrwxrwx 1 root root       4096 2008-11-21 18:17 System Volume Information
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

---

### Post by caljohnsmith on 2009-02-04
From that directory listing, you are missing your entire "C:\WINDOWS" folder; that folder basically holds the entire Windows operating system. Did you delete it by accident at some point? I think about the only thing you can do now is to grab your personal files from that partition and then reinstall Windows. If you still have that partition mounted on /mnt, you could access your personal files by doing:
```
nautilus /mnt/"Documents and Settings" &
```
And that will pull up a file browser where you can go through the Windows "Documents and Settings" directory. Good luck and let me know how it goes.

---

### Post by ubalderdash on 2009-02-04
It would seem that even the documents and settings have been either deleted or corrupted. I suspect this may have been caused by a virus attack as the machine was recently left connected to the web without protection and with Windows running. Perhaps a good reason to try and recover the space wasted by Windows.

Is it fairly easy to reformat that space as Ext3 ?

In any case your help has been extremely useful and very much appreciated.

Thanks!

---

### Post by caljohnsmith on 2009-02-04
I agree, sounds like it probably was a virus since you didn't have any virus protection in Windows. It's really easy to reformat it as ext3 at least; you can use the gparted partition editor for example, so you will probably first have to install gparted:
```
sudo apt-get install gparted
```
Or the Live CD all ready comes with gparted. Once installed, you can run it by going to System > Admin > Partition Editor. Make sure sda1 is unmounted first though:
```
sudo umount /dev/sda1
```
And then you can use gparted to format sda1 as you please. Good luck and let me know how it goes.

---

### Post by ubalderdash on 2009-02-04
How nice! All reformated and done but one thing leads to another and I would now like to remove the Grub menu. Any more brilliant ideas?

---

