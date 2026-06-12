---
title: "Mounting NTFS file system"
date: 2008-12-05
forum: General Help
---

### Post by thepenguinisatlarge on 2008-12-05
I basically want to be able to mount my XP partition to be able to play my music through ubuntu without having doubles. It won't mount my NTFS file system for some reason is there some process to do this??


TIA


James

---

### Post by taurus on 2008-12-05
Open a terminal and install the ntfs-config app.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

