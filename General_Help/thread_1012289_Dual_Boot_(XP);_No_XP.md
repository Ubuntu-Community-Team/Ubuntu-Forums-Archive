---
title: "Dual Boot (XP); No XP?"
date: 2008-12-15
forum: General Help
---

### Post by FlyingIsFun1217 on 2008-12-15
Hey!

XP is vital to some of my work, but when I installed linux, I did it in a non-standard way. Here's what the install looked like before ubuntu:

|------Vista------|------XP------|

And here's how it looks now:

|------Ubuntu------|--Swap--|------XP------|

But, no matter what partition number I use in Grub, I always get an error message that it cannot boot!

Is there a way to get my XP partition working with Grub? I need it for some of my stuff, so I can't just ditch windows...

Thanks!
FlyingIsFun1217

---

### Post by logos34 on 2008-12-15
it's probably because the windows boot files were on the vista partition which you deleted when you installed ubuntu.

Back up your XP files and follow this to do a recovery:

[http://support.microsoft.com/kb/922809](http://support.microsoft.com/kb/922809)

It will overwrite grub, so you'll have to restore the latter afterward (see link my signature)

add:

you might want to post

sudo fdisk -l

but it looks like xp is (or at least was) sda2, so your menu.lst entry should be root (hd0,1)

also to doublecheck what I said about boot files by looking in xp c: for files like ntldr, boot.ini, ntdetect, etc.  If not there, then you'll have to do a recovery

---

### Post by caljohnsmith on 2008-12-15
If you are just missing the XP boot files, you don't necessarily have to do a full Windows Repair in order to restore them, although that could certainly work. You can simply replace the three Windows boot files, i.e. boot.ini, ntldr, and NTDETECT.COM, and also configure the boot.ini for the correct partition, and that should be all it takes if missing the boot files is the only problem. In order to see if XP is just missing its boot files and also to get a better idea of your setup, how about downloading the attached "boot_info8.txt" script to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info8.txt
```
That will create a "BootInfo.txt" file on your desktop; please copy/paste the contents of that file to your next post, or you can attach the file itself to your post. That will help clarify your setup and whether XP is missing its boot files.

---

### Post by logos34 on 2008-12-15
You could get the files here

[http://www.tinyempire.com/notes/files/fixntldr.zip](http://www.tinyempire.com/notes/files/fixntldr.zip)

and copy them to c: (need to edit boot.ini though) if you'd rather try that route

---

### Post by FlyingIsFun1217 on 2008-12-16
Thanks for the follow-ups everybody; Currently, I'm at school, but when I get home, I'll try out the solutions mentioned.

Thanks for keeping my faith alive in the community!

---------------EDIT---------------

Does it matter that I restored XP's MBR (since I installed it after Vista), and had it as the MBR before I installed Ubuntu?

Thanks again!
FlyingIsFun1217

---

### Post by caljohnsmith on 2008-12-16
> **FlyingIsFun1217 said:**
> 
Does it matter that I restored XP's MBR (since I installed it after Vista), and had it as the MBR before I installed Ubuntu?

Thanks again!
FlyingIsFun1217
If you are currently using Grub to boot Ubuntu, then Grub is your MBR rather than having a Windows MBR (assuming you did a normal Ubuntu install and let Grub be installed to the MBR). Therefore you don't need to worry about having previously restored XP's MBR.

---

### Post by FlyingIsFun1217 on 2008-12-16
'sudo fdisk -l':

> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cf267

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       19456   156280288+   f  W95 Ext'd (LBA)
/dev/sda5            9586       19456    79288776    7  HPFS/NTFS
/dev/sda6               1        9460    75987355+  83  Linux
/dev/sda7            9461        9585     1004031   82  Linux swap / Solaris

Partition table entries are not in disk order


FlyingIsFun1217

---

### Post by logos34 on 2008-12-16
uh oh, XP is on a logical partition--usually the only way to boot it is if the bootloader files are located on another PRIMARY partition

---

### Post by FlyingIsFun1217 on 2008-12-16
And that was what I was thinking to (that XP would have to be on the first partition).

Is there... dare I ask... any way that I can switch the partitions from linux?

FlyingIsFun1217

---

### Post by logos34 on 2008-12-16
I used to have setup like yours, 'cept both xp...I installed 32-bit XP home to a logical partition after XP pro x64 (hda1).  Never tried to switch or anything like that.  

Maybe create a small primary ntfs or fat32 primary boot partition (before or after XP) and put the windows bootloader files there? (maybe I have a link like that somewhere, let me look)

---

### Post by logos34 on 2008-12-16
here's one

[http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition](http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition)

reading it now

EDIT:

So I guess I wasn't too far off:
> 
"But we took the easy way out by resizing the linux partition and created a teeny weeny FAT32 primary partition. We could have stopped there but instead we set up this small partition as the windows boot partition by coping the three windows boot files - boot.ini, ntldr, NTDETECT.com and running bootcfg, fixboot on the new mini C drive we created. Once this was done the system successfully booted of the C drive, chainloaded the Windows 2000 installation on D drive."

---

### Post by caljohnsmith on 2008-12-16
> **FlyingIsFun1217 said:**
> And that was what I was thinking to (that XP would have to be on the first partition).

Is there... dare I ask... any way that I can switch the partitions from linux?

FlyingIsFun1217
If you can post the output of that boot_info8.txt script, I can help you boot XP from a logical partition. I have helped several people in the forums boot XP/Vista from a logical partition; it usually only takes a little work and isn't too big of a deal.

---

### Post by FlyingIsFun1217 on 2008-12-16
> 
Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #6 for its boot files.

sda2:
    File system:  
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sda5:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sda5 starts at sector 63
    Operating System: 
    Boot files/directories present: 

sda6:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Linux
    Boot files/directories present:  /boot/grub/menu.lst /boot /boot/grub

sda7:
    File system:  swap
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cf267

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *          63   312560639   156280288+   f  W95 Ext'd (LBA)
/dev/sda5       153983088   312560639    79288776    7  HPFS/NTFS
/dev/sda6             189   151974899    75987355+  83  Linux
/dev/sda7       151974963   153983024     1004031   82  Linux swap / Solaris

Partition table entries are not in disk order
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        0, size=        0, Id= 0
/dev/sda2 : start=       63, size=312560577, Id= f, bootable
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=153983088, size=158577552, Id= 7
/dev/sda6 : start=      189, size=151974711, Id=83
/dev/sda7 : start=151974963, size=  2008062, Id=82

sda6/boot/grub/menu.lst

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/default.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
##      altoptions=(single-user) single
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

title		Windows XP
root		(hd0,6)
makeactive
chainloader	+1

title		Linux Mint
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint Recovery
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda6 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Linux Mint (Last Good Boot)
root		(hd0,5)
kernel		/boot/last-good-boot/vmlinuz root=/dev/sda6 ro quiet splash  last-good-boot
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

sda6/boot

total 12680
drwxr-xr-x  4 root root    4096 2008-12-14 18:13 .
drwxr-xr-x 20 root root    4096 2008-12-14 09:45 ..
-rw-r--r--  1 root root  507665 2008-10-24 03:29 abi-2.6.27-7-generic
lrwxrwxrwx  1 root root       1 2008-12-14 09:37 boot -> .
-rw-r--r--  1 root root   91364 2008-10-24 03:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-14 18:11 gfxmenu
drwxr-xr-x  2 root root    4096 2008-12-15 16:17 grub
-rw-r--r--  1 root root 8918790 2008-12-14 18:13 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 03:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 03:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 03:29 vmlinuz-2.6.27-7-generic

sda6/boot/grub

total 244
drwxr-xr-x 2 root root   4096 2008-12-15 16:17 .
drwxr-xr-x 4 root root   4096 2008-12-14 18:13 ..
-rw-r--r-- 1 root root    197 2008-12-14 09:45 default
-rw-r--r-- 1 root root     15 2008-12-14 09:45 device.map
-rw-r--r-- 1 root root   9440 2008-12-14 09:45 e2fs_stage1_5
-rw-r--r-- 1 root root   9120 2008-12-14 09:45 fat_stage1_5
-rw-r--r-- 1 root root     19 2008-12-14 09:45 installed-version
-rw-r--r-- 1 root root   8224 2008-12-14 09:45 iso9660_stage1_5
-rw-r--r-- 1 root root  10144 2008-12-14 09:45 jfs_stage1_5
-rw-r--r-- 1 root root   4165 2008-12-15 16:17 menu.lst
-rw-r--r-- 1 root root   8480 2008-12-14 09:45 minix_stage1_5
-rw-r--r-- 1 root root  11296 2008-12-14 09:45 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-14 09:45 stage1
-rw-r--r-- 1 root root 125674 2008-12-14 09:45 stage2
-rw-r--r-- 1 root root  10856 2008-12-14 09:45 xfs_stage1_5

StdErr Messages 

ls: cannot access /dev/hd?: No such file or directory
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
ls: cannot access /dev/hd??*: No such file or directory
mount: you must specify the filesystem type
/dev/sda2: unknown volume type
umount: sda2: not mounted
/dev/sda7 looks like swapspace - not mounted
mount: you must specify the filesystem type
umount: sda7: not mounted


Thanks again for your tremendous help!

ps: I added the XP entry for grub a while ago, it doesn't do anything...

FlyingIsFun1217

---

### Post by caljohnsmith on 2008-12-16
That's great, that clarifies what you will need to do to boot XP from your logical partition. You are unfortunately missing your XP boot files at the present moment, so I've attached them to this post and also configured the boot.ini file so it should work with your particular setup. How about downloading the attached "WinXP_boot_files.zip" to your desktop, and then do:
```
sudo mount /dev/sda5 /mnt
cd ~/Desktop
unzip WinXP_boot_files.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
Next open up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your Windows entry with:
```
title Windows XP
rootnoverify (hd0,4)
chainloader +1
```
And lastly, you definitely need to fix your Windows boot sector, because it currently shows that the XP partition starts at sector 63 when actually your XP partition starts at sector 153983088. So first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows sda5 partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "sectors are not identical", then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot, select Windows from your Grub menu, and let me know exactly what happens. :)

