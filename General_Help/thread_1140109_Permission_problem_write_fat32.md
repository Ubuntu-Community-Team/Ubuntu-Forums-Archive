---
title: "Permission problem write fat32"
date: 2009-04-27
forum: General Help
---

### Post by americano70e10 on 2009-04-27
Hi, I recently installed jaunty on my laptop and also have a fat32 partition on my hd for backup, so I added the line:

```

/dev/sda4	/media/Backup	vfat	iocharset=iso8859-1,umask=000	0

```

to my /etc/fstab.
So now the partition is mounted on startup and I can access it but cannot change anything on it due to permission (permission denied).

I also tried the following line on my /etc/fstab:

```

/dev/sda4	/media/Backup	vfat  quiet,defaults,rw 0 0

```

but it didn't work either...

Can anyone help?

Thanks in advance...

---

### Post by cariboo on 2009-04-27
Change the premission of your mount point to 777:

```
sudo chmod -R 777 /media/Backup
```

You can't set individual permissions on ntfs/vfat file systems.

---

### Post by americano70e10 on 2009-04-27
I didn't even have time to try your solution cariboo907 because after I created this thread I did some resizing (with gparted) to the fat32 partition and now I have full permission, I don't know how that happened but problem solved. Thank you for your time.

---

