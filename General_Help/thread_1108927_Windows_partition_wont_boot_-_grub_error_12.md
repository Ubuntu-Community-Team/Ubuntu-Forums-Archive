---
title: "Windows partition wont boot - grub error 12"
date: 2009-03-28
forum: General Help
---

### Post by newbuntus on 2009-03-28
I reinstalled ubuntu and it will no longer boot windows. It orginally came up with error 13 but i tried a few changes in the grub menu.lst file and now it comes up with error 12 saying no such device or something. Anyway here is the output of fdisk -l:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1989    15976611   83  Linux
/dev/sda3            1990       38913   296590896    f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda5            1990        8213    49991224+   7  HPFS/NTFS
/dev/sda6            8213       10703    19996168+   c  W95 FAT32 (LBA)
/dev/sda7           10703       14437    29998048+   7  HPFS/NTFS
/dev/sda8           14437       27508   104993248+   7  HPFS/NTFS
/dev/sda9           27508       38913    91612048+   7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc859c859

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         744     5976148+   7  HPFS/NTFS
/dev/sdb2             745        3099    18916537+   f  W95 Ext'd (LBA)
/dev/sdb5             745        2613    15002158    7  HPFS/NTFS
/dev/sdb6            2614        3099     3903763+  82  Linux swap / Solaris

-----------------------------------

Here is what I have in menu.lst:

title           Windows NT/2000/XP (loader)
root            (hd1,4)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


I think root might have been (hd1, 0) before I changed it but im not sure.

The windows partition is /dev/sdb5 according to fdisk. What do I put in the menu.lst so the boot to windows will work? cheers

---

### Post by mikewhatever on 2009-03-28
I'd try reverting to root(hd1,0). Windows likes to put its bootloader on the first partition even if the system is installed elsewhere.

---

### Post by newbuntus on 2009-03-28
Nope, back to error 13: invalid or unsupported executable format

---

### Post by newbuntus on 2009-03-28
anyone?

---

### Post by Bucky Ball on 2009-03-28
```
title           Windows NT/2000/XP (loader)
root            (hd1,4)
savedefault
makeactive
map             (hd1) (hd0)
map             (hd0) (hd1)
chainloader     +1
```

?

---

### Post by newbuntus on 2009-03-28
??

---

### Post by Bucky Ball on 2009-03-28
[http://users.bigpond.net.au/hermanzone/p15.htm#12_](http://users.bigpond.net.au/hermanzone/p15.htm#12_)

---

### Post by meierfra. on 2009-03-28
Try 

title Windows NT/2000/XP (loader)
rootnoverify (hd0,0)
chainloader +1

**If this did not work:**

In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by newbuntus on 2009-03-29
Thanks for the help guys. I've spent all day googling and trying a few things but no luck. 

I'm not sure why but my drives seem to have swapped/be swapping between sda/sdb unless I've just confused myself. So when i refer to drives below i'm referring to the drive with ony three partitions.

Anyway after I swapped the boot flag from sdb1 to sdb5 and commented out the makeactive in the grub menu.lst, I now get the message "Starting up ..." when selecting Windows from the grub menu. Unfortunately nothing else happens and i have to restart. 

I also tried copying a boot.ini, ntldr, and ntdetect.com to sdb5 since they weren't there. I did originally have an XP installation on sdb1 I think it was (the same drive as my current installation) but something went wrong with that which is why I have the current installation on a logical partition. Anyway I deleted the partition with the original installation. I'm thinking this installation was probably dependent on that one though. 

EDIT: meierfra, i tried changing menu.lst to what you said but got error 13 again.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc859c859

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    11,952,359    11,952,297   7 HPFS/NTFS
/dev/sda2          11,952,360    49,785,434    37,833,075   f W95 Ext d (LBA)
/dev/sda5    *     11,957,526    41,961,841    30,004,316   7 HPFS/NTFS
/dev/sda6          41,977,908    49,785,434     7,807,527  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000be6c0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    31,953,284    31,953,222  83 Linux
/dev/sdb3          31,954,608   625,136,399   593,181,792   f W95 Ext d (LBA)
/dev/sdb5          31,954,671   131,937,119    99,982,449   7 HPFS/NTFS
/dev/sdb6         131,937,183   171,929,519    39,992,337   c W95 FAT32 (LBA)
/dev/sdb7         171,929,583   231,925,679    59,996,097   7 HPFS/NTFS
/dev/sdb8         231,925,743   441,912,239   209,986,497   7 HPFS/NTFS
/dev/sdb9         441,912,303   625,136,399   183,224,097   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda5: UUID="369C3FA49C3F5D95" TYPE="ntfs" 
/dev/sda6: TYPE="swap" UUID="b4f8b0a7-b8cc-4f58-990d-936ed722841f" 
/dev/sdb1: UUID="77bc260a-e401-4fa4-abbc-0e28fc6c712a" TYPE="ext3" 
/dev/sdb5: UUID="E8A00848A0081FA4" LABEL="PROGRAMS" TYPE="ntfs" 
/dev/sdb6: LABEL="DATA" UUID="207C-1A2B" TYPE="vfat" 
/dev/sdb7: UUID="668CC0DF8CC0AB3F" LABEL="MUSIC" TYPE="ntfs" 
/dev/sdb8: UUID="78BCD0EEBCD0A7C0" LABEL="GAMES" TYPE="ntfs" 
/dev/sdb9: UUID="F490B64C90B61558" LABEL="MOVIES" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/pete/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pete)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=pete)
/dev/scd1 on /media/cdrom1 type iso9660 (ro,nosuid,nodev,utf8,user=pete)

