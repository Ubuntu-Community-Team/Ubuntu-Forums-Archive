---
title: "Boot problems"
date: 2009-01-28
forum: General Help
---

### Post by glethro on 2009-01-28
Last night i decided i did not like intrepid, so i formated the partition and installed hardy, all was good. However, i did not like the look of my partition table afterwards... to many screw ups before left bits scattered everywhere.

So i booted on a gparted live cd moved all my partitions around, wiped the linux half and then reinstalled hardy with grub. ... im guessing the moving **** around was a stupid idea because now my comp will not boot into windows.. no biggy dont use it that much.. but it has my download accelerator and games:P 

anyway when the comp starts grub loads, if i select ubuntu there are no problems, but when i select windows the comp basically just reboots. I dont get any error messages or strange gibberish. Screen simply goes black comp reboots and the grub menu pops back up. Im not sure if this is a Grub problem or an MBR probelm.. but any help would be appreciated :D

This is my menu.lst file
```
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=c5e21d3c-7296-4851-8ea9-0300201e8c24 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=c5e21d3c-7296-4851-8ea9-0300201e8c24 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)     # i tried playing with this number 
savedefault                   # but i just got errors
makeactive
chainloader	+1
```

And this is the output of fdisk -l
```
isk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd6aee043

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           29386       38913    76533660    5  Extended
/dev/sda2   *           1       16254   130560223+   7  HPFS/NTFS
/dev/sda3           16255       29385   105474757+   7  HPFS/NTFS
/dev/sda5           29386       38519    73368823+  83  Linux
/dev/sda6           38520       38913     3164773+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by GepettoBR on 2009-01-28
Maybe GRUB is pointing to the wrong partition for Windows. Mine likes to do that whenever it updates (in my case, the correct one is hd0,1 and it always switches to hd1,1). 

To know for sure which is the Windows partition (assuming it's still readable - sometimes "moving **** around" will bork an entire partition, which is why it's always recommended to back up valuable data before messing with partitions - enter the GRUB menu, then press **c** to go to a shell. Type ```
find /pagefile.sys
``` and GRUB will search all partitions for one that has the file "pagefile.sys" in it's root folder (the first folder). pagefile.sys is the Windows paging file, and by default only exists in the partition where Windows was installed. If GRUB returns a number that you haven't tried yet, try it out. If it says it couldn't find the file it's probable (but not certain) that the Windows partition is screwed up.

If it seems like I was overexplaining, don't be offended. Too much information is better than not enough, even if you already know most of it.

---

### Post by caljohnsmith on 2009-01-28
In the course of moving your partitions around, did you move the starting point of the Windows partition? If Windows is on sda2, it doesn't look like you did, but I just want to check because that can be a big problem for Windows. In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by glethro on 2009-01-28
Error 15:
File not found


hmm i hope that doesnt mean its screwed... 

i can access both the windows partitions from linux though..


i thought maybe after moving the partitions around from gparted the MBR couldnt locate them?? but then i dnt really know much about this whole partitioning, bootloaders and MBR thing..

---

### Post by GepettoBR on 2009-01-28
> **glethro said:**
> Error 15:
File not found


hmm i hope that doesnt mean its screwed... 

i can access both the windows partitions from linux though..


i thought maybe after moving the partitions around from gparted the MBR couldnt locate them?? but then i dnt really know much about this whole partitioning, bootloaders and MBR thing..

if you can access them from Linux, then they're not screwed :)

It's not the MBR's job to locate the partitions, all the MBR does is house the bootloader (in this case, GRUB) which does all the heavy lifting. GRUB didn't find the paging file, which might mean it's not reading the Windows partition. Please go to the GRUB shell again and type ```
geometry (hd0)
```. That should give you a list of partitions with their types, maybe we can work something out from there.

---

### Post by glethro on 2009-01-28
Just as a heads up i reinstalled hardy again... just to make sure there wasn't an error during the re installation... needless to say that didnt work :P
so here are the results of fdisk -l and menu.lst after the re install.
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd6aee043

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           29386       38913    76533660    5  Extended
/dev/sda2   *           1       16254   130560223+   7  HPFS/NTFS
/dev/sda3           16255       29385   105474757+   7  HPFS/NTFS
/dev/sda5           29386       38519    73368823+  83  Linux
/dev/sda6           38520       38913     3164773+  82  Linux swap / Solaris

Partition table entries are not in disk order
```
```
## ## End Default Options ##

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=ec2055a9-52d9-4d07-b5cf-cdad43585cb0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=ec2055a9-52d9-4d07-b5cf-cdad43585cb0 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ec2055a9-52d9-4d07-b5cf-cdad43585cb0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ec2055a9-52d9-4d07-b5cf-cdad43585cb0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```


