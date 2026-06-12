---
title: "Cant enable destkop effects, was able to in kubuntu"
date: 2008-02-03
forum: Desktop Effects &amp; Customization
---

### Post by wahr on 2008-02-03
I recently switched from kubuntu to the gnome based ubuntu, which is much more stable.

The problem is, I can't enable desktop effects!
I know my gma950 supports it.  I had compiz with emerald on my old install, and even managed to run xgl (with a bit of a strain)

Is there something I'm missing here? :confused:

---

### Post by FuturePilot on 2008-02-03
You probably need the Gnome package for Compiz
```
sudo apt-get install compiz-gnome
```

---

### Post by wahr on 2008-02-03
edit:

I figured out what I was I think.

During the initial live cd start up phase, there was a firmware interface glitch, and I restarted the x-server.  This apparently futzed the hardware detection and it cascaded from there.

I reinstalled (since it was a fresh install anyway) and it completely fixed the issue.

so to those who may stumble across this thread with the same problem, don't press ctrl+alt+backspace during the intial boot phase of the install cd.

---

