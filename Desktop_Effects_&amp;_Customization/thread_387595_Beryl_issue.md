---
title: "Beryl issue"
date: 2007-03-18
forum: Desktop Effects &amp; Customization
---

### Post by coosa on 2007-03-18
Dear all,
I had installed my ATI Driver successfully on AMD64 Edgy; I have then installed Beryl and every thing worked just fine;
All of the sudden a couple of days later after I rebooted my PC, Beryl wasn't working;
I remarked then that my ATI Driver has no more direct rendering where it had earlier!
So i restored back the old xorg drivers and reinstalled ATI til I had again the direct rendering as I could verify it with the command:
glxinfo |grep rendering
However, When I installed Beryl again and created a new xgl session for desktop, it doesn't have a direct rendering!
The weird thing is that at my default gnome session, it has a direct rendering; when I log off and change my session to xgl and then run the same command in my terminal under the new created xgl session, it states:
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
So I'm confused; I guess that Beryl is not working under the XGL Session since the direct rendering is disabled, but why is it then enabled under my default gnome session?!
Appreciate any help

regards

---

