---
title: "Annoying flicker in fullscreen-mode"
date: 2009-04-03
forum: Desktop Environments
---

### Post by nubbe on 2009-04-03
Why are apps in fullscreen-mode like firefox and evince making the screen flicker when changing active app? Is there a way to fix it? Will it be fixed in the future?
I have nvidia binary driver 177.82 and ubuntu 8.10 but this problem has been with me for several iterations of ubuntu.
Thanks to anyone who takes the time to give me a hint about this visual annoyance.

Nubbe

---

### Post by claymater on 2009-04-03
> **nubbe said:**
> Why are apps in fullscreen-mode like firefox and evince making the screen flicker when changing active app? Is there a way to fix it? Will it be fixed in the future?
I have nvidia binary driver 177.82 and ubuntu 8.10 but this problem has been with me for several iterations of ubuntu.
Thanks to anyone who takes the time to give me a hint about this visual annoyance.

Nubbe

I have the same kinda problem, it happens when I minimize and maximize too... (but I have a ATI card.)

---

### Post by maxim. on 2009-05-09
Try typing the following in the terminal
gconftool-2 --set /apps/compiz/general/screen0/options/unredirect_fullscreen_windows --type bool

Worked for me!

Got it from this blogpost [http://tombuntu.com/index.php/2008/09/03/fix-for-flickering-fullscreen-application-with-compiz/](http://tombuntu.com/index.php/2008/09/03/fix-for-flickering-fullscreen-application-with-compiz/)

---

