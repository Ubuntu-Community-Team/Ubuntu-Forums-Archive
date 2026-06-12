---
title: "OpenGL needs a different window manager?"
date: 2007-03-13
forum: Desktop Environments
---

### Post by Millibrain on 2007-03-13
Hi

I'm a very new user of Ubuntu (and Linux), and I would like to dabble in OpenGL. Some of the projects I would like to work on would involve full screen TV output. I was hoping that glutFullScreen() might have done this for me (it seems to work under MS XP) or, failing that, glutEnterGameMode (). 

Under Ubuntu glutFullScreen() gives me a maximised window, and glutEnterGameMode() fails to do anything at all even though a prior call to glutGameModeGet (GLUT_GAME_MODE_POSSIBLE) is positive. 

I read in another thread that it might be Ubuntu's window manager (Metacity?) which is causing the problem. Does anyone know which other window manager might work, and how I would change over to it? Would I notice any change in desktop appearance from Ubuntu's default setup? - I rather like it the way it is!

Many thanks in advance.

---

### Post by Michael R Head on 2007-07-16
Apparently, glutFullScreen() just sets the fullscreen hint for the Motif window manager. I'm looking for a way to do set the hint for other window managers. One thought is to use GTKGLEXT and use GTK's fullscreen api (gtk_window_fullscreen) and fill its content area with the GL canvas. I'm using python for my project, though, and the python bindings aren't in feisty (they're coming in gutsy, though).

---

