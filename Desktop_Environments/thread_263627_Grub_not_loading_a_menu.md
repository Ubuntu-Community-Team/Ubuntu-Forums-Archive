---
title: "Grub not loading a menu"
date: 2006-09-23
forum: Desktop Environments
---

### Post by Ghost Freeman on 2006-09-23
Hi, long time since using Ubuntu (been using Fedora Core due to a lack of burnable CDs), so I went ahead and installed 6.06 over my Fedora Core installed (I formatted the exsisting partitions). Anyways, when it loads up grub, it takes me straight to the command line.

Of course, this is no problem. I can type in the commands needed to boot into Linux and Windows without a problem, but I don't wanna get too comfortable with it. I'd like to have my GRUB Menu back. Any help would be appreciated.

below is my menu.lst. I should also note that even with hiddenmenu enabled it still won't let me access the menu after pressing ESC.
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=/dev/sdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-23-686
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

### Post by Herman on 2006-09-23
> title        Ubuntu, kernel 2.6.15-26-386
 root        (hd0,1)
 kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/sdb2 ro quiet splash
 initrd        /boot/initrd.img-2.6.15-26-386
 savedefault
 boot
 
 # This entry automatically added by the Debian installer for a non-linux OS
 # on /dev/sdb1
 title        Microsoft Windows XP Professional
 root        (hd0,0)
 savedefault
 makeactive
 map        (hd0) (hd1)
 map        (hd1) (hd0)
chainloader +1 So, do you have Windosws XP Professional installed on partition number 1, and Ubuntu installed on partition number 2 of your second hard disk? (sdb)?
Or are they both on your first hard disk? (hd0)
Maybe you need to either change sdb to sda, or else change (hd0) to (hd1)?
Or is Grub seeing your first hard disk as the second hard disk? What partition numbers do you enter from the command Line?
What is the output from 'sudo fdisk -lu'? ```
sudo fdisk -lu
``` Also, what is the output of ```
ls /boot/grub
```Regards, Herman :D

---

### Post by Ghost Freeman on 2006-09-23
They're on the same hard disk, hd0 (which GRUB set to hd1 at first due to a slip-up in the LiveCD installer). Linux picks up the drive with both Windows and Linux as sdb so there's no problem there.