================================ sda5/boot.ini: ================================

[Boot Loader]

timeout=30

Default=multi(0)disk(0)rdisk(0)partition(1)\Windows



[Operating Systems]

multi(0)disk(0)rdisk(0)partition(1)\Windows="1ST TRY THIS seleccione esto primero" /fastdetect

multi(0)disk(0)rdisk(1)partition(1)\Windows="2ND TRY THIS essayez ceci en deuzieme" /fastdetect

multi(0)disk(0)rdisk(0)partition(2)\Windows="3RD TRY THIS wahlen Sie diesen Third" /fastdetect

multi(0)disk(0)rdisk(1)partition(2)\Windows="4TH TRY THIS selezioni questo fourth" /fastdetect

multi(0)disk(0)rdisk(0)partition(3)\Windows="5TH TRY THIS selecione este fifth" /fastdetect

multi(0)disk(0)rdisk(1)partition(3)\Windows="6TH TRY THIS seleccione este sexto" /fastdetect

multi(0)disk(0)rdisk(0)partition(4)\Windows="7TH TRY THIS essayez ceci en septieme" /fastdetect

multi(0)disk(0)rdisk(1)partition(4)\Windows="8TH TRY THIS wahlen Sie dieses achte" /fastdetect

C:\="9TH TRY THIS selezioni questo nono"

D:\="10TH TRY THIS selecione este decimo"


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=77bc260a-e401-4fa4-abbc-0e28fc6c712a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=77bc260a-e401-4fa4-abbc-0e28fc6c712a

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		77bc260a-e401-4fa4-abbc-0e28fc6c712a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=77bc260a-e401-4fa4-abbc-0e28fc6c712a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		77bc260a-e401-4fa4-abbc-0e28fc6c712a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=77bc260a-e401-4fa4-abbc-0e28fc6c712a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		77bc260a-e401-4fa4-abbc-0e28fc6c712a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,4)
savedefault
#makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=77bc260a-e401-4fa4-abbc-0e28fc6c712a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=b4f8b0a7-b8cc-4f58-990d-936ed722841f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   5.0GB: boot/grub/menu.lst
   4.9GB: boot/grub/stage2
   4.9GB: boot/initrd.img-2.6.27-7-generic
   4.9GB: boot/vmlinuz-2.6.27-7-generic
   4.9GB: initrd.img
   4.9GB: vmlinuz

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb6

