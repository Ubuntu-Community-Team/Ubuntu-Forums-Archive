---
title: "[SOLVED] Dekstop effects could not be enabled?"
date: 2008-12-22
forum: General Help
---

### Post by munkyinvasion on 2008-12-22
So, I was using compiz just fine on my Eee pc 904HA, wobbly windows, multiple desktops, everyting. Now, it won't work. It just says that effects could not be enabled. The only thing i did was plug in an external monitor, and it said something about virtual resolution. Is there a way to fix it?

---

### Post by gettinoriginal on 2008-12-22
System > Admin > Hardware Drivers, sometimes changing monitors causes the system to set different drivers disabling the one you have set.

You also may want to go to System > Pref > Appearance > Visual Effects and make sure Extra or Custom is checked.   :P

---

### Post by munkyinvasion on 2008-12-27
Fixed it. Apparently, when I plugged in the monitor, Ubuntu made a copy of my xorg.conf file and made a new one that doesn't work with desktop effects. So, it is just a matter of replacing the new file with the old one after the monitor is unplugged.

---

### Post by omskates on 2008-12-27
Don't mean to "hi-jack" this thread but while on this subject;  My Compiz-Fusion does not play nice with Web-Cam chats (Skype), Open Office Suite (no tool bar) etc. Turning desktop effects to off fixes this as annoying as it is.  I suspect an Nvidea driver issue? Streaming and DVD playback are not effected.  If anyone has a work around I'd appreciate it.  --Thanks!

---

### Post by stderr on 2008-12-28
> **omskates said:**
> Don't mean to "hi-jack" this thread but while on this subject;  My Compiz-Fusion does not play nice with Web-Cam chats (Skype), Open Office Suite (no tool bar) etc. Turning desktop effects to off fixes this as annoying as it is.  I suspect an Nvidea driver issue? Streaming and DVD playback are not effected.  If anyone has a work around I'd appreciate it.  --Thanks!

I think you'd do better starting a new thread for this issue, as it seems to be very different from the main thread issue. Sounds rather odd, the driver's probably OK (I would assume...) if DVD playback etc is OK. Can't really venture any suggestions though. 

Some screenshots may help people grasp what you're experiencing.

---

