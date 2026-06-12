---
title: "External monitor"
date: 2008-01-19
forum: Desktop Environments
---

### Post by reiserfs on 2008-01-19
Hi, I have a laptop which has a projector connected to it (sometimes - only to watch movies). Basically I'd like to just use the standard laptop screen but when I plug a projector in, I push the key combo to switch to second screen and wallah, it works. But sadly I've not got this to work (different screen resolutions, and my key combo to switch to external output doesn't even work) so I've given up on that route.

I read that you can clone your screen. Here is my relevant X config to do that:

```

Section "Monitor"
    Identifier  "Generic Monitor"
    Option      "DPMS"
    HorizSync   28-64
    VertRefresh 43-60
    Option      "MonitorLayout" "CRT,LFP"
    Option      "Clone" "true"
EndSection

```

Simple enough. Everything works fine, except for the fact that when I play a movie, it only plays on the laptop screen while the projector screen the movie player window is just blank.

Does anyone know a way to get this working? I realise that with the above, I have to change screen resolutions so it looks OK on the projector. I can live with that. It beats what I have to do now (reboot laptop with projector plugged in so that it uses the projector screen instead of my laptop screen). I'm using Gutsy, and it's just a plain intel video card.

Thanks for any pointers!

---

### Post by sandr- on 2008-01-23
( To work with self-defined key combo's , install xbindkeys from the repository and use the interface to add commands to buttons. Just add the xbindkeys command to the startup script and it works )

With the dual monitor I can only help you with the experience I have with it. I use xrandr to switch between 'monitor setups': I have a notebookscreen, and a hooked up external 22" widescreen monitor. I followed this tutorial to get it working at my place: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) . I hope it works for you ! Good luck.

---

