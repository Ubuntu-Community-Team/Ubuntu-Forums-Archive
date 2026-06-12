---
title: "How do I set the volume in KDE?"
date: 2007-04-04
forum: Desktop Environments
---

### Post by mwob on 2007-04-04
Ahem, this is embarassing, but I can't find the option to set the volume in KDE at all!

Theres no speaker icon on the taskbar, and if I try to add applet to the taskbar, I can't see anything related to volume/sound :(

And, in the sound and multimedia settings, theres nothing in there either.... 

Thanks!

---

### Post by shotgunefx on 2007-04-04
going to the shell and typing kmix should do it. The link for the app might be under multimedia?

---

### Post by Jucato on 2007-04-04
Yep, Alt+F2, "kmix" should do it. And yep, it's under K Menu -> Multimedia.

---

### Post by darkos on 2007-04-04
try alsamixer too, in bash. Like this:```
alsamixer
```
and after you set your settings (toggle mute with key m) hit escape and save your settings by typing this ```
sudo alsactl store 0
```

---

