---
title: "Minimal Arch Linux + e17 - need advice"
date: 2009-02-23
forum: Desktop Environments
---

### Post by jaydoc on 2009-02-23
hi all

I made a desktop by putting an e17 desktop shell on top of a minimal Arch Linux install, a few days ago, but I am a little stumped after the initial configuration. Could someone guide me a little in that..? My aim is to make a minimal. sleek, one-app-per-function install, with as little "contamination" with kde/qt as possible - so I am looking for standalone apps common to all platforms/DEs that will do just that. Could you give me a list of such apps...? I am typing this from within that install, so I have indeed managed to find a good selection for some apps...

like firefox, lxterminal, pcmanfm, pidgin, openoffice, wine, leafpad, chmsee, evince...

I also have a few other questions.

Most important is - How can I get a trash icon function...? 

I am having real trouble in finding a good standalone systray, that will fit with the nice looks of e17.I did try stalonetray, but it looks so dull.

How do I make the apps like firefox, pcmanfm, etc take on that fantastic e17 look. 
I know that it is not entirely possible, so how can I at least make them look half as good..?

I am not sure how to change the default icons. How can I install a new icon set..? 

My final aim is to sort of roll my own live cd off this Arch install to carry around to use on some other similar systems. 

thanks.

---

### Post by kerry_s on 2009-02-23
for the icons and things:
pacman -S lxappearance

launch with> lxappearance

your screwed on the trash function, pcmanfm don't have it.
thunar does trash, but doesn't do desktop.

have no ideas on the tray, what about that tksystray?

---

### Post by benerivo on 2009-02-23
For the tray, try [trayer]("http://download.gna.org/fvwm-crystal/trayer/1.0/").

---

### Post by kerry_s on 2009-02-23
> **benerivo said:**
> For the tray, try [trayer]("http://download.gna.org/fvwm-crystal/trayer/1.0/").

that's in the repo to you can> pacman -S trayer

---

### Post by jaydoc on 2009-02-24
Thank you all, for the replies. 

For the system tray, I tried trayer, but ultimately went back to stalonetray, after I found a nice tutorial on this site abt making it startup, and also found the manpage on the official site that talks abt how to setup the .stalonerc file, so that the tray fits with the desktop look.I must say that now it looks a lot better.

I will try lxappaearance and get back with the results.

---

