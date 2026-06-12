---
title: "opengl wont go fullscreen"
date: 2005-08-17
forum: Gaming &amp; Leisure
---

### Post by rb123 on 2005-08-17
ive tried glutfullscreen and glutentergamemode, and both show the two bars at the top and the one across the bottom; in game mode, the mouse is blocked from the upper two bars and the lower one is non-functional, so i assume it is actually in game mode, but gnome (or metacity) is overriding opengl's attempt to go full screen. 

i assume that it will work correctly if i just run a window manager, but i'm so used to gnome i'd like to get it to work there as well. any tips?

thanks,

rod

---

### Post by Michael R Head on 2007-07-16
Apparently, glutFullScreen() just sets the fullscreen hint for the Motif window manager. I'm looking for a way to do set the hint for other window managers. One thought is to use GTKGLEXT and use GTK's fullscreen api (gtk_window_fullscreen) and fill its content area with the GL canvas. I'm using python for my project, though, and the python bindings aren't in feisty (they're coming in gutsy, though).

---

### Post by blitzer on 2007-07-16
I may not totally understand the problem here but would -Alt + enter change to full screen ?

The Alt + g allows the curser to move outside the window when in window mode.

---