---

### Post by FlyingIsFun1217 on 2008-12-16
Great! I'll try that in a few minutes and report back.

FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-12-16
Yep, that seemed to do the trick!

Numerous thanks!
FlyingIsFun1217

---

### Post by caljohnsmith on 2008-12-16
Glad to hear that worked OK; cheers and have fun with XP and Ubuntu. :)

---

### Post by meierfra. on 2008-12-16
I recommend to move the Windows entry in menu.lst above the line


### BEGIN AUTOMAGIC KERNELS LIST


otherwise it will disappear during the next kernel update.

---

### Post by logos34 on 2008-12-17
> **caljohnsmith said:**
> That's great, that clarifies what you will need to do to boot XP from your logical partition. You are unfortunately missing your XP boot files at the present moment...

Nice work, caljohnsmith.

I seem to remember now seeing something about this--maybe it was [this post]("http://ubuntuforums.org/showpost.php?p=4701367&postcount=251") by Herman.  Forgot that you could in fact boot windows on a logical partition.  I was mixing it up with the fact that windows' own bootloader won't boot windows on a logical because it only looks for an *active primary* partition with boot files, but that doesn't mean it can't be done with gub and some handywork.

---

### Post by caljohnsmith on 2008-12-17
> **logos34 said:**
> I was mixing it up with the fact that windows' own bootloader won't boot windows on a logical because it only looks for an *active primary* partition with boot files, but that doesn't mean it can't be done with gub and some handywork.
I think you are exactly right--the only thing that really stops a normal Windows user from being able to boot Windows from a logical partition is the fact that the Windows MBR can only boot a primary partition. So if you use a different boot loader like Grub that can boot a logical partition, it's usually not a problem to boot Windows from a logical partition if you put a little work into it. :)

---

### Post by FlyingIsFun1217 on 2008-12-17
Might I ask what the difference between a logical and primary partition is?

FlyingIsFun1217 :)

---

