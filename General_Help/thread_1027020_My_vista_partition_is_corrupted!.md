---
title: "My vista partition is corrupted!"
date: 2008-12-31
forum: General Help
---

### Post by dragos240 on 2008-12-31
I was resizing and moving some partitions in parted magic and then it seemed it would take 2 hours so i was going to try to play some tunes in my partitions, which i unknowingly mounted while the partitions were being moved and stuff. And now it says that some of the partition information is unreadable. Please tell me there is a way to fix this, because i have so much stuff on there that i access daily and my dad will murder me if he finds out that i cant boot into vista! Please help!!!

---

### Post by sovietdoughnut on 2008-12-31
i'm not sure what you can do, but until someone replies who does, it's probably a good idea to avoid mounting and modifying the partition to avoid further damage.

---

### Post by dragos240 on 2008-12-31
> **sovietdoughnut said:**
> i'm not sure what you can do, but until someone replies who does, it's probably a good idea to avoid mounting and modifying the partition to avoid further damage.
good idea.

---

### Post by caljohnsmith on 2008-12-31
How about posting the output of:
```
sudo fdisk -l
```
And then for whichever is the Vista partition, do the following (replace sdaX with the Vista partition):
```
sudo mount /dev/[COLOR="Blue"]sdaX[/COLOR] /mnt && ls -l /mnt
```
And let me know what errors the mount command returns; we can work from there if you want.

---

### Post by lintoon on 2008-12-31
Don't tell your dad what you have done for starters.  It's a computer and we all know they fail - right.  It's failed.  Simple as that.

Get yourself some browny points off your dad and backup the data immediately.  Next I would just reinstall Vista (If you really must do - Traitor lol).  Remember to delete any existing partitions during setup and use the whole drive for your (spit) Vista install.  Set up your users and reinstall your backed up data.

If your machine will not boot use a boot cd to get access to your data eg your ubuntu install cd or Knoppix.

Remember though any writing or access to the drive can severely affect it.  Get your data asap.

Hopefully someone on these forums can suggest a workaround without you having to reinstall. If not, the above seems to be your best option (in my opinion).

Good luck.

---

### Post by dragos240 on 2008-12-31
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a7d030c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       16998   136536403+   7  HPFS/NTFS
/dev/sda3           18305       38082   158866785   83  Linux

```

Thats the result of sudo fdisk -l

And i'm not really too familiar with mount please explain the next thing a bit more.

---

### Post by 2hot6ft2 on 2008-12-31
Do what caljohnsmith says to do. If anyone can fix you up he's the one as I see him dive in and fix a lot in here.

---

### Post by caljohnsmith on 2008-12-31
OK, please post the output of:
```
sudo mount /dev/sda2 /mnt && ls -l /mnt
```

---

### Post by dragos240 on 2008-12-31
> **caljohnsmith said:**
> OK, please post the output of:
```
sudo mount /dev/sda2 /mnt && ls -l /mnt
```

```

mount: you must specify the filesystem type

```

---

### Post by caljohnsmith on 2008-12-31
That's not looking good, but how about next trying:
```
sudo mount -t ntfs-3g -o force /dev/sda2 /mnt && ls -l /mnt
```

---

### Post by dragos240 on 2008-12-31
> **caljohnsmith said:**
> That's not looking good, but how about next trying:
```
sudo mount -t ntfs-3g -o force /dev/sda2 /mnt && ls -l /mnt
```

```

NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

---

### Post by caljohnsmith on 2008-12-31
OK, just to warn you, it doesn't look like there is a very good chance of recovering your Vista partition, but let's see if testdisk might be able to fix the boot sector so you can mount it; first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "write". I'm doubtful you will get that far with testdisk, but if testdisk does allow you to "Rebuild BS", then please post the output of the command again from post #10; we can go from there.

---

