---
title: "How do I Install Jaunty Using my Existing /home Partition?"
date: 2009-04-30
forum: General Help
---

### Post by Penguin Guy on 2009-04-30
I have the Jaunty .iso file and would like to perform a normal install but instead of using a fresh /home I would like to use my existing one. My /home folder is already partitioned. In my home folder I have my account, a guest account, and a share folder.

I would preferably like to create no users on instillation and then copy my users across. How would I do a user-less Ubuntu installation?
Presumably I can copy my user info across from copying the relevant lines contained in /etc/shadow?

More info would be great, thanks for your help!


Solved: Although my partitions seem to be muddled up (/dev/sda4 has dissapeared).

---

### Post by SentientFluid on 2009-04-30
If /home is already on a **separate **partition you can go through the regular install and set up the partitions manually.  Make sure your /home partition is **NOT **checked to format.

When you get to the user creation, use your old username exactly as it's spelled in your old user's account folder. I believe that will cause the "new" user account to use the old home folder.

---

### Post by Penguin Guy on 2009-04-30
I was specifically looking for information about my guest account working; I'll go ahead and install it but I am still looking for more information on adding accounts that already have folders.

Thanks! :KS

---

### Post by taurus on 2009-04-30
System -> Administration -> Users & Groups

---

### Post by SentientFluid on 2009-04-30
After the install, just adding the user with the sme name as before should make it use the existing user folder.

---

### Post by Penguin Guy on 2009-04-30
Oh, right; well in that case I'll just go right ahead - I'll post back my results when I'm done!

:KS

---

### Post by Penguin Guy on 2009-04-30
Oh dear; adding the home directory to fsck didn't work:
[COLOR="Green"]/dev/sda7 /home ext3 nodev,nosuid 0 2[/COLOR]


fdisk -l:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       10058    80734657+   7  HPFS/NTFS
/dev/sda3           10059       19452    75457305    5  Extended
/dev/sda5           19085       19452     2955928+  82  Linux swap / Solaris
/dev/sda6           10059       16534    52018407   83  Linux
/dev/sda7           16535       19084    20482843+  83  Linux

Partition table entries are not in disk order
```

Any ideas what I did wrong?


Edit: [COLOR="Green"]sudo mount -t ext3 /dev/sda7 /home[/COLOR]
When I try and open home now I get a 'Could not open - no such file or directory' 
error.

```
~$ umount /dev/sda7
umount: it seems /dev/sda7 is mounted multiple times
```

Ubuntu Forums CSS is malfunctioning...

*rebooting*

```
~$ sudo umount /dev/sda7
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

```
~$ mount -l -v
/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro) []
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
gvfs-fuse-daemon on /home/josh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=josh)
```

---

### Post by taurus on 2009-04-30
> **Penguin Guy said:**
> Oh dear; adding the home directory to fsck didn't work:
[COLOR="Green"]/dev/sda7 /home ext3 nodev,nosuid 0 2[/COLOR]


fdisk -l:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       10058    80734657+   7  HPFS/NTFS
/dev/sda3           10059       19452    75457305    5  Extended
/dev/sda5           19085       19452     2955928+  82  Linux swap / Solaris
/dev/sda6           10059       16534    52018407   83  Linux
/dev/sda7           16535       19084    20482843+  83  Linux

Partition table entries are not in disk order
```

Any ideas what I did wrong?


Edit: [COLOR="Green"]sudo mount -t ext3 /dev/sda7 /home[/COLOR]
When I try and open home now I get a 'Could not open - no such file or directory' 
error.

```
~$ umount /dev/sda7
umount: it seems /dev/sda7 is mounted multiple times
```

Ubuntu Forums CSS is malfunctioning...

*rebooting*

```
~$ sudo umount /dev/sda7
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

```
~$ mount -l -v
**[COLOR="Red"]/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)[/COLOR]** []
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
gvfs-fuse-daemon on /home/josh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=josh)
```

Looks like you've mounted /dev/sda7 as /!

```
cat /etc/fstab
sudo blkid
```

---

