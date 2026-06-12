---
title: "ISO mounting?"
date: 2009-03-08
forum: General Help
---

### Post by Monotoko on 2009-03-08
I was wondering how to mount an ISO image in (k)ubuntu? I know there both built on the same basis and use the same repos, so im assuming what works for one works in the other.

Im assuming this is possible in linux lol

Thank you :)

---

### Post by taurus on 2009-03-08
```
sudo mkdir /media/iso
sudo mount -t iso9660 filename.iso /media/iso -o loop
df -h
```

---