00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 20 21 00  |.X.MSWIN4.1.. !.|
00000010  02 00 00 00 00 f8 00 00  3f 00 f0 00 9f 33 dd 07  |........?....3..|
00000020  11 3c 62 02 24 26 00 00  00 00 00 00 02 00 00 00  |.<b.$&..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  81 00 29 2b 1a 7c 20 4e  4f 20 4e 41 4d 45 20 20  |..)+.| NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f eb 1c 5e fc  |  FAT32   ....^.|
00000060  b4 0e b7 00 ac cd 10 38  3c 75 f9 b4 00 cd 16 b8  |.......8<u......|
00000070  0d 0e cd 10 b0 0a cd 10  cd 19 e8 e1 ff 0d 0a 53  |...............S|
00000080  79 73 74 65 6d 20 69 73  20 6e 6f 74 20 69 6e 73  |ystem is not ins|
00000090  74 61 6c 6c 65 64 2e 0d  0a 48 69 74 20 61 20 6b  |talled...Hit a k|
000000a0  65 79 20 74 6f 20 72 65  62 6f 6f 74 2e 2e 2e 00  |ey to reboot....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

boot_info_script.txt: line 1043: [: =: unary operator expected
```

---

### Post by meierfra. on 2009-03-29
> I'm thinking this installation was probably dependent on that one though. 

Correct diagnosis.

> copying a boot.ini, ntldr, and ntdetect.com to sdb5 


Exactly that you needed to do.

> "Starting up ..."
This happens since you are trying to boot a logical partition.  But it can be fixed fairly easily:
 Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```
(Check whether Windows is on /dev/sda5. If it is on /dev/sdb5, use "/dev/sdb" in the preceding line)

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition  and choose
"boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit testdisk.

Reboot. After choosing Windows at the Grub menu, you should get the Windows Boot Menu. Choose the third item on that boot menu.
If this worked, you can edit "boot.ini" later so that you automatically boot into XP after  choosing XP at the Grub menu.

---

### Post by newbuntus on 2009-03-30
kick ****! It be working :). I had to change root to (hd0,1) and comment out the "map" lines though in the menu.lst. In fact maybe I didn't even need to rebuild the boot sector? I have a couple questions though:

1. Does RebuildBS in testdisk do the same thing as fixboot in windows recovery console?

2. Why is my IDE HD defined as a SCSI drive (sda/sdb) in linux and not hda/hdb which is how I thought IDE drives were defined in linux? Does my motherboard have a SCSI controller controlling my IDE drives or something or am I way off the mark?

Thanks again

---

### Post by meierfra. on 2009-03-30
> I had to change root to (hd0,1) 

Are you sure?  (hd0,1) is the second partition on your boot drive.  The second partition on /dev/sda is an extended partition and  the second partition on /dev/sdb is empty.

> Does RebuildBS in testdisk do the same thing as fixboot in windows recovery console?
No, "RebuildBS" fixes the Boot Parameter Block  (the first 80 bytes of an ntfs or fat partition).  Fixboot repairs the boot code, which starts right after the Boot Parameter Block.

> Why is my IDE HD defined as a SCSI drive (sda/sdb) in linux and not hda/hdb which is how I thought IDE drives were defined in linux?

Since Ubuntu 7.10 (or so)  Ubuntu is using  the same drivers for IDE and SCSI drive. Ever since all the hard drives are called "sd?"

---

### Post by Bucky Ball on 2009-03-30
Rockin' Newbuntus! Good news. Up and racing. Welcome and hope ya dig it.

---

### Post by newbuntus on 2009-03-30
Thanks for the info meierfra. I meant (hd0,4) btw not (hd0,1), just a typo. One more question, what's with the skipped partitions on my drives. For example I have sdb{1,2,5,6}. What happened to partition 3 and 4? 

Thanks Bucky, I'm liking it so far, apart from the trouble I had trying to get the nvidia driver to work before I decided to reinstall ubuntu. It is working nicely now though :).

---

### Post by meierfra. on 2009-03-30
> I meant (hd0,4) 

That  makes more sense. It  means that you did have the fix the boot sector.  And it also means that I was a little bit sloppy.  Looking back at the RESULTS.txt  both "(hd0,4)" and  "(hd1,4)" can  works, depending on which drive you are booting from. 
 
If you like to experiment,  add a second  Windows item to menu.lst. Namely the one  with "(hd1,4)" and the map lines. Then reboot, but set your bios  to  boot from the ubuntu drive. You should get the grub menu, you should be able to boot  into ubuntu and you should be able to boot into Windows using the newly added  Windows item.

