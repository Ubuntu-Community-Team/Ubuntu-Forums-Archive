---
title: "Gnome Bloated &amp; Slow ?"
date: 2007-02-27
forum: Desktop Environments
---

### Post by clash on 2007-02-27
Hey guys, i'm just curious. 

Just before anyone says it, i know about xfce, fluxbox etc. In fact i use flubox exclusively on an old (old old) machine. 

My question isn't if gnome is slow/bloated but why and what can be done about it ? 

In comparison even to windows gnome can just be so unresponsive. I know we're talking milliseconds here but it still matters. 

This is even on relatively fast machines too. I don't know about KDE, its a LONG time since i had any dealings with KDE (2.something i think) 

Anyhoo, just thought i'd get the ball rolling. 

Thanks.

---

### Post by ComplexNumber on 2007-02-27
i guess it depends whats slow. here are some tips to speed various things up:
-dont use icon themes that only use svg's. they tend to be very slow compared to png themes. compare the speed that it takes to load up the theme and applications using a theme when you are using the svg version of snowish compare to the png version

-don't use themes that rely on the pixmap engine. if the backgrounds to applications look like they have a pattern, then one can be sure that it uses the pixmap engine. it tends to be very slow. fast theme engines include murrina themes and mist themes.

-fire up gconf-editor, then search for "metacity". apps/metacity/general should be the 2nd one down in the list of hits. click on the "reduced resources" switch.

-switch off beagle. 

-put your themes and icons in /usr/share/themes and /usr/share/icons, respectively....instead of your home directory. i find that when such things as themes, icons, fonts etc that take up a log of diskspace are placed in the home directory, it slows things down.

---

