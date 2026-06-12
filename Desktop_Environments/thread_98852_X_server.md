---
title: "X server ???"
date: 2005-12-04
forum: Desktop Environments
---

### Post by culmen on 2005-12-04
I'm a beginner with Ubuntu. Have now installed it twice with the same result...
Failed to start the X server... I'm not getting that normal login page..I can login by using text editor but that's all... because of my limited skills and knowledge of Ubuntu and pc's in general I don't know at all what to do..
I have partioned Ubuntu to run in my hard drive which earlier was using only Microsoft XP..

---

### Post by Qrk on 2005-12-04
```
sudo dpkg-reconfigure xserver-xorg
```

Try using a different driver in the second screen. Vesa will work in a pinch.

---

