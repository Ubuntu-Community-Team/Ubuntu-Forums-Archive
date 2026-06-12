---
title: "Will I need to do any configuring when I upgrade my computer?"
date: 2005-12-10
forum: General Help
---

### Post by arcanistherogue on 2005-12-10
I plan on picking up another stick of 512 MB RAM and a new video card for my system, when I purchase them, will I need to configure them all special-like, or should it just detect them on the next bootup?

Thanks.

---

### Post by aysiu on 2005-12-10
My guess? 
RAM will be automatically detected.
Video card... you'll have to reconfigure it. In fact, X may not start up at all, and you may be dropped to the command-line, at which point you'll want to do a ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ninotob on 2005-12-10
Get an nvidia based card -- nvidia releases 3d acceleration linux drivers that work.

---

### Post by arcanistherogue on 2005-12-11
I know, I'm moving from a 6600 to a 6800GT :D

---