### Post by dragos240 on 2008-12-31
> **caljohnsmith said:**
> OK, just to warn you, it doesn't look like there is a very good chance of recovering your Vista partition, but let's see if testdisk might be able to fix the boot sector so you can mount it; first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "write". I'm doubtful you will get that far with testdisk, but if testdisk does allow you to "Rebuild BS", then please post the output of the command again from post #10; we can go from there.

Ok it gave me the option to rebuild! Good start! Now i have the results of this:
```

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
     Partition                  Start        End    Size in sectors
 2 * HPFS - NTFS              0   1  1 16997 254 63  273072807

filesystem size           273072807 8589934593
sectors_per_cluster       8 8
mft_lcn                   786432 393217
mftmirr_lcn               29213198 0
clusters_per_mft_record   -10 0
clusters_per_index_record 1 15
Extrapolated boot sector and current boot sector are different.







[  Dump  ]  [  List  ]  [ Write  ]  [  Quit  ]

                           List directories and files


```

Ok and i said to write:
```

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
     Partition                  Start        End    Size in sectors
 2 * HPFS - NTFS              0   1  1 16997 254 63  273072807

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.





[  Quit  ]  [  List  ]  [Rebuild BS]  [Repair MFT]  [  Dump  ]
                            Return to Advanced menu


```

---

### Post by caljohnsmith on 2008-12-31
OK, so next choose "write", quit testdisk, and then post again:
```
sudo mount -t ntfs-3g -o force /dev/sda2 /mnt && ls -l /mnt
```

---

### Post by dragos240 on 2008-12-31
> **caljohnsmith said:**
> OK, so next choose "write", quit testdisk, and then post again:
```
sudo mount -t ntfs-3g -o force /dev/sda2 /mnt && ls -l /mnt
```

