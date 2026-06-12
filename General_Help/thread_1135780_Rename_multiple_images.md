---
title: "Rename multiple images"
date: 2009-04-24
forum: General Help
---

### Post by borislevalle on 2009-04-24
Is there any way to rename multiple files without using all kinds of complicated commando's? In Windows (calm down, I quit on Windows) I would select 20 images with names like P343360 up to P343380, click "Rename", type "Paris" and hit Enter. It would come out like "Paris", "Paris (1)", "Paris (2)"... Why can't it be that simple in Ubuntu? Or did I miss something?
Thanks

---

### Post by bluefrog on 2009-04-24
gprename

---

### Post by _Purple_ on 2009-04-24
> **borislevalle said:**
> Is there any way to rename multiple files without using all kinds of complicated commando's? In Windows (calm down, I quit on Windows) I would select 20 images with names like P343360 up to P343380, click "Rename", type "Paris" and hit Enter. It would come out like "Paris", "Paris (1)", "Paris (2)"... Why can't it be that simple in Ubuntu? Or did I miss something?
Thanks

You can install krename if you are looking for an application with GUI.

```
sudo apt-get install krename
```

Then run it from terminal using
```
krename
``` 

If you are looking for a CLI application, you can try renrot.
```
sudo apt-get install renrot
```

---

### Post by mali2297 on 2009-04-24
Another option is to install the file manager Thunar. It has a bulk renamer.

---

### Post by borislevalle on 2009-04-24
Thanks a lot. I tried GPRename. Not bad, but it doesn't show thumbnails, so you need to switch from one window to another to check which images hide behind the file names. Isn't there something that integrates with Ubuntu's default file browser? (So you don't need to run a separate application.)

---

### Post by borislevalle on 2009-04-26
@mali2291
Thunar is the thing I really needed. Thanks a lot,
Boris

---

### Post by krtica on 2010-06-15
pyRename is in repository.
I'm quite satisfied with this tool.

---

