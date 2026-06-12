---
title: "Grub error 18 - Can't boot into XP"
date: 2009-06-02
forum: General Help
---

### Post by AndyCinDallas on 2009-06-02
I apologize in advanced for creating yet another Grub Error 18 thread, but I've spent the past 2 evenings looking through every related thread I can find and because everyone else's system is different, I couldn't find the answer to my issue.

I upgraded from Ubuntu 8.04 to 9.04 and it works fine - but now I can't get back into XP and from what I've been reading, it might be that one of my spare drives has been assigned as drive 0 (/media/disk) and my single drive with XP/Ubuntu as drive 1 (/media/disk-1) and I don't know how to fix it.

Here's what I have after having run the various commands that I've seen listed:

> sudo fdisk -l

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20da20da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       24791    96735397+   f  W95 Ext'd (LBA)
/dev/sda5           12749       24791    96735366    7  HPFS/NTFS

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e293e28

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3828    30748378+   7  HPFS/NTFS
/dev/sdb2            3829        4998     9398025    5  Extended
/dev/sdb5            3829        4922     8787523+  83  Linux
/dev/sdb6            4923        4998      610438+  82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *       13578      119522   850995205    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2           45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdc3           10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sdc4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1245a1a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       24792   199141708+   7  HPFS/NTFS



> ## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.24-24-generic
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-24-generic (recovery mode)
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro  single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 9.04, kernel 2.6.24-23-generic
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-23-generic (recovery mode)
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 9.04, kernel 2.6.24-22-generic
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-22-generic (recovery mode)
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro  single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 9.04, kernel 2.6.24-21-generic
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode)
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 9.04, kernel 2.6.24-19-generic
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-19-generic (recovery mode)
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 9.04, memtest86+
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1



> grub> find /boot/grub/stage1
 (hd1,4)


Any ideas, guys?

---

### Post by lindsay7 on 2009-06-02
Try editing you grub menu to change the windows root to hd0,0 in place of hd1,0.

type sudo gedit /boot/grun/menu.lst that is a small letter l, and save the file.  See if this fixes things.

IS:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 
```

Try:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 
```

---

### Post by AndyCinDallas on 2009-06-03
Thanks, Lindsay - I'll try that tonight once I get home from work.

---

### Post by Entropy_Sam on 2009-06-03
> **lindsay7 said:**
> ```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 
```
 
