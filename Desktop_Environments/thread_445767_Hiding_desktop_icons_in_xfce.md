---
title: "Hiding desktop icons in xfce"
date: 2007-05-16
forum: Desktop Environments
---

### Post by nieh on 2007-05-16
Hi 

anyone know howto hide the desktop icons in XFCE [7.04]

and another question also, is it possible to change the background color in thunar?

thx

Hein

---

### Post by nicepants on 2007-05-16
i'm not sure about the thunar question, but if you go to the xfce settings manager, there should be two that start with "D" (i'm at work, lol!) - one is desktop, i'm not sure if it's that one or the other one. anyway, it'll have two tabs once you select it, with the setting you're looking for being on the second tab. if i remember correctly, you can select between displaying icons on the desktop, displaying your minimized apps, and nothing.

---

### Post by kerry_s on 2007-05-17
mousepad ~/.config/xfce4/desktop/xfdesktoprc
copy and paste->

[file-icons]
show-filesystem=false
show-home=false
show-trash=false
show-removable=true


Restart xfdesktop to activate.

Thunar backgrounds are done with themes and/or custom settings in gtkrc-2.0

---

### Post by Nameless One on 2007-05-17
To switch off the desktop icons, it should be as easy as:
--> Right click the desktop 
--> Select 'Desktop Settings' 
--> Click the 'Behaviour ' tab at the top
--> Under the 'Desktop Icons' title, click the drop down box that may say either 'File/launcher icons' or 'Minimised application icons'
--> Select the 'None' option and then click 'Close'

I believe a change in Thunar backgrounds would require a change of the GTK2 theme, not sure though.

---

### Post by kerry_s on 2007-05-17
The problem is turning it off that way won't let you use desktop icons at all. I often save pages as icons on the desktop for pages i want to read later by draging the url to the desktop. plus i like the drives i plugin to still show on the desktop.

---

### Post by Nameless One on 2007-05-17
nieh didn't state the extent to which they wanted the icons to be removed, so I just replied with the most simple solution.
Thus:
--> If you want NO icons - take the easy route I stated prior.
--> If you still want removable drives to appear on the desktop - follow through with kerry_s' solution.

---

### Post by kerry_s on 2007-05-17
yeah, i guess your right "hide" is subjective. :)

---

### Post by mojoman on 2007-05-17
I've been playing around with this before but one thing I haven't managed to make sense of is partitions. Is it possible to hide other partitions (i.e. the windows partition) and still have removable media visible? Because I want my mp3-player or usb-HD to be visible but not the windows partion.

/mojoman

---

### Post by kerry_s on 2007-05-17
I would just move the mount point out of /media to /mnt in /etc/fstab. Then create the folders in mnt.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd2       /               ext2    defaults,errors=remount-ro 0       1
/dev/hdd3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       **/mnt/hdb1**               ext2    defaults 0       0

---

### Post by mojoman on 2007-05-17
> **kerry_s said:**
> I would just move the mount point out of /media to /mnt in /etc/fstab. Then create the folders in mnt.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd2       /               ext2    defaults,errors=remount-ro 0       1
/dev/hdd3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       **/mnt/hdb1**               ext2    defaults 0       0

Thanks! I gave it a go and it worked.

However, as far as I can see I can't access after moving the mount point (but that's probalby due to some error I made...). My fstab was a bit different, here's how it looks *after* I edited it:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=595cc4b6-0140-4eb6-a5ae-f84cbb7abc93 /               ext3    defaults,erro$
# /dev/sda1
UUID=2C708F07708ED6CC /mnt/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 $
# /dev/sda2
UUID=608a3d88-79ce-4aa3-857c-0bfaf881b29a /home     ext3    defaults        0  $
# /dev/sda3
UUID=b7a5c527-2320-40be-bf5e-b7e6a650f246 none            swap    sw           $
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
```

Now, all I did was to switch /media/sda1 to /mnt/sda1 and I'm not sure what you meant by "create the folders in mnt". If I want to look at the files in that partition (read only but still...) should the now be accessible through /mnt/sda1? That folder is empty. Is that because the partition isn't mounted?

On a side note, I had a look at fdisk -l after the changes and why on earth does it claim that my root partition is W95 FAT32???

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2           11474       24321   103201560    b  W95 FAT32
/dev/sda3            3825        4079     2048287+  82  Linux swap / Solaris
/dev/sda4            4080       11473    59392305   83  Linux
```

And it claims my boot flag is on sda1? Hmm, still, it boots up just the way it should....

---

### Post by kerry_s on 2007-05-17
Yeah, i should have told you to unmount it in /media first than mount it again after you moved it. When you reboot it should be all good. Sorry, i'm a bit tired these days, can't think of everything/anything.

---

### Post by mojoman on 2007-05-18
> **kerry_s said:**
> Yeah, i should have told you to unmount it in /media first than mount it again after you moved it. When you reboot it should be all good. Sorry, i'm a bit tired these days, can't think of everything/anything.

Ok, I got it working now. Thanks for your help!

---

