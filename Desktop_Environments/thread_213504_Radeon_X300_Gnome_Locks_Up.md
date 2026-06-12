---
title: "Radeon X300: Gnome Locks Up"
date: 2006-07-11
forum: Desktop Environments
---

### Post by OverclockedMind on 2006-07-11
OK, to preface the title of my post, the User's Guide for my motherboard with built in video refers to it as Radeon X300; however I've also seen Windows XP refer to it as 'Radeon Xpress 200.'

I downloaded Dapper yesterday since drivers for my RT2500-based Wifi card and my aforementioned video werent really 'there' in Breezy. To my pleasant suprise I've got X and networking without having to download and compile anything.

To my unpleasant suprise ;) with either the default driver (I'm thinking its 'ati' or 'radeon') or fglrx, X and Gnome will freeze solid; fglrx makes it longer before freezing. The easiest way to set this off is grab a resize handle on a window and start flipping it in and out; in about 15 seconds Gnome will come to a screeching halt.

fglrx install is the one included with Dapper.

I reconfigured xorg (dpkg-reconfigure xserver-xorg) and manually specified my monitor's refresh rates, the amount of VRAM (which is 64MB shared.) I know its specific to XWindows/Gnome/the driver, as long as im not using it and letting Gnome idle (and on the command line instead having switched ttys) then it's fine; and leaving the machine on overnight not actively using Gnome was fine, it's still waiting for me.

I've not downloaded the newest fglrx; looks like the one in Dapper's from May 16. I was hoping someone would know which direction I should go before I work on it again.

Any thoughts?

-- Joshua

---

### Post by OverclockedMind on 2006-07-11
Hey mods, does this maybe need to go in the Video and Sound forum? Sorry if I posted it in the wrong place and if it needs moved, feel free.

Edit: Found a thread about this...

[http://ubuntuforums.org/showthread.php?t=204910&page=12&highlight=x300](http://ubuntuforums.org/showthread.php?t=204910&page=12&highlight=x300)

and that an older driver version might work better... so do I go older then, newer? I'm going to give that topic a very thorough reading :)

---

### Post by OverclockedMind on 2006-07-18
Got rid of the trouble by disabling the frame buffer and DRI in case anyone has the same problem and needs to fix it up. Lost some pretties but hey reliability comes first.

-- Joshua

---

