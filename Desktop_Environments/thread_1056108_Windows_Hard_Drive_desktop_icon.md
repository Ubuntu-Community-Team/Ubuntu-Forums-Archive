---
title: "Windows Hard Drive desktop icon"
date: 2009-01-31
forum: Desktop Environments
---

### Post by psom on 2009-01-31
I want every time I log on ubuntu to be have a desktop icon of the hard drive partition I use in Windows. Any help?

Thank you.

Psom

---

### Post by taurus on 2009-01-31
Install ntfs-config (assuming your windows partition is ntfs filesystem) and use it to configure your windows partition.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

