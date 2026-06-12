---
title: "OpenGL apps don't work"
date: 2010-05-23
forum: Desktop Environments
---

### Post by Aleva13 on 2010-05-23
Hi all.  Ive been using Ubuntu for over 2 years and I've never had this problem.
Whenever I try to start an OpenGL app in the terminal, I get a message to the point of "could not create GL context."  It was working until around the last update.  I know it's not a hardware problem because my windows partition works as well as ever.

I'm using Hardy Heron with the closed Nvidia driver with a Geforce 9800gt
'glxinfo | grep OpenGL' gives
```
Error: glXCreateContext failed

```

---

### Post by 3rdalbum on 2010-05-24
How did you install your graphics driver? If you ran the installer from the Nvidia website (which I imagine you did, because the one in Hardware Drivers would be too old for your 9000-series card), then you need to reinstall the driver every time you get a kernel update.

---

### Post by Aleva13 on 2010-05-24
Thanks!  Problem solved.

---

