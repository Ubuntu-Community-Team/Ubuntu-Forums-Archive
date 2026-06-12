---
title: "Changing Brightness on Battery Power Freezes Computer"
date: 2009-01-25
forum: General Help
---

### Post by holdie on 2009-01-25
So I've been having my computer randomly lock up on me for the last few weeks and I think I finally found out why.  Basically, if I boot up the computer on battery everything works normally and, because of the new power setting, the screen is dimmer.  

Occasionally I will want a brighter screen to read something, and as soon as I change the brightness (usually using the Fn key on my keyboard) the computer locks up, the keyboard is no longer responsive, and I have to reboot.  

This happens almost every time I do this, has anyone heard of something like this before?

Thanks

---

### Post by rjklindsay on 2009-11-04
Im having the same problem on my Samsung R560, ever since I installed Karmic.  If I try to adjust the brightness, using Fn+Up, the Brightness control appears in the top right corner, and starts flickering, but the brightness does not change. Also, the keyboard and mouse buttons become non-responsive, and I have to switch off the laptop.  

When playing Nexuiz, the mouse stops working when a keyboard button is pressed, so I cant run and turn at the same time.  

Jaunty had less bugs and is better looking, so I've gone back to Jaunty until Lucid is ready.

---

### Post by rjklindsay on 2010-01-15
I found a workaround for adjusting screen brightness on Karmic:
The Fn-UP and Fn-Down keys are supposed to adjust the brightness, but on Karmic, they just cause most of the keyboard to lock up.
You can get the keyboard working correctly again by pressing Ctrl-F3 followed by Ctrl-F7.

The Gnome brightness control applet also does not work.

The only way to adjust brightness, is from the command-line.
To lower the brightness, type: smartdimmer -s 30
For full brightness type:  smartdimmer -s 100

---

