---
title: "GRUB...stage 2"
date: 2009-03-08
forum: General Help
---

### Post by Saxcore on 2009-03-08
Hiya. I've had a bit of a look around, and can't seem to find anything directly about this problem. However, i'm pretty new to Linux, so this should be something simple!

I have two hard drives, one with Windows on, and one as a large storage drive with a Linux partition too. After a long drought without Linux, i finally put GRUB on my windows HDD mbr again. After a bit of tweaking in Linux, i restarted my computer to find that Windows now doesn't load. I can select it in the GRUB menu, but after flashing up a quick bit of text saying "Starting up... GRUB loading Stage2", i'm promptly returned to the GRUB menu.

As far as i can tell, my menu.lst has the right instructions on it. Is it something to do with not being able to find stage2?

Thanks alot! Sam.

---

### Post by hexanol on 2009-03-08
Well, if you have a grub menu, then this IS stage2. stage1 is in the MBR, stage1.5 is in the DOS compatibility zone. Looks like something is wrong with your menu.lst file. Could you post the content of your menu.lst file and the output of "sudo -l parted" ?

Here's an interesting link on how [GRUB fits in a disk]("http://www.pixelbeat.org/docs/disk/").

---

### Post by Saxcore on 2009-03-08
Hiya hexanol, thanks for the reply. Ok, here's my menu.lst. I haven't changed much in it, just commented out some old versions in the menu that i think i don't need... i could have done something fundamentally wrong here...

```
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
timeout		30

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
# kopt=root=UUID=ada6c807-fab4-437f-93b8-4b01a11ddbc0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ada6c807-fab4-437f-93b8-4b01a11ddbc0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ada6c807-fab4-437f-93b8-4b01a11ddbc0 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

#title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ada6c807-fab4-437f-93b8-4b01a11ddbc0 ro quiet splash
#initrd		/boot/initrd.img-2.6.22-14-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ada6c807-fab4-437f-93b8-4b01a11ddbc0 ro single
#initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```


...and here's the output of "sudo -l parted"; Somehow, i don't think i'm entering it right!

```
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
```


Cheers for the link! Pretty interesting.

---

### Post by hexanol on 2009-03-08
Hah, well sorry, my mistake, it's actually "sudo parted -l". :oops:

---

### Post by Saxcore on 2009-03-08
Hehe ah yeah i should have spotted that one. Hmm, are there any more arguments to enter with parted? It seems to not like "-l", and is also waiting for an input.

---

### Post by hexanol on 2009-03-08
Well, since you must run parted as root, you might have to enter your password but else...

This is what the command outputs on my system. Alternatively, you can give me the output of "sudo fdisk -l"

```
$ sudo parted -l
[sudo] password for etienne: 
Model: ATA ST3500320AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  92.2GB  92.2GB  primary   ntfs         boot 
 2      92.2GB  118GB   25.6GB  primary   ext3              
 3      118GB   118GB   98.7MB  primary   fat32        lba  
 4      118GB   500GB   382GB   extended                    
 5      118GB   126GB   8192MB  logical   ext3              
 6      126GB   134GB   8192MB  logical   linux-swap        
 7      134GB   317GB   183GB   logical   fat32        lba  
 8      317GB   500GB   183GB   logical   ext3  
```

---

### Post by Saxcore on 2009-03-08
Ah, that gave me what you're looking for i think:

```
samuel@samuel-linux:~$ sudo fdisk -l
[sudo] password for samuel: 

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91822053

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4501    36149248    7  HPFS/NTFS

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6b47c7f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       68509   550296128    7  HPFS/NTFS
/dev/sdb2           68509       69784    10241024    c  W95 FAT32 (LBA)
/dev/sdb3   *       69785       77491    61906477+  83  Linux
/dev/sdb4           77492       77825     2682855    5  Extended
/dev/sdb5           77492       77825     2682823+  82  Linux swap / Solaris
```

Cheers :)

---

### Post by hexanol on 2009-03-08
Well, sorry, but I'm not sure to know exactly where the problem lies. Your menu.lst file looks fine. I have never seen GRUB do this before so I don't really know where I should look at.

---

### Post by meierfra. on 2009-03-08
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Saxcore on 2009-03-08
Hi meierfra. Here you go; the results of the boot_info_script. Does this shed any light?

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 1226150552 on boot drive #2 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91822053

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    72,300,543    72,298,496   7 HPFS/NTFS

