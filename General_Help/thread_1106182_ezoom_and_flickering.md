---
title: "ezoom and flickering"
date: 2009-03-25
forum: General Help
---

### Post by Pig on 2009-03-25
Hello,

I am using Hardy (fresh install, upgraded) on a Toshiba Tecra R10 (but I'm not sure the hardware has to do with the problem). I have the restricted drivers install for my NVidia Quadro 150M so that I can use ezoom.

I've set ezoom to only move the screen when I move the cursor to the edges of the screen (I'm willing to post exactly settings if you tell me what to type or I can also attach screenshots of the config screen if needed).

The problem is that whenever the desktop is zoom (i.e., this doesn't happen if, say, I press Super+1), the screen flickers white sometimes when a program is loading (e.g., opening a terminal, firefox loading a page, etc). It flickers in "burst" (i.e., flickers once, wait a second, flickers twice, stops flickering).

It seems to flicker less if I move the mouse less while the program are loading (using cpu(?)). Moving the mouse inside the zoomed area (so that the area itself doesn't move) still causes more flickering.

The system is still perfectly usable (it doesn't flicker when nothing happens) but it is really annoying.

I'm wondering if anyone else is having this problem or if others would be willing to try this (since desktop effects are easy to enable nowadays) and tell me what happens.

---

### Post by Pig on 2009-03-26
Bump?

Should I be assuming that this is not happening on anyone else's computer?

---

### Post by evilaim on 2009-03-26
it is most likely your video settings.  I know people get video flickering if they have visual effects on.  If you can, disable compiz and see if that helps.

Another way to check if your video card is installed right would be to look into EnvyNG.  sudo apt-get install envyng-gtk
That's the GUI version, envyng-core is the CLI version.  It will find out what video card you have installed and download and install the latest drivers.

Good luck.

-Evil

---

### Post by Pig on 2009-03-26
Yes, indeed it is most likely my video setttings. However, disabling compiz would defeat the purpose of what I'm trying to do (zooming). As I have mentioned, if I don't zoom in (at all), there is no flickering (even if compiz is still enabled).

EnvyNG is unable to identify my video card. I believe that I have to wait for 177 to be backported to Hardy for that (unless someone can tell me how to manually install).

---

### Post by Pig on 2009-03-26
So it seems that nvidia has its own installer (which I can use to get the newest version). Is there any reason I should not just download that and run it?

---

