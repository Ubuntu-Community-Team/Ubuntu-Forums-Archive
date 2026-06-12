---
title: "Cairo Dock Screen Corruption"
date: 2009-12-10
forum: Desktop Environments
---

### Post by Minsky on 2009-12-10
I've been using Cairo Dock for the past week or so and I've been very pleased with it. I have an ATI HD4830 card running under the ATI 9.11 drivers and I use the dock with OpenGL. I've had no problems until tonight, after I had downloaded and installed the latest update via Update Manager. Whenever I log in now, the bottom 1 inch section of the screen appears corrupted, but when I hover the mouse pointer over it, it sorts itself out and the dock displays and operates correctly thereafter without any problems. Does anyone know what is causing this and how to rectify it?

---

### Post by kevinwmiller on 2009-12-10
I got Cairo, I thought it was lame.

If you want Mac OS X, get Mac OS X..  

Anyways, I didn't think it fit, was too flashy and the bottom border covers it most the time.

---

### Post by earthpigg on 2009-12-10
> Does anyone know what is causing this and how to rectify it?

i recall having a similar problem several months back.

in my case, it was because the dock was loading ***before*** compiz.... so when the window manager transitioned from metacity to compiz, it left crap like that behind.

couple possible solutions:

-set dock to wait 2-4 seconds before loading. 
-dont have it autostart, and start it manually

---

### Post by fabounet on 2009-12-11
are you using the auto-hide with an image as the callback zone ?
there is a small bug with it, the image is not redrawn correctly.
current fix is to remove the image (transparent callback zone), or to update to the bzr version, where the bug is already fixed.

---

### Post by Minsky on 2009-12-11
Thanks for the replies guys, the dock is rendering properly again whenever I log in.

@fabounet
I changed the **Fill background with:** setting in the **Appearance** tab, from **Image** to **Colour graduation** which did the trick. As an aside, how do I update the image (which was set as **_x_.bg.png.png**) to the bzr version?

@earthpigg
I haven't tried setting a delay for the dock to load because I'm unsure how to. For future reference, how do I set a time delay for an application before it loads?

---

### Post by fabounet on 2009-12-13
the image is part of the theme.
it should work with an image as well.
maybe te given image was corrupted ? you can try with another image to see.

---

