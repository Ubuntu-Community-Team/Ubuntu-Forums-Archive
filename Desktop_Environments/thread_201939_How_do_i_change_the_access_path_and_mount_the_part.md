---
title: "How do i change the access path and mount the partition"
date: 2006-06-22
forum: Desktop Environments
---

### Post by shazbot on 2006-06-22
Okay so I played around a little and managed to  to a  get the access path to my windows partion to "/tmp/disks-conf-hda1", now how do I change a "real" path address  and get it to mount, the device dev/hda1 in partition1, all this I seen in the disk manager under dapper

In the file browser it's seen as 47.3 GB Volume

But am a little lost, well quite a lot really so any help to get it mounted so that I can acces it would be great,

 Thanks for anyhelp

played around again and got this message

sudo mount -t ntfs /dev/hda1 /mnt/win
mount: /dev/hda1 already mounted or /mnt/win busy
mount: according to mtab, /dev/hda1 is mounted on /tmp/disks-conf-hda1

help please

---

### Post by mannheim on 2006-06-22
I'm not sure I quite understand your post, but I think you first need to unmount the drive from its present mountpoint, and **then** mount it again. So unmount it with:

```

sudo umount /tmp/disks-conf-hda1

```

then mount it with

```

sudo mount -t ntfs -o ro /dev/hda1 /mnt/win

```
 
I'm not sure if "-o ro" is needed, because it may be the default: you certainly want to mount the drive "read-only" to avoid damaging your ntfs filesystem.

---

### Post by lamego on 2006-06-22
Also make sure you change the entry for it on /etc/fstab .

---

### Post by shazbot on 2006-06-23
Okay have done the previous message so the access path seems ok ' /mnt/win ' but no joy when double clicking on HD Icon but then am not sure what I have to add to th fstab, here is what I have so far

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Thanks again for some help

PS I'v just added this to the fstab /dev/hda1  /mnt/win  ntfs  ro  0 0
But no luck cant even see the partion now :(

---

### Post by ifokkema on 2006-06-23
[QUOTE=shazbot]PS I'v just added this to the fstab /dev/hda1  /mnt/win  ntfs  ro  0 0
But no luck cant even see the partion now :([/QUOTE]

Take a look at this page:
[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

---

### Post by shazbot on 2006-06-23
Well I have already tried 

/dev/hda1 /mnt/win ntfs nls=utf8,umask=0222 0 0 
 
which i took from this page and slightmymodified it but it didnt work and Im sorry but I dont really understand the logic in all this

---

### Post by ifokkema on 2006-06-23
[QUOTE=shazbot]Well I have already tried 

/dev/hda1 /mnt/win ntfs nls=utf8,umask=0222 0 0 
 
which i took from this page and slightmymodified it but it didnt work and Im sorry but I dont really understand the logic in all this[/QUOTE]
Could you define "didn't work" - did you get an error message?
Did you make sure the drive was not mounted when editing the fstab file, and did you run
```
sudo mount -a
```
afterwards?

---

### Post by aysiu on 2006-06-23
Here's the logic:

Partition to mount: **/dev/hda1**
Where you'll find it once it's mounted: **/mnt/win**
What filesystem the partition is: **ntfs**
Options to mount it with (read-only, with the correct character encoding): **nls=utf8,umask=0222 0 0**

It's not enough for you to have that line in your /etc/fstab. There are a few other things:

1. The directory /mnt/win actually has to exist. You can't mount the partition to a non-existent location: ```
sudo mkdir /mnt/win
``` If that command tells you the directory can't be created because it already exists, that's good. And if you get no error, that's also good.

2. After you make changes to the /etc/fstab, you have to remount the partition for the changes to take effect: ```
sudo umount /dev/hda1
sudo mount -a
```

3. There cannot be more than one entry for the same partition. You can't simultaneously have this line ```
/dev/hda1 /mnt/win ntfs ro 0 0
``` and this line ```
/dev/hda1 /mnt/win ntfs nls=utf8,umask=0222 0 0
```

Just have this line for /dev/hda1 and no other line for /dev/hda1: ```
dev/hda1 /mnt/win ntfs nls=utf8,umask=0222 0 0
```

---

### Post by shazbot on 2006-06-23
Okay I added the line to the fstab

# /etc/fstab: static file system information.
/dev/hda1 /mnt/win ntfs nls=utf8,umask=0222 0 0

after re boot nothing happens, have tried to mount the partion doing

sudo mount -a

This gives me NO message what so ever, but still have no partion in the computer file browser, so what am I missing  ??

thanks again in advance

---

### Post by aysiu on 2006-06-23
See--when you say "nothing happens," what are you expecting to happen?

Go to Places > Computer.
Press Control-L.
Type ```
/mnt/win
```
Hit Enter.
See anything?

---

### Post by shazbot on 2006-06-23
This is what I get when I type mnt/win

Couldn't display "computer:///mnt/win"
The location is not a folder.

---

### Post by aysiu on 2006-06-23
It shouldn't be ```
computer:///mnt/win
``` It should be just plain ```
/mnt/win
```

---

### Post by shazbot on 2006-06-23
That works thanks :)

but is there no way to get the icon of the partition to show like the CD rom and the filesystem ??

---

### Post by aysiu on 2006-06-23
Well, if you bookmark the location in Nautilus, it'll show up in Places.

If you want it to show up on the desktop, you can just ```
ln -s /mnt/win ~/Desktop/win
```

---

### Post by shazbot on 2006-06-23
Now that is clever, merci mille fois (thanks a thousand times) :p 

So much to learn, but such fun as long as there are people like you  to help sometimes

again many thanks

---

