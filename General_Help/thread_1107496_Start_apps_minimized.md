---
title: "Start apps minimized?"
date: 2009-03-26
forum: General Help
---

### Post by heartburnkid on 2009-03-26
Hey, trying to autostart a couple of apps on session start in the background on my Mythbuntu box.  The problem is, about half the time, they start after MythTV, and thus the windows appear in front of it.  Since I'm intending this system to be a set-top box, this is less than ideal behavior.  Is there a way to autostart these apps minimized?  Failing this, is there a way to delay MythTV's start by a few seconds to allow these apps to start first??

---

### Post by issih on 2009-03-26
It sort of depends on the programs in question... look at their man pages or append --help after the command in a terminal to get info on what options they offer.


Quit often its -m as an option, but it really depends on the program author as to what they chose to use as an option, if indeed they offer it at all.

Hope that helps.

---

### Post by heartburnkid on 2009-03-26
> **issih said:**
> It sort of depends on the programs in question... look at their man pages or append --help after the command in a terminal to get info on what options they offer.


Quit often its -m as an option, but it really depends on the program author as to what they chose to use as an option, if indeed they offer it at all.

Hope that helps.

Thanks, but that was the first thing I thought of.  Unfortunately, one of said apps is a Java applet that doesn't seem to have this option.  Is there a way to do this that doesn't necessarily depend on the app supporting it?

---

### Post by issih on 2009-03-26
This:

[http://tripie.sweb.cz/utils/wmctrl/](http://tripie.sweb.cz/utils/wmctrl/)

may help you out, although you will still get a flash as the app starts and is then minimised.

---

