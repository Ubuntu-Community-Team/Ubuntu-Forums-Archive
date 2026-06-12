---
title: "blank screen after login"
date: 2008-06-10
forum: Desktop Environments
---

### Post by portilhe on 2008-06-10
After logging in with the graphical interface I get a blank screen, but the mouse is working and it seems to be "clicking" the applications on my top panel, as the cursor turns into a spinning wheel.

This happens with the sessions "Run Xclient script" and "Gnome", but not with "Gnome failsafe"...
I am using Hardy and this did not happen before, it just started to behave like this yesterday.

Please help!

Thanks

---

### Post by shakabra on 2008-06-11
Are you able to login via the normal GUI and THEN it goes to a white screen. If so this may be an issue with compiz/desktop effects. To get your gui back

1.login as normal, wait till the login sounds are finished allowing enough time for all your normal stuff to load (panels nautilus etc.)
2.press alt-f2 to bring up the run application dialog (obviously you won't see it but it should be there)
3.enter "metacity --replace" without the quotes and press enter

With any luck metacity should kill compiz and replace it as you window manager giving you you gui back. To make this change permanent go to system>prefs>appearance and turn of desktop effects.
__________________

---

### Post by portilhe on 2008-06-11
It works! Thank you so much!

I tried to completely remove compiz and reinstall it with Synaptic but that didn't solve the problem. Also, when I try to turn effects back on the problem reappears. Not that I care so much about the effects, but is it possible to solve the problem? And should I report it as a bug?

Again, thank you!

> **shakabra said:**
> Are you able to login via the normal GUI and THEN it goes to a white screen. If so this may be an issue with compiz/desktop effects. To get your gui back

1.login as normal, wait till the login sounds are finished allowing enough time for all your normal stuff to load (panels nautilus etc.)
2.press alt-f2 to bring up the run application dialog (obviously you won't see it but it should be there)
3.enter "metacity --replace" without the quotes and press enter

With any luck metacity should kill compiz and replace it as you window manager giving you you gui back. To make this change permanent go to system>prefs>appearance and turn of desktop effects.
__________________

---

### Post by trumpcouptimmy on 2008-06-11
I happened to me also. I did the alt-F2 number and it worked. My settings were on "none" all the time. It reappeared when I rebooted. I completely removed compiz and the problem is gone. Since this was recent and all the posts seem recent, it is probably a update error. I update whenever there are some. It should be reported because it happens to more than one user and the workaround points to the culprit. For the last day, I thought my system was broken and I'd have to cold install. Sure scared me, I'm now going to do a partimage. The thing that had me reassured was that everything was there when I used the live cd.

---

