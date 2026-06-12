---
title: "Write access to second storage drive"
date: 2009-01-28
forum: General Help
---

### Post by MartyBuntu on 2009-01-28
I have a second hard drive installed in my computer that I use mainly for storing media files.

I have PYSDM set up to auto mount the drive at boot, no problem.
I can browse the files, but I cannot add or delete files. How can I take ownership of this drive? I do have a mount point for it.

---

### Post by MartyBuntu on 2009-01-28
**gksudo nautilus /my/directory**

...will allow me to delete files this way.

I'd rather do it by clicking my mounted drive icon on the desktop.

---

