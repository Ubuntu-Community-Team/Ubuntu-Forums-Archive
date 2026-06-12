---
title: "Vista C Drive is not mounted"
date: 2009-05-18
forum: General Help
---

### Post by AddictedGamer on 2009-05-18
on Ubuntu I can not get to the Windows Side with the Vista installed so I can not test Wine out with any .exe programs on the Windows Side

---

### Post by taurus on 2009-05-18
Install ntfs-config and use it to configure your ntfs partition.  However, don't expect wine to be magic potion.  It will not run all the windows programs.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by AddictedGamer on 2009-06-02
Thanks for the help I'll try it :D

---

