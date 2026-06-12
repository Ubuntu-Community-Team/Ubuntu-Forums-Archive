---
title: "Low resolution in KDM."
date: 2007-06-04
forum: Desktop Environments
---

### Post by Ole Eivind on 2007-06-04
I've installed Kubuntu on a Fujitsu Siemens Amilo Pro V3205 laptop. I fixed the resolution to 1280x800 with 915resolution, and this works great in KDE, however the login screen is shown in a horribly low resolution (I would guess 800x600).

If anybody knows how I could fix this it would be highly appreciated.

---

### Post by blackened on 2007-06-04
If it's anything like GDM, then it uses the first usable resolution listed in xorg.conf. 

Ex.
```
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection

```

Because 1280x1024 is the first listed resolution, GDM defaults to that. You might have a look at xorg.conf and see if KDM works the same way.

---

### Post by Ole Eivind on 2007-06-04
Thanks, that worked!

I hadn't even considered this as the kde resolution was correct.

---

### Post by blackened on 2007-06-04
Glad it helped. Also good to know that the two do work the same in that respect.

---