```
sudo mount -t ntfs-3g -o force /dev/sda2 /mnt && ls -l /mnt
total 4276108
-rwxrwxrwx 1 root root         24 2006-09-18 17:43 autoexec.bat
drwxrwxrwx 1 root root      49152 2008-12-26 08:00 $AVG8.VAULT$
drwxrwxrwx 1 root root       4096 2008-10-25 12:41 BlueJ
drwxrwxrwx 1 root root       4096 2006-06-11 20:36 Boot
-rwxrwxrwx 1 root root         48 2008-12-26 21:34 boot.ini
-rwxrwxrwx 1 root root     438840 2006-11-02 04:53 bootmgr
-rwxrwxrwx 1 root root       8192 2006-06-11 20:36 BOOTSECT.BAK
drwxrwxrwx 1 root root          0 2008-08-23 20:36 Cache508
-rwxrwxrwx 1 root root         10 2008-12-29 15:12 config.sys
drwxrwxrwx 1 root root       4096 2008-12-26 21:43 CPM
drwxrwxrwx 1 root root       4096 2008-12-20 20:42 cygwin
drwxrwxrwx 1 root root          0 2007-09-03 22:22 Documents
drwxrwxrwx 1 root root          0 2007-12-23 17:22 Documents and Settings
drwxrwxrwx 1 root root      40960 2008-11-28 15:27 Downloads
drwxrwxrwx 1 root root          0 2008-05-03 11:42 DriveKey
-rwxrwxrwx 1 root root     241664 2006-12-07 13:24 EMicon.dll
-rwxrwxrwx 1 root root     122514 2008-12-26 20:24 Gearwink logo.png
-rwxrwxrwx 1 root root     367996 2008-12-26 20:23 Gearwink Logo.xcf
drwxrwxrwx 1 root root          0 2007-09-03 22:17 google
drwxrwxrwx 1 root root          0 2007-09-03 22:01 Graphics
-rwxrwxrwx 1 root root 2011684864 2008-12-29 19:02 hiberfil.sys
-rwxrwxrwx 2 root root         96 2008-12-26 21:34 ioSpecial.ini
-rwxrwxrwx 1 root root          0 2008-03-12 19:38 IO.SYS
drwxrwxrwx 1 root root       4096 2008-03-22 09:13 j2sdk1.4.2_17
drwxrwxrwx 1 root root          0 2008-12-20 20:26 mingw
-rwxrwxrwx 1 root root          0 2008-03-12 19:38 MSDOS.SYS
drwxrwxrwx 1 root root          0 2007-09-03 22:03 MSOCache
drwxrwxrwx 1 root root          0 2008-03-16 02:12 Multimedia Files
-rwxrwxrwx 1 root root     262144 2008-12-25 22:09 ntuser.dat
-rwxrwxrwx 2 root root      65536 2008-12-25 22:09 ntuser.dat{27a43dab-d2f2-11dd-bdec-001bb9e31710}.TM.blf
-rwxrwxrwx 2 root root     524288 2008-12-25 22:09 ntuser.dat{27a43dab-d2f2-11dd-bdec-001bb9e31710}.TMContainer00000000000000000001.regtrans-ms
-rwxrwxrwx 2 root root     524288 2008-12-25 22:09 ntuser.dat{27a43dab-d2f2-11dd-bdec-001bb9e31710}.TMContainer00000000000000000002.regtrans-ms
-rwxrwxrwx 2 root root       5120 2008-12-25 22:09 ntuser.dat.LOG1
-rwxrwxrwx 2 root root          0 2008-12-25 22:09 ntuser.dat.LOG2
drwxrwxrwx 1 root root          0 2008-03-13 19:58 OutputFolder
-rwxrwxrwx 1 root root 2325610496 2008-12-29 19:02 pagefile.sys
-rwxrwxrwx 1 root root        163 2007-09-03 22:08 power2go.log
drwxrwxrwx 1 root root       8192 2008-12-20 14:25 ProgramData
drwxrwxrwx 1 root root      32768 2008-12-26 10:48 Program Files
drwxrwxrwx 1 root root       4096 2008-05-10 16:14 Python25
drwxrwxrwx 1 root root       4096 2008-11-14 17:32 $RECYCLE.BIN
-rwxrwxrwx 1 root root        420 2007-09-03 22:00 RHDSetup.log
drwxrwxrwx 1 root root          0 2008-12-13 21:05 rscache
drwxrwxrwx 1 root root      28672 2008-12-26 23:06 System Volume Information
drwxrwxrwx 1 root root          0 2008-10-25 11:52 Temp
drwxrwxrwx 1 root root          0 2008-11-08 20:30 ubuntu-backup
-rwxrwxrwx 1 root root   38626224 2008-12-26 20:29 unetbootin_partitionmanagerrev146_all.deb
-rwxrwxrwx 1 root root         80 2007-09-03 23:21 USBPatch.log
drwxrwxrwx 1 root root       4096 2008-09-28 08:13 Users
drwxrwxrwx 1 root root       4096 2008-10-08 19:49 wamp
-rwxrwxrwx 1 root root       7319 2008-10-18 17:54 wbScript.txt
drwxrwxrwx 1 root root      32768 2008-12-25 22:09 Windows

```

Oh my god, thats all my windows files!!!

---

### Post by caljohnsmith on 2008-12-31
Fantastic, it looks like testdisk worked its magic and you are in luck! :) I don't know if Vista will be bootable or not, but at least you can access your files in Vista. How about rebooting and see if by chance you can  boot into Vista, and we can work from there.

---

### Post by 2hot6ft2 on 2008-12-31
I love watching you work your magic caljohnsmith.:D

---

### Post by caljohnsmith on 2008-12-31
> **2hot6ft2 said:**
> I love watching you work your magic caljohnsmith.:D
Thanks for your kind words, but testdisk deserves all the credit; I'm amazed sometimes at what that program can do that even Microsoft's own tools can't. :)

---

