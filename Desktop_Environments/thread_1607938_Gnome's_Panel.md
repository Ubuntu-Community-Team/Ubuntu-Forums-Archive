---
title: "Gnome's Panel"
date: 2010-10-28
forum: Desktop Environments
---

### Post by moosehadley on 2010-10-28
The top panel on my desktop, on the right side, which has a Session Applet, the clock Applet, the Indicator Applet, and the Notification Applet.

Sometimes, when I boot, they are all distorted (See Image), and I have to manually delete the applet and add it again to fix it.
This seems to happen randomly on certain boots, and I'm not sure what causes it.
However, it only started doing this after I installed NVidia's drivers.

[IMG]http://dl.dropbox.com/u/2655032/Ubuntu/broken.png[/IMG]

[IMG]http://dl.dropbox.com/u/2655032/Ubuntu/fixed.png[/IMG]

---

### Post by mcduck on 2010-10-28
This actually seems to be a bug in the Indicator-Applet, at least that's the one that causes the graphics problem and it always occurs in that applet and around it. And this happens pretty much regardless of your graphics card/drivers, at least I've seen it happening on all kinds of systems.

I doubt there's anything that can be done about it, apart from waiting for the applet's developers to sort it out. But to ease your pain, you don't need to remove the applets and add them back again, or log out  or anything like that. Simply restarting the Gnome-panel works fine (to do that just hit Alt-F2 and run *killall gnome-panel*. It will restart automatically).

---

### Post by moosehadley on 2010-10-28
Ok, thanks

---

### Post by Janghou on 2010-11-02
Clock applet distorted here aswell in 10.10.
On several machines.

Isn't a bug only in the indicator applet

---

### Post by neel.d on 2010-11-24
> **mcduck said:**
> This actually seems to be a bug in the Indicator-Applet, at least that's the one that causes the graphics problem and it always occurs in that applet and around it. And this happens pretty much regardless of your graphics card/drivers, at least I've seen it happening on all kinds of systems.

I doubt there's anything that can be done about it, apart from waiting for the applet's developers to sort it out. But to ease your pain, you don't need to remove the applets and add them back again, or log out  or anything like that. Simply restarting the Gnome-panel works fine (to do that just hit Alt-F2 and run *killall gnome-panel*. It will restart automatically).


Works perfectly in 10.10 64 bit. Thanks a lot mcduck. I have been trying to find a solution for this for a long time :)

---

