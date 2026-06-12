---
title: "Installed Ubuntu, wiped out Windows boot"
date: 2009-01-11
forum: General Help
---

### Post by DeadTaco on 2009-01-11
First let me explain the situation before I installed ubuntu.
I had Windows Vista on one partition, and Windows XP on the other.  I find vista to be useless, so I installed Ubuntu over it.  Unfortunately, as I later found out, I think that partition was controlling the boot menu.  Now Grub can't see my Windows XP partition at all.

EDIT: Forgot an important note.  When I select windows from the menu, it gives the error:
Error 12: Invalid Device Requested


I've done tons of forum and net searching, and came to many solutions -- none have worked.  I made sure boot.ini, ntldr, and ntdetect.com were all on the partition with windows XP.  I've tried setting the bootable flag with Gparted, and that didn't work.  I've tweaked the grub menu.lst file without any success.

Here is my current fdisk -lu 
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   187510679    93754316   83  Linux
/dev/sda2       187510680   398283479   105386400    f  W95 Ext'd (LBA)
/dev/sda5   *   193505823   398275919   102385048+   7  HPFS/NTFS
/dev/sda6       187510806   193502924     2996059+  82  Linux swap / Solaris

```

I tried to use KGrubEditor to add a Windows boot option, and failed there as well.

Here is the windows line from my menu.lst
```

title Windows XP
root (hd0,4)
chainloader +1
savedefault
makeactive

```

I have removed the 'makeactive' line after setting the bootable flag in Gparted, but it didn't seem to make a difference.

Any suggestions?
Thanks!

EDIT #2: Do I have to tweak the boot.ini file in the Windows folder?  Currently, it says:
```

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```
Since I added a swap partition and ubuntu root partition where the vista partition used to be, then did the partition numbers change?

---

### Post by sendblink23 on 2009-01-11
I know this is worng to be mentioned...  but it seems fair.. since your Ubuntu & Windows XP issues

Honestly that is extremely weird I would suggest  back up everything (Files you need that are very important) on DVDs or an External Hard drive ***Of Your Current UBUNTU***

Since its pretty messed up the errors that you are getting, since your ubuntu Cover up .. on the **EX** Vista partition

U know what I mean ... reinstall Ubuntu, with the LiveCD ..  *First Delete through Gparted the current Ubuntu partitions ext3 & swap*.. afterwards, Expand yoru Windows XP Partition COMPLETELY .. choose Apply....  and afterwards .. still inside LiveCD you should be able to install it again perfectly..  I'm pretty sure this time, Windows XP will be recognized in your New Grub list, and yoru ubuntu will work perfectly as it should with no errors



> **DeadTaco said:**
> First let me explain the situation before I installed ubuntu.
I had Windows Vista on one partition, and Windows XP on the other.  I find vista to be useless, so I installed Ubuntu over it.  Unfortunately, as I later found out, I think that partition was controlling the boot menu.  Now Grub can't see my Windows XP partition at all.

EDIT: Forgot an important note.  When I select windows from the menu, it gives the error:
Error 12: Invalid Device Requested


I've done tons of forum and net searching, and came to many solutions -- none have worked.  I made sure boot.ini, ntldr, and ntdetect.com were all on the partition with windows XP.  I've tried setting the bootable flag with Gparted, and that didn't work.  I've tweaked the grub menu.lst file without any success.

Here is my current fdisk -lu 
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   187510679    93754316   83  Linux
/dev/sda2       187510680   398283479   105386400    f  W95 Ext'd (LBA)
/dev/sda5   *   193505823   398275919   102385048+   7  HPFS/NTFS
/dev/sda6       187510806   193502924     2996059+  82  Linux swap / Solaris

```

I tried to use KGrubEditor to add a Windows boot option, and failed there as well.

Here is the windows line from my menu.lst
```

title Windows XP
root (hd0,4)
chainloader +1
savedefault
makeactive

```

I have removed the 'makeactive' line after setting the bootable flag in Gparted, but it didn't seem to make a difference.

Any suggestions?
Thanks!

EDIT #2: Do I have to tweak the boot.ini file in the Windows folder?  Currently, it says:
```

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```
Since I added a swap partition and ubuntu root partition where the vista partition used to be, then did the partition numbers change?

---

### Post by DeadTaco on 2009-01-11
Sendblink, I'm not sure I understood your instructions.

It doesn't matter now anyway.  Someone suggested that I use a program called "testdisk" and I successfully destroyed my entire hard drive.  I lost windows and ubuntu and everything on both.  It's now showing the entire disk as a single NTFS partition.

Damnit.

---

