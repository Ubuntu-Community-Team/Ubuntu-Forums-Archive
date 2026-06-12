---
title: "Overlapping partitions error from parted"
date: 2009-02-21
forum: General Help
---

### Post by rajeshja on 2009-02-21
The problem:
If I use GParted (whether from a live CD or my running Ubuntu installation) it shows all the space in my hard-drive as "unallocated".
So I run parted from a terminal and it complains - Error: Can't have overlapping partitions.

I run fdisk -l /dev/sda and it gives me: 

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00098469

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    5  Extended
/dev/sda2           18713       19457     5984181   82  Linux swap / Solaris
/dev/sda5               1        4863    39061953   83  Linux
/dev/sda6            4864        8511    29302528+  83  Linux

```

I don't see any overlaps, except for the fact that all the Linux partitions are inside the Extended partition. But isn't that how its supposed to be?

I added a Linux partition using fdisk, but that's just a pain. I still have free space on the disk and would like to know how to get GParted working again.
And I would prefer an option that doesn't require me to reinstall Ubuntu.


In case it helps, this is how it happened:

Last April, I installed Hardy Heron on a brand new PC with two hard-disks, and it worked just fine. GParted worked, everything just worked. I had around half of my disk partitioned for use with Linux.
Then I realised that Wine doesn't support a couple of Windows games I own, so I decided to keep a small Windows partition on my machine just for those games. So I booted off the XP cd, and tried to create a partition for Windows. But since the beginning of my disk was Linux, it wanted to name the partition I was creating, as D: or E:. I tried some experimentation there (can't remember what), and made the mistake of allowing Windows to write to the partition table. After that I could never used parted of gparted to modify my disk partitions. 

Thanks in advance for any help!

---

### Post by caljohnsmith on 2009-02-21
> **rajeshja said:**
> 
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00098469

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]/dev/sda1   *           1       19457[/COLOR]   156288321    5  Extended
[COLOR="Red"]/dev/sda2           18713       19457[/COLOR]     5984181   82  Linux swap / Solaris
/dev/sda5               1        4863    39061953   83  Linux
/dev/sda6            4864        8511    29302528+  83  Linux

```

Actually you do have overlapping partitions, because your sda2 primary partition is inside of your sda1 extended partition; therefore sda2 should be a logical partition. Are either of your linux partitions supposed to be primary partitions? Or do you want all your partitions to be logical partitions? If you would like some help repairing your partition table, how about posting:
```
sudo fdisk -lu
sudo sfdisk -d
```
If you are unsure of whether your linux partitions should be primary/logical, it would help to get more info about your setup in order to figure out what they were before your partition table became corrupt; how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. We can work from there if you want.

---

### Post by rajeshja on 2009-02-21
sudo fdisk -lu /dev/sda

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00098469

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312576704   156288321    5  Extended
/dev/sda2       300608343   312576704     5984181   82  Linux swap / Solaris
/dev/sda5             189    78124094    39061953   83  Linux
/dev/sda6        78124158   136729214    29302528+  83  Linux

```

 sudo sfdisk -d /dev/sda

```

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=312576642, Id= 5, bootable
/dev/sda2 : start=300608343, size= 11968362, Id=82
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=      189, size= 78123906, Id=83
/dev/sda6 : start= 78124158, size= 58605057, Id=83

