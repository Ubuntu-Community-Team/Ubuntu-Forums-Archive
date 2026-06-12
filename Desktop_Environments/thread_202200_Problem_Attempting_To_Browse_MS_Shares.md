---
title: "Problem Attempting To Browse MS Shares"
date: 2006-06-23
forum: Desktop Environments
---

### Post by Doovoo on 2006-06-23
Here's the story.

I have two hard drives, one running Dapper, and one running XP (soon to be reformatted and used for extra space).  I'm trying to browse my files on my XP drive using either Nautilus or Konqueror, but I'm not having any luck. This always worked in the past, and I'm puzzled as to why it doesn't now. 

When I try to open my Windows drive, I get the error...  

"You do not have the permissions necessary to view the contents of "disks-conf-hda1"."

What's up with this? What permissions do I need, that I don't have, and why don't I have them. Any help is appreciated.

---

### Post by oldmanstan on 2006-06-23
go to system >> administration >> disks

click on the harddrive in question on the left, then hit the "paritions" tab on the right

what is the "access path", is it set?

---

### Post by Doovoo on 2006-06-23
it's set as "/tmp/disks-conf-hda1"

---

### Post by ifokkema on 2006-06-23
[QUOTE=Doovoo]it's set as "/tmp/disks-conf-hda1"[/QUOTE]
Huh? That seems weird to me.

What does your /etc/fstab file look like?

---

### Post by Doovoo on 2006-06-23
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by ifokkema on 2006-06-24
[QUOTE=Doovoo]```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```[/QUOTE]


Type this in your console:
```
sudo mkdir /media/windows
sudo gedit /etc/fstab

```and add this line:
```
/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0
```
save the file and exit gedit. Then type in your console:
```
sudo umount /dev/hda1
sudo mount -a

```Your windows share is now mounted at /media/windows and should be accessible by you.

---

### Post by Doovoo on 2006-06-24
That worked, thanks

---

