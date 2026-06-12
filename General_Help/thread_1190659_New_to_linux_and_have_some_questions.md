---
title: "New to linux and have some questions"
date: 2009-06-18
forum: General Help
---

### Post by awdowns on 2009-06-18
Today is my first day using ubuntu.  I installed it as a 2nd os with after win xp sp3.  I used partition magic 8 to set aside 15gb to install ubuntu on.  I must have hurried through the install and did not read clearly but it ended up taking just what was needed off my xp partition to install on.  I then tried to use the ubuntu partition editor.  After installing the editor, it told me my partition was full.  So I booted up windows and opened partition magic and got the error 117 cant read partition or something like that.  So I restarted the computer and got grub error 17.  After trying to fix it using the ubuntu disc I deleted the 15 gig partition and reinstalled ubuntu.  Now I have 2 partitions of ubuntu installed and one win xp.  I want to get rid of the first attempt but im scared Ill mess it up again, so how would I go about doing that without getting the grub error again?  

Thanks, 

-Steve

---

### Post by monkey186 on 2009-06-18
i would just delete the partition with the first attempt, and merge it with XP using partition magic. worst case scenario if the grub gets messed up again you will just reinstall ubuntu again on the correct 15gb partition.

---

### Post by delcypher on 2009-06-18
Hi awdowns. Could you clarify what you mean by > it ended up taking just what was needed off my xp partition to install on? Do you mean that the ubuntu install resized your windows partition and then installed ubuntu on the extra space that was made?

- In future I would highly advise choosing the advanced option during the install when ubuntu is deciding how to partition your drives.

Could you post the output of the following three commands (go into Applications > Accessories > Terminal) (in ubuntu - the working one)?
```
sudo fdisk -l
cat /boot/grub/menu.lst
mount
```

The first will list the partitions on available drives on your computer and the second is the contents of the configuration file for GRUB and the third lists the mounted partitions.

Essentially what you need to do is identify which ubuntu partition isn't being used. Once you've done that I would recommend booting into a livecd and using the partition editor (System > Administration > Partition editor) to delete the old ubuntu partition and then resize one or more partitions to take the freed space.  After that you will need to edit your GRUB configuration file to remove the entries for the old ubuntu install and possibly change the partition numbers too (if you remove the old ubuntu partition it may change the partition number of some of your used partitions). Once you've done that I'd recommend doing a disk check (if you resized an NTFS windows partition schedule a full disk check in windows, if you resized an ext3 partition then you can use a fsck to check the partition).

Unfortunately things may get more complicated if for some reason GRUB is running off your old ubuntu partition, but hopefully it isn't. If it is you will need to reinstall GRUB - it's quite easy to do and there are plenty of guides for doing it.

If you post the output of the commands above we can take you through the process. Hope this helps.

---

### Post by awdowns on 2009-06-18
> **delcypher said:**
> Hi awdowns. Could you clarify what you mean by ? Do you mean that the ubuntu install resized your windows partition and then installed ubuntu on the extra space that was made?


Exactly

I know which partitions arent being used.  When I installed the first time, it only took 2.3gb off my xp partition.  /dev/sda6 and /dev/sda7 is from my first attempt

Thanks alot for looking at this for me

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27522751

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22170   178080493+   7  HPFS/NTFS
/dev/sda2           22171       24792    21061215    f  W95 Ext'd (LBA)
/dev/sda5           22497       22879     3076416    7  HPFS/NTFS
/dev/sda6           22171       22474     2441817   83  Linux
/dev/sda7           22475       22496      176683+  82  Linux swap / Solaris
/dev/sda8           22880       24706    14675346   83  Linux
/dev/sda9           24707       24792      690763+  82  Linux swap / Solaris

Partition table entries are not in disk order

_______________________________________________________________________________________

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
# kopt=root=UUID=85f8e143-f2fd-451a-9057-da263e4873d9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=85f8e143-f2fd-451a-9057-da263e4873d9

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
uuid        85f8e143-f2fd-451a-9057-da263e4873d9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=85f8e143-f2fd-451a-9057-da263e4873d9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        85f8e143-f2fd-451a-9057-da263e4873d9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=85f8e143-f2fd-451a-9057-da263e4873d9 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        85f8e143-f2fd-451a-9057-da263e4873d9
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=80f4e1fc-8938-4711-8915-ff7ffa95f16d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=80f4e1fc-8938-4711-8915-ff7ffa95f16d ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, memtest86+ (on /dev/sda6)
root        (hd0,5)
kernel        /boot/memtest86+.bin  
savedefault
boot
[FONT=monospace]
_________________________________________________________________________

/dev/sda8 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/steve/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=steve)

[/FONT]

---

### Post by delcypher on 2009-06-18
Okay things look okay, the copy of GRUB you are using is on your current Ubuntu partition so things should be easy.

1. Boot using a livecd and start the partition editor and delete /dev/sda6 and /dev/sda7 and then resize the other partitions as you so desire. Then restart.

2. Because you are removing /dev/sda6 and /dev/sda7 there is a possibility that when you reboot your computer that it won't be able to boot from the hard drive because it may try to get GRUB from a now non existent partition number. I don't know exactly how it works so that's why I'm not sure. But if when you restart you get an error message (such as error 17 [http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors]("http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors")) you will need to reinstall GRUB to the MBR. A guide on doing this is available at [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351").

3. Assuming you are able to boot (or you weren't but you've fixed the issue by reinstalling GRUB to the MBR) you can remove the old ubuntu entries from /boot/grub/menu.lst by commenting them out .These are the three entries at the end of the file as listed below. You need to edit the file using a text editor with root privileges (If you don't know how to do this then run ```
gksudo gedit /boot/grub/menu.lst
``` in the terminal and make the necessary changes). Make a back-up first just incase you do something wrong.

--comment out last three entries in /boot/grub/menu.lst so it looks like this.
```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
#title Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda6)
#root (hd0,5)
#kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=80f4e1fc-8938-4711-8915-ff7ffa95f16d ro quiet splash
#initrd /boot/initrd.img-2.6.28-11-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
#title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda6)
#root (hd0,5)
#kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=80f4e1fc-8938-4711-8915-ff7ffa95f16d ro single
#initrd /boot/initrd.img-2.6.28-11-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
#title Ubuntu 9.04, memtest86+ (on /dev/sda6)
#root (hd0,5)
#kernel /boot/memtest86+.bin
#savedefault
#boot
```

4. Run a disk check on the partitions you resized. In windows you can use scandisk. In Ubuntu you can do it from the livecd (probably easier as you have full access) check out this guide [here]("http://www.cyberciti.biz/faq/linux-unix-check-file-system-consistency/").


Hopefully that's it, let me know how you get on and good luck!

---

### Post by awdowns on 2009-06-20
Thanks alot for the help!  Ive got everything working except for removing the old ubuntu from the grub boot screen.  The code you posted was the same as the code in the file, Just formatted slightly different.  Im not sure if I was supposed to copy and paste it or what.   Ive pasted the last three entries from  gksudo gedit /boot/grub/menu.lst for you to look at.


Thanks again, 

-Steve


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=80f4e1fc-8938-4711-8915-ff7ffa95f16d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=80f4e1fc-8938-4711-8915-ff7ffa95f16d ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, memtest86+ (on /dev/sda6)
root        (hd0,5)
kernel        /boot/memtest86+.bin  
savedefault
boot

---