### Post by sendblink23 on 2009-01-11
> **DeadTaco said:**
> Sendblink, I'm not sure I understood your instructions.

It doesn't matter now anyway.  Someone suggested that I use a program called "testdisk" and I successfully destroyed my entire hard drive.  I lost windows and ubuntu and everything on both.  It's now showing the entire disk as a single NTFS partition.

Damnit.


OMG  why did you do that..

What i was saying it was all inside  LIVECD  and you did not had to erase your windows XP  partition ...  

Well you screwed it up


Okay do this NOW..  Since you are Simply as a new hard drive in your computer with nothing in it


Re Install    Windows XP  (update the whole thing as normal in windows)

After you are done set up running windows..  then   insert the liveCD ...  and well install Ubuntu Again ....   now  just well make the partition you originally wanted for Ubuntu...  as normal install

This time you will be fine.  Dual boot  Ubuntu & Windows XP

---

### Post by DeadTaco on 2009-01-11
I didn't erase the partition.  Testdisk wiped out the entire hard disk and destroyed all of the partitions on it.  Now the entire disk is showing up as a single, corrupted NTFS partition.

At this point I think I'll take a break from ubuntu.  I just lost too much stuff and am a bit peeved at the moment.

---

### Post by Spinal_Tap on 2009-01-11
Some advice for next time DeadTaco (as I have done this before too): save all valuable information (papers, photos, install rar's, etc) onto an external source that you will not be working on before you start doing anything serious. It requires a lot of front time, but it is much less frustrating in the end.

I really do hope that you don't give up.

---

### Post by Tweak1029 on 2009-01-11
Hey DeadTaco.  Odd to see you outside of RB.

I think that what they were trying to say was to back up your Windows partition.  I'd recommend SuperGRUB if you have an issue like this again.  You burn it to a CD and it works wonders for finding and booting and even fixing GRUB issues.  It will make sure that the problem lies in GRUB and not the partition, at the very least.

> Testdisk wiped out the entire hard disk and destroyed all of the partitions on it. Now the entire disk is showing up as a single, corrupted NTFS partition.

That bites :(

Good luck with whatever OS you decide to use.

---

### Post by caljohnsmith on 2009-01-11
If Deadtaco used testdisk to change his HDD's partition table, what you are saying is not true, sendblink23. Testdisk does not erase everything on the HDD, it merely changes the HDD's partition table stored in the MBR (Master Boot Record) and the partition tables in the EBRs (Extended Partition Records) associated with each of the logical partitions. So all the data on the HDD is still there, but it is just not easily accessible since the partition table is currently invalid.

DeadTaco, if you haven't all ready reinstalled everything, there is a good chance we can recover your partitions if you haven't done anything more than use testdisk to change your partition table. Let me know and we can work from there if you want.

---

### Post by DeadTaco on 2009-01-11
Yeah, I haven't touched the disk yet simply because of that reason.  I know the data is recoverable, but figured I'd just wait for a new day before trying anything.  Frustration was setting in last night, and I figured I'd better walk away before I did something destructive (as I'm sure you could tell by my earlier post).

I do save all information to external drives.  Nothing major was lost, so I'm not freaking out by any means.  I learned that lesson years ago.

I'm just frustrated that I have to reinstall everything again, which is time consuming.  Also, while not critical, I had some stuff in my documents and settings that could save me a full day of time to recreate.

If we can correct the partition problem, then that will save me a ton of time.  Like I said, I haven't touched the computer since eviscerating my partitions, so all data is hiding on there intact.

Ubuntu is still my primary OS on my other systems, but it would figure that the one time I try to install it on a windows box, I goof it up.  Bad hair day.

Small world, Tweak :)

EDIT:  My first post shows how my partitions were set up, including their beginning and ending points on the disk.  I assume this info is useful.

---

### Post by caljohnsmith on 2009-01-11
OK, how about downloading the attached "partition_table.txt" file to your Ubuntu Live CD desktop, and then do:
```
sudo sfdisk -f /dev/sda -O ~/Desktop/sda_sectors_modified.save < ~/Desktop/partition_table.txt
```
That will produce a lot of output, including some warnings, so you don't need to be alarmed; but please post the output. The command above will also create a small "sda_sectors_modified.save" file on the Ubuntu desktop, and that will be a back up of the sectors that the sfdisk command modifies. Please save that file some place safe, like a USB stick, or you could even upload it to your email account. Next reboot your Live CD, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. And lastly, please post the output of:
```
sudo sfdisk -d /dev/sda
```
And we can work from there if you want. :)

---

### Post by DeadTaco on 2009-01-11
First, let me thank you ahead of time for helping me out here.

