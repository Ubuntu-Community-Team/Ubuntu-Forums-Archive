---
title: "MPlayer &amp; DPMS Problem"
date: 2006-06-04
forum: Desktop Environments
---

### Post by mirkov on 2006-06-04
When playing videos with 
```
mplayer -v filename
```
, I get the message
```
DPMS is Disabled
```
, but after exactly 5 minutes + the time set for display suspend to kick in, the display gets suspended during the playback. The problem does not occur with xine, and did not occur with mplayer in Breezy. 

A 'xset q' after the playback has startet states also that DPMS is Disabled, but it gets somehow enabled after 5 mins, and the power management kicks in. After some googling, the only link that seemed related is
[http://mplayerhq.hu/pipermail/mplayer-dev-eng/2004-October/030261.html]("http://mplayerhq.hu/pipermail/mplayer-dev-eng/2004-October/030261.html")

I'm running Dapper with the latest updates & mplayer from the repositories (version 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8).

---

### Post by mirkov on 2006-06-15
I found the culprit, it was gnome-power-manager. Whatever is set up in gnome-power-preferences, is transferred to corresponding xserver settings every 5 minutes, by gnome-power-manager daemon and takes precedence over whatever is set by xset or xscreensaver. As this is a desktop pc, I don't need battery state and this behaviour is rather annoying, because it breaks mplayer.

BTW, for some reason, this did not happen in breezy and does after upgrade to dapper.

Now I only have to find the way to tell gnome, not to start this deamon at start up. Until then, I'll just kill it in a start up script.

I have to whine a bit - it is far from obvious that there is such a component like gnome-power-manager, and in it's documentation there is no hint about this 'feature'. This whole learning process is rather time-consuming.

---

### Post by dmalinovsky on 2006-06-26
You can edit list of startup programs via "System/Preferences/Sessions", choose "Startup Programs" tab.  Hope it'll help, because I have this issue too. :(

---