From the command line its hd(0,1) for Linux and hd(0,0) for Windows, which I later made the changes in menu.lst when I came to this discovery. As mentioned above, the installer was thinking hd(1,*) was the HD with the Windows install (which its not, that's one of my "junk" drives)

Here's the output of my fdisk
```

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   320159384   160079661    c  W95 FAT32 (LBA)

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    95570684    47785311    7  HPFS/NTFS
/dev/sdb2        95570685   127025954    15727635   83  Linux
/dev/sdb3       137532465   138062609      265072+   f  W95 Ext'd (LBA)
/dev/sdb4       141612975   156296384     7341705    7  HPFS/NTFS
/dev/sdb5       137532528   138062609      265041   82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   156296384    78148161    c  W95 FAT32 (LBA)

```

and ls /boot/grub
```
default        fat_stage1_5  menu.lst~        reiserfs_stage1_5  xfs_stage1_5
device.map     jfs_stage1_5  menu.lst_backup  stage1
e2fs_stage1_5  menu.lst      minix_stage1_5   stage2

```

Hope this helps!

---

### Post by Herman on 2006-09-23
```
title Ubuntu, kernel 2.6.15-26-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot
``` Maybe try setting your 'root=/dev/sdb2' to 'root=/dev/sda2' then, and see if that fixes it or not. :D

  Would you have been getting any error messages with that, like error message 17 perhaps?

Regards, Herman

---

### Post by Ghost Freeman on 2006-09-23
Nope, trying sda2 causes an error 12.

---

### Post by Herman on 2006-09-23
> 12 : Invalid device requestedThis error is returned if a device string is recognizable but does not fall under the other device errors.  That's really strange... :confused:

..well what exact commands are your using to boot with from the command line? You should be able to use the same commands in your menu.lst.

What if you try some of the tricks in this link to try to run some tests and see if you can find out how Grub is viewing you computer, 
                                   How to get GRUB's Command Line to investigate a computer.........................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer")

It could be that you will find out something interesting that way.  I really wish I could be there, you have a really interesting problem. :D
You should find out that /vmlinuz is on (hd0,1) and /sbin/init *should be* too, but in your case it doesn't seem to be...?

But actually, according to your fstab -lu output, your operating system would really be on sdb, which is normally (hd1) to Grub, in most computers.

You could also try to 'cat' your (hd0,1)/boot/grub/menu.lst, that would be interesting, to see if Grub can find it. 
.... Or 'find' /boot/grub/menu.lst and make grub search for it and tell you where grub thinks it is. :D
That might shed some light on the subject! :D
And also try to 'cat' your device.map as well, if you like, just to see what's in there.
Regards, Herman :D

---

### Post by Ghost Freeman on 2006-09-23
here are the exact commands:

> root (hd0,1)
kernel /boot/vminuz-2.6.15-23-686 root=/dev/sdb2 quiet splash

initrd /boot/initrd.img-2.6.15-23-686

boot

Also, 'cat'ting device.map points sdb as hd1. Which is definitely not right since both partitions can't boot from hd1 (tested this in Grub from the terminal) Could I edit device.map and try that?

---

### Post by Herman on 2006-09-24
> Could I edit device.map and try that? That seems to me like it might be the right idea, the Gnu Grub manual advises that, especially if you have IDE and SCSI disks mixed.
I only have plain old IDE drives myself, so I have never needed to edit any of my device.maps.  I have no experience with it, but there might be someone else around who can help. 
Just make sure you create yourself a backup of it before you do anything, so you can just re-install it if you want.
I think it will be a safe thing to try.
If you have a [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php") ready you won't get into any trouble that you can't get yourself back out of.
Regards, Herman :D

---

### Post by Ghost Freeman on 2006-09-24
I don't have a Super Grub Disk, but I can restore the device.map with my Ubuntu LiveCD if I must.

Unless there's something I don't know.

---

### Post by Ghost Freeman on 2006-09-25
That Super Grub Disk did the trick! Thank you so much!

Problem solved.

---

### Post by Herman on 2006-09-25
You're most welcome! I'm glad you managed to fix it.  Very good!   :D
Regards, Herman

---

### Post by Theimon on 2006-09-27
I'm experiencing the same problem but I'm not sure how to fix it. I could have started a new topic but since this one is just 2 days old, I figured it would be best to throw it in here.

Same as the TS my Grub won't load a menu, also hitting ESC won't bring it up. This is a 3 days old Ubuntu install, my former install had no problems regarding Grub so I'm curious how to fix this.

First of, my device.map:
```

(hd0)	/dev/sda
(hd1)	/dev/hda
(hd2)	/dev/hdb

```

Next up, my menu.lst:
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,2)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-k7
root		(hd0,2)
kernel		/vmlinuz-2.6.15-27-k7 root=/dev/sda1 ro quiet splash
initrd		/initrd.img-2.6.15-27-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-k7 (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.15-27-k7 root=/dev/sda1 ro single
initrd		/initrd.img-2.6.15-27-k7
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,2)
kernel		/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash
initrd		/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro single
initrd		/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

And the commands I now use to boot up Ubuntu:
```

root (hd0,2)

kernel		/vmlinuz-2.6.15-27-k7 root=/dev/sda1 ro quiet splash

initrd		/initrd.img-2.6.15-27-k7

boot

```

It boots and all is well, but it gets a bit annoying to have to put in commands everytime I boot.
Any views or comments on this matter?

---

### Post by Herman on 2006-09-27
I don't know, but I hope someone will come along who does. In the meantime, here is a link to the [Gnu Grub Manual]("http://www.gnu.org/software/grub/manual/grub.html").
And here is a link to the part where it recommends editing your device.map file, if that's the right answer to this problem (I'm not sure), [15.3 The map between BIOS drives and OS devices]("http://www.gnu.org/software/grub/manual/grub.html#Device-map")
I wish I could help more, but as I already said, I have never needed to do this myself as I use only IDE disks, so have never had this problem. 
If you solve it and let everyone know exactly how you did it will help others in the future.
Good luck, I hope that helps a little bit anyway, Regards, Herman :D

---

### Post by adrian15 on 2006-09-28
> **Theimon said:**
>  Same as the TS my Grub won't load a menu, also hitting ESC won't bring it up. This is a 3 days old Ubuntu install, my former install had no problems regarding Grub so I'm curious how to fix this.


Can you please check #8 on [Super Grub Disk & Grub FAQ]("http://adrian15.raulete.net/grub/tiki-index.php?page=EnFaq") and tell us if it has worked for you?
Thank you.

Do not worry about the device.map file.

adrian15

---

### Post by Theimon on 2006-09-28
I've read through the Grub manual from front to back and also took a look at the Super Grub manual. The second seemed a workaround so I took up the Grub manual first.
It seems to me Grub mixed up the disks, so it couldn't properly locate the menu.lst and possibly some other files either. So what I did now was reboot my pc and at the Grub command line:
First made sure which hd* is my /dev/sda (since I kow how my disks are partitioned, I would recognize them by the number of parts):
```

root (hd0 <TAB>

```
I did this for all my disks, which resulted in (hd0) being my /dev/sda.
I have a seperate /boot and from what I've read, it's better to tell Grub the partition as well so I did:
```

setup (hd0,2)

```
It installed all necessary files successfully. Rebooted.
After that a nice Grub menu showed at my screen smiling at me :)

Thanks for pointing me in the right direction  :D

---

