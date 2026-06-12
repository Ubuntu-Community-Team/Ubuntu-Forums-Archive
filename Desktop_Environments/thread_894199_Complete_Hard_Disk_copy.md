---
title: "Complete Hard Disk copy"
date: 2008-08-19
forum: Desktop Environments
---

### Post by SexyTechDude on 2008-08-19
Hey guys! Does anyone know the easiest way I can COMPLETELY duplicate my hard disk?

Assume I just built a new computer with EXACTLY the same components, but I want everything that I have on HERE to be on there as well without bothering several hours of installation.

How would I go about making an EXACT duplicate of this hard drive?

As easy as possible please!

Thank you:)

---

### Post by cdtech on 2008-08-19
You can use the dd command:
```
dd if=/dev/hda of=/dev/hdb conv=notrunc,noerror
```


Read about it in my sig......

---

### Post by prshah on 2008-08-19
> **SexyTechDude said:**
> Hey guys! Does anyone know the easiest way I can COMPLETELY duplicate my hard disk?
Assume I just built a new computer with EXACTLY the same components, but I want everything that I have on HERE to be on there as well without bothering several hours of installation.
How would I go about making an EXACT duplicate of this hard drive?


There's a whole bunch of (easy) suggestions in this thread; you can use any of them: [http://ubuntuforums.org/showthread.php?t=874643](http://ubuntuforums.org/showthread.php?t=874643)

---

### Post by SexyTechDude on 2008-08-19
Thanks a lot I appreciate it! :)

---

### Post by erwall on 2008-08-19
Could also try Clonezilla.  I use it quite a bit, has been a great tool.  You can download a Clonezilla live iso file and give it a shot.  You can do disk->image, image->disk, disk->disk.  The image files can also be written and read from a samba or ssh mount that it can establish in the live cd.

---