```

I'm guessing the "cylinder boundary" message above means something useful? The problem did occur because I did some partition changes using my XP CD.

I don't really remember whether my partitions are supposed to be logical or primary.

I've downloaded the bootinfo script and am reviewing it before I run it. Will be back with more info shortly.

---

### Post by rajeshja on 2009-02-21
Here are the results of the bootinfo script

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00098469

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,576,704   312,576,642   5 Extended
/dev/sda5                 189    78,124,094    78,123,906  83 Linux
/dev/sda6          78,124,158   136,729,214    58,605,057  83 Linux
/dev/sda2         300,608,343   312,576,704    11,968,362  82 Linux swap / Solaris

/dev/sda1 overlaps with /dev/sda2

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x14991498

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    61,432,559    61,432,497   7 HPFS/NTFS
/dev/sdb2          61,432,560   112,631,714    51,199,155  83 Linux
/dev/sdb3         112,631,715   174,064,274    61,432,560  83 Linux
/dev/sdb4         174,064,275   235,561,094    61,496,820  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="34d6cb82-75ac-48e5-aa1d-b59c56055817" TYPE="swap" 
/dev/sda5: UUID="1b074d33-d7d0-4a47-8244-71f9b354628b" TYPE="ext3" 
/dev/sda6: UUID="135b10c5-454e-4529-bc5f-46e7db39e43a" TYPE="ext3" 
/dev/sdb1: UUID="B0C45753C4571B44" TYPE="ntfs" 
/dev/sdb2: UUID="e4dd1536-75ca-4971-a8a4-40879ce78e94" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="08cfdc69-f182-4e91-a2e5-1d793a7323c2" TYPE="ext3" 
/dev/sdb4: LABEL="Videos" UUID="1c08ef98-5248-44cc-9c0f-1ce8d182e19f" TYPE="ext3" 

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
/dev/sda6 on /data type ext3 (rw,relatime)
/dev/sdb3 on /data2 type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/scd0 on /media/cdrom0 type iso9660 (rw,nosuid,nodev,utf8,user=rajeshja)
gvfs-fuse-daemon on /home/rajeshja/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rajeshja)
/dev/sdb4 on /data/movies type ext3 (rw)


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
timeout		7

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
# kopt=root=UUID=1b074d33-d7d0-4a47-8244-71f9b354628b ro

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1b074d33-d7d0-4a47-8244-71f9b354628b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1b074d33-d7d0-4a47-8244-71f9b354628b ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1b074d33-d7d0-4a47-8244-71f9b354628b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1b074d33-d7d0-4a47-8244-71f9b354628b ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows XP 
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=1b074d33-d7d0-4a47-8244-71f9b354628b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
# UUID=cdba0b49-cd93-49c8-a91e-bcfe65817be9 /backup         ext3    relatime        0       2
# /dev/sda7
#UUID=1bee345f-bd5a-49f2-9bf7-1cefe2bf0814 /data           ext3    relatime        0       2
/dev/sda6	/data	ext3	relatime	0	2
# /dev/sda8
#UUID=93c06716-7c83-4071-8cde-866ffc9b6e2f /home           ext3    relatime        0       2
# /dev/sda5
UUID=34d6cb82-75ac-48e5-aa1d-b59c56055817 none            swap    sw              0       0
/dev/sdb3	/data2	ext3	relatime	0	2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  31.2GB: boot/grub/menu.lst
  31.3GB: boot/grub/stage2
  31.3GB: boot/initrd.img-2.6.27-11-generic
  31.3GB: boot/initrd.img-2.6.27-9-generic
  31.3GB: boot/vmlinuz-2.6.27-11-generic
  31.3GB: boot/vmlinuz-2.6.27-9-generic
  31.3GB: initrd.img
  31.3GB: initrd.img.old
  31.3GB: vmlinuz
  31.3GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

Note, I've not been providing the output of fdisk for my second hard-drive, just to avoid confusion. That drive doesn't have any "overlapping partitions" or any other such errors. It just contains some data partitions. If you think having more info on that is important, I'll paste that here too.

---

### Post by caljohnsmith on 2009-02-21
According to your fstab, your swap partition was previously sda5, but it looks like since then you reinstalled Grub and reconfigured your menu.lst so that your Ubuntu main partition is now sda5. So I think the best thing to do would be to convert the swap partition into sda7 and leave your Ubuntu main partition as sda5. In order to do that, how about downloading the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk --no-reread -f /dev/sda  < ~/Desktop/partition_table.txt
```
And please post the output. Next reboot, and please post the new output of:
```
sudo fdisk -lu
sudo parted /dev/sda print
```
And we can work from there.

---

### Post by rajeshja on 2009-02-28
Hey, sorry for not responding before, but I had some trouble with my broadband connection over the week.

Your instructions worked beautifully!

$ sudo fdisk -lu /dev/sda
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00098469

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312576704   156288321    5  Extended
/dev/sda5             189    78124094    39061953   83  Linux
/dev/sda6        78124158   136729214    29302528+  83  Linux
/dev/sda7       300608343   312576704     5984181   82  Linux swap / Solaris

```


$ sudo parted /dev/sda print

```

Model: ATA ST3160215AS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  160GB   160GB   extended               boot 
 5      96.8kB  40.0GB  40.0GB  logical   ext3              
 6      40.0GB  70.0GB  30.0GB  logical   ext3              
 7      154GB   160GB   6128MB  logical   linux-swap        

```

I can now use GParted to partition my disk! Thanks a million!

I don't remember reinstalling grub, but this might have happened during some automatic updates. I do remember having to change (hd0,5) to (hd0,4) though. Can't remember the exact reasons for this.

Is there anything else I need to do?

Also, how exactly did moving swap to the end of the list help? Any pointers to documentation that clears this up, would be appreciated.

---

### Post by caljohnsmith on 2009-02-28
> **rajeshja said:**
> 
Is there anything else I need to do?

Also, how exactly did moving swap to the end of the list help? Any pointers to documentation that clears this up, would be appreciated.
That's good news, I'm glad to hear the partition changes went smoothly and gparted can now see all your partitions. I don't think there is anything else you need to do, because fortunately your fstab uses the swap UUID to mount your swap partition; therefore changing the swap partition from a primary partition to a logical partition was not a problem for Ubuntu. And about the partition change, we changed swap from primary partition sda2 to logical partition sda7, so that's why swap ended up at "the end of the list". It's worth mentioning that you can distinguish a primary partition from a logical partition simply by its number: all primary partitions are numbered 1-4 (sda1-sda4), while logical partitions are always numbered starting with 5 (sda5), regardless of how many primary partitions you may have. "sfdisk" can be a powerful tool for correcting partition table problems like you had, but it can also be dangerous if one is not first aware of all the partition rules that go with creating an extended partition. If you want to read more about how the standard MS-DOS partition table works (that's what your partition table is), you could start by reading these articles:

[http://en.wikipedia.org/wiki/Mbr](http://en.wikipedia.org/wiki/Mbr)
[http://en.wikipedia.org/wiki/Extended_partition](http://en.wikipedia.org/wiki/Extended_partition)

Anyway, cheers and enjoy your Ubuntu install. :)

---

### Post by rajeshja on 2009-02-28
Thanks a lot!

I'm sure I've read the bit about primary partitions being numbered 1-4, but never made the connection to it being the key to my "overlapping partitions" problem. Now it all makes sense.

I've been enjoying Ubuntu for 10 months now, but the whole gparted thing was just a pain in my backside. I finally got tired of staring at the output of fdisk last week, and thought "Hey, that's what the community is for". And it helped!

Thanks for the info about the UUID. It'll help me to cleanup my fstab now.

I'll updated the subject of this thread to say [Solved] now.

---

