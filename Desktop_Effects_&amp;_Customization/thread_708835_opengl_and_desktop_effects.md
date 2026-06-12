---
title: "opengl and desktop effects?"
date: 2008-02-26
forum: Desktop Effects &amp; Customization
---

### Post by deathsshadow77 on 2008-02-26
In Ubuntu Gutsy 7.10 I get a weird problem while using opengl at the same time as compiz

if i do something such as preview screensavers in system>preferences>screensaver the area being rendered in 3d will flicker black and worst case senario the desktop will crash.
When this happens I have to restart.
This also happens in any other 3d program such as google earth or 3d games.

i am on an ati 1950xt and have drivers installed from envy
I just really want to get my screensavers working

---

### Post by Melcar on 2008-02-27
There are a few threads on this "problem".  What it comes down to is, unless you're running an nvidia card with the latest proprietary drivers, Using Compiz with any form of acceleration (opengl, Xv, etc.) will give you screen flickering.  If you really want to run Compiz, you're going to have to use X to render (this applies to screensavers too).  This is a limitation of the current xserver, and not really a bug of the ATI drivers.

---

### Post by deathsshadow77 on 2008-02-28
how exactly would go about doing this?

---

### Post by bellwells on 2008-02-28
deathshadow,

Time for me to give a little back to this wonderful forum.  I had great sucess reading forlong.blogage.de/article/2007/8/26/......  There are a few references to his web site on these forums.  Very very helpful.  I do, however, have a nVidia card.

Ron

---

