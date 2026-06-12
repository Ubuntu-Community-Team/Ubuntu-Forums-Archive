---
title: "Krfb halts system: VNC client reports &quot;WriteExact error while writing&quot;"
date: 2008-10-06
forum: Desktop Environments
---

### Post by timjamz on 2008-10-06
Hello!  I'm just getting started with ubuntu, and pretty fresh to linux in general -- please bear with me.

I'm running hardy heron with kubuntu (kde 3.5) on an old Dell GX110 p3-1GHz 384MB. My problem is present over both wired and wireless NIC, and present when trying to connect to KDE from a Windows PC using either tightVNC or UltraVNC.

The problem is... I log into the ubuntu box and launch Krfb server (wide open, broadcast, allowing control, no password), then try to connect from the Win PC via IP over the default 5900 port.  I get a screenshot of KDE (can move the KDE mouse for about 10 seconds wired, and not at all wireless) - then the whole ubuntu system just halts. No error messages, just stops responding... no mouse, can't f1 f2 f3 etc to terminal, ping doesn't even respond.  I kinda thought that was impossible with linux, but leave it to me.

Obviously, this isn't a whole lot of technical info... I am a noob, so please point me in the right direction!  What info can I provide that might help get this figured out?

Thanks for any help you can give! :)

---

### Post by timjamz on 2008-10-06
Ah-ha! I figured it out... I used freeNX instead. :-$

[http://michigantelephone.wordpress.com/2007/10/15/how-to-install-nx-server-and-client-under-ubuntukubuntu-linux/](http://michigantelephone.wordpress.com/2007/10/15/how-to-install-nx-server-and-client-under-ubuntukubuntu-linux/)

This works like a charm!

---