Um, that won't work. Crucially, Windows needs to think it's on hd0, and the above statement switches the mapping around so that hd0 is hd1, and vice-versa. If you use rootnoverify(0,0), remove the two "map" statements:
 
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1 
```
 
If this fails to work, this is how i made it work for me after playing around with things a couple of weeks ago:
 
When the boot loader pops on on startup, move the cursor over "Microsoft Windows XP Professional", press e to edit the command list (iirc) then e to edit the first line (i.e. rootnoverify(...)).
 
Then delete the last part of the statement so that is says something like ```
rootnoverify(hd0,
``` and press Tab. In this case, it'll display the partition list on hd0. Hopefully from this, you can figure out which partition is your Windows partition. (HINT: pay attention to the filesystem type identifiers. You should be able to figure out which number relates to XP's NTFS if you look around your other hard drives. IIRC, 0x82 is ext3, 0x83 is Linux-swap and 0x7 is NTFS, but don't quote me on that ;-))
 
Try the tab autocompletion trick with all your hard drives until you figure out which drive/partition corresponds to your Windows partition. If it's not on hd(hd0,0) then (and ONLY then) should you re-map the hard drives.
 
If you can't figure out the correct one on sight, it doesn't matter. Pick a possible candidate and if it doesn't work, hit hit ctrl+alt+delete and try again until it works. Each time you select a drive other then (hd0,0), remembering to re-map the drives so Windows thinks it's on (hd0,0).
 
Remember which drive you picked and how you had to map the drives if at all, and once you've got it, Boot into Ubuntu and update /boot/grub/menu.lst accordlingly.
 
Good luck!

---

### Post by VMC on 2009-06-03
You also say "..."XP/Ubuntu as drive 1...", but from the fdisk output, Ubuntu is on drive 2 - sdb5.

Output this, ```
sudo blkid
```, so we can match up UUID's

---

### Post by AndyCinDallas on 2009-06-03
Thanks, guys - going to be home in about an hour so I'll see what I can do to keep you posted as to the progress.

> **VMC said:**
> You also say "..."XP/Ubuntu as drive 1...", but from the fdisk output, Ubuntu is on drive 2 - sdb5.
Yes, that's my point - the first drive (Disk /dev/sda) is just my spare drive, the second drive (Disk /dev/sdb) is actually where XP and Linux reside. I'm trying to say that sdb should actually be seen by Grub as sda

---

### Post by AndyCinDallas on 2009-06-03
> **VMC said:**
> Output this, ```
sudo blkid
```, so we can match up UUID's

Here you are:

> sudo blkid

/dev/sda1: UUID="2648C77548C741F3" TYPE="ntfs" 
/dev/sda5: UUID="9AA0D2FBA0D2DCB7" TYPE="ntfs" 
/dev/sdb1: UUID="1C6434EF6434CD70" TYPE="ntfs" 
/dev/sdc: UUID="22B09707B096E119" TYPE="ntfs" 
/dev/sdd1: UUID="55D123D9E79ABF54" LABEL="External USB" TYPE="ntfs" 
/dev/sdb5: UUID="aaba139c-19a4-476e-9b74-9aa127994217" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="69bcb85d-bb14-4141-a4bb-2d5fd26e92de" 


---

### Post by lindsay7 on 2009-06-03
Can you do this, it will give us all the info about you machine,

Please download this and place it on your Desktop in Ubuntu:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

You will have you run it, so that we can gather more information about your hard drive setup and boot process to troubleshoot the problem more clearly.

After you download it to the Desktop, right-click it and click Properties, then click the Permissions tab and check the box at the bottom of the window that 'allows executing'.

Then click the Applications menu at the top right of your screen, followed by the Accessories menu and then click Terminal. A black window will come up, in it type the following commands, ending each line with a press of the Enter key:

Code:

cd ~/Desktop
sudo ./boot*.sh

Please remember that in Linux, everything is case sensitive. Therefore, a lowercase 'd' is different than an uppercase 'D'. Also, you will be prompted for the password you gave when you installed Ubuntu whenever you use the 'sudo' command. The 'sudo' command escalates privileges and in this case is needed to properly view the hard drives and boot process.

After you have done this, it should place a Results.txt file on your desktop. Double-click that file and select Edit->Copy. Then return here and start a new reply message. In this message, click the # sign at the top of the message editor box and this will give you CODE tags; click between these tags ({code]here[/code}) and paste the contents that you copied from the Result

---

### Post by AndyCinDallas on 2009-06-03
Thanks for the help so far :)

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdc
 => No known boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb5 and 
                       looks at sector 63053363 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20da20da

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620   398,267,414   193,470,795   f W95 Ext d (LBA)
/dev/sda5         204,796,683   398,267,414   193,470,732   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3e293e28

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    61,496,819    61,496,757   7 HPFS/NTFS
/dev/sdb2          61,496,820    80,292,869    18,796,050   5 Extended
/dev/sdb5          61,496,883    79,071,929    17,575,047  83 Linux
/dev/sdb6          79,071,993    80,292,869     1,220,877  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69205244

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *    218,129,509 1,920,119,918 1,701,990,410   7 HPFS/NTFS
/dev/sdc2         729,050,177 1,273,024,900   543,974,724  74 Unknown
/dev/sdc4       2,692,939,776 2,692,991,410        51,635   0 Empty

/dev/sdc1 ends after the last sector of /dev/sdc
/dev/sdc1 overlaps with /dev/sdc2
/dev/sdc2 ends after the last sector of /dev/sdc
/dev/sdc4 ends after the last sector of /dev/sdc

Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1245a1a1

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   398,283,479   398,283,417   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="2648C77548C741F3" TYPE="ntfs" 
/dev/sda5: UUID="9AA0D2FBA0D2DCB7" TYPE="ntfs" 
/dev/sdb1: UUID="1C6434EF6434CD70" TYPE="ntfs" 
/dev/sdb5: UUID="aaba139c-19a4-476e-9b74-9aa127994217" TYPE="ext3" 
/dev/sdb6: UUID="69bcb85d-bb14-4141-a4bb-2d5fd26e92de" TYPE="swap" 
/dev/sdc: UUID="22B09707B096E119" TYPE="ntfs" 
/dev/sdd1: UUID="55D123D9E79ABF54" LABEL="External USB" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/andy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=andy)
/dev/sdd1 on /media/External USB type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer


=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=aaba139c-19a4-476e-9b74-9aa127994217

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.24-24-generic
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-24-generic (recovery mode)
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro  single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 9.04, kernel 2.6.24-23-generic
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-23-generic (recovery mode)
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 9.04, kernel 2.6.24-22-generic
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-22-generic (recovery mode)
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro  single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 9.04, kernel 2.6.24-21-generic
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode)
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 9.04, kernel 2.6.24-19-generic
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-19-generic (recovery mode)
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=aaba139c-19a4-476e-9b74-9aa127994217 ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 9.04, memtest86+
uuid		aaba139c-19a4-476e-9b74-9aa127994217
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=aaba139c-19a4-476e-9b74-9aa127994217 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=69bcb85d-bb14-4141-a4bb-2d5fd26e92de none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


  32.2GB: boot/grub/menu.lst
  32.2GB: boot/grub/stage2
  32.2GB: boot/initrd.img-2.6.24-19-generic
  32.1GB: boot/initrd.img-2.6.24-19-generic.bak
  32.2GB: boot/initrd.img-2.6.24-21-generic
  32.1GB: boot/initrd.img-2.6.24-21-generic.bak
  32.2GB: boot/initrd.img-2.6.24-22-generic
  32.2GB: boot/initrd.img-2.6.24-22-generic.bak
  32.2GB: boot/initrd.img-2.6.24-23-generic
  32.1GB: boot/initrd.img-2.6.24-23-generic.bak
  32.2GB: boot/initrd.img-2.6.24-24-generic
  32.2GB: boot/initrd.img-2.6.24-24-generic.bak
  32.2GB: boot/initrd.img-2.6.28-11-generic
  32.2GB: boot/vmlinuz-2.6.24-19-generic
  32.2GB: boot/vmlinuz-2.6.24-21-generic
  32.2GB: boot/vmlinuz-2.6.24-22-generic
  32.1GB: boot/vmlinuz-2.6.24-23-generic
  32.1GB: boot/vmlinuz-2.6.24-24-generic
  32.2GB: boot/vmlinuz-2.6.28-11-generic
  32.2GB: initrd.img
  32.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 f0 00 00 00 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  af f8 50 09 00 00 00 00  |..........P.....|
00000030  00 00 0c 00 00 00 00 00  8a 0f 95 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  19 e1 96 b0 07 97 b0 22  |..............."|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 80 6f  |ng...NTLDR is .o|
000001c0  6d 70 07 65 73 73 65 64  00 0d 0a 50 72 65 00 73  |mp.essed...Pre.s|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 00 6f  | Ctrl+Alt+Del .o|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

Unknown MBR on /dev/sdd

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d5 50 88 46  |......u..1.F.P.F|
00000080  d2 be 68 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..h....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fc cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fc e9 c7 47 fd 92  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 33  ||U........R....3|
00000130  db 8a de 8b 46 0a 33 d2  83 e1 3f f7 f1 91 97 8b  |....F.3...?.....|
00000140  46 08 f7 f7 42 87 ca 3b  da 72 17 43 f7 f3 8a f2  |F...B..;.r.C....|
00000150  86 c5 d1 e8 d1 e8 0a c8  d0 cc d0 cc 0a f4 84 e4  |................|
00000160  74 02 b4 41 5b 8a d3 c3  0d 0a 4d 42 52 20 45 72  |t..A[.....MBR Er|
00000170  72 6f 72 20 00 0d 0a 00  72 65 73 73 20 61 6e 79  |ror ....ress any|
00000180  20 6b 65 79 20 74 6f 20  62 6f 6f 74 20 66 72 6f  | key to boot fro|
00000190  6d 20 66 6c 6f 70 70 79  2e 2e 2e 00 00 00 00 00  |m floppy........|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  a1 a1 45 12 00 00 80 01  |..........E.....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 99 52 bd 17 00 00  |......?....R....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1


Unknown BootLoader  on sdc2


Unknown BootLoader  on sdc4



=============================== StdErr Messages: ===============================

hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc4: No such file or directory
hexdump: /dev/sdc4: No such file or directory
```

---

### Post by lindsay7 on 2009-06-03
A quick question for you, do you have your windows xp install disk handy?

It looks like you windows mbr is missing and needs to be reistablished. Here is how you do it if you have the xp install disk. If you do not have it where are other ways to get this done. After you put this back on you computer you will have to redo the grub menu, but that is easy. Lets do one at a time.

[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)

---

### Post by AndyCinDallas on 2009-06-03
Sure do, yes

---

### Post by lindsay7 on 2009-06-03
See my last post for the instructions, I added them.

---

### Post by lindsay7 on 2009-06-03
After you add the mbr, by the way I think you just type fixmbr, you do not need to add the drive, you will need to redo the grub menu.

Do the following,


sudo grub
find /boot/grub/stage1
(it will give a (hdx,y)
root (hdx,y)
setup (hd0)
quit

Then reboot and see if this fixed it.

---

### Post by AndyCinDallas on 2009-06-03
Ok, I reckon I can get the MBR up and running to get into Windows - but it'll wipe out Grub then, right? So how would I get back into Linux to edit grub?

---

### Post by lindsay7 on 2009-06-03
You use the Ubuntu install cd. Use the live cd portion of it. You go to the terminal and type the commands in post #13

---

### Post by AndyCinDallas on 2009-06-04
Ok, I'll have to do that tomorrow - the Sandman is beating me to death here. Again, thanks for the help - I appreciate you sticking with me :)

---

### Post by lindsay7 on 2009-06-04
Ok, I will follow up tomorrow.

---

### Post by AndyCinDallas on 2009-06-04
fixmbr worked to get me back into Windows, where I'm writing this from (amazing how much like a toy it looks after using Linux).

Next I'll boot from the Live CD and run those commands in grub - wish me luck ;)

---

### Post by AndyCinDallas on 2009-06-04
Nope, no grub - it just boots back to Windows:

I booted with the Live CD, opened a terminal and did this:

sudo grub
find /boot/grub/stage1

it gave me(hd1,4)
So I then did:
root (hd1,4)
setup (hd0)
quit

Rebooted and Windows only

---

### Post by lindsay7 on 2009-06-04
Try again and use "setup (hd1) in place of setup (hd0).  Run the whole thing again. Hopefully this will do it.

sudo grub
find /boot/grub/stage1
(it will give a (hdx,y)
root (hdx,y)
setup (hd1)
quit

---

### Post by AndyCinDallas on 2009-06-04
Ok, have done so as follows:

> grub> find /boot/grub/stage1
 (hd1,4)

grub> root (hd1,4)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

Once I type "quit", it then says this:

> Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$ 

Going to reboot now and see what happens.

---

### Post by AndyCinDallas on 2009-06-04
No joy - it does exactly what it did in the beginning - grub starts, I select Windows and I get the same Error18.

I'm convinced that this happening because of the whole LBA issue - I think that, for some reason, my XP/Linux drive is being seen as the second drive and not the primary.

---

### Post by lindsay7 on 2009-06-04
The only thing that I can think of at this point is to try changing the boot priority in you bios set up and see if that fixes anything. Other then that I am stumped. Sorry I could not help you get this fixed. When you do, let me know how it turned out. Thanks by the way for the pictures.

---

### Post by AndyCinDallas on 2009-06-04
Ah, well - I haven't lost anything and learned new stuff, so it's a win overall - my thanks to you :)

The pics - you're welcome ;)

---

### Post by VMC on 2009-06-04
I found this in regards to Grub stage2 error#18

> 18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 

From your post#9

Windows partition is indeed on SDB1. Orignally you said before update that Windows was on the first HD, SDA1. And it worked at that point, correct?

From the above, 18 error, is there anything in your BOIS menu that has options for the second hard drive that you can show us.

---

### Post by Entropy_Sam on 2009-06-05
I don't think the problem is a missing/broken MBR. From what I can see from the code posted by AndyCinDallas, the drives aren't mapped correctly or GRUB isn't actually pointing at the Windows drive.
 
If GRUB sees sdb1 as (hd0,0), the code to boot XP is
 
```
 
rootnoverify(0,0)
chainloader +1

```
 
If Grub sees sdb1 as (hd1,0) the code to boot XP is
 
```
 
rootnoverify(1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

```
 
And so on for all present bootable media.
 
I've also noticed that if I've completely disabled booting from a USB drive in BIOS, booting with a USB drive inserted confuses my BIOS and causes it to resets the boot-order of my permanent HDs, which seems to be directly related to the numbers (hdo, hd1 etc) uses to identify my HDs.
 
My primary boot drive is sdb (XP on partition 1, Ubuntu on 2), but as I've set it as the first (only) bootable hard drive in BIOS, GRUB sees it as hd0. That means I don't need to re-map it when calling rootnoverify(...).
 
Andy, please try the above code snippets, or a slight modification of them with the currect drive number specified. Use tab-autocomplete along with the editor provided when you edit the code from GRUB on startup to make sure you're selecting the correct drive. GRUB doesn't necessarily specify them in the same order as they are specified in Ubuntu.
 
edit:
 
**rootnoverify **is _crucial_ here. See this post: [http://ubuntuforums.org/showthread.php?p=7393801#post7393801](http://ubuntuforums.org/showthread.php?p=7393801#post7393801)

---

### Post by AndyCinDallas on 2009-06-05
> **VMC said:**
> Windows partition is indeed on SDB1. Orignally you said before update that Windows was on the first HD, SDA1. And it worked at that point, correct?

From the above, 18 error, is there anything in your BOIS menu that has options for the second hard drive that you can show us.
Yes, everything was booting just fine when I installed 8.04 - only when I installed 9.04 did this issue crop up.

My little 40 Gb drive is my master IDE drive where Windows and Linux resides and that hasn't changed. As for the Bios, I'll see what I can find.

---

### Post by AndyCinDallas on 2009-06-05
> **Entropy_Sam said:**
> I don't think the problem is a missing/broken MBR. From what I can see from the code posted by AndyCinDallas, the drives aren't mapped correctly or GRUB isn't actually pointing at the Windows drive.
That's pretty much my belief, too - I think that the drives got switched around in Grub somehow and because Windows is now apparently beyond that LBA area, it faults....

---

### Post by Entropy_Sam on 2009-06-05
In post #9 on this thread, I took a look at the contents of your menu.lst as it was at the time, and you'd used root(0,0) instead of rootnoverify(0,0). Everything else looked correct, but I think that was a fatal error.
 
I sorted all this out on my own PC a week or 2 ago - at the time I'd made af ew newb mistakes trying to resize/copy partitions and move a Ubuntu installation to another HD. The upshot of that was that I had no less then THREE identical ubuntu installations, two of which were on partitions with identical UUIDs. Throw into the mix that my stupid BIOS kept switching the boot order (and GRUB's disk identification schema along with it) every time I stuck my Live USB stick in, and it all made for a VERY confusing setup.
 
Trying to set up fstab and GRUB when I couldn't even be sure which of the three installations would be booted from next was a nightmare, but it forced me to learn quickly.

---

### Post by AndyCinDallas on 2009-06-05
That's just the way it came up, Sam - I hadn't changed a thing at that time apart from installing 9.04, but I'll edit that when I get home.

---

### Post by AndyCinDallas on 2009-06-05
Ok, I check my BIOS and the boot order is as follows:

IDE Primary Master - Maxtor 40Gb (where XP and Linux reside)
IDE Primary Slave - WD 80 Gb
IDE Secondary Master - HP DVD
IDE Third Master - Maxtor 200Gb (external USB)


Disks as Linux sees them:
**Disk /dev/sda**: 203.9 GB

**Disk /dev/sdb**: 41.1 GB
 /dev/sdb1: TYPE="ntfs" 
 /dev/sdb5: TYPE="ext3" 
 /dev/sdb6: TYPE="swap"

**Disk /dev/sdc**: 80.0 GB

So I figure that big old 200Gb drive has somehow moved up to first place.

So basically I can get into Windows (and Linux only via the Live CD) - so any ideas on how to remap these drives so that Grub sees my 40Gb as /dev/sda and not /dev/sdb ?

---

### Post by Entropy_Sam on 2009-06-06
Glad to know it worked :-)

Take a look at /boot/grub/device.map. The contents of mine is:
```
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sbc
```

Seems self-explanatory enough.

I presume this changes the Linux device name rather than the GRUB disk number, as the the GRUB disk number seems to be based on the BIOS boot order.

---

### Post by VMC on 2009-06-06
> **Entropy_Sam said:**
> Glad to know it worked :-)

