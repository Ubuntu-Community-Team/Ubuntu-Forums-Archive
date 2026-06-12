---
title: "Slow/White windows in beryl or compiz / compiz fusion"
date: 2007-08-24
forum: Desktop Effects &amp; Customization
---

### Post by Cows on 2007-08-24
Hello everyone, 

I bought a laptop a few weeks ago and decided to test out Compiz Fusion.

I have a Intel 950 Chipset. 
Xorg is using "i810" drivers and I need to know if this is correct.

The problem is that the first time I install Compiz Fusion it works great, I also tried out normal Compiz and Beryl, The same thing happens.. first time works great, then when reboot it permanently gets screwed. 

After the first try the windows look like this after they have been opened - [http://i6.photobucket.com/albums/y213/Nibbler26/Screenshot-7.png](http://i6.photobucket.com/albums/y213/Nibbler26/Screenshot-7.png)

I'm pretty sure that the GFX drivers are all up to date, I did a "sudo aptitude install xserver-xorg-video-intel" to get the 1280x800 resolution, although I don't know if i810 drivers are the native drivers for this laptop.

---

### Post by Cows on 2007-08-24
Bump

---

### Post by ittiam on 2007-08-24
Well I use the 945GM chipset and it works fine with me. Did you try fiddling with window managers? Changing to beryl or metacity...

---

### Post by Cows on 2007-08-24
Yea I have 945 but 945 = 950 chipset. I tried compiz / compiz fusion / beryl, and they all work the first time but then after i reboot it gets messed up. The only way I can get my WM back up is if I invisibility press ALT + F2 and type metacity --replace. Are you using the i810 drivers and if so what steps do you take to update your graphics card?

---

### Post by ittiam on 2007-08-25
i am not using i810 drivers in particular...in feisty it just works out of box! While i was using edgy i installed 915resolution to get  eye candy working! are u trying to start compiz-fusion during startup? if not what happens when you use alt-f2 and run  (after reboot). 

```
compiz --replace -c emerald &
```

I use KDE...when i switch my window manager to beryl from KWIN after startup...but once i run the above thing it works fine.

---

### Post by Cows on 2007-08-25
Yea I tried to start it from startup and it doesn't work well. I tried to start it up from alt + f2 and it did the same thing. ATM i just turned on my computer and tried it, so far it's working great. Ill have to use 915 resolution to see if it's just the "xserver-xorg-video-intel". Can you tell me whats the difference between the "xserver-xorg-video-intel" and "915resolution"?

---

### Post by ittiam on 2007-08-26
well i dont know much about the difference...a little bit of googling suggested me 915resolution which i tried and it just worked

---

### Post by Cows on 2007-08-26
Alright, next time I reinstall Ubuntu I will try 915resolution. Atm I don't know what happened but it just fixed itself :).

---

