---
title: "Need a higher screen resolution but can't get it?"
date: 2008-01-21
forum: Desktop Effects &amp; Customization
---

### Post by Full-choke on 2008-01-21
I can only get 1024x768 and I would like something higher like 1280x1086.  Is there a way I can do get that higher resolution?

Thanks,
F-C

---

### Post by glotz on 2008-01-21
```
sudo dpkg-reconfigure xserver-xorg
```
Then <ctrl>+<alt>+<backspace>

---

### Post by lvleph on 2008-01-21
can't you just add it to /etc/X11/xorg.conf?

---

### Post by cdtech on 2008-01-21
Yes, and you can set it as your default resolution. Just looking through my xorg.conf file right now to set the video ram myself.

---

