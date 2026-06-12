---
title: "Can't mount NTFS"
date: 2009-02-03
forum: General Help
---

### Post by bigbadbrad on 2009-02-03
I reinstalled Ubuntu 8.10 on my laptop again. Before hand I had Vista in there. Before I wiped it I created a NTFS partition that contains all my music and a few pictures. When I try to access it from Ubuntu it gives me an error saying I should go into Windows and safely remove, which I can't, or force mount it. I'm in no way familiar with force mounting. Can anyone help me? It's sda2 that I need.

---

### Post by jerome1232 on 2009-02-03
You can force the mount or you can run ntfsfix on it. Of course you need to adjust /dev/sdxx to the real /dev path and in the mount command readjust /media/mountpoint to the real mountpoint.

```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdxx
```

or to force the mount

```
sudo mount /dev/sdxx /media/mountpoint -o force
```

---

### Post by bigbadbrad on 2009-02-04
Awesome it works, thanks,

Did they take away the thanks button or am I blind?

---

### Post by blazemore on 2009-02-04
They took it away :(

---

### Post by vanadium on 2009-02-04
If you do not have windows on that laptop, then you should reformat that ntfs partition to ext3 (or another linux file system). Force-mounting an ntfs partition is not something you want to do on a routine basis. ntfsfix is limited in the extend by which it can fix an ntfs volume.

---

