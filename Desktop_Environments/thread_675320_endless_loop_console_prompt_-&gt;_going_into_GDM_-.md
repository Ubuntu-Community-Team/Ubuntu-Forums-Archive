---
title: "endless loop: console prompt -&gt; going into GDM -&gt; drops back to the console prompt .."
date: 2008-01-22
forum: Desktop Environments
---

### Post by boondocks on 2008-01-22
I just applied the latest set of updates on a Ubuntu 7.10 desktop.
Then I rebooted the system.  Went to get some lunch.

Now it does not display the graphical login screen.
Instead it is going thru an endless loop trying to configure xorg.
I see the console prompt -> going into GDM -> drops back to the console prompt ...
It has been doing this for more than 40 mins.

How do I stop this endless looping?

---

### Post by tzulberti on 2008-01-23
It seems that the xorg configuration got wrong. Edit the file:/etc/X11/xorg.conf and change de video driver to vesa (generic). Then do: sudo /etc/init.d/gdm restart.

---

