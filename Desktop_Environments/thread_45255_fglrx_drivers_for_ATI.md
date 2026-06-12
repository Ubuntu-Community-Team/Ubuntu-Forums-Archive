---
title: "fglrx drivers for ATI"
date: 2005-06-29
forum: Desktop Environments
---

### Post by Avianca757 on 2005-06-29
Hi:

I have an ATI Radeon 9600xt and Ubuntu hoary 5.04, I installed the fglrx drivers, they seemed to install ok, fireglcontrol showed accurate info, but I wasn't able to put the refresh rate in a lower setting than 85hz, and I need 60hz.

Does anybody know how to do this?

Thank you!

---

### Post by rachii on 2005-06-29
why do you NEED 60hz??????   the higher the better, 60 just puts strain on your eyes and gives you a headache

---

### Post by jsimmons on 2005-06-29
[QUOTE=rachii]why do you NEED 60hz??????   the higher the better, 60 just puts strain on your eyes and gives you a headache[/QUOTE]
 Anything over 60hz is wasted on LCD monitors.

---

### Post by Avianca757 on 2005-06-29
Well.... actually I have a CRT but it's a cheap piece of junk and won't accept more than 60hz at 1024x768... that's why I need it.

Anybody?

---

### Post by rachii on 2005-06-29
ahh, yeas...sorry i didnt even think of lcd before.
in /etc/X11/xorg.conf what is listed under the "monitor" section?
do you have the horizontal sync, and the vertical refresh rates listed?

---

### Post by Avianca757 on 2005-06-29
it says "Generic Monitor", refresh rates are correct there and it works when I use the ati driver (right now I'm using it and I'm at 1024x768 @ 60hz with no problems).

But when I use the drivers I intend to use, no criteria is changed in the refresh rates (just some modules and the "driver" field).  When installing the fglrx drivers it creates another config file in X11 called XF86Config-4, I looked there and the horizontal and vertical sync parameters are ok, there is a list of modes but if I change it the whole thing gets screwed (I did it and didn't fix anything, moved another thing there and I couldn't even start X!).

So I don't know, xorg.conf is ok, using default drivers I get to desired combination of resolution and refresh rate.  Using the other drivers it creates XF86Config-4 and can't go lower than 85hz, which my cheap CRT can't take at 1024x768.

---

