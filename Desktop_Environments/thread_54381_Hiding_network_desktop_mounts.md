---
title: "Hiding network desktop mounts"
date: 2005-08-04
forum: Desktop Environments
---

### Post by Hig on 2005-08-04
I have two network shares fstab mounted but they show up on my desktop.

Is there an easy way to hide them?

(Short and sweet)

Also:

I have fstab mounting a local NTFS drive but it doesn't work. ```
/dev/hda1	/mnt/windows	ntfs	ro	0	0
```

However by using this command it works perfectly. how can I translate this into an automatic mount?
```
sudo mount -t ntfs -o umask=0222,nls=utf8 /dev/hda1 /mnt/local/hda1
```

EDIT: Where do I put the above to get it to automatically run on login?

---

### Post by macgyver2 on 2005-08-04
[QUOTE=Hig]I have two network shares fstab mounted but they show up on my desktop.

Is there an easy way to hide them?

(Short and sweet)[/QUOTE]
Go to Applications --> System Tools --> Configuration Editor

Now, in the tree on the left hand side expand "apps"...then scroll down and expand "nautilus"...then highlight "desktop". Now in the window on the right the last selection should be "volumes_visible". Uncheck the box and the icons on the desktop should disappear right away!

[QUOTE=Hig]Also:

I have fstab mounting a local NTFS drive but it doesn't work. ```
/dev/hda1	/mnt/windows	ntfs	ro	0	0
```

However by using this command it works perfectly. how can I translate this into an automatic mount?
```
sudo mount -t ntfs -o umask=0222,nls=utf8 /dev/hda1 /mnt/local/hda1
```

EDIT: Where do I put the above to get it to automatically run on login?[/QUOTE]
I would think that if you changed your fstab entry for that drive from what you have to
```
/dev/hda1	/mnt/local/hda1 ntfs	ro,umask=0222,nls=utf8 0	0
```
it should automatically mount it with the same options and in the same place that your command does.

---

