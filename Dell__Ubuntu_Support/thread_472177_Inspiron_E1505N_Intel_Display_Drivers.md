---
title: "Inspiron E1505N Intel Display Drivers"
date: 2007-06-12
forum: Dell  Ubuntu Support
---

### Post by mark on 2007-06-12
Having recieved & fiddled around with my Inspiron E1505N laptop for a whole day now (!), I'm kinda curious if anybody else has explored the realms of beyond the stock i810 display driver for the standard Intel 950GM display adapter.  I configured mine for 1280x800 (I opted for the WXGA "True Life" wide screen LCD) with the standard driver and all seems okay so far.  I can even turn on Desktop Effects and wobble my windows and rotate my workspaces on a cube.  However...

Intel does have this ([http://www.intellinuxgraphics.org/install.html](http://www.intellinuxgraphics.org/install.html)) site  and I wondered if any brave souls out there had tried the "latest 'n greatest" (before I break my shiny new computer<g>).

Anybody?

---

### Post by angryfirelord on 2007-06-20
Ubuntu already has that driver in its repositories. [xserver-xorg-video-intel](http://packages.ubuntu.com/feisty/x11/xserver-xorg-video-intel)

---

### Post by bunted on 2007-06-20
I have used both the i810 driver and the intel driver.  The i810 (w/915resolution patch) works very similarly to the intel driver.  However, any patching or use of a different driver takes away the Fn+F8 CRT/LCD functionality.

I've been using the intel driver recently.  Using the vanilla i810 driver severely limited my screen resolution choices.

---

