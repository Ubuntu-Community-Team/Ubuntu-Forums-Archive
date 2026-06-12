---
title: "where is the gui?"
date: 2006-01-14
forum: General Help
---

### Post by mgaski on 2006-01-14
i have tried to startx after login but all i get is lines of color flickering across the screen for a second or two and then my monitor goes into suspend mode. alt-cntl-f1 shows me that certain fonts renderering is already registered at priority 0 and that client 6 rejected from local host. this occurred right after installing. i changed hostname from ubuntu to another name during install. i am thinking that the video configuration isn't right somewhere. i use a s3 trios 64v2-dx/gx video card. what could be the problem?

---

### Post by aysiu on 2006-01-14
Try ```
sudo dpkg-reconfigure xserver-xorg
```

---

