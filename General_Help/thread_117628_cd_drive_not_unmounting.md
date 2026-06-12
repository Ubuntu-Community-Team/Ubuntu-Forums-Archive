---
title: "cd drive not unmounting?"
date: 2006-01-15
forum: General Help
---

### Post by jonny_boy27 on 2006-01-15
i have icons on my desktop and in my places menu for the past three cds i put in my drive (and have subsequently removed) which i cant get rid of. i assume it is because they have not unmounted (and my attempts to do this with umount have not worked). can anyone help?

---

### Post by GeneralZod on 2006-01-15
[QUOTE=jonny_boy27] i assume it is because they have not unmounted (and my attempts to do this with umount have not worked). [/QUOTE]

Did the umount command return any error messages?

Also, please post results of 

```

cat /etc/fstab

```

and 


```

cat /etc/mtab

```

---

### Post by jonny_boy27 on 2006-01-15
here's

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd1       /home           ext3    defaults        0       2
/dev/hda3       /windows        ntfs    defaults        0       0
/dev/hda5       /xchange        vfat    defaults        0       0
/dev/hda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```
and
```

jonathan@meerkat:~$ cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-9-386/volatile tmpfs rw,mode=0755 0 0
/dev/hdd1 /home ext3 rw 0 0
/dev/hda3 /windows ntfs rw 0 0
/dev/hda5 /xchange vfat rw 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0

```

i tried
```

sudo umount /hda

```

which didnt produce any errors but the phantom icons are still there. i tried it a second time and got an error saying "/dev/hda is not mounted"

---

### Post by GeneralZod on 2006-01-15
Hmmm...odd.  The unmounting is plainly not an issue, so I'd say it's some problem with the gnome-volume-manager or something.  Can't be of more help as GNOME's not my area of expertise; sorry :/

---

### Post by wyohermit on 2006-01-15
[QUOTE=jonny_boy27]here's

/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

sudo umount /hda


From your fstab it would appear that your cdrom would be mounted on /dev/hdb not on /dev/hda

---

