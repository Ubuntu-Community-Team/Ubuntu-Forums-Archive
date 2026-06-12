---
title: "Audio Players Not Loading"
date: 2005-12-03
forum: Desktop Environments
---

### Post by Haku on 2005-12-03
I've been running Ubuntu 5.10 with no issues up until now. My last install I had used the automatrix to throw a lot of stuff on my system, but as I started to read around I heard people saying it was not a good tool to use and could break your install down the road. All my audio players were working fine at this time though.


So I wiped the drive and started over.
Basically this is what I did after install

Installed K7 smp kernel for my dual core AMD.
Removed all nvidia drivers from the system
Insatlled the 7676 drivers for my 7800GT
Installed nvidia nforce drivers from their site (ethernet)
Installed all the gstreamer plugins on Synaptic for better audio support.
Installed amaroK, mplayer, and xmms (even restarted again to make sure)

None of the above audio players will load for me. I installed them all from synaptic, tried uninstalling them, reinstalling them. At this time I have not found any other applications that do not load.

When I launch amarok the logo pops up for half a second and goes away. Nothing after that.

If I try to run mplayer or xmms nothing happens. I just click on the icon and stare at a blank screen. Totem Movie Player does load however and has no problems playing music files.

I've also installed other programs, like bittornado, and they run without issue.

---

### Post by abou on 2005-12-04
Did you install the ALSA sound drivers and disable system sounds like the bongos?

---

