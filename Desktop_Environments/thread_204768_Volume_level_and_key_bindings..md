---
title: "Volume level and key bindings."
date: 2006-06-27
forum: Desktop Environments
---

### Post by G Morgan on 2006-06-27
My Ubuntu desktop recognises my volume control keys on my keyboard but they don't control the volume of the desktop (I'm not sure what they control but it isn't anything useful). They are currently bound using the 
System->Preferences->Keyboard Shortcuts->Sound->Volume up/down 
option this gives a nice volume up/down image when pressed but doesn't actually change the volume. 

What I want to know is if there is a console command to increment or decrement volume through ALSA so I can bind it myself through gconf-editor.

Cheers.

---

### Post by DjBones on 2007-08-13
lol i think your getting a little ahead of yourself there,
if you just want to change the mixer that the buttons control (mine was set to Capture for some reason and I wanted it on Front)
so you just pop open gconf /->desktop->gnome->sound and change the value of the default mixer.

although if your hell-bent on using the terminal, i wouldn't know how to fix it that way haha

---

