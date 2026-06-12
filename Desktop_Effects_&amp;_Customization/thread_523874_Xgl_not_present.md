---
title: "Xgl not present ?"
date: 2007-08-12
forum: Desktop Effects &amp; Customization
---

### Post by ShaolinF on 2007-08-12
Hi GUys,

Im trying to run compiz but it keeps telling me XGL is not installed even though I have already installed it. Im still quite new to linux so I could be wrong. DOes anyone have any ideas ?

```
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: '' 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:17478): Wnck-WARNING **: Unhandled action type (nil)
```

---

### Post by drkyle3 on 2007-12-05
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

---

### Post by FuturePilot on 2007-12-05
If you have a Nvidia card you don't need XGL. That warning is normal for Nvidia users. Is it working at all? If it's not could you post your xorg.conf?
```
cat /etc/X11/xorg.conf
```

---

### Post by drkyle3 on 2007-12-05
Well it worked for me.  [http://ubuntuforums.org/showthread.php?t=630898](http://ubuntuforums.org/showthread.php?t=630898)

---

