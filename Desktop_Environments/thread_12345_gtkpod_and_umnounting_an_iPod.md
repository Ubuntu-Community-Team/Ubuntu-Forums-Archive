---
title: "gtkpod and umnounting an iPod"
date: 2005-01-23
forum: Desktop Environments
---

### Post by mattack on 2005-01-23
I'm using gtkpod to update my iPod but I'm having trouble unmounting it...
The iPod shows up as sda2 on my desktop when I plug it into my computer and the mount point in gtkpod is /media/sda2. I can update it all fine and dandy, quit gtkpod, right click on the sda2 icon on the desktop go to unmount volume and I get the error:

Unable to unmount the selected volume
umount: /media/sda2: device is busy
umount: /media/sda2: device is busy
Error: umount failed

my appologies if this is the wrong place to post this...

---

### Post by danip on 2005-01-24
I have the same problem with my iriver sometimes...i just unplug it anyways.

---

### Post by poofyhairguy on 2005-01-24
[QUOTE=mattack]I'm using gtkpod to update my iPod but I'm having trouble unmounting it...
The iPod shows up as sda2 on my desktop when I plug it into my computer and the mount point in gtkpod is /media/sda2. I can update it all fine and dandy, quit gtkpod, right click on the sda2 icon on the desktop go to unmount volume and I get the error:

Unable to unmount the selected volume
umount: /media/sda2: device is busy
umount: /media/sda2: device is busy
Error: umount failed

my appologies if this is the wrong place to post this...[/QUOTE]


Can you post your fstab?

---

### Post by Mike Nasvadi on 2005-01-24
I had the exact same problem with my ipod.  I don't think it was GTKpod's fault because even when I mount it without GTKpod I couldn't unmount it.

Post the /etc/fstab and maybe someone can shed some light.  I would like to know as well :)

Oh yeah, I just unplugged it and it has never been hurt.  These things are pretty durable and its not like you are doing anything bad by not unmounting it.

---

### Post by mattack on 2005-01-24
the contents of /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

maybe this other info would be useful. Before I installed gtkpod I was using thi iPod as an external HDD to transfer files from Windows to Linux. It mounted at the same place (sda2) and unmounting it was no problem...

---

### Post by Mike Nasvadi on 2005-01-25
Try adding this line to the fstab
```

/dev/sda2       /mnt/ipod        auto   auto,rw,user    0        0
```

Then shut down and start back up (yes you have to shut down, restarting won't do the trick for osme reason I have discovered)

---

### Post by mattack on 2005-01-25
[QUOTE=Mike Nasvadi]Try adding this line to the fstab
```

/dev/sda2       /mnt/ipod        auto   auto,rw,user    0        0
```

Then shut down and start back up (yes you have to shut down, restarting won't do the trick for osme reason I have discovered)[/QUOTE]

This seems to mess everything up... can't mount the iPod, and can't update it gtkpod.
I reverted back to the old fstab as posted above.
In gtkpod I have the mount point as /media/sda2
and now I can unmount via the icon on my desktop but the iPod still says do not disconnect.

---

### Post by jensyt on 2005-01-25
[QUOTE=mattack]This seems to mess everything up... can't mount the iPod, and can't update it gtkpod.
I reverted back to the old fstab as posted above.
In gtkpod I have the mount point as /media/sda2
and now I can unmount via the icon on my desktop but the iPod still says do not disconnect.[/QUOTE]
I manually mount and unmount my iPod, and it never says the whole disconnect dialog. I have yet to find any corruption on either my Linux or proprietary Apple partitions on the iPod. If I were you I wouldn't really worry about it.

Just as a notice, though: I do not suggest disconnecting it without proper notification. If you have mission critical data stored on your iPod, take heed to follow the official directions.

---

### Post by snowblink on 2005-01-25
I've been playing with my 2nd Gen iPod via firewire.

In gtkpod preferences, you can set it to manage mounting and unmounting of your iPod. I have this ticked. When I plug in the iPod, it is picked up as a drive /dev/sda2 - if a file window pops up, close it. Do your iPod things, then quit gtkpod. Hopefully, this will let you disconnect.

If not, then unmount the drive and see if it is ok to disconnect. In my case, it would sometimes not show as mounted, but the iPod would still not ok me.

Now you have to remove the kernel module.
sudo modprobe -r spb2
Hopefully, you can remove your iPod now.

sudo modprobe spb2
after you have removed the iPod.

Hope that helps.

---

### Post by mattack on 2005-01-25
[QUOTE=snowblink]I've been playing with my 2nd Gen iPod via firewire.

In gtkpod preferences, you can set it to manage mounting and unmounting of your iPod. I have this ticked. When I plug in the iPod, it is picked up as a drive /dev/sda2 - if a file window pops up, close it. Do your iPod things, then quit gtkpod. Hopefully, this will let you disconnect.

If not, then unmount the drive and see if it is ok to disconnect. In my case, it would sometimes not show as mounted, but the iPod would still not ok me.

Now you have to remove the kernel module.
sudo modprobe -r spb2
Hopefully, you can remove your iPod now.

sudo modprobe spb2
after you have removed the iPod.

Hope that helps.[/QUOTE]

Your setup is just like mine. however when I call sudomodprobe -r spb2, here's what I get:
```
matt@mattack:~ $ sudo modprobe -r spb2
Password:
FATAL: Module spb2 not found.
```

---

### Post by snowblink on 2005-01-26
Sorry typo. Should be sbp2

---

### Post by mattack on 2005-01-26
even after sudo modprobe -r sbp2 the iPod is still saying do not disconnect...

this is really frustrating.  :x

---

### Post by el toro on 2005-01-26
If you're using firewire to connect your iPod, try issuing this command:
```
eject /dev/sda2
``` 
and see what happens.

---

### Post by mattack on 2005-01-26
no firewire...  usb 1.0
my PC is, shall we say, *lacking*.  :neutral:

---

### Post by jamin_l on 2005-01-27
```

#!/bin/sh
modprobe sbp2
mount /dev/sda2 /mnt/ipod

```

Unmounting iPod script:
```

#!/bin/sh
umount /mnt/ipod
rmmod sbp2

```

---

### Post by squallbsr on 2005-05-09
sometimes you have to type (USB iPods only)

```
sudo eject /dev/sda
```

---

