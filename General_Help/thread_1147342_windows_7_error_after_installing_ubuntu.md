---
title: "windows 7 error after installing ubuntu"
date: 2009-05-03
forum: General Help
---

### Post by m4rc1n on 2009-05-03
So, i just installed ubuntu on my laptop. Now, the problem is that i can't access my windows 7 partition. I can't boot into windows and the DVD can't find the windows instalation to repair. Now, what to do? Thanks ( linux noob)

---

### Post by nacho32 on 2009-05-03
under the grub are you choosing other operating systems? On the desktop under places tab do you see windows 7 ?  I did a triple boot XP win 7 beta and ubuntu and it all works fine

---

### Post by codeseer on 2009-05-03
Please download this and place it on your Desktop in Ubuntu:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

I'll have you run it, so that we can gather more information about your hard drive setup and boot process to troubleshoot the problem more clearly.

After you download it to the Desktop, right-click it and click Properties, then click the Permissions tab and check the box at the bottom of the window that 'allows executing'.

Then click the Applications menu at the top right of your screen, followed by the Accessories menu and then click Terminal. A black window will come up, in it type the following commands, ending each line with a press of the Enter key:

```

cd ~/Desktop
sudo ./boot*.sh

```

Please remember that in Linux, everything is case sensitive. Therefore, a lowercase 'd' is different than an uppercase 'D'. Also, you will be prompted for the password you gave when you installed Ubuntu whenever you use the 'sudo' command. The 'sudo' command escalates privileges and in this case is needed to properly view the hard drives and boot process.

After you have done this, it should place a Results.txt file on your desktop. Double-click that file and select Edit->Copy. Then return here and start a new reply message. In this message, click the # sign at the top of the message editor box and this will give you CODE tags; click between these tags ({code]**here**[/code}) and paste the contents that you copied from the Results.txt file.

---

### Post by BslBryan on 2009-05-03
> **codeseer said:**
> Please download this and place it on your Desktop in Ubuntu:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

I'll have you run it, so that we can gather more information about your hard drive setup and boot process to troubleshoot the problem more clearly.

After you download it to the Desktop, right-click it and click Properties, then click the Permissions tab and check the box at the bottom of the window that 'allows executing'.

Then click the Applications menu at the top right of your screen, followed by the Accessories menu and then click Terminal. A black window will come up, in it type the following commands, ending each line with a press of the Enter key:

```

cd ~/Desktop
sudo ./boot*.sh

```

Please remember that in Linux, everything is case sensitive. Therefore, a lowercase 'd' is different than an uppercase 'D'. Also, you will be prompted for the password you gave when you installed Ubuntu whenever you use the 'sudo' command. The 'sudo' command escalates privileges and in this case is needed to properly view the hard drives and boot process.

After you have done this, it should place a Results.txt file on your desktop. Double-click that file and select Edit->Copy. Then return here and start a new reply message. In this message, click the # sign at the top of the message editor box and this will give you CODE tags; click between these tags ({code]**here**[/code}) and paste the contents that you copied from the Results.txt file.

+1.  I just hope you haven't written over your Windows partition.

---

### Post by codeseer on 2009-05-03
> **BslBryan said:**
> +1.  I just hope you haven't written over your Windows partition.

Yeah, that's what I was thinking. Some people oppose the manual partitioning, but I highly recommend it to avoid all kinds of issues like that.

---

### Post by m4rc1n on 2009-05-03
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320,0 GB, 320072933376 byte
255 huvuden, 63 sektorer/spår, 38913 cylindrar, totalt 625142448 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Diskidentifierare: 0x28242824

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    77,979,509    77,979,447   5 Extended
/dev/sda5                 126    77,979,509    77,979,384  83 Linux
/dev/sda2          81,915,435   476,648,549   394,733,115   7 HPFS/NTFS
/dev/sda3         476,648,550   625,137,344   148,488,795   7 HPFS/NTFS
/dev/sda4          77,979,510    81,915,434     3,935,925  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="1AE3F96C56F328AA" TYPE="ntfs" 
/dev/sda3: UUID="C014AC4814AC4370" TYPE="ntfs" 
/dev/sda4: UUID="562e47be-c10d-48c9-8ea8-ba48c249a01e" TYPE="swap" 
/dev/sda5: UUID="f15934d7-8cca-424b-9a28-e23665f86798" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/paapa/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=paapa)


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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=f15934d7-8cca-424b-9a28-e23665f86798 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f15934d7-8cca-424b-9a28-e23665f86798

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f15934d7-8cca-424b-9a28-e23665f86798
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f15934d7-8cca-424b-9a28-e23665f86798 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f15934d7-8cca-424b-9a28-e23665f86798
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f15934d7-8cca-424b-9a28-e23665f86798 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f15934d7-8cca-424b-9a28-e23665f86798
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=f15934d7-8cca-424b-9a28-e23665f86798 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=562e47be-c10d-48c9-8ea8-ba48c249a01e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


   2.0GB: boot/grub/menu.lst
   1.8GB: boot/grub/stage2
   2.0GB: boot/initrd.img-2.6.28-11-generic
   1.9GB: boot/vmlinuz-2.6.28-11-generic
   2.0GB: initrd.img
   1.9GB: vmlinuz
