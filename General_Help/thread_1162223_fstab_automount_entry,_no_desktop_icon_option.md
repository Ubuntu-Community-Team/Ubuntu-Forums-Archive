---
title: "fstab automount entry, no desktop icon option ?"
date: 2009-05-17
forum: General Help
---

### Post by zero7404 on 2009-05-17
i've got this entry in my fstab file to automount my Storage drive when ubuntu starts:

```
/dev/sdb1 /media/Storage ntfs-3g defaults,locale=en_US.utf8 0 0
```

and it works fine. the drive appears on the desktop  each time i boot. is there a switch or option i can add to this line so that the icon does not appear on the desktop ?

i still want the drive visible in nautilus and accessible, but don't want the icon on the desktop....is it possible ?

---

### Post by Legace on 2009-05-17
Open Terminal, type in gconf-editor and press Enter.

Then browse to /apps/nautilus/desktop and uncheck volumes_visible :)

---

### Post by unutbu on 2009-05-17
Here is another method: to stop mounted drives from appearing on desktop, just use fstab to mount them in /mnt (anywhere other than /media).

---

### Post by zero7404 on 2009-05-17
thanks for the tips....

unutbu, if i mounted the drive with /mnt rather than media, does that classify it as a different type of volume in the filesystem ? when i browse the drive with nautilus, i noticed it's classified as a 'picture cd'....

legace, i thought it was somewhere in that configuration window, just didn't know where, volume is no longer on the desktop, thanks. does it also apply to cd/dvd media ?

---

### Post by unutbu on 2009-05-17
zero7404, I really don't know how nautilus determines if something is a "picture cd", or if mounting the partition in /mnt will affect that. Why not try and see?

I think the main difference between the method described by Legace and me is that 
unchecking /apps/nautilus/desktop/volumes_visible will hide all partitions on the desktop,
whereas you can selectively hide partitions by choosing to mount them in /mnt using fstab.

---

### Post by zero7404 on 2009-05-17
> **unutbu said:**
> zero7404, I really don't know how nautilus determines if something is a "picture cd", or if mounting the partition in /mnt will affect that. Why not try and see?

I think the main difference between the method described by Legace and me is that 
unchecking /apps/nautilus/desktop/volumes_visible will hide all partitions on the desktop,
whereas you can selectively hide partitions by choosing to mount them in /mnt using fstab.

wouldn't mind trying it out just to see, so would i be replacing the "/media/" in the statement with "/mnt/" ? does this alter any of the paths on the drive ? i use the directories in the drive when booting into windows as well. it is a separate disc that doesn't contain an OS on it.

---

### Post by unutbu on 2009-05-17
Yes, ```


/dev/sdb1 /media/Storage ntfs-3g defaults,locale=en_US.utf8 0 0

```
would become
```

/dev/sdb1 /mnt/Storage ntfs-3g defaults,locale=en_US.utf8 0 0

```

Unfortunately, this would mean that while in Ubuntu, all the files on sdb1 would be 
located at /mnt/Storage instead of /media/Storage.

Editing /etc/fstab will have no effect on how the drive is accessed while booted into Windows.

---

### Post by zero7404 on 2009-05-17
> **unutbu said:**
> 
Unfortunately, this would mean that while in Ubuntu, all the files on sdb1 would be 
located at /mnt/Storage instead of /media/Storage.

why 'unfortunately' ? are the contents not accessible in the same way as with /media/ ?

---

### Post by unutbu on 2009-05-17
It is only unfortunate if you have programs or symlinks that assume the files are located at /media/Storage. If no such assumptions have yet been made, then there is no problem.

---

### Post by zero7404 on 2009-05-17
changed the entry in fstab, restarted and can't find the device in nautilus....

---

### Post by michy99 on 2009-05-17
Did you make the new mount point in /mnt?```
sudo mkdir /mnt/Storage
```

---

### Post by zero7404 on 2009-05-17
no i didn't, so i'll do that. so i gather that ubuntu auto-created the /media/Storage/ mountpoint ?

been inching along slowly with the ubuntu pocket guide, i only skimmed thru the filesystem section, didn't see this....

should i first unmount /media/storage, then create the dir ?

---

### Post by error420 on 2009-06-13
> **Legace said:**
> Open Terminal, type in gconf-editor and press Enter.

Then browse to /apps/nautilus/desktop and uncheck volumes_visible :)

Thank you very much. This worked perfectly in 9.04. Now all my fstab mount points are hidden on the desktop. Thank goodness because every time I logged on the icons would be scattered in random locations.

---

