---
title: "fat32 prob"
date: 2005-05-23
forum: Desktop Environments
---

### Post by demosdemon on 2005-05-23
when I mount my fat32 partition, it doesn't properly mount the folders... whenever I open the fs through the terminal it can cd into the folders, but the GUI fileview won't open the folders... anyone know why?

---

### Post by Rainbow Demon on 2005-05-23
What command do you using? Did you forget about "-t vfat -o umask=000"?

---

