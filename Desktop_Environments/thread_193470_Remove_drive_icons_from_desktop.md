---
title: "Remove drive icons from desktop"
date: 2006-06-10
forum: Desktop Environments
---

### Post by Rondonjin on 2006-06-10
I have two hard drive icons on my desktop that are mounts of the two partitions of my second hard disk. Is it possible to remove them from the desktop? They are already in my bookmarks in Nautilus and they are also in the 'Computer' folder on the desktop. I know I can use Gconf-Editor and set it not to display volumes but that would mean any USB removable device I plug-in would not be displayed either and I want their icons on the desktop when plugged in.

Wayne

---

### Post by jvictor on 2006-06-10
open  a terminal

$gconf-editor
apps>nautilus>desktop > volumes visible (unselect) to remove *ALL* volumes icon

But I dont know of any direct method for only allowing USB drives

HTH

---

### Post by Rondonjin on 2006-06-10
[QUOTE=jvictor]open  a terminal

$gconf-editor
apps>nautilus>desktop > volumes visible (unselect) to remove *ALL* volumes icon

But I dont know of any direct method for only allowing USB drives

HTH[/QUOTE]

As I said, I know I can use gconf-editor to remove all volumes but it's just those two I don't want to see. If I recall they weren't displayed when I was using FC5.

Wayne

---

### Post by meatbites on 2006-06-12
I would also be keen on knowing if this is possible, as I keep all my mounted drives in /media (for the sake of continuity). In fact, I'd much rather have a shortcut to that folder.

I suspect it has something to do with the /etc/fstab file, because the drives I added post-install do not appear on the desktop.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>                       <dump>  <pass>
proc            /proc           proc    defaults                        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro      0       1
/dev/sda1       /media/winntfs  ntfs    nls=utf8,umask=0222             0       0
/dev/sda2       none            swap    sw                              0       0
/dev/sda4       /media/data     vfat    iocharset=utf8,umask=000        0       0
/dev/sdb5       /media/data36   ntfs    nls=utf8,umask=0222             0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto                 0       0

```

As you may have guessed, /dev/sda holds both my Windows and Ubuntu installs. The only drive that appears on my desktop is /dev/sda1 -- the Windows partition.

Am I perhaps on the right track or just delusional?

Update: Definitely delusional. Upon rebooting (ahem), it turns out that the other partitions are now also on the desktop. So, I guess it has nothing to with fstab after all. Any ideas?

---

### Post by darkpark on 2006-06-12
I *think* by default ubuntu displays icons on the desktop for any volume that's mounted in /media.   I believe that if you change the mount point to /mnt for any volumes that you don't want to appear on the desktop, you'll be alright.

[QUOTE=meatbites]I would also be keen on knowing if this is possible, as I keep all my mounted drives in /media (for the sake of continuity). In fact, I'd much rather have a shortcut to that folder.

I suspect it has something to do with the /etc/fstab file, because the drives I added post-install do not appear on the desktop.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>                       <dump>  <pass>
proc            /proc           proc    defaults                        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro      0       1
/dev/sda1       /media/winntfs  ntfs    nls=utf8,umask=0222             0       0
/dev/sda2       none            swap    sw                              0       0
/dev/sda4       /media/data     vfat    iocharset=utf8,umask=000        0       0
/dev/sdb5       /media/data36   ntfs    nls=utf8,umask=0222             0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto                 0       0

```

As you may have guessed, /dev/sda holds both my Windows and Ubuntu installs. The only drive that appears on my desktop is /dev/sda1 -- the Windows partition.

Am I perhaps on the right track or just delusional?

Update: Definitely delusional. Upon rebooting (ahem), it turns out that the other partitions are now also on the desktop. So, I guess it has nothing to with fstab after all. Any ideas?[/QUOTE]

---

### Post by meatbites on 2006-06-12
I can confirm that this does indeed work. If you don't want a mounted device on your desktop, force it to mount in /mnt rather than /media.

Thanks for the pointer, darkpark!

---

### Post by Rondonjin on 2006-06-13
[QUOTE=darkpark]I *think* by default ubuntu displays icons on the desktop for any volume that's mounted in /media.   I believe that if you change the mount point to /mnt for any volumes that you don't want to appear on the desktop, you'll be alright.[/QUOTE]

Yes, the same thought occured to me as I was doing a beer run the other day! It's funny how things seem clearer when you're NOT in front of your PC :D 

Wayne

---

### Post by Kevkill on 2006-06-13
[QUOTE=meatbites]I can confirm that this does indeed work. If you don't want a mounted device on your desktop, force it to mount in /mnt rather than /media.
[/QUOTE]

I would also like to do this but I am new and do not know how to force my drives to mount in /mnt. Does anyone have any suggestions on reading material so I can get up to speed with Ubuntu. 

