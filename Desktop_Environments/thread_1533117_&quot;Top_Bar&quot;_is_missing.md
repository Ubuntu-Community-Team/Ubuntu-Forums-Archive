---
title: "&quot;Top Bar&quot; is missing"
date: 2010-07-17
forum: Desktop Environments
---

### Post by amigammon on 2010-07-17
I have a Sony Vaio Laptop that I have Ubuntu with Gnome and XFCE and I can choose between the two. Since I have installed XFCE when I run Gnome all the top bars on my open applications that allow me to move the windows around are missing. I can use the windows key to "grab" and move the windows around, but what happened? Some file must have been renamed or removed or something when I installed XFCE. 

Does anybody have a hint as to what is going on?

---

### Post by dv3500ea on 2010-07-17
Not sure exactly what is going on but try pressing alt-f2 and entering ```
metacity --replace
``` as a temporary solution.

---

### Post by amigammon on 2010-07-17
Thanks for the reply. That metacity command worked and also turned off my wobbly windows. Any more help you can offer?

cj

---

### Post by not1 on 2010-07-18
I also have this problem after a recent fresh install of 10.04 :(

---

### Post by Sharang.d on 2010-07-18
Try putting in
```

gnome-wm

```
in the "Run Application" Window (Allt+F2).
Worked for me :)

---

