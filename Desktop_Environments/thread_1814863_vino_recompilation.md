---
title: "vino recompilation"
date: 2011-07-30
forum: Desktop Environments
---

### Post by topikpl on 2011-07-30
Hi,

I've recompiled vino (remote desktop) package with [FONT="Courier New"]--enable-gnome-keyring=no[/FONT]. I've been bothered by the local request to unlock keyring, while accessing the box remotely, kind of hard to perform ;)

After [FONT="Courier New"]./configure; make; make install[/FONT] the gnome file [FONT="Courier New"]vino-server.desktop[/FONT] has been placed in [FONT="Courier New"]/usr/local/etc/xdg[/FONT] - this way the server didn't start automatically after machine start. I had to manually link it to [FONT="Courier New"]/etc/xdg/autostart[/FONT] - now the server starts after machine start as expected.

Was it preferred way to fix the problem? Or should I provide some extra options to [FONT="Courier New"]./configure[/FONT], or add the path [FONT="Courier New"]/usr/local/etc/xdg[/FONT] to some system variable?

I'm an Ubuntu newbie and I'd appreciate your hints.

Cheers

---