/dev/sda1 ends after the last cylinder of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6b47c7f9

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,100,594,303 1,100,592,256   7 HPFS/NTFS
/dev/sdb2       1,100,595,200 1,121,077,247    20,482,048   c W95 FAT32 (LBA)
/dev/sdb3    *  1,121,079,960 1,244,892,914   123,812,955  83 Linux
/dev/sdb4       1,244,892,915 1,250,258,624     5,365,710   5 Extended
/dev/sdb5       1,244,892,978 1,250,258,624     5,365,647  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sdb1: UUID="E6985EEB985EB9AF" TYPE="ntfs" 
/dev/sdb2: LABEL="SHARE" UUID="9A1A-175C" TYPE="vfat" 
/dev/sdb3: UUID="ada6c807-fab4-437f-93b8-4b01a11ddbc0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="71c9ea2b-2285-462e-a22e-6246c8982f3f" 

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
/dev/sdb3 on /media/disk type ext3 (rw,nosuid,nodev)


=========================== sdb3/boot/grub/menu.lst: ===========================

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
timeout		30

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
# kopt=root=UUID=ada6c807-fab4-437f-93b8-4b01a11ddbc0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ada6c807-fab4-437f-93b8-4b01a11ddbc0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ada6c807-fab4-437f-93b8-4b01a11ddbc0 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

#title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ada6c807-fab4-437f-93b8-4b01a11ddbc0 ro quiet splash
#initrd		/boot/initrd.img-2.6.22-14-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ada6c807-fab4-437f-93b8-4b01a11ddbc0 ro single
#initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=ada6c807-fab4-437f-93b8-4b01a11ddbc0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=71c9ea2b-2285-462e-a22e-6246c8982f3f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 627.8GB: boot/grub/menu.lst
 627.7GB: boot/grub/stage2
 627.1GB: boot/initrd.img-2.6.22-14-generic
 627.2GB: boot/initrd.img-2.6.22-14-generic.bak
 627.1GB: boot/initrd.img-2.6.24-21-generic
 627.2GB: boot/initrd.img-2.6.24-21-generic.bak
 627.2GB: boot/vmlinuz-2.6.22-14-generic
 627.2GB: boot/vmlinuz-2.6.24-21-generic
 627.1GB: initrd.img
 627.1GB: initrd.img.old
 627.2GB: vmlinuz
 627.2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo/sdb2: device is busy
umount: /tmp/BootInfo/sdb2: device is busy
```

EDIT: "Moutning failed"? ...hmmm. I don't think it lets me explore the windows drive (in Linux) come to think of it, and i swear it used to....

---

### Post by meierfra. on 2009-03-08
Instead of installing Grub to the MBR, you   installed Grub to the boot sector of the  windows partition.   So you have to reconfigure grub and   fix the Windows boot sector:

[B]Step1) Reconfigure grub:
[/B]
Open a terminal and then open the file menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```

change 

# groot=(hd1,1)

to 

# groot=(hd0,2)

Change  your windows item to

title		Windows Vista/Longhorn (loader)
root	       (hd1,0)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader	+1

Save  and close the file.

Back in the terminal:

```
sudo update-grub
```


[B]Step 2 Fix the Vista Bootsector.
[/B]
Install testdisk via

```
sudo apt-get install testdisk
```
(If you get an error message you might have to enable  the  "universe" repositories)

Run tesdisk via

```
sudo  testdisk /dev/sda 
```

Choose  "Proceed", choose "Intel", choose "Advanced", select the sda1 Windows partition, choose "Boot", then choose "Backup BS". Type "y" to confirm.  Press "q" a few  times to quit testdisk.

Reboot and set your bios to boot from the Ubuntu drive. Hopefully you will now be able to boot into Ubuntu and Windows.

---

### Post by Saxcore on 2009-03-09
Awesome, thanks alot meierfra! I should have guessed it was something to do with that, i think i remember when i over wrote it!

I'm just doing it now... I'm on the last step, on the testdisk program; after i choose proceed nothing seems to be happening, it's just bringing up another prompt. Am i doing it right?

---

### Post by meierfra. on 2009-03-09
After you select "proceed" and press "enter",  you should get a new screen (inside the same terminal)  where you can choose "intel" .... (Follow the instructions from my previous post). If you get stuck somewhere, copy the content of the terminal and post it here.

---

### Post by Saxcore on 2009-03-09
Hmm it's not bringing up the new screen. It's just putting a new "prompt" at the bottom of the screen (in a really weird place) when i press enter. I've tried re-installing it with "sudo apt-get install testdisk" again, which didn't seem to do anything. Bah.

---

### Post by meierfra. on 2009-03-09
Try this:

download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:


```
cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda
```

Select proceed and follow the same instruction as before.

---

### Post by Saxcore on 2009-03-09
Done. I'm now on windows.. Thanks alot meierfra, that was incredibly helpful! ..i'll be more careful next time i'm messing around with GRUB :D

Cheers, Sam.

---

### Post by meierfra. on 2009-03-09
> Done. I'm now on windows..

Good news. Have fun with Ubuntu and Vista.

---

