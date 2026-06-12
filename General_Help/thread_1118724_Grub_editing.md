---
title: "Grub editing"
date: 2009-04-07
forum: General Help
---

### Post by jhinds on 2009-04-07
If I select "e" at the grub boot menu and edit the script operating behind the windows choice using this syntax:

title		Windows XP (loader)
root		(hd1,0)
savedefault
makeactive
Map (hd0) (hd1)
Map (hd1) (hd0)
chainloader	+1


it will boot windows.  An edit "here" will not survive a reboot, however, and one must therefore apply the edit within ubuntu itself. I used this to edit: sudo nano /boot/grub/menu.lst.  I made the edit, saved the file, which should have been the final and complete fix.  But something else is going on because when I rebooted and chose windows I got the same error as before and when I then looked at the script, again using "e" at the grub splash on boot, the changes I made and saved to menu.lst from within ubuntu were gone...but they are still there if I go back into ubuntu and view menu.lst.  So, I am thoroughly perplexed.  The syntax I view from using "e" at the grub splash on bootup reads:

root (hd0,1)
savedefault
makeactive
chainloader +1

Any assistance would be greatly appreciated.  Of course, I am new at this, so take that into consideration please.

---

### Post by oldos2er on 2009-04-07
Do you have more than one Linux boot partition?

---

### Post by matmat07 on 2009-04-07
Or more than one entry of windows. I have a laptop an it has 3 (recovery, vista and homemedia like). I think i wil be also different if you use grub 2

---

### Post by jhinds on 2009-04-07
Only one linux boot partition.  Linux is on its own drive as is my lone install of winxp.

---

### Post by meierfra. on 2009-04-07
Are you sure that you are editing the correct file?  (There was a case a couple of weeks ago where somebody edited "menu.1st" instead of "menu.lst")

Are you sure you saved the file correctly?  (saving with nano is a little tricky. You might use "gksudo gedit /boot/grub/menu.lst" instead of nano.)

**If none of this helps:**

Download the Boot Info Script to your desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and type:


```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.


Also post the output of

```
ls -l /boot/grub
```

---

### Post by jhinds on 2009-04-08
meierfra,
I don't think I have a menu.1st.  Anyhow, I worked on the menu.LST and when I finished used cntrl x to exit whereupon it gave me the option to save the file by entering a "Y", which I did.  I'm sure I am doing something wrong, however.
I'll follow your instructions and let you know what happened, but it might be a little while.  Your post caught me just as I was considering reinstalling grub from live CD.  Not the option I want to pursue.  The computer has multiple HD,s, hot swap bays, multicard readers, etc., and I think grub has a hard time determining exactly how to call the location of the winxp install.  And besides I want to learn from mistakes which I won't really do if I merely reinstall stuff.  That just covers up my errors.

Thanks.  I'll be back.

---

### Post by jhinds on 2009-04-08
meierfra,

Here is results.txt from sudo bash ~/desktop/boot_info_script*.sh:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x011b011c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   468,648,179   468,648,117  83 Linux
/dev/sda2         468,648,180   488,392,064    19,743,885   5 Extended
/dev/sda5         468,648,243   488,392,064    19,743,822  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x011b011b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00e800e8

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="6e393f5f-4a20-4e47-afec-2b71869ca567" TYPE="ext3" 
/dev/sda5: UUID="9e2bd177-1b48-47bf-a6d2-6a06b6929d3e" TYPE="swap" 
/dev/sdb1: UUID="04DC86DFDC86CA7E" LABEL="Windows XP" TYPE="ntfs" 
/dev/sdc1: UUID="FACC7CADCC7C65B3" LABEL="Rackspace" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=6e393f5f-4a20-4e47-afec-2b71869ca567 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6e393f5f-4a20-4e47-afec-2b71869ca567

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
uuid		6e393f5f-4a20-4e47-afec-2b71869ca567
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6e393f5f-4a20-4e47-afec-2b71869ca567 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		6e393f5f-4a20-4e47-afec-2b71869ca567
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6e393f5f-4a20-4e47-afec-2b71869ca567 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		6e393f5f-4a20-4e47-afec-2b71869ca567
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows XP (loader)
root		(hd1,0)
savedefault
makeactive
Map (hd0) (hd1)
Map (hd1) (hd0)
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6e393f5f-4a20-4e47-afec-2b71869ca567 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9e2bd177-1b48-47bf-a6d2-6a06b6929d3e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 220.1GB: boot/grub/menu.lst
 220.1GB: boot/grub/stage2
 220.2GB: boot/initrd.img-2.6.27-7-generic
 220.1GB: boot/vmlinuz-2.6.27-7-generic
 220.2GB: initrd.img
 220.1GB: vmlinuz

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(2)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Microsoft " /fastdetect

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin /usepmtimer

=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

---

### Post by jhinds on 2009-04-08
And, here is output from ls -l /boot/grub:

```
total 224
-rw-r--r-- 1 root root    197 2009-04-05 15:28 default
-rw-r--r-- 1 root root     45 2009-04-05 15:28 device.map
-rw-r--r-- 1 root root   8108 2009-04-05 15:28 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-04-05 15:28 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-04-05 15:28 installed-version
-rw-r--r-- 1 root root   8712 2009-04-05 15:28 jfs_stage1_5
-rw-r--r-- 1 root root   4639 2009-04-05 21:55 menu.lst
-rw-r--r-- 1 root root   4607 2009-04-05 18:19 menu.lst~
-rw-r--r-- 1 root root   4639 2009-04-06 20:19 menu.lst_backup
-rw-r--r-- 1 root root   7352 2009-04-05 15:28 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-04-05 15:28 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-04-05 15:28 stage1
-rw-r--r-- 1 root root 121460 2009-04-05 15:28 stage2
-rw-r--r-- 1 root root   9556 2009-04-05 15:28 xfs_stage1_5
```

---

### Post by meierfra. on 2009-04-08
As far as I can see Grub is installed correctly. So reinstalling grub will not help. For some reason you seem to be unable to edit "menu.lst":

The last time menu.lst was modified was on Sunday:

> -rw-r--r-- 1 root root   4639 2009-04-05 21:55 menu.lst

Also menu.lst is still showing the wrong entry:

> title		Windows XP (loader)
root		(hd1,0)
savedefault
makeactive
Map (hd0) (hd1)
Map (hd1) (hd0)
chainloader	+1

So try to edit menu.lst with

```
gksudo gedit /boot/grub/menu.lst
```

After you save  the file, close the file and open it again to see whether your changes did stick.

---

### Post by jhinds on 2009-04-08
:p Success!

meierfra,
After I got back to the computer I used gedit to edit the file and it worked.  Don't know why sudo nano didn't, but I am sure it was operator error.

Hey!  Thanks a lot.  File this one under seeing is not always believing.

---

### Post by meierfra. on 2009-04-08
> Success!
Great. Have fun with XP and Ubuntu.

---

### Post by grickaby on 2009-04-08
Help!

It's a long story...but I just installed Jaunty and I lost my windows in grub. 

I know that it's on /dev/sda7/

But don't know how to setup grub :(

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu jaunty (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

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

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x870fcc8c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,461,459    78,461,397  83 Linux
/dev/sda2          78,461,460   894,836,564   816,375,105   f W95 Ext d (LBA)
/dev/sda5          81,915,498    90,333,494     8,417,997   7 HPFS/NTFS
/dev/sda6          90,333,558   771,955,379   681,621,822   7 HPFS/NTFS
/dev/sda7         771,955,443   894,836,564   122,881,122   7 HPFS/NTFS
/dev/sda8          78,461,586    81,915,434     3,453,849  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="079382d3-3ca9-49df-84bb-cb1830178052" TYPE="ext4" 
/dev/sda5: UUID="E054F5CD54F5A706" LABEL="SWAP" TYPE="ntfs" 
/dev/sda6: UUID="20EA5F5EEA5F2EF2" LABEL="Game" TYPE="ntfs" 
/dev/sda7: UUID="F0A82069A8203110" TYPE="ntfs" 
/dev/sda8: UUID="2ea10848-64f9-40d4-ac47-9a395b98ad58" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/greg/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=greg)


=========================== sda1/boot/grub/menu.lst: ===========================

hiddenmenu
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
# kopt=root=UUID=079382d3-3ca9-49df-84bb-cb1830178052 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=079382d3-3ca9-49df-84bb-cb1830178052

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

title Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=079382d3-3ca9-49df-84bb-cb1830178052 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=079382d3-3ca9-49df-84bb-cb1830178052 ro  single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu jaunty (development branch), memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
rootnoverify (hd0,6)
chainloader +1
makeactive


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=079382d3-3ca9-49df-84bb-cb1830178052 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=2ea10848-64f9-40d4-ac47-9a395b98ad58 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .4GB: boot/grub/menu.lst
   1.6GB: boot/grub/stage2
   4.5GB: boot/initrd.img-2.6.28-11-generic
    .3GB: boot/vmlinuz-2.6.28-11-generic
   4.5GB: initrd.img
    .3GB: vmlinuz
```