@ GepettoBR These are the results of geometry (hd0)
```

drive 0x80: C/H/S = 1023/255/63, The number of sectors = 625142448,LBA
    Partition num: 1, Filesystem type unknown, partition type 0x7
    Partition num: 2, Filesystem type unknown, partition type 0x7
    Partition num: 4, Filesystem type is ext2fs, partition type 0x83
    Partition num: 5, Filesystem type unknown, partition type 0x82

```
Partition number 3 isnt there :P 
haha ya im backing up all 200 gigs onto me extHdd :P so maybe not completely screwed

@caljohnsmith
im pretty sure i did.. like 98%
the partition table looked like this before
```

| [         ][   /dev/sda2    ][      ][    /dev/sda3  ][/dev/sda5}][/dev/sda6] |
| [ 79.5 gb ][    124.51 GB   ][ free ][    100.59 gb  ][    15gb  ][   2gb   ] |
| [  free   ][     NTFS       ][      ][     NTFS      ][   ext3   ][   swap  ] |

```(im not 100% sure on last 2 sections)

it now looks like this
```

| [   /dev/sda2    ][    /dev/sda3  ][/dev/sda5} ][ /dev/sda6 ] |
| [    124.51 GB   ][    100.59 gb  ][  69.97gb  ][   3.02 gb ] |
| [     NTFS       ][     NTFS      ][   ext3    ][   swap    ] |

```

i wanted to get rid of that random free spacing spread throughout my comp so i basically moved everything over to the left than wiped the linux portion. after that was done i took all that free space and installed hardy on it..

as for the results.txt. it looks like this 
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd6aee043

Partition  Boot        Start          End         Size  Id System

/dev/sda1        472,070,025  625,137,344  153,067,320   5 Extended
/dev/sda5        472,070,088  618,807,734  146,737,647  83 Linux
/dev/sda6        618,807,798  625,137,344    6,329,547  82 Linux swap / Solaris
/dev/sda2    *            63  261,120,509  261,120,447   7 HPFS/NTFS
/dev/sda3        261,120,510  472,070,024  210,949,515   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="160CF0EA0CF0C5B1" LABEL="ACER" TYPE="ntfs" 
/dev/sda3: UUID="E0A04CC1A04C9FC0" TYPE="ntfs" 
/dev/sda5: UUID="ec2055a9-52d9-4d07-b5cf-cdad43585cb0" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="50cf08bc-dcf9-4526-a0f1-9b657ad6be2c" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/glethro/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=glethro)

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
# kopt=root=UUID=ec2055a9-52d9-4d07-b5cf-cdad43585cb0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=ec2055a9-52d9-4d07-b5cf-cdad43585cb0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=ec2055a9-52d9-4d07-b5cf-cdad43585cb0 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ec2055a9-52d9-4d07-b5cf-cdad43585cb0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ec2055a9-52d9-4d07-b5cf-cdad43585cb0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=ec2055a9-52d9-4d07-b5cf-cdad43585cb0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=50cf08bc-dcf9-4526-a0f1-9b657ad6be2c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location  of files loaded by Grub: ===================


 261.7GB: boot/grub/menu.lst
 261.6GB: boot/grub/stage2
 261.7GB: boot/initrd.img-2.6.24-19-generic
 261.7GB: boot/initrd.img-2.6.24-19-generic.bak
 261.8GB: boot/initrd.img-2.6.24-23-generic
 261.7GB: boot/initrd.img-2.6.24-23-generic.bak
 261.8GB: boot/vmlinuz-2.6.24-19-generic
 261.8GB: boot/vmlinuz-2.6.24-23-generic
 261.8GB: initrd.img
 261.7GB: initrd.img.old
 261.8GB: vmlinuz
 261.8GB: vmlinuz.old

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-28
It looks like your Windows entry in the menu.lst is fine, so it definitely sounds like you have a Windows problem if the computer reboots when you select Vista from your Grub menu. I'm fairly certain it's because you moved the starting point of the Vista partition, but maybe it will be fixable without too much hair-pulling. How about booting your Vista Install CD, go to the command line and do:
```
chkdsk /r
bootrec /rebuildbcd
```
And run the chkdsk command as many times as it takes until it reports no errors. If you don't have a Vista Install CD, you can instead download and use a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Once you are done with the above commands, reboot, and let me know how far you get when you try booting Vista from Grub. We can work from there if you want.

