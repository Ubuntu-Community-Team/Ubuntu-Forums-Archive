---
title: "How to change automount point of usb hdd?"
date: 2009-01-10
forum: General Help
---

### Post by morelam on 2009-01-10
Hi! I'm running ubuntu 8.04. I've been tried to change automount point of my external usb hdd but I couldn't do that. After changeing it by rightclicking properities --> Volume tab and setting new mount point to /home/patryk/Documents I get error message "mount_point cannot contain the following characters: newline G_DIR_SEPARATOR (usually /)" while remountig. I can mount it manualy from within terminal by typing command: sudo mount /dev/sdb2 /home/patryk/Documents. My fstab file looks like that:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=0dc83d48-fe14-4cf0-96ff-5e55e89e2ca3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=6d30aafb-fe52-4131-bd76-d9ff5c49485d /home           ext3    relatime        0       2
# /dev/sda5
UUID=994deaf7-0906-42e4-a6df-2a5632ca7290 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
My internal hdd is partitioned as follows:1st windows ntfs 2nd windows ntfs 3rd extended partition with 3 logical disks sda5 sda6 sda7
So it looks like fstab has nothing to do with automounting usb drives. Am I right? Do you know how solve this issue?

---

### Post by mc4man on 2009-01-10
Leave your fstab alone.
When you use the properties of a drive or volume to change the auto mount location you can only enter the new directory name you want to use in /media.

Note that you should **not** create that directory, it will be created when the drive is connected and removed when the drive is unmounted.

So in your case you should have only used Documents.

To fix

Without the drive connected

make sure there is no folder in /media named Documents, if so delete.

In a terminal go gconf-editor

scroll down to system -> storage -> volumes and find the volume, it will be obvious.
Highlight it and on right side, right click on the mount_point .... and choose edit key.
Remove everything but Documents.

See screen 1

What you might really want to do is edit everything from the key and change the volume label of the drive to Documents. That way it will automount to /media/Documents with a display name of Documents

To rename (change volume label) of usb drives (after fixing as above

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by morelam on 2009-01-12
Cheers Man! That's all I needed. It's my first post on this forum and I'm wondering if I should mark my post as solved somehow or just live it like this?

---

### Post by TVTrukChik on 2009-01-12
You can click on "Thread Tools" at the top of this page and mark the problem solved from there.  You can also click on the little yellow and red icon at the bottom right of mc4man's post to give him a "thanks" for his help.

---