```
greg@ubuntu:~$ sudo ls -l /boot/grub
total 216
-rw-r--r-- 1 root root    197 2009-04-08 18:10 default
-rw-r--r-- 1 root root     15 2009-04-08 11:48 device.map
-rw-r--r-- 1 root root   8288 2009-04-08 18:10 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-04-08 18:10 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-04-08 18:11 installed-version
-rw-r--r-- 1 root root   8712 2009-04-08 18:10 jfs_stage1_5
-rw-r--r-- 1 root root   3125 2009-04-08 18:17 menu.lst
-rw-r--r-- 1 root root   3125 2009-04-08 18:16 menu.lst~
-rw-r--r-- 1 root root   4612 2009-04-08 17:28 menu.lst_original
-rw-r--r-- 1 root root   7352 2009-04-08 18:10 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-04-08 18:10 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-04-08 18:10 stage1
-rw-r--r-- 1 root root 121740 2009-04-08 18:11 stage2
-rw-r--r-- 1 root root   9556 2009-04-08 18:10 xfs_stage1_5
greg@ubuntu:~$ 

```

I've been searching the forums and tried this:

title Windows XP
rootnoverify (hd0,6)
chainloader +1
makeactive

but no luck, i get ERROR 13 something about invalid executable...

---

### Post by meierfra. on 2009-04-08
grickaby: It seems you deleted  or formated the partition containing the XP boot files.  To fix your problem use this tutorial:


[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

In Step 1  use /dev/sda7 

In Step 3 use "partition(4)"

In Step 4 use 

title XP
rootnoverify (hd0,6)
chainloader +1


You have to carry out Step 5.

Just for future reference: It is better to start a new thread than adding a problem to an existing thread.

---

### Post by grickaby on 2009-04-08
Sorry.

Thank you though. This worked...except now I get a bunch of "CORRUPT .DLL ERRORS" when windows boots.

I'm going to try the windows recovery console.

Thanks again!

---

### Post by jhinds on 2009-04-09
probably all you need to do to windows is rebuild your mbr....then make sure grub points to the right place.  I had to do this too.

---

