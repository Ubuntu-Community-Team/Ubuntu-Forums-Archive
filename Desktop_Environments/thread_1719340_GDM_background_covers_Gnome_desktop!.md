---
title: "GDM background covers Gnome desktop?!"
date: 2011-04-01
forum: Desktop Environments
---

### Post by reverendryan on 2011-04-01
This is so bizarre I'm not even sure what to search google for. 

When I log in, the GDM background stays on one of my screens. It appears, however, that Gnome and my applications are running properly on that screen - as I move the mouse around, the pointer changes just as I would expect. The GDM root window is simply covering everything. 

I've tried logging out/in and rebooting, but that hasn't helped. I assume that if I simply kill the GDM processes that my session will exit. This seems to have started since I last installed updates (that's why I rebooted the first time earlier today).

Thanks for any thoughts you have on this issue.

---

### Post by Krytarik on 2011-04-01
That's indeed weird! Try reinstalling "gdm":
```
sudo apt-get install --reinstall gdm
```
Then reboot, or at least restart GDM.

Greetings.

---

### Post by reverendryan on 2011-04-01
> **Krytarik said:**
> That's indeed weird! Try reinstalling "gdm":

Good idea, I'll give that a go. Thanks.

---

### Post by reverendryan on 2011-04-04
> **reverendryan said:**
> Good idea, I'll give that a go. Thanks.

No such luck. I tried switching to KDM and that didn't do it either, however there is one step in the right direction: I now see the Gnome background on that monitor rather than the gdm background. The Gnome background is still blocking everything, tho.

For example, when I do this:
```
DISPLAY=:0.2 xclock
```
xclock runs and is apparently on that screen. If I guess where it is I can move it and the mouse cursor changes to the grabby-hand. But I can't actually see the clock.

At least I've narrowed it down to a Gnome problem.

---

### Post by reverendryan on 2011-04-04
Looks like it was actually a Compiz problem. I disabled visual effects entirely and my missing desktop appeared and it has stayed since I've re-enabled them.

Oh well, I'm just glad to have the screen back.

---

### Post by Krytarik on 2011-04-04
> **reverendryan said:**
> Looks like it was actually a Compiz problem. I disabled visual effects entirely and my missing desktop appeared and it has stayed since I've re-enabled them.
Check its settings in "System -> Preferences -> CompizConfig Settings Manager -> General Options -> Display Settings -> Outputs".

Are you using separate xscreens for both monitors, or TwinView/Xinerama?

---