### Post by Penguin Guy on 2009-04-30
```
~$ sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D5-0614" TYPE="vfat" 
/dev/sda2: UUID="3E0822A808225F61" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="1138edc2-d0c8-4c9e-b4ab-b02ba5dddb93" 
/dev/sda6: UUID="60b4ec0f-9e67-474d-aeca-68dcf277d66a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="e7673a9a-8d79-4ba6-b438-bb1c3178dd9b" TYPE="ext3"
```
I'm not sure exactly what you mean seeing as my system still works.

---

### Post by taurus on 2009-04-30
You tried to mount /dev/sda7 to /home but /dev/sda7 has already mounted to /!  What happens to /dev/sda6?

Of course, your system is still worked.  If your old /home is on /dev/sda7, then you can probably kiss your old stuff good bye if you installed Jaunty on it.

---

### Post by Penguin Guy on 2009-04-30
That's the part that confuses me the most - OS is fine, home is fine, and home and OS have not been mixed. So how can sda7 be mounted on /?

---

### Post by Dragon6 on 2009-04-30
I have same question , I'm kinda beginner 
I'm having ubuntu 8.10 now installed and want to install 9.04 , what are the correct steps to do so to make sure all files in my home partition will be safe 
As I know that 9.04 has the capability of ext4 filesystem , and if I need to make all partitions as ext4 , what to do to make this installation goes as I mentioned correctly 
I have the "root" partition , "swap" partition and "home"

Thanks

---

### Post by Penguin Guy on 2009-04-30
You don't need to reinstall, upgrading will do fine. it is also possible to upgrade a ext3 to a ext4 automatically without loss of data. There is actually little reason for a fresh install unless you want a challenge.

---

### Post by Penguin Guy on 2009-04-30
Should I just wipe everything and install fresh? - I forgot to mention earlier that I've backed up /home with bzip2 to a USB drive and have also cloezilla'd the entire filesystem not long ago. In other words: I have nothing to loose.

---

### Post by Dragon6 on 2009-04-30
actually I have iso image of 9.04 so i don't need to upgrade
how to do that ?
Thanks

---

### Post by Penguin Guy on 2009-04-30
It is impossible, or near impossible to upgrade with a .iso file.
You can do a fresh install if you wish - but then you will go through this complication. Before attempting what I have done - make sure you have backed up your data; otherwise you will stand a fair chance of loosing your data.

---

### Post by SentientFluid on 2009-04-30
Penguin Guy, I'm not sure what went wrong. Every time I've done it in the past everything worked fine.  But like Taurus pointed out, mount shows sda7 mounting as /.

After you ran your install, did you boot directly into your user account with your home folder intact?  How did you partition/format the drives? Did you try to manually add /dev/sda7 to fstab?

---

### Post by Penguin Guy on 2009-05-01
```
~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# [COLOR="Red"]/ was on /dev/sda7 during installation[/COLOR]
UUID=e7673a9a-8d79-4ba6-b438-bb1c3178dd9b /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1138edc2-d0c8-4c9e-b4ab-b02ba5dddb93 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

```
~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       10058    80734657+   7  HPFS/NTFS
/dev/sda3           10059       19452    75457305    5  Extended
/dev/sda5           19085       19452     2955928+  82  Linux swap / Solaris
/dev/sda6           10059       16534    52018407   83  Linux
/dev/sda7           16535       19084    20482843+  83  Linux