Thanks
-Kev

---

### Post by yongkailoon on 2007-11-02
I would like to know if I am suppose to put /mnt or something like /mnt/hdd1 at the Mount Point ? Your help is very much appreciated.

---

### Post by kerrymorgan1 on 2007-11-02
[http://www.joshgerdes.com/blog/2007/10/30/move-mounted-partition-icons-from-the-desktop-in-ubuntu-710/](http://www.joshgerdes.com/blog/2007/10/30/move-mounted-partition-icons-from-the-desktop-in-ubuntu-710/)

will explain how to do it

BUT!!! i did that and it disappeared off the desk top....... and i can't find it anywhere else either.

did i do it right? or was that what it was suppose to do?

---

### Post by noremacyug on 2008-04-18
> **kerrymorgan1 said:**
> [http://www.joshgerdes.com/blog/2007/10/30/move-mounted-partition-icons-from-the-desktop-in-ubuntu-710/](http://www.joshgerdes.com/blog/2007/10/30/move-mounted-partition-icons-from-the-desktop-in-ubuntu-710/)

will explain how to do it

BUT!!! i did that and it disappeared off the desk top....... and i can't find it anywhere else either.

did i do it right? or was that what it was suppose to do?

i'm having the same issue.  i created the directory /mnt/Storage and then edited the fstab's mount point for the drive to be /mnt/Storage as well.  rebooted and viola, the drive was gone from the desktop......... as well as nautilus.  can someone please tell me how to fix this, it's driving me nuts.

---

### Post by noremacyug on 2008-04-18
anyone???

---

### Post by noremacyug on 2008-04-19
please......... i know someone knows how to achieve this.

---

### Post by defrex on 2008-05-07
The drive should be mounted in the place you assigned it. So in nautilus just browse over to /mnt/Storage. It seems to be the case that the nautilus shortcut icons above and beyond just the desktop only look in /media.

For those who weren't sure exactly how this is done, a quick howto:

Create a new folder in the /mnt directory for your new mount point. A command that would accomplish this is:
```
sudo mkdir /mnt/drivename
```

Then edit /etc/fstab. You can do that by pressing alt+f2 and typing (or entering into a command line) this:
```
gksudo gedit /etc/fstab
```

Then, find the drive you want to move, and change it's mount point to /mnt/drivename (or whatever you named the folder).

For example, in my fstab file I changed the line from
```
# /dev/sda1
UUID=07D8-010F  /media/sda1     vfat    utf8,umask=007,gid=46 0       1
```
to 
```
# /dev/sda1
UUID=07D8-010F  /mnt/sda1     vfat    utf8,umask=007,gid=46 0       1
```

After a restart, you shouldn't see the drive on your desktop anymore.

Note: this also seems to remove the shortcuts from nautilus, meaning you'll have to browse to /mnt/drivename to see the data there in.

---

### Post by gimfred on 2008-05-09
> this won't work for me, as I mount mine already under my home directory
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=01bb4790-3dc6-426c-bde6-5d8b8998aee6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=0ccf078a-9750-41a8-8ba4-e01207b16045 /boot           ext3    relatime        0       2
# /dev/sdb1
UUID=ca379265-26a4-4fce-bd69-71ee6bc814d3 /home           ext3    relatime        0       2
# /dev/sdc1
UUID=6d0e434b-bc96-4e8f-af4c-f3153278a92b /home/gimfred/Documents ext3    relatime        0       2
# /dev/sda6
UUID=e9213a26-a8cf-4008-bbe9-283d3c66ad91 /opt            ext3    relatime        0       2
# /dev/sda10
UUID=02f7b036-56ed-4230-a607-1139a85d59db /tmp            ext3    relatime        0       2
# /dev/sda7
UUID=26950bae-ab82-451b-b588-226c12207d8e /usr            ext3    relatime        0       2
# /dev/sda8
UUID=6abae719-2ae7-453d-8c75-6d24e7455bea /usr/local      ext3    relatime        0       2
# /dev/sda5
UUID=9c340c0b-1706-438b-b994-4db27dd62e76 /var            ext3    relatime        0       2
# /dev/sdb3
UUID=f92dd611-154c-49ad-9527-2d5606ea4fbd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0...

What mounts into media? It doesn't mount my sdc1 partition in media but I see it on the desktop...

mtab only has the option to mount it at ~/Documents/ same as fstab...

---

### Post by Jaggenaut on 2008-07-19
Hi!

When I used Gutsy I changed fstab so the drives didn't mount in /media. This made the icons on the desktop to go away. But now when I have upgraded to Hardy the icons is there again.. and now it desn't help to mount them outside /media.. Anyone have any suggestions?

/ Jagg

---

