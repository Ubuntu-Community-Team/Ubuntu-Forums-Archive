---
title: "Can I change the bootup font size?"
date: 2005-02-12
forum: Desktop Environments
---

### Post by rosslaird on 2005-02-12
I have a 19 inch LCD display, and when Ubuntu boots up some of the text is cut off on the left side of the screen. I'm missing two or three characters, which is a bit annoying. I had Gentoo installed on this same machine, and when it booted the fonts were resized (smaller) and the margins were adjusted so that the text fit neatly within the viewing area. I imagine this is a bootsplash or gensplash or framebuffer (or whatever) optimization, and I wonder if I can do the same thing in Ubuntu (without having to recompile my kernel!).

I suppose I could play around in grub.conf to see if this can be adjusted from there, but it would be nice to get some confirmation before messing around and rendering my system unbootable.

Once I get into X, everything is fine. The viewing area fits nicely into the screen.

Ross

---

### Post by drasko on 2005-02-12
Take a look at the /etc/console-tools/config. It is pretty much explanatory, but I never have been changeing it... At the enf of file youll see :

# Turn on numlock by defalt
#LEDS=+num
APP_CHARSET_MAP=iso15
SCREEN_FONT=lat0-sun16

so I guess this last line is something to aim at... Try changing the font - avilable font are in /usr/share/consolefonts/

Hope that helps,
Drasko

---

### Post by alastair on 2005-02-12
I usually add the something like :

vga=791

to the grub boot command line (after "quiet", or whatever). I think you can also say something like "vga=ask" and it will prompt for a code. You might need to experiment.

---

### Post by rosslaird on 2005-02-12
Yup, vga=791 did the trick.
Thanks for the help.

Ross

---