### Post by dragos240 on 2008-12-31
Ok, it won't boot, it says that it's not a bootable disk and that i should insert a disk of a floppy to continue, and when i pushed enter or return (whatever you call it) it said loading stage2: and i waited a minuite and nothing happened.

---

### Post by caljohnsmith on 2008-12-31
Were you using Grub originally as your boot loader? I would assume so since you have a linux partition on that drive. If you were using Grub, you can reinstall Grub with:
```
sudo grub
grub> root (hd0,2)
grub> setup (hd0)
grub> quit
```
And let me know if you get the Grub menu OK on start up.

---

### Post by 2hot6ft2 on 2008-12-31
> **caljohnsmith said:**
> Thanks for your kind words, but testdisk deserves all the credit; I'm amazed sometimes at what that program can do that even Microsoft's own tools can't. :)
Not true. You made the diagnosis, took him thru it step by step, even every step thru test disk. So while test disk may have recovered the partition information he would have never made it that far without your help.

I've seen you jump in on some of the harder problems and get them sorted out. You have a real grasp of the way it works and a talent for troubleshooting things. So credit where credit is due.

When I see you start helping someone I like to sit back and see how you go about resolving things maybe if I watch enough some of it will be beat into my head.:popcorn:

You do great things.

---

### Post by dragos240 on 2008-12-31
> **caljohnsmith said:**
> Were you using Grub originally as your boot loader? I would assume so since you have a linux partition on that drive. If you were using Grub, you can reinstall Grub with:
```
sudo grub
grub> root (hd0,2)
grub> setup (hd0)
grub> quit
```And let me know if you get the Grub menu OK on start up.

Well i installed vista first then about a year later i found out about ubuntu and started using WUBI and then 4 months later i split my partitions and am using grub. should i type those things in grub or in the terminal emulator?

---

### Post by caljohnsmith on 2008-12-31
So on start up you were getting the Grub menu first and not the Vista boot menu, right? If that's true, then go ahead and run those Grub commands in a terminal, and please post the output.

---

### Post by dragos240 on 2008-12-31
> **caljohnsmith said:**
> So on start up you were getting the Grub menu first and not the Vista boot menu, right? If that's true, then go ahead and run those Grub commands in a terminal, and please post the output.
```


grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 

```


Now i'm going to test if i can boot, wish me luck.

---

### Post by caljohnsmith on 2008-12-31
Also, please post the output of:
```
cat /boot/grub/menu.lst
```
And make sure your Vista entry uses (hd0,1). If it does, go ahead and reboot, and see if you can boot Vista; if not, let me know exactly what happens when you try and boot Vista from Grub.

---

### Post by dragos240 on 2008-12-31
> **caljohnsmith said:**
> Also, please post the output of:
```
cat /boot/grub/menu.lst
```And make sure your Vista entry uses (hd0,1). If it does, go ahead and reboot, and see if you can boot Vista; if not, let me know exactly what happens when you try and boot Vista from Grub.

Ok the output is long:

```
cat /boot/grub/menu.lst
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)[code]cat /boot/grub/menu.lst
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=07446460-fa38-4d28-bf91-23ef304158d1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=07446460-fa38-4d28-bf91-23ef304158d1

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

title        Ubuntu 8.10, kernel 2.6.27-9-generic
uuid        07446460-fa38-4d28-bf91-23ef304158d1
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=07446460-fa38-4d28-bf91-23ef304158d1 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid        07446460-fa38-4d28-bf91-23ef304158d1
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=07446460-fa38-4d28-bf91-23ef304158d1 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        07446460-fa38-4d28-bf91-23ef304158d1
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=07446460-fa38-4d28-bf91-23ef304158d1 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        07446460-fa38-4d28-bf91-23ef304158d1
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=07446460-fa38-4d28-bf91-23ef304158d1 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        07446460-fa38-4d28-bf91-23ef304158d1
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1
```# kernel    /vmlinuz root=/dev/hda2 ro
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
## e.g. kopt=root=/dev/hda1 ro```
cat /boot/grub/menu.lst
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=07446460-fa38-4d28-bf91-23ef304158d1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=07446460-fa38-4d28-bf91-23ef304158d1

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

