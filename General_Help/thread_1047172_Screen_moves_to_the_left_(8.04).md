---
title: "Screen moves to the left (8.04)"
date: 2009-01-22
forum: General Help
---

### Post by TheTank on 2009-01-22
Hello all.

I am having a problem that my left screen (I have a dual monitor setup) will randomly move to the left a random number of pixels.

I cannot yet say when this happens or under what circumstances. I had initially thought it might be related to compiz but after disabling it, the problem still appeared.

Please note that only the rendering of the screen is affected. The mouse still stays and I can basically still work with the screen if act like everything is still at it's old place.

Restarting X11 fixes the issue (but also forces me to close all apps). Plus my wife is pretty helpless when this happens.

System:
Hardy with all current updates and backports.
Nvidia 7600 with drivers installed from envy.

Also sometimes the menu bars will jump around after rebooting (only happens very seldom). While just an annoyance (I can simply move them back) it is still strange.

Can anyone help me out?

---

### Post by svrkispm on 2009-01-22
i have exactly the same problem (dual mon and left scr.), my guess is that its caused by my ati x1400 drivers, but i cant replicate it on demand and i have no idea what causes it.
what helps for me is to change resolution to something else and then change it back - i dont have to restart X this way.

---

### Post by TheTank on 2009-01-23
> **svrkispm said:**
> i have exactly the same problem (dual mon and left scr.), my guess is that its caused by my ati x1400 drivers, but i cant replicate it on demand and i have no idea what causes it.
what helps for me is to change resolution to something else and then change it back - i dont have to restart X this way.
Thanks for the reply.

But if we both have the problem but use different cards and drivers, then I doubt it has something to do with the card and/or drivers.

But as we both have dual monitors, it seems to be an issue with them.

Maybe more info can help others.
I have a dual DVI card.
The left (the one with the issue) is the main screen.
The dual monitor support was configured via nvidia-settings.
I will post my xorg.conf when I get home.

For screenapps I use conky (2 instances) and tilda.

---

### Post by TheTank on 2009-05-19
Update:
Still happens, even if very sporadically.

It seems to have reduced since I disabled / reduced compiz features.
Yet still very annoying.

---

