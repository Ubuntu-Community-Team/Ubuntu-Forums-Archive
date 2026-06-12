---
title: "Doom3 problems"
date: 2006-09-26
forum: Gaming &amp; Leisure
---

### Post by Naegling23 on 2006-09-26
When I start doom3, it does not go full screen, it opens a window on my desktop.  The problem is that the window is larger than my desktop, so I cant see the whole screen.  I cannot access any menu's, and I cannot alt+tab out of the doom3 window.  Can anyone help!  Whenever I try to launch the game, I cannot play, and have to turn my computer off in order to exit the game.

---

### Post by Ferrat on 2006-09-27
just open the folder 

/home/[your username]/.doom3/base/

and edit the file DoomConfig.cfg

Search for SET fullscreen "0"

then change the 0 to 1 so is says SET fullscreen "1" instead

---

### Post by Naegling23 on 2006-09-27
in the cfg file, I have

seta r_fullscreen "1"

thats the closest thing I can find as to what you told me.

Problem is still there.

---

### Post by Naegling23 on 2006-09-27
ok, I figured it out, it turns out that I had accidentally set it to a widescreen resolution without a widescreen monitor, so it popped up on screen, and the extra bleed off screen so that I could not access it.  I hid my upper and lower toolbars, and I was able to get to the game settings (it took some magic, I couldnt actually see them) and changed the system to 640x480 and non full screen.  I was then able change the resolution to the correct one in fullscreen, it works fine now.

It just goes to show you that its never what it seems.  I thought the problem was either with the game not displaying correctly, or that it was stealing my mouse, so I couldnt move the x window around.  Turns out the problem was that I cant figure out 4:3 resolutions.

---