Here is the result of the first part: 
```

Disk /dev/sda: 24792 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  24791   24792- 199141708+   7  HPFS/NTFS
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048 187510679  187508632  83  Linux
/dev/sda2     187510680 398283479  210772800   f  W95 Ext'd (LBA)
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5     193505823 398275919  204770097   7  HPFS/NTFS
/dev/sda6     187510806 193502924    5992119  82  Linux swap / Solaris
Warning: partition 5 does not start at a cylinder boundary
Successfully wrote the new partition table

Re-reading the partition table ...

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)


```

Holy crap.  Thank you.  The partitions are all back!  You're my hero for the week.

I need to reboot to get the rest of your instructions completed, but you should know that you fixed the partition table.  I am copying all critical XP files now, just in case, then rebooting.  Man, what a day.

I'll post the results for the rest of your instructions shortly.

---

### Post by DeadTaco on 2009-01-11
Here is the content of the results.txt file.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  Geometry: 240 Heads and 63 sectors per Track.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda6: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  Geometry: 64 Heads and 63 sectors per Track. No errors 
                       found in the Boot Parameter Block.
    Mounting failed:
mount: /dev/sdb1 already mounted or sdb1 busy
mount: according to mtab, /dev/sdb1 is mounted on /cdrom

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x15711570

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   187510679    93754316   83  Linux
/dev/sda2       187510680   398283479   105386400    f  W95 Ext'd (LBA)
/dev/sda5       193505823   398275919   102385048+   7  HPFS/NTFS
/dev/sda6       187510806   193502924     2996059+  82  Linux swap / Solaris

Partition table entries are not in disk order

sfdisk -V /dev/sda:

Warning: partition 5 does not start at a cylinder boundary

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 2047 MB, 2047678976 bytes
64 heads, 63 sectors/track, 991 cylinders, total 3999373 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         245     3995711     1997733+   6  FAT16

sfdisk -V /dev/sdb:

/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="bcbb0b31-f2f8-496d-b67e-74f10b4a92b1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="B8185FAA185F6682" TYPE="ntfs" 
/dev/sda6: UUID="c03730ac-2250-4346-aca7-5793ebe845a4" TYPE="swap" 
/dev/sdb1: SEC_TYPE="msdos" UUID="4015-0F9F" TYPE="vfat" 
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
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda5 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

=========================== sda1/boot/grub/menu.lst: ===========================

default 0
timeout 3

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
# kopt=root=UUID=bcbb0b31-f2f8-496d-b67e-74f10b4a92b1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bcbb0b31-f2f8-496d-b67e-74f10b4a92b1

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
# defoptions=splash vga=795 quiet

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

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=bcbb0b31-f2f8-496d-b67e-74f10b4a92b1 ro splash vga=795 quiet
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=bcbb0b31-f2f8-496d-b67e-74f10b4a92b1 ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP partition hd0,4
root (hd0,4)
chainloader +1
savedefault
makeactive

title Windows XP
root (hd0,4)
chainloader +1
savedefault
makeactive


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bcbb0b31-f2f8-496d-b67e-74f10b4a92b1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=c03730ac-2250-4346-aca7-5793ebe845a4 none            swap    sw              0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 11936
drwxr-xr-x  3 root root    4096 2009-01-10 16:54 .
drwxr-xr-x 20 root root    4096 2009-01-10 16:42 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  3 root root    4096 2009-01-11 05:54 grub
-rw-r--r--  1 root root 8164277 2009-01-10 16:54 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 01:29 vmlinuz-2.6.27-7-generic

=============================== sda1/boot/grub: ===============================

total 240
drwxr-xr-x 3 root root   4096 2009-01-11 05:54 .
drwxr-xr-x 3 root root   4096 2009-01-10 16:54 ..
-rw-r--r-- 1 root root    197 2009-01-10 16:42 default
-rw-r--r-- 1 root root     60 2009-01-10 16:42 device.map
-rw-r--r-- 1 root root   8108 2009-01-10 16:42 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-10 16:42 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-10 16:42 installed-version
-rw-r--r-- 1 root root   8712 2009-01-10 16:42 jfs_stage1_5
-rw-r--r-- 1 root root   2917 2009-01-11 05:54 menu.lst
-rw-r--r-- 1 root root   2923 2009-01-11 05:36 menu.lst~
-rw-r--r-- 1 root root   4310 2009-01-10 16:53 menu.lst.backup
-rw-r--r-- 1 root root   2834 2009-01-11 04:55 menu.lst.bak
-rw-r--r-- 1 root root   4323 2009-01-10 16:58 menu.lst_original
-rw-r--r-- 1 root root   7352 2009-01-10 16:42 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-10 16:42 reiserfs_stage1_5
drwxr-xr-x 2 root 1000   4096 2009-01-10 16:53 splashimages
-rw-r--r-- 1 root root    512 2009-01-10 16:42 stage1
-rw-r--r-- 1 root root 121460 2009-01-10 16:42 stage2
-rw-r--r-- 1 root root   9556 2009-01-10 16:42 xfs_stage1_5

