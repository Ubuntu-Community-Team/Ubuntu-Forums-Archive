---
title: "Mounting NTFS partition at boot"
date: 2005-08-24
forum: Desktop Environments
---

### Post by nkessler2000 on 2005-08-24
I'm trying to mount my NTFS partition at boot, but I'm having an issue. 

My NTFS parition is on a SATA disk and Ubuntu is installed on an IDE disk. 

I edited my fstab to mount /dev/sda1, and you can see when the system is booting that it's trying to, but it says that "special device /dev/sda1 does not exist". If I mount the partition after the system is booted up, it works a-ok. 

My guess is that the module for the SATA adapter isn't loaded at the time it tries to mount the filesystems in fstab. Is there any way I can work around this?

On a side note, I can't get Grub to boot Windows from the SATA disk. In the Grub menu.lst file, it's configured to boot from (hd1,0). Is that okay for this setup?

---

### Post by marsian on 2005-08-25
[QUOTE=nkessler2000]

My guess is that the module for the SATA adapter isn't loaded at the time it tries to mount the filesystems in fstab. Is there any way I can work around this?
[/QUOTE]
Did you try to add this module at the beginning of /etc/modules ?

---

### Post by daschl on 2005-08-25
[QUOTE=nkessler2000]I'm trying to mount my NTFS partition at boot, but I'm having an issue. 

My NTFS parition is on a SATA disk and Ubuntu is installed on an IDE disk. 

I edited my fstab to mount /dev/sda1, and you can see when the system is booting that it's trying to, but it says that "special device /dev/sda1 does not exist". If I mount the partition after the system is booted up, it works a-ok. 

My guess is that the module for the SATA adapter isn't loaded at the time it tries to mount the filesystems in fstab. Is there any way I can work around this?

On a side note, I can't get Grub to boot Windows from the SATA disk. In the Grub menu.lst file, it's configured to boot from (hd1,0). Is that okay for this setup?[/QUOTE]


maybe you can post your fstab here?

---

### Post by nkessler2000 on 2005-08-25
[QUOTE=marsian]Did you try to add this module at the beginning of /etc/modules ?[/QUOTE]

I've tried it now, and still the same problem. 

I put sata_sil at the top of /etc/modules, but when it tries to mount the NTFS partition from the SATA drive at boot, it still says "mount: special device /dev/sda1 does not exist". It still mounts fine after booting all the way.

---

### Post by nkessler2000 on 2005-08-25
[QUOTE=daschl]maybe you can post your fstab here?[/QUOTE]

Here you go

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /boot           ext3    defaults        0       2
/dev/hdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1	/mnt/ntfs	ntfs	ro,nls=utf8,umask=0222	0	0

```

---

### Post by schdefan on 2005-08-25
> It still mounts fine after booting all the way. 
So is it mounting or not?
Try to put the following in your /etc/fstab
```
/dev/sda1	/mnt/ntfs	ntfs	defaults	0	0
```
And also put the ntfs module in your /etc/modules.

xxfunkxx

---

### Post by nkessler2000 on 2005-08-25
[QUOTE=schdefan]So is it mounting or not?
Try to put the following in your /etc/fstab
```
/dev/sda1	/mnt/ntfs	ntfs	defaults	0	0
```
And also put the ntfs module in your /etc/modules.

xxfunkxx[/QUOTE]

It mounts, but only if the system is booted all the way up.

So if I do "mount -a" after booting to remount all the filesystems in the fstab, it works a-ok. 

However, at boot time it can't even see that there is a "/dev/sda1", as indicated by the error I'm getting. 

I'll try your suggestion of putting ntfs into /etc/modules though

EDIT: putting nfts in /etc/modules didn't work

---