---

### Post by glethro on 2009-01-28
downloading now :P

thanks

---

### Post by GepettoBR on 2009-01-28
GRUB doesn't show pertition 3 because it's an extended partition - only the logical partitions inside #3 are shown.

But the fact that it says your Windows partition type is unknown suggests that maybe the problem is mounting it. Can you mount that partition when you boot into Hardy?

---

### Post by caljohnsmith on 2009-01-28
> **GepettoBR said:**
> GRUB doesn't show pertition 3 because it's an extended partition - only the logical partitions inside #3 are shown.

But the fact that it says your Windows partition type is unknown suggests that maybe the problem is mounting it. Can you mount that partition when you boot into Hardy?
I think you might be forgetting that Legacy Grub has no support for NTFS partitions--it can't read them, and it always reports them as "unknown". That's also why you can't use the Grub "find" command to find files in an NTFS partition, it will always return "file not found" just like glethro got. If you want a Grub that supports reading NTFS partitions, you have to use something like Grub4DOS or NeoGrub; but it is not necessary to read the NTFS partition in order to boot them, because all you are doing is "chain loading" or booting the Windows boot sector.

---

### Post by glethro on 2009-01-30
sorry this took so long.. many,  many things came up :P (IB Orals :/ )
okay... so i have to thank you caljohnsmith that worked very well... in fact i think it worked better than you expected as i didn&#8217;t even need to use those commands.. i simply put the cd in and hit repair windows :P and it looks like it has done it all for me.. right now it just checking the disk but it got past the grub menu which is defiantly a relief. 
ill test out the system when this is all done at let you know 

btw maybe you can answer this so i dont have to start a new thread.. i tried to install oss (4 times) by using the guide located here [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
i tried this using both ways the .deb and compiling from source..
however when i run the command sudo make deb
sudo dpkg -i oss*.deb
or make
when i restart the comp wont load... it just hangs at the desktop. can move mouse around but i cant drag boxes, click on icons or use any of the buttons.. any ideas? btw im using hardy heron.

---

### Post by GepettoBR on 2009-01-30
Since it's an unrelated issue, I think you should start a new thread. It would more easily attract the attention of people who have the knowledge to help you.

---

### Post by glethro on 2009-01-30
alright, thanks


btw everything works great, vista starts up.. yey :P and ubuntu at least seems a little more stable, i just downloaded a .deb package and installed it.. they must have changed something in the new version that makes it incompatible with that guide.

anyway thanks GepettoBR and caljohnsmith, this is my first thread that has ever actually been solved :P

---

### Post by GepettoBR on 2009-01-31
You're very welcome. May all your future threads be as fortunate.

---

