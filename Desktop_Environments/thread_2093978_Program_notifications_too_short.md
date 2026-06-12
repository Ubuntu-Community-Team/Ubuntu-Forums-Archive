---
title: "Program notifications too short"
date: 2012-12-12
forum: Desktop Environments
---

### Post by mcarro on 2012-12-12
Hi.  I am experiencing a problem with notifications in Kubuntu.  Some programs (e.g., mail-notification) have started to show Ubuntu notifications in the style of gnome's notify-send, and, besides, they appear for an amount of time too short.  This happened after I logged out of KDE, logged in in Ubuntu/Unity, and then came back to KDE.

I really preferred the KDE notification stack.  Any idea of what could have happened, and how I can revert to programs using the KDE notification style?  

If not, maybe someone know how to make KDE abide by the time Gnome notifications are specified to stay on the screen.  Right now, using notify-send from the shell with a long timeout (e.g., 'notify-send --expire-time=10000 "Hello"') makes them appear and immediately disappear.

Thanks a lot in advance!

---

### Post by SeijiSensei on 2012-12-12
I have only Kubuntu.  My notifications seem to stay on screen for the ten second period you mention above.  My guess is that your experience has something to do with having installed both desktop environments.

You can view expired notifications for a while by clicking on the circular notification icon in the tool bar.  Eventually they are no longer available, but I don't know how long that is.

---

### Post by apmcd47 on 2012-12-12
Check to see if any part of Gnome is still running on your system. I remember once Nautilus would leave something running in the background which would then restart every time you started a new session, that is, logged in, regardless of the desktop you logged into. One of the reasons I hate Gnome.

Andrew

---

