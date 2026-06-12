---
title: "Mounting/Viewing Win Partitions"
date: 2005-07-12
forum: Desktop Environments
---

### Post by oneybm on 2005-07-12
It's the Semi Noob to Linux again.....

In Suse 9.2 and 9.0, the last distros I tried before this, my Windows partition auto mounted in the GUI and I'm trying to figure out how to do something similar to that so I have an icon on the Gnome Desktop.  Good news is that I did figure out how to at least auto-mount it with read only rights on boot using the guide through fstab but, how do I get the icon/link that I'm looking for?

Thanks you all have been great thus far,
Oneybm
The Semi Noob to Linux

---

### Post by varunus on 2005-07-12
I read this somewhere, not sure if it works, but you can try it.  To make the windows partition show up on the desktop and in your Computer place, open up your /etc/fstab, and change:

```
/dev/hdsomething xx xxx xxx xxxx
```

to

```
dev/hdsomething xx xxx xxx xxxx
```

Removing the first slash, I've heard, tricks GNOME into thinking its a mountable device and makes the icon show up (rather than just seeing it as an extension of your hard drive).  Try it.

Good luck.

---

### Post by oneybm on 2005-07-13
Well I didn't get lucky with that one.  Gave me an error stating special device dev/hda1 doesn't exist so I put that first / back.  Here's what my fstab looks like if it'll help.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```

Again, thank you very much all for the oustanding help.

---

### Post by Knome_fan on 2005-07-13
Hm, if it is mounted I think it should show up under Places -> Computer.

If that's the case I think you can simply drag and drop the icon on the desktop if you want it there.

---

### Post by oneybm on 2005-07-13
[QUOTE=Knome_fan]Hm, if it is mounted I think it should show up under Places -> Computer.

If that's the case I think you can simply drag and drop the icon on the desktop if you want it there.[/QUOTE]

Well after taking a look at what you mentioned and actually looking in the /media directory (DOS Junky) I noticed that all the mounted items were there and they had a folder that was linked.  So I just made a link on my desktop to /media/windows and it works.   :oops: 

Boy do I have a lot to learn...

---

