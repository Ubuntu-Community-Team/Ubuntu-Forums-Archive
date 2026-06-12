---
title: "hide some desktop icons, show others?"
date: 2007-03-26
forum: Desktop Effects &amp; Customization
---

### Post by isecore on 2007-03-26
This is a bit of a strange question, and I'm not sure it's even possible.

See, here's the thing. I've got several drives mounted in /media. I've got three Windows-partitions mounted (my old Windows-install from before I more or less converted fulltime to Ubuntu) as well as four Samba-shares permanently mounted. 

This means that if I show volume icons on the desktop I have several icons that I feel are in the way. I don't need these icons there every time, I'm fine with them hanging around in the Places-menu and such. I only want the Trashbin-icon on my desktop.

However, unchecking the showing of volume icons on the desktop in gconf-editor also means that I won't be seeing USB-thumbdrives or the volumes that are inserted into my MMC-cardreader on the desktop either. This on the other hand is a major annoyance since when I'm done with them I then have to open up "Computer" and unmount them from there (apparently they hotplug just fine, but don't hot-unplug as well) before pulling them out.

So, is there a way to hide SOME desktop icons, and let others show? I really want to hide the icons from the NTFS and Samba-volumes but on the other hand I really want the desktop to show thumbdrives and cardreader-volumes when they are inserted. It's just more logical for me that way, and also hides seven icons which I don't need/want on my desktop.

Like I said, I think this isn't possible - but if not now then I hope the Gnome-devs consider implementing this somehow. And if it's possible, can someone point me in the right direction?

EDIT: Whoops, I might have put this in the wrong category. If some admin/moderator could move it to a more proper category I think it might be good. Sorry!

---

### Post by Jose Catre-Vandis on 2007-03-27
You can do this, its a bit of a hack, and not perfect, but might do what you want. This will only work for shares and not the "automagic" volumes indicating your other partitions.

open Nautilus as root
browse to your /media directory or wherever you created your directories to mount your shares

Right Click on a chosen directory and create a link

Next right click on the link and change the permissions so that you can copy the link to your desktop.

Once on your desktop, edit the name to your liking, and accept you will have to live with the link emblem

repeat as necessary

Go into gconf-editor and untick visible volumes

This seems to work.

If anyone knows how to remove the link emblem, or howto symlink an automagic partition........

---

### Post by kerry_s on 2007-03-27
Try creating a ".hide" file in the desktop folder than just put the names of the folders you want to hide.

---

### Post by orb9220 on 2007-03-28
All you have to do is edit your fstab.

For my windows drives I creaded a folder in my home called drives and folders called winxp and dataHd.

Then in fstab i point to those new folders which I still can see in nautilus but they are not on the desktop.

---

### Post by mcduck on 2007-03-28
> **orb9220 said:**
> All you have to do is edit your fstab.

For my windows drives I creaded a folder in my home called drives and folders called winxp and dataHd.

Then in fstab i point to those new folders which I still can see in nautilus but they are not on the desktop.
This is the way to go. Just mount those drives anywhere else than in /media, and they won't show on your desktop. :) I'm using /mnt myself.

---

### Post by Jose Catre-Vandis on 2007-03-29
> **orb9220 said:**
> All you have to do is edit your fstab.

For my windows drives I creaded a folder in my home called drives and folders called winxp and dataHd.

Then in fstab i point to those new folders which I still can see in nautilus but they are not on the desktop.


Can you please give an example of what you put in fstab, this would help?

---

### Post by mcduck on 2007-03-29
For example, after install I had my storage partition mounted as hda6 and with icon on my desktop. The entry for it in fstab was like this:
```

# /dev/hda6
UUID=66280a28-42cb-4664-ad19-0a0753ebda3a /media/hda6    ext3    defaults        0       2
```

To get rid of the icon I first created a new place to mount the drive by running 'sudo mkdir /mnt/storage', and then edited the line in fstab to look like this:
```
# /dev/hda6
UUID=66280a28-42cb-4664-ad19-0a0753ebda3a /mnt/storage    ext3    defaults        0       2
```

As I still wanted to access the partition easily without having to browse through the file system, I then created a symbolic link from the new mount point to make my storage appear inside my home directory by running 'ln -s /mnt/storage ~/Storage'.

---

### Post by orb9220 on 2007-03-29
> /dev/sdb1     /home/orb/Drives/114GB-fat32/     vfat    defaults,utf8,umask=007,gid=46 0       0

Would mount my fat32 to a folder in /home/orb//Drives/114GB-fat32 which i can access thru nautilus,etc...

Of course I first have to create the folders first. Making my Drives folder than a folder in Drives called 114GB-fat32.

And you can name your folders anything you want. Just make sure they are the same in the fstab as you have created in your home folder.

Anything that is a device in /media folder is by default shown on the desktop.

And you have to reboot to see the changes.

---

### Post by isecore on 2007-03-31
> **orb9220 said:**
> All you have to do is edit your fstab.

For my windows drives I creaded a folder in my home called drives and folders called winxp and dataHd.

Then in fstab i point to those new folders which I still can see in nautilus but they are not on the desktop.

Of course this is an alternative, but then the drives won't show up in the "Places" menu in Gnome, which in my opinion is counter-productive. The whole reason why I want to hide certain drives from my desktop is since they will still be quickly available in the "Places" menu instead.

Mounting the drives in some folder such as /home/myusername/drives/somedrive of course won't show it on the desktop, but instead I have to go hunting through Nautilus every time I want to access any of these seven drives. Sure, I don't need them on my desktop - but I would still like to have them quickly accessible through the "Places" menu.

I think the Gnome/Nautilus devs really need to take this into account when developing new versions - the ability to hide arbitrary drives from displaying on the desktop.

---

### Post by Jose Catre-Vandis on 2007-03-31
> **mcduck said:**
> For example, after install I had my storage partition mounted as hda6 and with icon on my desktop. The entry for it in fstab was like this:
```

# /dev/hda6
UUID=66280a28-42cb-4664-ad19-0a0753ebda3a /media/hda6    ext3    defaults        0       2
```

To get rid of the icon I first created a new place to mount the drive by running 'sudo mkdir /mnt/storage', and then edited the line in fstab to look like this:
```
# /dev/hda6
UUID=66280a28-42cb-4664-ad19-0a0753ebda3a /mnt/storage    ext3    defaults        0       2
```

As I still wanted to access the partition easily without having to browse through the file system, I then created a symbolic link from the new mount point to make my storage appear inside my home directory by running 'ln -s /mnt/storage ~/Storage'.

Thanks Mcduck, I get the picture now. "Similar" to my suggestion, but overcomes the "automagic" volumes issue I couldn't resolve. isecore does have a point though. How about two entries in fstab for the same volume? One automagic the other manual. I haven't tried it, but past efforts kind of tell me it might work? [EDIT] just tested and it works :-)

