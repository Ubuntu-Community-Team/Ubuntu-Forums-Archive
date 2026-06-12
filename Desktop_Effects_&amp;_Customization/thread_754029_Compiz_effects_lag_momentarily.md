---
title: "Compiz effects lag momentarily"
date: 2008-04-13
forum: Desktop Effects &amp; Customization
---

### Post by Amranu on 2008-04-13
Hello. 

Recently I've noticed that if I do not use compiz fusion effects for a minute or two, the next time I use them (minimize, switch focus/desktop) they will be very choppy for a few moments, and after that they go back to normal fine speed.

I really can't tell what's causing this. While this is happening compiz eats up cpu. This has only been happening recently and I haven't noticed this before today. I have not enabled or disabled anything in effects recently.

Anyone know what's wrong?

(my specs re an 8400m gs with a 2.4ghz core 2 duo penryn and 4gb of ram)

---

### Post by FuturePilot on 2008-04-13
Sounds like you ran into the little thing called Powermizer :shock:
What it does is scale your GPU. When the Compiz effects return to normal, that's when Powermizer decides to step up the GPU to full speed.
Unfortunately there's no way to control Powermizer. But I can say that the latest Beta driver from Nvidia has significantly increased performance. I'm using it now on Hardy and the Compiz animations have been the smoothest I've ever seen them on this 8400 GS.

---

### Post by tempest on 2008-04-13
I noticed the same behavior on my 8600 GT. If i have the nvidia settings applet open to the powermizer tab I can see the gpu scale up right after initiating a compiz effect. You can see the value by running "nvidia-settings" and then opening GPU 0/Powermizer. It is interesting to watch. It would be nice to have a gnome-panel applet similar to the CPU scaling monitor.

---

### Post by Zorael on 2008-04-14
I believe there are some settings you can alter someplace to lock it in performance mode.

[http://www.nvnews.net/vbulletin/showthread.php?t=110949](http://www.nvnews.net/vbulletin/showthread.php?t=110949)

You can also write scripts that run certain commands every ~25 seconds or so to keep it from powermizing down. I know I saw a fancy one someplace, but my dirty one works.

```
#!/bin/bash
echo starting glxloop, killall glxloop to terminate
while true; do glxinfo >/dev/null; sleep 25; done &
echo
```

Save it as /usr/bin/glxloop, make it executable, run it at Compiz start or autostart (Sessions).

---

