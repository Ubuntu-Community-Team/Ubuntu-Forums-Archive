---
title: "Why my google earth flickers all the time?"
date: 2009-01-04
forum: General Help
---

### Post by lidengdeng on 2009-01-04
I installed google earth 4.2. But when it starts to run, it flickers all the time while getting pictures from Internet. And finally it turns black after finishing getting image data. And it flickers again when I uses the mouse to drag the image.

Has this happened to you?

---

### Post by detroit/zero on 2009-01-04
Are you using compiz-fusion?

If so, use the fusion-icon to switch off compiz while GoogleEarth is running. For some reason GE and CF don't play together nicely.

If you don't have the fusion icon in your panel, I believe entering ```
metacity --replace &
``` at a terminal will switch you over while you use GE, and then enter ```
compiz --replace &
```when you're done.

Hope this helps!

---

### Post by binbash on 2009-01-04
disable compiz when opening google earth

---

### Post by cmb11 on 2009-01-04
I can run compiz and google earth at the same time on my system with no problems... so it must be one of the plugins that is creating this bug...

---

### Post by detroit/zero on 2009-01-04
> **cmb11 said:**
> I can run compiz and google earth at the same time on my system with no problems... so it must be one of the plugins that is creating this bug...
do you have a video card?

I have a toshiba laptop with the Intel 945 chipset that can't run GE without disabling compiz, while my desktop (with an nvidia card) doesn't have a problem.

Maybe it has something to do with memory? I don't know.

---

