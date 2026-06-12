---
title: "External hard drive being automatically mounted read-only"
date: 2006-08-26
forum: Desktop Environments
---

### Post by mmcmonster on 2006-08-26
I have an external firewire hard drive connected to an ubuntu 6.06 system.  The external drive has a single partition which is formatted as ext3.

When I turn the drive on, it shows up on the desktop.  I can read off the drive without any problems.  I cannot write to the drive unless I am root, however.

I would like my regulat user account to be able to write to the drive.

Please note, the drive is being automatically mounted, and there is no entry for it in /etc/fstab.

(The drive is apparently mounted as **/dev/sdg5**)

```

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb5       /mnt/media      ext3    defaults        0       2
$ mount | grep ieee
/dev/sdg5 on /media/ieee1394disk type ext3 (rw,nosuid,nodev)
$

```

---

### Post by bullgr on 2006-08-26
first delete the entry "type", i thing it's not needed.
> /media/ieee1394disk [COLOR="Red"]type[/COLOR]

and after that open a terminal and try this command
> sudo chmod -R 777 /media/ieee1394disk
to give read-write permitions to all users.

---

### Post by mmcmonster on 2006-08-26
Well, I can't get rid of the work 'type', since I don't actually use any commands to mount the drive.  I just turn the drive on, and it automatically gets mounted. :-(

There is no entry in /etc/fstab, and I don't use any mount command to mount the drive.

Also, when I turn it off, the directory in /media is automatically deleted. :-(

---

### Post by mmcmonster on 2006-08-26
An interesting effect.

If I change the permissions on the directory in /media, I can write to the directory from the terminal, but not create a folder in nautilus.  Also, once folders are create, I can craete sub-folders. ???

---

### Post by bullgr on 2006-08-26
then the drive is mounted and shows the content in /media/ieee1394disk open a terminal and use the command
> sudo chmod -R 777 /media/ieee1394disk
is it working?

this command change all the permisions of the files/folders/subforders to read-write any user.
and if you switch the drive off, the permisions are still remains.
next time you switch on the drive, you can read-write again.

---

### Post by jackn on 2006-08-26
Following what [pyman]("http://www.ubuntuforums.org/showthread.php?p=1414476") has successfully done:
```
mount -o rw,remount /media/ieee1394disk
```
to correct the read-only status. This should be done only *after* the self-mount.
Yes, your 'mount' says the drive is 'rw', but I don't know whether that is actually the case.
You should, besides, run 'dmesg' after a self-mount, to make sure you know the device name.

Or
```
mount -o rw,remount,umask=077 /media/ieee1394disk
```
to correct permission issues.

In my hands, too, 'mount' allows changing the mount properties of a self-mounted MP3 player, *after* self-mounting, with no fstab entry.

Apparently, once it is self-mounted, it is possible to use 'mount' to remount a system, though it has no fstab entry.

Finally, if this works, a little script could be written, not by me yet..., to do this automatically after self-mounting.
Alternatively, a whole new hal file could be written to self-mount this properly. Have never done this myself, but it seems doable, although some trouble. 
How about going the easy way and letting me know if you're interested later?! 
Please keep us posted.

Jackn

---

### Post by mmcmonster on 2006-08-27
Thanks a lot.  Everything works fine now.

---

### Post by jackn on 2006-08-27
Great news.

Would be nice to know what you did to get it to work.

Thanks,
Jackn

---

### Post by mmcmonster on 2006-08-27
I did a chown *user:user* /media/*devicename*.  Even though that directory was only being created when the device was plugged in, it apparently got created the next time around with the same permissions as previously.

---

### Post by hardran3 on 2007-10-21
Thank You! I had the same issue but this fixed it.:)

---

### Post by blowski on 2008-04-25
I had the same problem. It was mounting easily enough, but always in read only. I've got a Seagate 750GB external drive, btw.

After doing a chown and chmod (without the drive being mounted), it just changed them back when the drive was mounted. It wouldn't let me change it when the drive was mounted ('permission denied').

The only thing that has worked was adding this to my /etc/fstab file in the options area.
```
uid=username,gid=username
```

(where username is your login name).

Total Linux n00b so if there's a reason why I shouldn't do that, please do point it out.

---

