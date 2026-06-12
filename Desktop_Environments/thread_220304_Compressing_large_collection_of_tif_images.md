---
title: "Compressing large collection of tif images"
date: 2006-07-21
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-07-21
I have 3.5gb of TIF images on my hard drive that I have been using for a project at work.  I don't need access to them any time soon, but I would prefer to keep them on my hard drive in case I do.  Is there a way I can easily compress them so that they take up less space?  Is the best way just to tar.gz the folder, or is there some other way I don't know about?

---

### Post by istoyanov on 2006-07-21
If your .tiff fileas use some sort of compression internally, you won't be able to compress them further. But you may try to compress them with tar & bzip:```
tar vcjf archivename.tar.bz2 /directory/where/the/tiffs/are/
```

HTH

---

### Post by Lunar_Lamp on 2006-07-21
Well, I've started it going, let's hope this compresses them (as it will take ages to do it, hehe).

---

### Post by Lunar_Lamp on 2006-07-21
From 3.5 to 1.9gb, not a bad result I guess :)

---

