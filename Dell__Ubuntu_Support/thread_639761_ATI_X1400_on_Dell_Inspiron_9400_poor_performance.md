---
title: "ATI X1400 on Dell Inspiron 9400 poor performance"
date: 2007-12-13
forum: Dell  Ubuntu Support
---

### Post by Gyatak on 2007-12-13
Hi,

I recently upgraded to Gutsy on my Dell Inspiron 9400, and had to do a complete reinstall. After much configuring (and switching from KDE to Gnome), I finally got things really stable with decent performance.

This morning I followed [_some recommendations for getting some missing Dell functionality running correctly_]("http://debian.helicroc.com/inspiron_gutsy.html"), and now I'm having a performance issue with my ATI card. Everything is crawling and my screen is refreshing in broad diagonal swipes. When I try to scroll up or down, things really crawl. I haven't even tried to run Compiz, and Gnome moves so slowly, I've switched back to bare KDE.

I remember running into a fix for this at one point, but can't find it. I seem to remember it hinging around the configuration of the fglrx driver. BTW, if I type fglrxinfo in the konsole, it logs my out of my current session.

Can you help?

---

### Post by Paul S on 2007-12-14
Just a guess, but it sounds like your running Xgl without compiz.  Try starting compiz or uninstalling xserver-xgl.

HTH

---

### Post by Gyatak on 2007-12-14
Thanks. Somehow I worked this out. Again. I followed all the instructions I could find, and then miraculously everything worked this morning.

I wish I knew what I did...:confused:

---