Take a look at /boot/grub/device.map. The contents of mine is:
```
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sbc
```

Seems self-explanatory enough.

I presume this changes the Linux device name rather than the GRUB disk number, as the the GRUB disk number seems to be based on the BIOS boot order.

Thank you. I only have one hard drive with multiple partitions and I don't "suffer" from what happened here. It's good to know. I was puzzled about Andy's delima, now I know. From the Grub Manual:
**15.3 The map between BIOS drives and OS devices**

---

### Post by Entropy_Sam on 2009-06-06
> **AndyCinDallas said:**
> 
So basically I can get into Windows **(and Linux only via the Live CD)**

Sorry, missed the paranthesised bit until I took another look at this thread just now.

Am I right in understanding that selecting rootnoverify(...) booted you into Windows okay, but now your Linux installation won't boot from GRUB, or is your Linux problem related to something else?

If it's a GRUB problem you're having booting Linux, you'll want the relevant section of /boot/grub/menu.lst to look like this:

```
title         Ubuntu 9.04, kernel YOUR-KERNEL-VERSION
uuid        UU1D-0F-Y0UR-L1NUX-R00T-P4RT1T10N
kernel         /boot/vmlinuz-YOUR-KERNEL-VERSION root=UUID=UU1D-0F-Y0UR-L1NUX-R00T-P4RT1T10N ro splash
savedefault
initrd         /boot/initrd.img-2.6.29.4
quiet
```You can find the UUID of your Linux partition when editing menu.lst with System->Administration->Partition Editor. Just copy and paste it.

You might be able to specify your root partition with **root(...)** but I don't think **rootnoverify(...) **will work if you're booting Linux from GRUB (in case that's what's currently there).

The good thing about using UUID's is that if for some reason GRUB's hard disk numbering changes, you don't need to specify a different disk number - it's automatically detected for you.

Hope that helps!

---

### Post by AndyCinDallas on 2009-06-06
Thanks for the help - what I did last night and today is I bit the bullet and decided to get Windows and Linux off that tiny 40Gb drive and move everything over to the 200Gb drive - just poor disk management on my part until now, which obviously made solving the problem ridiculously complex. 

It's all now working 100% - the first 50Gb for Windows, the next 50Gb for Ubuntu and the last 100Gb as another Windows partition \\:D/

---

