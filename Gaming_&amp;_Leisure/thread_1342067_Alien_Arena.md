---
title: "Alien Arena"
date: 2009-11-30
forum: Gaming &amp; Leisure
---

### Post by HarrisonNapper on 2009-11-30
I realize there's already an AA09 thread open, but that seems to be about a different issue than the one I've run into. I've got AA07 and 09 both installed and working on my computer. However, though they both worked flawlessly in Jaunty, in Karmic I can not run and look around at the same time. Sometimes the view will change and I can usually look freely while running backwards, but not while running forward. As one can imagine, it makes the game somewhat difficult to play :D Anyone have any ideas?

Edit: Problem was between keyboard and chair. Didn't realize default option in Karmic for touchpad was that it was disabled while typing. System>Prefs>Mouse>Touchpad is where one goes to disable this feature.

---

### Post by Irritant on 2009-11-30
Hmm, maybe setting the in_dgamouse 1 cvar will help.  I think that's the name of it.

---

### Post by HarrisonNapper on 2009-11-30
[FONT=Arial][SIZE=3]That's done by typing in_dgamouse 1 in the console, right? I also tried in_dgamouse 1 cvar (just in case). I've also tried setting it to zero and appending .bashrc with [/SIZE][/FONT][FONT=Arial][SIZE=3]"export SDL_VIDEO_X11_DGAMOUSE=0".

Also, it only happens when I am both moving and looking. There isn't really any lag or slowness otherwise. Unfortunately, looking while moving happens to be the most important part of the game. Furthermore, my weapon will not fire, either, so basically it is intermittently not accepting input from the mouse while a key is being pressed.

Anyone experienced this or have ideas for a fix?
[/SIZE][/FONT]

---

### Post by HarrisonNapper on 2009-12-01
bump.

---

### Post by sionco on 2009-12-06
> **HarrisonNapper said:**
> 

Edit: Problem was between keyboard and chair. Didn't realize default option in Karmic for touchpad was that it was disabled while typing. System>Prefs>Mouse>Touchpad is where one goes to disable this feature.

Thanks, I was having the same problems on urban terror, i cant believe that it was that simple

---