Original entry (automagic)
```
# /dev/hda6
UUID=66280a28-42cb-4664-ad19-0a0753ebda3a /media/hda6    ext3    defaults        0       2
```

_Additional_ entry in fstab (after adding /testdir directory to /mnt)

```
/dev/hda6    /mnt/testdir    ext3    defaults    0    2
```

Then create symlink from /mnt/testdir to desktop/wherever

Nice :-)

Any answers on how to remove a symlink emblem (in Windows you used Powertoys to remove the arrows from shortcuts)

---

### Post by christiaanb on 2007-04-04
Hey Guys,

I'm a newbie and struggle a bit..hope you can help.

I have a 80gig hdd; 15gig Windows2000,15gig ubuntu, and 50gig Fat 32.

I've been trying to get the drive icon show on the desktop, but it wont...

Here is my fdisk -l:
christiaanb@christiaan-desktop:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1530    12289693+   c  W95 FAT32 (LBA)
/dev/hda2            1531        3442    15358140   83  Linux
/dev/hda3            3443        3506      514080   82  Linux swap / Solaris
/dev/hda4            3507        9729    49986247+   b  W95 FAT32

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         524     4208998+   b  W95 FAT32

Here is my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=83f6ed29-1553-4d90-9cd9-261ad4fac610 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=8c1a3539-36c8-4c8e-afa3-3f7df0b238f8 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto         0         0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto         0         0
/dev/hda4      /media/Extra       vfat defaults,umask=0000      0         0

I would like for he drive to mount in /media/Extra , and it mounts fine! I can access the drive through that dir, and read/write to the drive. Now all I want is an icon of that drive on my desktop.

Any suggestions?
Please speak "slowly" and "clearly"...i'm a newbie...lol

Thanks
GB
Christiaan ;)

---

### Post by christiaanb on 2007-04-04
Never mind...I found the problem...not sure if it was the problem though... I changed the /media/Extra to /media/extra, i rebooted, and there it was...

Thanks any way...

---

### Post by tictacman on 2007-04-21
Wanted to do this in ubuntu 7.04. Just figured that I have completely unrelated problem - sata drives recognised as removable drives so I'll make a separate thread

---

### Post by isecore on 2007-04-26
My question still stands: Is it possible to hide some drive icons on the desktop while showing others?

Yes, I still know I can hide them all by turning off the showing of such volumes in gconf-editor, but that's not what I want. Is what I want even possible?

---

### Post by zo2.0 on 2007-05-01
Hi!

First, and maybe the easiest way : mount your partitions in /mnt and not in /media

UUID=47963b11-165d-40dc-8d59-736802334da9 /mnt/archive1 ext3 defaults 0 2


Other solution I've found : use power of HAL. Check those articles :
[http://www.redhat.com/magazine/003jan05/features/hal/](http://www.redhat.com/magazine/003jan05/features/hal/)
[http://www.mythic-beasts.com/~mark/random/hal/](http://www.mythic-beasts.com/~mark/random/hal/)

and this one which talks exactly about your problem
[http://gnomesupport.org/forums/viewtopic.php?t=11831](http://gnomesupport.org/forums/viewtopic.php?t=11831)

But I didn't succeed to make it work for me (maybe later if I find time)

Enzo

---