title        Ubuntu 8.10, kernel 2.6.27-9-generic
uuid        07446460-fa38-4d28-bf91-23ef304158d1
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=07446460-fa38-4d28-bf91-23ef304158d1 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid        07446460-fa38-4d28-bf91-23ef304158d1
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=07446460-fa38-4d28-bf91-23ef304158d1 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        07446460-fa38-4d28-bf91-23ef304158d1
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=07446460-fa38-4d28-bf91-23ef304158d1 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        07446460-fa38-4d28-bf91-23ef304158d1
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=07446460-fa38-4d28-bf91-23ef304158d1 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        07446460-fa38-4d28-bf91-23ef304158d1
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1
```##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=07446460-fa38-4d28-bf91-23ef304158d1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=07446460-fa38-4d28-bf91-23ef304158d1

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

title        Ubuntu 8.10, kernel 2.6.27-9-generic
uuid        07446460-fa38-4d28-bf91-23ef304158d1
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=07446460-fa38-4d28-bf91-23ef304158d1 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid        07446460-fa38-4d28-bf91-23ef304158d1
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=07446460-fa38-4d28-bf91-23ef304158d1 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        07446460-fa38-4d28-bf91-23ef304158d1
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=07446460-fa38-4d28-bf91-23ef304158d1 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        07446460-fa38-4d28-bf91-23ef304158d1
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=07446460-fa38-4d28-bf91-23ef304158d1 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        07446460-fa38-4d28-bf91-23ef304158d1
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1[/code]

And when i tried to boot the same message and results occured from last time.

---

### Post by caljohnsmith on 2008-12-31
OK, do you have your Vista Install CD? If so, I would boot that, go to the command line and do:
```
bootrec /fixboot
chkdsk /r
```
And run the chkdsk command as many times as it takes until it reports no errors. Then reboot, see if you can boot Vista again, and let me know exactly what happens. Also, if you don't have a Vista Install CD, you can download and use a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Unfortunately I have to go now, but I will be back tomorrow morning, and we can pick up there if you like. In the meantime, you can at least access your Vista partition now in Ubuntu. Good luck, and by the way, Happy New Year. :)

---

### Post by dragos240 on 2008-12-31
> **caljohnsmith said:**
> OK, do you have your Vista Install CD? If so, I would boot that, go to the command line and do:
```
bootrec /fixboot
chkdsk /r
```And run the chkdsk command as many times as it takes until it reports no errors. Then reboot, see if you can boot Vista again, and let me know exactly what happens. Also, if you don't have a Vista Install CD, you can download and use a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Unfortunately I have to go now, but I will be back tomorrow morning, and we can pick up there if you like. In the meantime, you can at least access your Vista partition now in Ubuntu. Good luck, and by the way, Happy New Year. :)

Thank you, happy new year to you too! I'm downloading the recovery torrent right now. See you tomorrow morning, i hope to fix this.

EDIT: I'm going to be gone from 12:00 to about 1:00 EST so be patient :p

EDIT:Where are you?

---

### Post by caljohnsmith on 2009-01-01
I've just been waiting for your update is all. What happened about running those commands? Do you get any further about booting Vista? Please keep in mind that when you "edit" one of your posts, I'm not notified of the changes even though I have email notification set on all the threads I follow. So if you can, please make a new post with any updates so I will get an email alert. :)

---

### Post by dragos240 on 2009-01-02
> **caljohnsmith said:**
> I've just been waiting for your update is all. What happened about running those commands? Do you get any further about booting Vista? Please keep in mind that when you "edit" one of your posts, I'm not notified of the changes even though I have email notification set on all the threads I follow. So if you can, please make a new post with any updates so I will get an email alert. :)

Ok, sadly i cant really do anything right now until sunday 12:00 EST T_T .

---

### Post by caljohnsmith on 2009-01-04
[QUOTE=dragos240 via private message]Thank you for all your help, but there are a few things that i need to clear up, i could see my windows files via terminal emulator, but I couldn't access my /windows directory, it just appeared blank. How can i mount it so that nautilus can see it? Also the vista disk thing looked more like a vista instalation disk when i booted into it. Could you give me a hand here, i'll be here all day.[/QUOTE]
That's not a good sign, so how about posting the output of:
```
sudo mount /dev/sda2 /mnt
ls -l /mnt /mnt/Windows /mnt/Windows/*
```
Also, did you download the Vista Recovery CD? If so, it has an option to get to the command line, but just not at the main menu if I remember correctly.

---

### Post by dragos240 on 2009-01-04
> **caljohnsmith said:**
> That's not a good sign, so how about posting the output of:
```
sudo mount /dev/sda2 /mnt
ls -l /mnt /mnt/Windows /mnt/Windows/*
```Also, did you download the Vista Recovery CD? If so, it has an option to get to the command line, but just not at the main menu if I remember correctly.

For the first thing, :
fuse: mount failed:```
Device or resource busy
```, when i mounted /dev/sda2 because i think thats my ubuntu partition.

And the second one i cant post, because it was so long that the terminal emulator couldn't display all of it,

---

### Post by caljohnsmith on 2009-01-04
OK, how about posting:
```
sudo fdisk -lu
mount
```
And we can go from there.

---

### Post by dragos240 on 2009-01-04
> **caljohnsmith said:**
> OK, how about posting:
```
sudo fdisk -lu
mount
```And we can go from there.

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a7d030c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *          63   273072869   136536403+   7  HPFS/NTFS
/dev/sda3       294053760   611787329   158866785   83  Linux


```and now i'll try to mount it

```

mount: according to mtab, /dev/sda2 is already mounted on /mnt
mount failed

```


EDIT: I can now access my windows files from /mnt

---

### Post by caljohnsmith on 2009-01-04
So can you see all the system files OK under /mnt/Windows? If so, how about booting the Vista Recovery CD, and at the first main menu I think you have to choose to install Vista or something like that, even though it is a recovery CD; but after that you will get an option to go to the command line. Then run the commands from post #27 and let me know the results. Also try booting Vista again and let me know what happens.

---

### Post by dragos240 on 2009-01-04
> **caljohnsmith said:**
> So can you see all the system files OK under /mnt/Windows? If so, how about booting the Vista Recovery CD, and at the first main menu I think you have to choose to install Vista or something like that, even though it is a recovery CD; but after that you will get an option to go to the command line. Then run the commands from post #27 and let me know the results. Also try booting Vista again and let me know what happens.

If it installs windows doesn't windows wipe the entire disk? Becuase that will worry me.

---

### Post by dragos240 on 2009-01-04
> **caljohnsmith said:**
> So can you see all the system files OK under /mnt/Windows? If so, how about booting the Vista Recovery CD, and at the first main menu I think you have to choose to install Vista or something like that, even though it is a recovery CD; but after that you will get an option to go to the command line. Then run the commands from post #27 and let me know the results. Also try booting Vista again and let me know what happens.

Hey! My vista boots now! You have my gratitude!! Thank you!

---

### Post by caljohnsmith on 2009-01-04
Glad to hear that Vista is finally booting again. Cheers and have fun with Vista and Ubuntu. :)

---

### Post by dragos240 on 2009-01-05
> **caljohnsmith said:**
> Glad to hear that Vista is finally booting again. Cheers and have fun with Vista and Ubuntu. :)

I'll have fun with ubuntu on my time and when my dad comes i'll use my vista! Because i hate vista, but my dad likes, it. Thanks again!

---

