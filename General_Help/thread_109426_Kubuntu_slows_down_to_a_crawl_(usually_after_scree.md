---
title: "Kubuntu slows down to a crawl (usually after screensaver)"
date: 2005-12-28
forum: General Help
---

### Post by Ninjagecko on 2005-12-28
Hello.

I'm curious if anyone has any insight into this:

After letting KDE run a little while (30min or so) it immediately becomes unbearably slow (i.e. will take you 15 minutes to type 'top' into a command prompt and reboot).

I have no idea why it does this. When I do *top*, nothing is taking up more than a sliver of my CPU/memory. When I do *free*, nothing seems to be the problem. If nothing returned by 'top' is causing my computer to run so slowly, what could be the matter? Could it be something in the kernel?

I'm not sure if this had anything to do with it, but recently I changed my display from 16->24 colors, and commended out the DRI section in my xorg.conf (in an attempt to fix a problem where X-win would suddenly crash with no error messages).

(Other wierd things which have happened: The Ubuntu startup splash logo changed to a Kubuntu logo suddenly; perhaps it was around the time I updated amaroK, but still that's pretty weird...)

I installed Kubuntu over Ubuntu, but I never had this problem until recently.

Soon I will attempt to turn off my screensaver (helios, an OpenGL screensaver) and see if that fixes the problem.

---

### Post by Refrozen on 2005-12-28
Run [ps aux](http://manlib.com/man/207) | [grep](http://manlib.com/man/155) helios and see if it's still running.

Also check the xscreensaverd status.

---

### Post by Ninjagecko on 2005-12-29
That was one of the first things I did; kill -9'ing it didn't help.

It was though apparently the fault of the screensaver (or ACPI, or some interaction thereof), because when I turned off screensavers and powersaving the problem doesn't happen again.

Just a heads up to anyone who might have the same problem. Not sure what the problem is though... or if it happens with other OpenGL screensavers.

---

