---
title: "[SOLVED] ext2 and ext3 error"
date: 2008-12-28
forum: General Help
---

### Post by Feivel on 2008-12-28
I have an extra hard drive that I connected through a USB enclosure. For whatever reason it was unable to read the drive (probably old windows 95 fs) so I deleted the old partition (through gparted) and relabled and reformated. Problem is when I format to ext2 or ext3 any time I try to write a file to the disk I get an "operation not supported by backend" error and the disk shows as internal media instead of a USB drive. Oddly enough, when I reformat to NTFS, the error disappears and everything works fine (the drive shows as USB). Any idea why ext2 and ext3 don't work on the hd?

---

### Post by drs305 on 2008-12-28
How are you mounting this drive? Is it being mounted automatically? Do you have any entries in fstab for this device? If so, please post the contents:
```

cat /etc/fstab
*also if mounted as ext3:*
mount

```

---

### Post by Feivel on 2008-12-28
> **drs305 said:**
> How are you mounting this drive? Is it being mounted automatically? Do you have any entries in fstab for this device? If so, please post the contents:
```

cat /etc/fstab

```

It automounts as a USB device with NTFS. It does not automount with either ext2 or ext3. I can fix the automount problem but the "operation not supported" error is the biggest problem. After manually mounting I can see the lost & found folder but can't write anything to the drive.

---

### Post by drs305 on 2008-12-28
> **Feivel said:**
> After manually mounting I can see the lost & found folder but can't write anything to the drive.

ntfs sets permissions at the time of mounting and will allow read/write access even though the mountpoint is 'owned' by root. 

For ext3, make yourself the owner of the folder the device is mounting on:
```

sudo chown -R yourusername: /media/*mountpoint*
chmod -R 750 /media/*mountpoint*
```

---

### Post by Feivel on 2008-12-28
> **drs305 said:**
> ntfs sets permissions at the time of mounting and will allow read/write access even though the mountpoint is 'owned' by root. 

For ext3, make yourself the owner of the folder the device is mounting on:
```

sudo chown -R yourusername: /media/*mountpoint*
chmod -R 750 /media/*mountpoint*
```

Didn't even need the second command. Working now. Whenever a disk is formatted through gparted does it default to giving ownership to root? IOW, every time I format a disk in gparted do I have to change ownership to myself?

---

### Post by drs305 on 2008-12-28
> **Feivel said:**
> Didn't even need the second command. Working now. Whenever a disk is formatted through gparted does it default to giving ownership to root? IOW, every time I format a disk in gparted do I have to change ownership to myself?

No you won't. For ext2/3, think of it more as anytime you make a *mountpoint*, you will have to set the ownership as you did above. Ext2/3 will mount and the contents by default are assigned to whoever owns the mountpoint. *Any* ext2/3 partition created by gparted would mount to the ownership of the mountpoint.

---

### Post by Feivel on 2008-12-28
> **drs305 said:**
> No you won't. For ext2/3, think of it more as anytime you make a *mountpoint*, you will have to set the ownership as you did above. Ext2/3 will mount and the contents by default are assigned to whoever owns the mountpoint. *Any* ext2/3 partition created by gparted would mount to the ownership of the mountpoint.

See...even an old dog like me can learn new stuff :)

---