In facts I recommend  to do that (assuming that you are able to set your bios to boot from the Ubuntu drive)

If it works, I suggest to remove grub from your Windows drive, so  you will boot directly into Windows if you boot from the Windows drive. This way, if something happens to the Ubuntu partition, you still will be able to boot into Windows.  Removing grub is easy


```
sudo apt-get install lilo
sudo -M lilo  /dev/sda ext 
```

This installs a Windows style MBR (one that  just boots the active partition). But it  is little bit more advanced than a regular Windows MBR, since it can boot logical partitions.
(Only do this if you were able to boot into Ubuntu and Windows from the Ubuntu drive)

> 
or example I have sdb{1,2,5,6}. What happened to partition 3 and 4? 
Primary partition are numbered 1-4 and logical partition numbers 5 and higher.  So if you only have  2 primary partitions,  two of the numbers from 1 to 4 will be missing. Logical partitions always are numbered consecutively and start at exactly 5. Primary partitions don't have to be consecutive.  For example you could have sdb{2,4,5,6,7} but not sdb{1,2,3,4,5,7}

---

### Post by Bucky Ball on 2009-03-31
Envyng is sometimes an option if your having problems and chooses automatically. It's in the repositories. (Synaptics Package Manager). But as they say, if it ain't broke, don't fix it!

---

### Post by newbuntus on 2009-04-01
Ok, I put the map options back on and changed the root back to (hd1,4) and booted from the other drive which worked fine. So i installed lilo as you said but i did it on sdb as my drives had switched again. I assume this drive switching is because of the map option in the menu.lst right? So it would seem this affects how linux sees the drives as well as windows correct? How exactly does the map option work? Does the bootloader in the mbr pass the boot drive number to the bootsector of the partition, and the map option changes it? I know it's probably more complex than that, but anyway. 

Anyhow Windows now boots automatically if i boot from hd0, so all is good. My bios is a bit of a b*tch though as i can't seem to permanently set it to boot from hd1. No big deal though.

Bucky, the old saying didn't apply in this case though, because it was kind of broke. I kept getting a whole bunch of errors on start up, and couldn't use some 3D programs and effect because it was using some default driver or something.

The problem i had with the nvidia driver was some kind of conflict with new and old drivers, although i cant remember the exact error. Anyhow I was pretty sure that if i could could completely uninstall the old drivers i'd be able to get it to work, but none of the ways i tried got rid of the remnants of the old driver. I even reinstalled the old conflicting driver version so i could uninstall it again. I literally spent a whole week trying to fix it and it pissed me off good! I dont think i tried envy though. Do you reckon it would have fixed this?

---

### Post by meierfra. on 2009-04-01
> I assume this drive switching is because of the map option in the menu.lst right? 

As far as I know, the map command has nothing to do with the device name switching.    Device names are assigned by the kernel during boot up using the "udev" rules.  Those udev rules are supposed to always assign  the same device names (unless you physically swap drives), but this process does not work  perfectly and in some rare cases device names can change from boot to boot. I have no idea what really causes it.


> how exactly does the map option work? Does the bootloader in the mbr pass the boot drive number to the bootsector of the partition, and the map option changes it?
The windows  boot sector gets its information about the boot drive from the bios.  The map command somehow is able to virtually change that information so that windows is told that (hd1) is the boot drive.
But this change is only temporarily and should not influence linux.


 > i can't seem to permanently set it to boot from hd1.
Sorry, if I would have know that, I wouldn't  have recommended   booting from the Ubuntu drive. You might consider physically swapping  the two hard drives.  Or you could  put Grub back onto the Windows drive:

If Ubuntu is on /dev/sdb:

sudo grub
root (hd1,0)
setup (hd0)
quit


If Ubuntu is on /dev/sda:

sudo grub
device (hd0) /dev/sdb
device (hd1) /dev/sda
root (hd1,0)
setup (hd0)
quit

---

### Post by newbuntus on 2009-04-02
Thanks, i think i'll keep lilo there though at leaast for now. Its weird though because i'm sure i've been able to permanently change the boot device on every other motherboard i've had, yet this is probably the best mobo i've had and I can't. Maybe it's because the other drive is a sata drive.

---

