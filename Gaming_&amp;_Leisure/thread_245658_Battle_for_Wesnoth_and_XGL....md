---
title: "Battle for Wesnoth and XGL..."
date: 2006-08-28
forum: Gaming &amp; Leisure
---

### Post by tribaal on 2006-08-28
Hi folks!

I recently got hooked on the "Battle for Wesnoth" game (from the universe repos), which is very good.

A few days after that I installed XGL, and from then on I couldn't play Wesnoth: there is a huge transparency bug on the main menu and on some hexes (I can see my desktop wallpaper through it). 
I keep switching sessions from XGL to Xorg to play games... but it's getting annoying. Any way to get Wesnoth to display properly while running XGL?

Thanks a lot!

- trib'

---

### Post by _simon_ on 2006-08-28
I use this:

[http://www.ubuntuforums.org/showthread.php?t=176636&highlight=XGl+opengl+games](http://www.ubuntuforums.org/showthread.php?t=176636&highlight=XGl+opengl+games)

---

### Post by tribaal on 2006-08-28
Thanks for the answer, but unfortunately my graphics card is an ATI (using fglrx)... Wesnoth however is not an openGL game... just plain old 2d.

Is there some workaround for non opengl games that will work with fglrx drivers?

Cheers

- trib'

---

### Post by Sam on 2006-08-28
> **tribaal said:**
> Thanks for the answer, but unfortunately my graphics card is an ATI (using fglrx)... Wesnoth however is not an openGL game... just plain old 2d.

Is there some workaround for non opengl games that will work with fglrx drivers?

Cheers

- trib'

simon's link will do the trick even if it's in 2D.

---

### Post by tribaal on 2006-08-28
Cheers mate.

Indeed, it works wonders for 2d, even if unfortunately I can't use it to play openGL games... yet? :)

-trib'

---

### Post by kwaanens on 2006-08-28
With gnome-compiz-manager from beerorkid-repos you get a tray icon in Gnome where you can shut down GL Desktop. Works very well.
When I try to start ppracer it won't work with GL Desktop enabled, but with GL shut down it runs as it's supposed to. At least I think so.

- Ketil

---

### Post by tribaal on 2006-08-28
Hum interesting... I have XGL from beerorkid but I can't seem to find the "turn off XGL" button in the tray... 

Is that a panel applet?

- trib'

---

### Post by kwaanens on 2006-08-28
Install gnome-compiz-manager
It will be present it sessions as default. And I think it starts automatically after install.

---

### Post by tribaal on 2006-08-28
Yup, just installed it.
A quick logout/login and it works perfectly.

Thanks a lot :)

- trib'

---

### Post by Tyltyl on 2006-08-28
You can also run it from a terminal with this command

> XLIB_SKIP_ARGB_VISUALS=1 wesnoth

---

