---
title: "Konqueror - disable effect on open file/directory konqlistviewrc"
date: 2007-09-03
forum: Desktop Environments
---

### Post by pheeror on 2007-09-03
Hi,
I would like to disable effect that you can see when you double click on icon in konqueror. Icon fades out, but what is worse it groves on at the same time. It looks cool, but I use KDE for maximal effective, and this is quite disturbing. I tried edit konqlistviewrc - but it seems there is no doucmentation for this config file, in [kcontrol|systemsetting]/icons::advanced I can set effects only for active(select) and disabled ..

Even all, it seems kubuntu specific - it's not in archlinux, neither in fedora - both use kde 3.5.7.

thanks for any help in advance
-- pheeror

---

### Post by GeneralZod on 2007-09-03
Try this:

[http://ubuntuforums.org/showthread.php?t=392930](http://ubuntuforums.org/showthread.php?t=392930)

---

### Post by pheeror on 2007-09-03
Thanks! That's it!

just for future purpose ...
in ~/.kde/share/config/kdeglobals 
```

[KDE]
VisualActivate=0

```

---

