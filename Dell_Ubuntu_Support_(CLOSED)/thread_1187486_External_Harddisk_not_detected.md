---
title: "External Harddisk not detected"
date: 2009-06-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shyb0y85 on 2009-06-14
am having a DEll inspiron 6400 with Ubuntu 9.0.4 installed.
complete beginner user.
the problem i have is that external harddisk is sometymes not recognized.
if i boot up the laptop with the external hdd already connected it shows and works ok, if i remove the external and try n plugin again it isnt detected. until after restart.
also, if i restart without the external hdd plugged in and the plugin after it will recognize. but once i remove, it isnt recognized. its like it only recognizes usb once per restart. 
also to note, even if another usb device is connected it isnt detected. 
any ideas.  i think maybe the usb drivers might be corrupted or sthn.
anyway to reinstall the usb drivers again

---

### Post by itix on 2009-06-15
Are you unmounting the External Disk(s) correctly? If not, the folder where they were mounted may still be there and there might be a problem when the computer try to mount them.

Can you post the output of [COLOR="Navy"]ls /media[/COLOR] here please? Just open a terminal (applications => accessories => terminal) and paste (ctrl + SHIFT + v) the command and hit enter... then copy (ctrl + SHIFT + c) and post here, mmmkay? :)

---

### Post by crawall on 2009-06-16
I have the same problem, here is the information after ls /media:

cdrom  cdrom0

What's the problem?

---

### Post by shyb0y85 on 2009-06-17
cdrom  cdrom0  More Partitions  Program Files


the 2 partitions are on my main harddisk. not the external harddisk

---

### Post by itix on 2009-06-17
So the problem is clearly not with uncorrect unmounts. If it had been there would have been a lot Thenameofyourexternalharddrive_, Thenameofyourexternalharddrive__ and Thenameofyourexternalharddrive___ in there.

There are two files called fstab and mtab. They are located at [COLOR="Navy"]/etc/fstab[/COLOR] and [COLOR="Navy"]/etc/mtab[/COLOR]. Could you please check that file for me the next time this happens. Normally you should get a warning when the drive is already mounted accorting to fstab but something might be wrong anyway.

Just post them here if you don't understand their content.

---

### Post by shyb0y85 on 2009-06-20
no idea what all the mumbo-jumbo is, just copy pasted everythn

-ftsab
> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=027a1ef3-15ca-4c14-8e22-a6c0b3130b5c /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a289e38f-7333-4009-b179-91508aab1608 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# For USB access with Virtualbox
none    /proc/bus/usb    usbfs    devgid=125,devmode=664    0  0


-mtab

> /dev/sda7 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-13-generic/volatile tmpfs rw,mode=755 0 0
none /proc/bus/usb usbfs rw,devgid=125,devmode=664 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/valentino/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=valentino 0 0
/dev/sda5 /media/More\040Partitions fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda3 /media/Program\040Files fuseblk rw,nosuid,nodev,allow_other,blksize=2048 0 0



okay some more details, if i just plug out the harddisk and plugin it in it works fine. but if the harddisk is in use, lets say rythymbox is playing mp3 from the harddisk, and i prematurely plugout the harddisk, all the usb ports dont work anymore til after restart.

and sthn else
only with primary harddisk
> valentino@dell-desktop:~$ ls /media
cdrom  cdrom0  Comedy Central  More Partitions  Program Files

with external harddisk
> valentino@dell-desktop:~$ ls /media
cdrom   Comedy Central   Game HUB           More Partitions  Program Files
cdrom0  Comedy Central_  Ministry of Sound  Movie HUB

notice that Comedy Central is also shown when the external harddisk is removed. it seems lyk its hardcoded in. even after restart it stil shows in the ls /media. but it shouldnt be there.

---

