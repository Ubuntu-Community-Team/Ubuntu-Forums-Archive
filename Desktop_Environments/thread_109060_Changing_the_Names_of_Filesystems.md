---
title: "Changing the Names of Filesystems"
date: 2005-12-27
forum: Desktop Environments
---

### Post by Hangetsu on 2005-12-27
I have two filesystems which have been given the default names /media/hda3 and /media/hda6.  If I wanted to have them renamed to /data and /settings (two fat32 partitions I'm using for shared settings across Linuz and WinXP), what steps do I need to take to do this?

I tried modifying the fstab alone, but that didn't work so I assume there are additional files to change.

Thanks!

---

### Post by dcstar on 2005-12-27
[QUOTE=Hangetsu]I have two filesystems which have been given the default names /media/hda3 and /media/hda6.  If I wanted to have them renamed to /data and /settings (two fat32 partitions I'm using for shared settings across Linuz and WinXP), what steps do I need to take to do this?

I tried modifying the fstab alone, but that didn't work so I assume there are additional files to change.

Thanks![/QUOTE]
Create those names as directories in your filesystem, set their permissions as you want them, then edit your /etc/fstab file to change the mount points to these new locations.

---

### Post by Hangetsu on 2005-12-27
[QUOTE=dcstar]**Create those names as directories in your filesystem, set their permissions as you want them**, then edit your /etc/fstab file to change the mount points to these new locations.[/QUOTE]

Where can I do this?

---

### Post by professor_chaos on 2005-12-27
basically you have to do two things. Change the directory name/path and then change this in the /etc/fstab file.

If you have the mount point /media/hda and you want it to be /media/settings then 

```
sudo umount /media/hda

sudo mv /media/hda /media/settings
```

then ```
sudo gedit /etc/fstab
```

modify the line /media/hda to /media/settings
then ```
sudo mount /media/settings
```

I like to keep all mount points grouped together in the same directory for organization. ie. /media. But you could change them to anywhere, including /

---

### Post by Hangetsu on 2005-12-27
OK, that makes sense then.  I'll give it a go later and let you know how it went, thanks!

---

