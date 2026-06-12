---
title: "Can't write..."
date: 2009-03-29
forum: General Help
---

### Post by infinitelink on 2009-03-29
Hello.

I'm using Kubuntu 8.1. I have a fat32 to share between linux and windows, and on that fat32 partition I can "create new" a folder or file, but I cannot cut/copy a file and paste it to the fat32. I just get "Could not write to [location]". The same applies to any drive I plug into the USB, also.

Anyone know what's going on? Ideas?

---

### Post by cariboo on 2009-03-30
If you make the mount point world read/writeable you should have full access to the files on the drive. Open an Applications-->Accessories-->Terminal and type:

```
sudo chmod -R 777 /media/<fat32_drive>
```

change <fat32_drive> to your drives mount point.

Jim

---

