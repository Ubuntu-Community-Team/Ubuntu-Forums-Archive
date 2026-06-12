---
title: "Icons in Taskbar disappear"
date: 2010-02-01
forum: Desktop Environments
---

### Post by Benj_C on 2010-02-01
Hi,

Quite often, at start after I shut down my latptop, my taskbar is completely empty and inactive. I can't right-click on it and add anything. The rest is working fine: shortcuts work, terminal works, software works through terminal, sticky notes are opened....

I'm running Karmic.

Thanks,

Ben

---

### Post by Stone2065 on 2010-02-01
Sounds similar to my current problem. I installed last night, did some customizing (adding the weather temp to the bar, changed the way the time's showing, etc. Real major changes here. Did a proper shutdown last night, went to bed, got up, fired up the computer and all taskbars were GONE. Icons were still there, I could right click to get to some things (I have Xubuntu, not Ubuntu) but still... I have no way to "normally" shut off the computer. I'm not real keen on just flipping the switch to turn it off. My wife said "well, if/when you get it fixed, how about just shutting off the monitor?"... I might just start doing that...

Stone

---

### Post by Benj_C on 2010-02-01
Hi,

Interesting. I did some basic modifications too. All my shortcuts, apps or icons are on the lower bar as I removed the upper one. I wonder if it's related to the Weather Forecast add-on. Do you use the default one (US National Weather Service)?

Also, is that a regular thing? Cause for me, it's not. Sometimes, it happens twice in a row, and some other times I don't get any problem for several consecutive boots.

Btw, when this happens I restart from the terminal : sudo shutdown -r now. Though, this means you have a shortcut or an icon for the terminal.

Ben

---

### Post by Stone2065 on 2010-02-01
You may be onto something with the weather doodad... I had it too. Bloody strange, that's for sure. Mine is fixed now, thanks to a command line string that reset my bar to factory. I found it on here, but have no idea where, other than I was searching for "Disappeared" for search criteria.

Stone

---

### Post by Benj_C on 2010-02-08
Update: It seems that "sudo killall gnome-panel" solves this issue. The other day, I could not recover my taskbar just by rebooting. I tried several times. Even the day after. Nothing would work. I first created another panel "sudo gnome-panel". And after using "killall", it went back to my former one. Except without the weather forecast - disappeared! It went back though, after a complete boot. This thing is really weird. Seems quite unstable to me.

---

### Post by mcduck on 2010-02-08
> **Benj_C said:**
> Update: It seems that "sudo killall gnome-panel" solves this issue. The other day, I could not recover my taskbar just by rebooting. I tried several times. Even the day after. Nothing would work. I first created another panel "sudo gnome-panel". And after using "killall", it went back to my former one. Except without the weather forecast - disappeared! It went back though, after a complete boot. This thing is really weird. Seems quite unstable to me.

"killall gnome-panel" will restart the panel. No need for "sudo", it's runnign under your own user so you don't need root permissions for restarting it.

(actually killall will just kill the panel, but since it's been sconfigured as a required component in Gnome it will be automatically started again when you kill it. :))

...and you definitely should not start the panel with "sudo", it's your desktop so you want the panel to run as your own user. Not to mention that starting *any* graphical apps with sudo is generally a bad idea as well (iuse gksuod for them instead), you'll end running apps with root user's permissions but using your normal user's configuration files.. So when you save anys ettings the changes are that your user's configuration files end overwritten with root permissions.

Anyway, are you talking about the weather forecast applet, or the weather forecast feature in the clock applet? Which ever you are having problems with, try the other one... ;)

---

### Post by Benj_C on 2010-02-10
I ran into the same situation and simply tried: killall gnome-panel. Which also works and brings back my original panel, minus the weather forecast applet. It will probably come back after the next boot.

---

### Post by Benj_C on 2010-03-02
So I removed the weather applet (not the one besides the calendar, the independent one) and everything is fine now.

---

### Post by libssd on 2010-06-17
Misery loves company. The weather disappeared from the clock applet yesterday. Using sudo killall gnome-panel didnothing, nor did removing/re-adding the clock applet, so I gave up trying to get it back as part of the clock applet, and added the separate weather applet. 10.04.

---

