---
title: "File share won't automount"
date: 2006-08-08
forum: Desktop Environments
---

### Post by srunni on 2006-08-08
I edited my /etc/fstab file to mount a Windows file share on my LAN. However, when I restart my computer, the share is once again unmounted, and I must run
```
sudo mount -a
``` before I can access the share. Isn't /etc/fstab supposed to contain the shares that are automounted on startup?

---

### Post by computergroove on 2006-08-08
This might be a dumb question but have you installed samba server?

---

### Post by srunni on 2006-08-08
I did
```
sudo apt-get install samba
```
and
```
sudo apt-get install smbfs
```

---

