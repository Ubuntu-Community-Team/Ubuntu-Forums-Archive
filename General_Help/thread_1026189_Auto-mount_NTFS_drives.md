---
title: "Auto-mount NTFS drives?"
date: 2008-12-30
forum: General Help
---

### Post by Dgurion on 2008-12-30
I have 2 500gb NTFS storage drives.. How would I go about making these drives auto-mount on startup?

---

### Post by taurus on 2008-12-30
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by Dgurion on 2008-12-30
Thank you for the quick reply. Didn't realise it was THAT easy.. Hehe.. Thanks again..

---

