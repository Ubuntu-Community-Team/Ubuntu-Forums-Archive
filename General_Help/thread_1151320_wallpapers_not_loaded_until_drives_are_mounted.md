---
title: "wallpapers not loaded until drives are mounted"
date: 2009-05-06
forum: General Help
---

### Post by sridarshan on 2009-05-06
i recently changed my ubuntu from 8.10 to 9.04....whenever i start my laptop the walllpapers wont get loaded until the drive containing that walllpaper is not mounted?!so the startup wallpaper will be the default ubuntu wallpapers.

---

### Post by cariboo on 2009-05-07
You can automount the drive in /etc/fstab using somethig like this:

```
/dev/sdb1 /mountpoint ext3  relatime  0  2
```

Have a look at the [fstab howto]("http:///ubuntuforums.org/showthread.php?t=283131")

---

### Post by pancham on 2009-05-07
You can also can copy the picture to the home/usr/picture folder,,, this can work just as good

---

