---
title: "[SOLVED] Evolution and Desktop Effects - help?"
date: 2007-12-19
forum: Desktop Effects &amp; Customization
---

### Post by vortex0007 on 2007-12-19
I recently figured out how to get Dual-monitor mode, or "Big Desktop" working with my ATI Radeon x1950 card and Ubuntu 7.10 using the ATI linux drivers. Then after some more tinkering I was able to turn on the Extra Visual Effects in Ubuntu.

The only problem I'm having is that when I open Evolution and then double-click on a message in my inbox, the new window opens up on the FAR, FAR right-hand corner of the second monitor. 

Maybe that's not clear. Imagine two monitors. Evolution is on the left hand monitor. I open a message, the new window is now on the second monitor hiding in the corner. 

Is there a way to configure Evolution to not open the window at the far right-hand side of 2nd monitor? 

Note that if I open the first message, drag the window back to the left hand monitor, then move to the next message without closing the window, it stays in place. It's only when a new window is launched does it put it on the wrong side of the wrong monitor.

---

### Post by randomnote1 on 2007-12-19
are you running Ubuntu or Kubuntu?

---

### Post by vortex0007 on 2007-12-19
Ubuntu

---

### Post by randomnote1 on 2007-12-19
I've run into some interesting issues with Gnome (Ubuntu uses by default) and the way it manages windows.  Long story short, it really control where the windows shows up, just so long as it is in the current active workspace.  As far as I know, there is no way to get it to do exactly what you're thinking of using Gnome.  KDE may be a different story, but I don't know much about it.

---

### Post by pjones0404 on 2007-12-20
if you have desktop effects enabled. try to go to the compiz manager and choose the place windows plugin. adjust the settings here and see if it helps. when i installed compiz all the windows would start in the left hand corner. i set it to centered and it always stats them in the middle now.

hope this helps.

---

### Post by vortex0007 on 2007-12-20
Sorry, but what is "compiz manager" and how do I launch it?

---

### Post by pjones0404 on 2007-12-20
it is the gui used to adjust all the settings for compiz.

run "sudo apt-get install compizconfig-settings-manager"

once this is done u should have a menu option under preferences-advanced desktop effect settings. this is where u can adjust all the effects and such. then look in the place windows area to see if this helps.

---

### Post by vortex0007 on 2008-01-04
Thanks you for the advice - I'm abandoning this current configuration and am going back to a single monitor. Ubuntu is crashing daily with Big Desktop running and it's just not worth the hassle.

---

