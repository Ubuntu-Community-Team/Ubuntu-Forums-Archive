---
title: "Getting a Mount to Work"
date: 2009-04-17
forum: General Help
---

### Post by BadEyedia on 2009-04-17
I have been having a problem with a mount that I have. It is a 500gig external hard drive. When I plug it in, it gives me an error message that says the drive cannot be mounted. So I ran this command:

```
sudo mount /dev/sdb1 /mnt/pass
```

After that the drive mounts and I can view the contents of the drive, but when I try to add a new file, I get another error—permission denied.

---

### Post by taurus on 2009-04-17
What filesystem is /dev/sdb1?

```
sudo fdisk -l
```

---

### Post by BadEyedia on 2009-04-17
Fat32

---

### Post by taurus on 2009-04-17
```
sudo umount /dev/sdb1
sudo mount -t vfat /dev/sdb1 /mnt/pass **-o umask=000**
ls -la /mnt
```

---

### Post by BadEyedia on 2009-04-20
Thanks, that worked.

---

