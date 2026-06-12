---
title: "permissions read only after CD-R restore"
date: 2006-01-13
forum: General Help
---

### Post by rfruth on 2006-01-13
A week ago I had to reformat and start over from scratch, (sad story goes here) luckly I had backed up my home folder onto a CD-R using the built in CD/DVD creator in Nautilus 2.12.1 b4 the sad story - now all is well again, anyway all the files from my CD-R (not the breezy install CD) after being copied back onto my local hard disk are owned by root and the permissions are read (not write) for the owner (me), why does breezy go to the liberty of changing the file permissions for me and is there a way to prevent this ?  (IIRC Win XP does the same thing) :rolleyes:

---

### Post by matthewv on 2006-01-13
I think this just happens because the cd-r is a readonly device... Anyway you should be able to fix it from the terminal by
```

sudo chown -R <username> /home/<username>/
chmod -R 755 /home/<username>/

```

---

### Post by rfruth on 2006-01-13
Thanks Matt !

---

