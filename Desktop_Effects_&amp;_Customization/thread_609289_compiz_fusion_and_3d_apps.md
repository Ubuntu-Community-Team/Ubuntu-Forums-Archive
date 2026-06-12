---
title: "compiz fusion and 3d apps"
date: 2007-11-10
forum: Desktop Effects &amp; Customization
---

### Post by yuvlevental on 2007-11-10
how do you bypass the x server so you can run 3d apps w/compiz fusion enabled? and nvidia

---

### Post by smartboyathome on 2007-11-10
You can only run 3d apps if your video card supports them. What video card to you have?

---

### Post by yuvlevental on 2007-11-10
i have nvidia. I meant to say w/compiz fusion

---

### Post by FuturePilot on 2007-11-10
I'm not quite sure what you mean. Xserver is what is responsible for the graphical interface. If you try to bypass Xserver, well, you're at a command line. If you're having problems with 3D apps and Compiz you can simply disable Compiz before starting the app like this
```
metacity --replace
```
And then when you're done you can enable Compiz again
```
compiz --replace
```
You can use Alt+F2 to enter those commands

---

