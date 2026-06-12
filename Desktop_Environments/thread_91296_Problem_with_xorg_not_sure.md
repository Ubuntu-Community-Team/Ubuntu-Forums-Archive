---
title: "Problem with xorg??? not sure"
date: 2005-11-16
forum: Desktop Environments
---

### Post by ch13f121 on 2005-11-16
I think I have a problem with xorg, when I log out of my session this green pixellated crap shows up and the computer locks down. not to mention it takes FOREVER to load up gdm. I does this when I install the nvidia drivers...

---

### Post by Qrk on 2005-11-17
That sounds like a problem. Since you have the nvidia drivers installed, why don't you try...
```

sudo dpkg-reconfigure xserver-xorg
```

change whatever was there in the 2nd dialog, (right after the autodetect question,) to nvidia. (Probably right under what you use, nv) If this doesn't work, nv is still wrong. Try some others, vesa will do in a pinch.

---

### Post by ch13f121 on 2005-11-17
yeah I did that and it worked, but I was using official nvidia drivers, not the normal one that you use when you install ubuntu

---

### Post by az on 2005-11-17
Try the linux-restricted-modules ones.  nvidia-glx.

If it is an older card, you may need the nvidia-legacy ones.  Synaptic search nvidia

---

### Post by ch13f121 on 2005-11-17
its a geforce 2 mx400, so its not a legacy, at least nvidia said it wasn't on their website. that's what I used, and it messed up. I switched my xorg config from nvidia to nv(which is default) no problem anymore.

---

