---
title: "Re enable disabled wallpaper"
date: 2009-02-07
forum: General Help
---

### Post by mybrownianmotion on 2009-02-07
Hi all, I was messing around with vinagre, doing remote desktop viewing from one of my computers to the other, and then I set one of the computers to disable wallpaper under remote desktop preferences, advanced. This worked fine, and when I connected from the other computer, the wallpaper was disabled, but now that I am finished, the wallpaper did not come back, and I can't for the life of me get it back on. Even rebooting did not bring it back, when the computer starts up, I can see the wallpaper its supposed to use for a few seconds, then its covered up by the plain brown screen of a disabled wallpaper.

Anybody know how to fix this please?

---

### Post by Tim Sharitt on 2009-02-07
Hit Alt-F2 and enter gconf-editor. Once it opens, navigate to desktop > gnome > background and make sure 'draw_background' is enabled.

---

### Post by mybrownianmotion on 2009-02-07
Thanks, that did it!

---

### Post by edubs428 on 2009-02-16
> **Tim Sharitt said:**
> Hit Alt-F2 and enter gconf-editor. Once it opens, navigate to desktop > gnome > background and make sure 'draw_background' is enabled.

sorry to jump in on this, but it sounds similar to my problem and i havent gotten a response... what if you dont have that option listed to "draw background"? I also cannot change my resolution or themes... please help?! I've tried reinstalling all things compiz, to no avail...


Erik

---

### Post by in_rainbow on 2009-02-17
thanks that did it for me

---

### Post by dashaund on 2009-03-06
Thanks, worked for me too!

---

### Post by AndrooUK on 2009-04-16
Oh wicked, just what I needed!  :D

---

### Post by ionoff on 2009-04-21
This fixed my problem as well, thanks.

---

