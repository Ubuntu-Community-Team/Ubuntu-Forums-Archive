---
title: "Adding Windows to Grub"
date: 2008-12-17
forum: General Help
---

### Post by Crym on 2008-12-17
I cannot seem to add Windows to Grub.
I'm using Ultimate Edition (think it is wrapped around Ubuntu 8.10).
I got two sata harddrives, but the second one is only used for storage (ntfs-filesystem).
The first one is divided into 3. 
According to GParted, Linux is on /dev/sda1 (ext3), and sda2 is divided into two: sda4 as swap, and sda6 is the windows partition (ntfs).
(I'm also quite new in Linux).
Windows have never been visible on Grub since I installed Linux.

readout after sudo fdisk -l:


Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7be47be4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17210   138239293+  83  Linux
/dev/sda2           17211       24320    57111075    f  W95 Ext'd (LBA)
/dev/sda5           17211       17946     5911888+  82  Linux swap / Solaris
/dev/sda6           17947       24320    51199123+   7  HPFS/NTFS

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6dc79fb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91202   732574552    7  HPFS/NTFS





my /boot/grub/menu.lst looks like this:



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

#A splash image for the menu
#splashimage=/boot/grub/splashimages/KUBUNTU_splashscreen_blue_neon_logo_03.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=9b64a01f-0135-4506-9e57-b555cce0f5e4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9b64a01f-0135-4506-9e57-b555cce0f5e4

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		9b64a01f-0135-4506-9e57-b555cce0f5e4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9b64a01f-0135-4506-9e57-b555cce0f5e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		9b64a01f-0135-4506-9e57-b555cce0f5e4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9b64a01f-0135-4506-9e57-b555cce0f5e4 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9b64a01f-0135-4506-9e57-b555cce0f5e4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9b64a01f-0135-4506-9e57-b555cce0f5e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9b64a01f-0135-4506-9e57-b555cce0f5e4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9b64a01f-0135-4506-9e57-b555cce0f5e4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9b64a01f-0135-4506-9e57-b555cce0f5e4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


Thanks,
Crym

---

### Post by caljohnsmith on 2008-12-17
Is Windows on your 750 GB sdb drive? It looks like sdb1 might be a data partition though. If Windows was on your sda drive (the drive you installed Ubuntu to), then unfortunately it looks like Windows was overwritten during the install. Did you use the "guided" or "manual" partitioning options when you installed Ubuntu?

---

### Post by Crym on 2008-12-17
the 750GB (sdb) is just a harddrive with data. 
sda is the one i installed windows and linux on.
i installed windows first, and created all the partitions then.
then i installed linux. windows was installed on the third partition(sda6) on sda, and linux on the first(sda1) and swap (sda5) on second.
i found something on an other forum, saying something about windows having to be on the very first partition to be able to boot. can anyone confirm this?

---

### Post by Michaelg14 on 2008-12-17
At the end of /boot/grub/menu.lst you should have something like this


> # This is a divider, added to separate the menu items below from the Debian
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



Where is says root  (hdo,1) is where it points to the location of Windows.  You will need to enter the disk # and partition # for your setup.

Window does not need to be in the first partition to boot.  My Ubuntu is in hd(0,0) and as you can see, windows is in the second partition.

---

### Post by Michaelg14 on 2008-12-17
At the end of /boot/grub/menu.lst you should have something like this


> # This is a divider, added to separate the menu items below from the Debian
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



Where is says root  (hdo,1) is where it points to the location of Windows.  You will need to enter the disk # and partition # for your setup.

Window does not need to be in the first partition to boot.  My Ubuntu is in hd(0,0) and as you can see, windows is in the second partition.

Sorry for the double post.

---

### Post by caljohnsmith on 2008-12-17
> **Crym said:**
> the 750GB (sdb) is just a harddrive with data. 
sda is the one i installed windows and linux on.
i installed windows first, and created all the partitions then.
then i installed linux. windows was installed on the third partition(sda6) on sda, and linux on the first(sda1) and swap (sda5) on second.
i found something on an other forum, saying something about windows having to be on the very first partition to be able to boot. can anyone confirm this?
OK, I didn't notice you had a logical NTFS partition on your sda drive, that was my mistake. To boot Windows from a logical partition takes some work though; in order to get a clearer picture of your setup, how about downloading the attached "boot_info9.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info9.txt
```
That will create a "BootInfo.txt" file on your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and help determine how to proceed with booting Windows from your logical sda6 partition.

---

### Post by Crym on 2008-12-17
I have tried different versions of hd0,1 through 4 without any luck.

this is the info from my BootInfo.txt:


Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #1 for its boot files.
No known boot loader is installed in the MBR of /dev/sdb

sda1:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Linux
    Boot files/directories present:  /boot/grub/menu.lst /boot /boot/grub

sda2:
    File system:  
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sda5:
    File system:  swap
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sda6:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sda6 starts at sector 63
    Operating System: XP
    Boot files/directories present: 

sdb1:
    File system:  ntfs
    Boot sector  type:  Vista
    Boot sector  info:  According to the info in the boot sector, sdb1 starts at sector 63
    Operating System: 
    Boot files/directories present: 


Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7be47be4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   276478649   138239293+  83  Linux
/dev/sda2       276478650   390700799    57111075    f  W95 Ext'd (LBA)
/dev/sda5       276478713   288302489     5911888+  82  Linux swap / Solaris
/dev/sda6       288302553   390700799    51199123+   7  HPFS/NTFS

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6dc79fb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1465149166   732574552    7  HPFS/NTFS



Edit:
What is the difference between a logical partition and a normal partition?
Is there a certain way to create partitions for linux and windows on the same disk without making any logical? (in case of reinstalling in the future)

---

### Post by caljohnsmith on 2008-12-17
OK, as I suspected, your Windows partition is unfortunately missing its three necessary boot files according to that script you ran; I've attached the files you need to this post and also configured the boot.ini file so it should work with your particular setup. How about downloading the attached "WinXP_boot_files.zip" to your desktop, and then do:
```
sudo mount /dev/sda6 /mnt
cd ~/Desktop
unzip WinXP_boot_files.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
Next open up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And at the very bottom add the following entry:
```
title Windows XP
rootnoverify (hd0,5)
chainloader +1
```
And lastly, you definitely need to fix your Windows boot sector, because it currently shows that the XP partition starts at sector 63 when actually your XP partition starts at sector 288302553. So first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows sda6 partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "sectors are not identical", then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot, select Windows from your Grub menu, and let me know exactly what happens. We can work from there. :)

---

### Post by Crym on 2008-12-17
That made it work :D
Thank you very much! =)
Just one more thing, what is the difference between a logical partition and a normal partition?

---

