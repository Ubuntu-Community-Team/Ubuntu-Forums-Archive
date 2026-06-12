---
title: "External hard disk permissions!"
date: 2008-12-04
forum: General Help
---

### Post by koolcracker on 2008-12-04
So I have my external harddrive formatted as ext3 for some reason, and I jsut reinstalled ubuntu and wanted to copy all of my files back, but I need permissions to do that, so I go into root, and all of the copied files now need a root permission to read. It would take hours to manually change all of the permissions. Is there an easy way to do this? It would be of great help.

---

### Post by iaculallad on 2008-12-04
> **koolcracker said:**
> So I have my external harddrive formatted as ext3 for some reason, and I jsut reinstalled ubuntu and wanted to copy all of my files back, but I need permissions to do that, so I go into root, and all of the copied files now need a root permission to read. It would take hours to manually change all of the permissions. Is there an easy way to do this? It would be of great help.

```
sudo chown -R username:username /mountpoint/of_your_external_drive
```

---

