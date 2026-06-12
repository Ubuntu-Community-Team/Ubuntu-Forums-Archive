---
title: "why disk mounter don't work??"
date: 2006-07-03
forum: Desktop Environments
---

### Post by pmaker on 2006-07-03
I can't understand why disk mounter don't work with etc/fstab/.

If i automount the differents drives on boot up, it works, but if no mount the unit (/dev/hda5 for example) don't works.

This is my fstab archive.:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2	/               ext3    defaults,errors=remount-ro 0       1
/dev/hda1	/media/hda1     ntfs    noauto,ro,users,nls=utf8,umask=0222       0       0
/dev/hda5	/media/hda5     ntfs    noauto,ro,users,nls=utf8,umask=0222       0       0
/dev/hda7	/media/hda7     vfat    noauto,rw,users,utf8,umask=0000       0       0
/dev/hda6	none            swap    sw              0       0
/dev/hdc	/media/cdrom0   udf,iso9660 users,noauto     0       0
#Tarjeta SD
#/dev/??? /media/sdcard vfat noauto,rw,users,exec,sync 0 0

I hope your suggestions

Thanks.

Sorry for my bad english, i'm spanish.

---

### Post by tonyr on 2006-07-03
Can you tell a little more about what is not working?  Are you trying to mount
the drive with a command like
```

mount /media/hda5

```
in a terminal, or with the drop down menu at the Places->Computer->hda5 icon ?

---

### Post by pmaker on 2006-07-03
in the applet don't appear (no show the icons) the icons of the units (like hda5)?

Do you understand me? Sorry for my english

---

### Post by tonyr on 2006-07-03
The **noauto** option in the lines from your **fstab** file mean 
"do not mount when command **mount -a** is used".  When your
machine boots, part of the startup process is to mount all of the devices
in the **fstab** file with the **mount -a** command, so the all of those
devices are not mounted at boot time.   

The two options **noauto** and **users** in those lines mean
"do not mount this at boot time, but allow any user to mount and
unmount it".

You should be able to mount them yourself, either from **Places->Computer**,
or in a terminal (**Applications->Accessories->Terminal**) by typing (for example)
the command
```

mount /media/hda5

```

---

### Post by pmaker on 2006-07-04
yes, i'm with you. this is correct, and i can do that.

but i wish can do this operations with the applet disk mounter, in the menu bar of gnome. With breezy i can do this, but with dapper drake i can't. I hope you can understand my english and the things that i tell to you.

thanks a lot.

---

### Post by tonyr on 2006-07-04
I'm sorry, I am not familiar with the disk mounter applet in Breezy.  I do know that
there were changes in the disk management system between Breezy and
Dapper.

---

