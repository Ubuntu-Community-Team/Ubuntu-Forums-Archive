---
title: "Ubuntu completely frozen"
date: 2009-08-07
forum: Desktop Environments
---

### Post by karusho on 2009-08-07
I'm not sure exactly what happened, but I did a system update on Ubuntu 9.04 and after the reboot, everything is frozen.

It gets past the loading bar and loads up a pale background and shows the mouse, and immediately locks up after that. I can't move the mouse, the keyboard has no response, and networking is apparently dead, as I can't SSH or VNC into it, and the router shows it as "offline".

I think there was a kernel update that may have screwed something up.

Help please?
Thanks in advance.

---

### Post by karusho on 2009-08-07
Update:

Ok, so I booted into recovery mode. 

Dropping into root shell prompt works, nothing wrong that I can tell, until I try to start X and it loads the GUI and then it freezes.

Dropping into netroot gives me "wmaster0 unknown address type 801" and freezes.

---

### Post by Soley on 2009-08-07
I'll be the first to say that I'm not the smartest one here when it comes to problems in Linux. What I would try would be to install a new desktop environment. If you're running gnome, try downloading kubuntu-desktop. 

But, honestly, I don't even know if that's possible. I've never had to boot into recovery mode, so I don't know what features are available.

Hopefully someone else can help with this issue.

---

### Post by karusho on 2009-08-07
I have no way of downloading anything at the moment, as trying to start networking causes it to freeze up.

---

### Post by NoBugs! on 2009-10-06
Maybe 9.04 doesn't support your graphics card? I noticed that was the case on an older computer I tried it on. Have you run it from a livecd to see if it works there?

---