================================ sda5/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional P2" /noexecute=optin /fastdetect

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-11
Great, it looks like all your partitions are back OK now, and they are all mountable and readable so that's a good sign; have you tried booting into your Ubuntu install yet? It looks like everything is still configured correctly for you to do so. How about trying that first, and if you can get into Ubuntu OK, then open up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your current Windows entry to:
```
title Windows XP
rootnoverify (hd0,4)
chainloader +1
```
It looks like your Windows boot.ini file is currently configured correctly so that you can boot Windows from the sda5 logical partition where it is right now, so go ahead and reboot, try Windows from your Grub menu, and let me know exactly what happens. We can work from there. :)

---

### Post by DeadTaco on 2009-01-11
It found the partition, but it just shows the text "Starting up ... " in a black console window, and nothing further.

It looks like this is a windows problem now, and not Ubuntu.

Edit: Forgot to mention that Ubuntu loads up fine.

EDIT EDIT:  Looks like a common problem with dual booting.  I see a few people saying to simply use a windows boot CD in recover mode and run chkdsk to fix it.  Or FIXMBR.  Will this step on Grub if I do this?

---

### Post by caljohnsmith on 2009-01-11
> **DeadTaco said:**
> It found the partition, but it just shows the text "Starting up ... " in a black console window, and nothing further.

It looks like this is a windows problem now, and not Ubuntu.

Edit: Forgot to mention that Ubuntu loads up fine.

EDIT EDIT:  Looks like a common problem with dual booting.  I see a few people saying to simply use a windows boot CD in recover mode and run chkdsk to fix it.  Or FIXMBR.  Will this step on Grub if I do this?
Definitely I wouldn't do the "fixmbr", because that replaces Grub with a Windows MBR (Master Boot Record); but the "chkdsk" command you mention would be a good place to start:
```
chkdsk /r
```
And run it as many times as it takes until it reports no errors. Let me know if it helps or not about booting Windows.

---

### Post by caljohnsmith on 2009-01-11
Deadtaco, I just received word from meierfra, the author of the script you ran, and it seems there might be a bug in the script that prevented it from correctly analyzing your Windows boot sector. So the bottom line is that your Windows boot sector probably needs fixing, based on the symptoms you describe. To check if that's the problem, how about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. We can work from there.

---

### Post by DeadTaco on 2009-01-11
Windows chkdsk did find errors and repaired them, but still can't get into windows.

Also, the testdisk program is what screwed me up last time, but I'll give it another shot since I have nothing to lose at this point.

The results will be posted shortly.  Thanks again for your help.

---

### Post by DeadTaco on 2009-01-11
Well, I wish I had some good news...

Luckily, I have great news.  Windows booted up!  Buddy, I cannot thank you enough.

You get one hundred internet points which can be cashed in at your local DNS server.

I am happy once again!  :guitar:

---

### Post by caljohnsmith on 2009-01-11
I'm really glad to hear both Windows and Ubuntu are booting OK now; cheers and have fun with them. :)

---

### Post by swamishreeji on 2009-12-11
i saw your post of your problem and saw the solution, however, i'm not sure this will work for me...

BACKGROUND:  
Ubuntu 9.10 installed on Dell 700m Inspiron
was trying to create a USB Startup Disk & was fooling around with the GParted utility to delete the USB partition and recreate (since i couldn't get my other laptop to boot from the USB after the USB Startup Disk created it).  The Startup DIsk utility finished installing Ubuntu on the USB (4GB) and then i rebooted my machine.  I got an error that said "No loader".  THen hit ctrl-alt-delete to reboot again.  Then got a black screen with only the word "DRMK 8.00 loading' (something like that) and then nothing would happen.  Did some research & found that i probably have a corrupted partition table (not sure how that happened)...funny part about this is that i was going to back up the partition that had all my data files on it before this happened.

CalJohnSmith mentioned something about at partition-table.txt file that was attached in DeadTaco's message...was wondering how to get that txt file...

BTW, here's the output from fdisk....
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006fd73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         491     3943926    6  FAT16

i know i had at least 3 partitions, but it seems like none of those partitions exists anymore...

any help would be greatly appreciated!

---

### Post by swamishreeji on 2009-12-14
Figured out what was wrong...used Test Disk to restore the partitions...now just need to reinstall GRUB...

---