[COLOR="Red"]Partition table entries are not in disk order[/COLOR]
```

```
~$ sudo mkdir /media/home
~$ sudo mount -t ext3 /dev/sda6 /media/home
~$ cd /media/home
/media/home$ ls
**[COLOR="RoyalBlue"]guest[/COLOR]**  **[COLOR="RoyalBlue"]josh[/COLOR]**  **[COLOR="RoyalBlue"]share[/COLOR]**
```

---

### Post by Penguin Guy on 2009-05-01
Which means I should be able to fix the problem by adding [COLOR="Green"]/dev/sda6 /home ext3 nodev,nosuid 0 2[/COLOR] to /etc/fstab.
Trying that now...
[SIZE="4"][COLOR="Green"]Success!![/COLOR][/SIZE] Everything works flawlessly!

If anyone could explain why my system says it's booting from [s]sda6[/s] hd(0,6) though then I would greatly appreciate that. I may wipe my system and install Jaunty with a /home partition then restore my data on to that anyway because all my partitions seem messed up.

But anyway; thanks for all the help guys :KS - sorry I didn't post /etc/fstab earlier.

---

### Post by Longinus00 on 2009-05-01
> If anyone could explain why my system says it's booting from sda6 though then I would greatly appreciate that. 

What does it say if you do 
cat /boot/grub/menu.lst
?

---

### Post by Penguin Guy on 2009-05-07
Sorry for my late reply - for some reason it did not appear in my 'User CP' page. I have uninstalled and reinstalled Jaunty to try and get things to work but there is still something funny going on with the partitions (seems to be missing /dev/sda4).
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
# kopt=root=UUID=7f28427f-ad21-4e02-89d4-e6893cd2fafb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9a38ec70-85ab-4e35-ac92-c953d3939a1f

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
uuid		9a38ec70-85ab-4e35-ac92-c953d3939a1f
kernel		/vmlinuz-2.6.28-11-generic root=UUID=7f28427f-ad21-4e02-89d4-e6893cd2fafb ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		9a38ec70-85ab-4e35-ac92-c953d3939a1f
kernel		/vmlinuz-2.6.28-11-generic root=UUID=7f28427f-ad21-4e02-89d4-e6893cd2fafb ro  single
initrd		/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		9a38ec70-85ab-4e35-ac92-c953d3939a1f
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

```

Thanks!

---

### Post by Longinus00 on 2009-05-07
> **Penguin Guy said:**
> Sorry for my late reply - for some reason it did not appear in my 'User CP' page. I have uninstalled and reinstalled Jaunty to try and get things to work but there is still something funny going on with the partitions (seems to be missing /dev/sda4).
Thanks!

The reason your computer says it is booting from hd(0,6) is because it is, hd(0,6) = sda7 not sda6. Secondly, there is nothing wrong with not having a /dev/sda4.

---

### Post by Penguin Guy on 2009-05-08
Thanks for reassuring me; but could you explain the logic behind the missing out of /dev/sda4?

---

### Post by Longinus00 on 2009-05-08
> **Penguin Guy said:**
> Thanks for reassuring me; but could you explain the logic behind the missing out of /dev/sda4?

Your sda3 partition is an extended partition. Contained within in it are the logical partitions sda5, sda6, and sda7. All logical partitions start labeled at 4< to differentiate them from primary partitions which are always <5. Because you don't have a primary partition after sda3, you don't have a partition labeled sda4.

If you're curious as to how your hard drive is laid out you can install a partition editor to examine your disk graphically. 
```
$ sudo apt-get install gparted
```
After you install gparted you can start it by going into "System->Administration->Partition Editor". By default gparted won't be able to do much with ntfs based windows partitions so if you want that functionality you have to install ntfsprogs.
```
# sudo apt-get install ntfsprogs
```
Be careful about messing around in gparted if you aren't familiar with disk partitioning.

---

### Post by Penguin Guy on 2009-05-09
> **Longinus00 said:**
> Your sda3 partition is an extended partition. Contained within in it are the logical partitions sda5, sda6, and sda7. All logical partitions start labeled at 4< to differentiate them from primary partitions which are always <5. Because you don't have a primary partition after sda3, you don't have a partition labeled sda4.

If you're curious as to how your hard drive is laid out you can install a partition editor to examine your disk graphically. 
```
$ sudo apt-get install gparted
```
After you install gparted you can start it by going into "System->Administration->Partition Editor". By default gparted won't be able to do much with ntfs based windows partitions so if you want that functionality you have to install ntfsprogs.
```
# sudo apt-get install ntfsprogs
```
Be careful about messing around in gparted if you aren't familiar with disk partitioning.
Having dev/sdaX different to (hd0,X) is confusing - I'll have to watch out for this in the future. Thanks for the info! :KS

---