```And no i have not whiped the whole harddrive. I am a advanced PC user but i am new to Ubuntu. I don't know why my windows wont show up. I can access the partition and my files but that's it.

---

### Post by codeseer on 2009-05-03
It looks like you don't have a Grub entry for Windows 7. So, let's have you do steps 1-5 here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

The live cd is the same cd you used to install with, just put it in and restart. You should be presented with a menu where you can select 'try ubuntu without making changes'.

After you have done this, please post another Results.txt using the previous method. If you do not delete the current Results.txt the new one will have a number attached to he file name.

---

### Post by m4rc1n on 2009-05-03
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320,0 GB, 320072933376 byte
255 huvuden, 63 sektorer/spår, 38913 cylindrar, totalt 625142448 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Diskidentifierare: 0x28242824

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    77,979,509    77,979,447   5 Extended
/dev/sda5                 126    77,979,509    77,979,384  83 Linux
/dev/sda2          81,915,435   476,648,549   394,733,115   7 HPFS/NTFS
/dev/sda3         476,648,550   625,137,344   148,488,795   7 HPFS/NTFS
/dev/sda4          77,979,510    81,915,434     3,935,925  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="1AE3F96C56F328AA" TYPE="ntfs" 
/dev/sda3: UUID="C014AC4814AC4370" TYPE="ntfs" 
/dev/sda4: UUID="562e47be-c10d-48c9-8ea8-ba48c249a01e" TYPE="swap" 
/dev/sda5: UUID="f15934d7-8cca-424b-9a28-e23665f86798" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/paapa/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=paapa)


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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=f15934d7-8cca-424b-9a28-e23665f86798 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f15934d7-8cca-424b-9a28-e23665f86798

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f15934d7-8cca-424b-9a28-e23665f86798
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f15934d7-8cca-424b-9a28-e23665f86798 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f15934d7-8cca-424b-9a28-e23665f86798
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f15934d7-8cca-424b-9a28-e23665f86798 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f15934d7-8cca-424b-9a28-e23665f86798
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=f15934d7-8cca-424b-9a28-e23665f86798 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=562e47be-c10d-48c9-8ea8-ba48c249a01e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


   2.0GB: boot/grub/menu.lst
   1.8GB: boot/grub/stage2
   2.0GB: boot/initrd.img-2.6.28-11-generic
   1.9GB: boot/vmlinuz-2.6.28-11-generic
   2.0GB: initrd.img
   1.9GB: vmlinuz
```
Still no luck.. Think I just have to reinstall windows

---

### Post by mysoogal on 2009-05-03
hey dude next time use wubi installer ! :KS

try to avoid ubuntu 9.04 just in-case you have a very hmm outdated system find the ubuntu 8.10 ISO then mount that ISO to F: drive whatever and should ask you how you like to install ubuntu ! pick the middle option and install it on C: with 15 GB space, thats how my setup is right now everything is smooth.

im on double boot with xp and ubuntu ! its very good 

oh about your problem, i heard you need to remount the NTFS partion back into Grub so it picks it up.

---

### Post by m4rc1n on 2009-05-03
> **mysoogal said:**
> hey dude next time use wubi installer ! :KS

try to avoid ubuntu 9.04 just in-case you have a very hmm outdated system find the ubuntu 8.10 ISO then mount that ISO to F: drive whatever and should ask you how you like to install ubuntu ! pick the middle option and install it on C: with 15 GB space, thats how my setup is right now everything is smooth.

im on double boot with xp and ubuntu ! its very good 

oh about your problem, i heard you need to remount the NTFS partion back into Grub so it picks it up.
laptop bought a couple of months ago and outdated.... ehm.. anywho about the last thing u said, how do i remount the NTFS partition to Grub?

---

### Post by codeseer on 2009-05-03
Wubi causes a lot of problems for people; I don't personally recommend it at all.

The issue is Windows 7. It is designed in a way that it works against grub.

Let's see if we can't get it to jump in manually.

Do this at the Terminal after booting Ubuntu:

```
gksudo gedit /boot/grub/menu.lst
```

Scroll to the bottom of that file, where it says:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

```

Then append this to the end of the file:

```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows 7
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

Now, press the Save button and reboot to see if you have a menu entry for Windows 7. If you do, select it and see what happens.

---

### Post by m4rc1n on 2009-05-03
now i hav another problem.. i got pissed and used fixmbr with my windows dvd and now i can't boot ubuntu but only windows :P

---

### Post by codeseer on 2009-05-03
Try the steps 1-5 again off the live cd, that should fix it.

Then add what I posted above and see what it gives you when trying to boot Windows.

Here's the link: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by m4rc1n on 2009-05-05
> **codeseer said:**
> Try the steps 1-5 again off the live cd, that should fix it.

Then add what I posted above and see what it gives you when trying to boot Windows.

Here's the link: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
gave me a BOOTMGR is missing error. can it have to do with the fact that i have instaled ubuntu on a ext4 partition?

---

### Post by codeseer on 2009-05-05
The 'BOOTMGR is missing' error is Windows. See if you can do a fixboot from the CD.

---

### Post by m4rc1n on 2009-05-08
> **codeseer said:**
> The 'BOOTMGR is missing' error is Windows. See if you can do a fixboot from the CD.
Yes, now everything works :) Thanks a lot for all the help i've got!!

---

