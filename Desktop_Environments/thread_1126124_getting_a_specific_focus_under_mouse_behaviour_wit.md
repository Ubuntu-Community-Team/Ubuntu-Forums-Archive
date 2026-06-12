---
title: "getting a specific focus under mouse behaviour with Gnome"
date: 2009-04-15
forum: Desktop Environments
---

### Post by spip on 2009-04-15
I am running ubuntu/gnome, fresh 8.10 install.  Hadn't used ubuntu and a linux desktop environment for 2-3 years, I'm amazed at the improvements.

In any case, I would like to stick to gnome, but I like the "focus under mouse" and "do not activate on click" behaviour available in KDE's window manager.  I don't know how to get this with metacity (I am assuming this is still the default gnome window manager?)

Just to be clear, what I would ideally want:
1. focus follows the mouse
2. clicking on a window does not raise it, only clicking on the window's frame/taskbar raises it.

I know that #1 is possible by going in System->Preferences->Windows, but without #2 it's not what I'm attempting to achieve.  Overall, this is the behaviour I knew and liked when working on sun sparcstations way back in university.

Is this behaviour possible from Gnome's window manager? If not, should I run another window manager, and if so which one?  That is pretty much the only thing I want out of a window manager, other than it being lightweight.

Thanks,
spip

---

### Post by mcduck on 2009-04-15
Yes, it's possible, although disabling raise on click is not recommended and the comments for this setting state that you shouldn't use it and if something breaks it's your own fault as you enabled something that doesn't really work nice with every application.. ;)

Anyway, hit alt-f2 and run "gconf-editor" to start the Configuration editor. Then browse to apps/metacity/general, and set the "focus_mode" to "sloppy" or "mouse". Next, disable "raise_on_click".

("Sloppy" focus means that the window is focused when mouse moves over it, and keeps focus until something else is focused. "Mouse" means that a window is focused *only* when mouse is over that window.)

If are using Compiz (the "Desktop Effects"), just open CompizConfig Settings Manager, and in general Options, under the "Focus & raise Behaviour"-tab disable "Click to Focus" and "Raise on Click".

---

### Post by spip on 2009-04-17
Thank you, that exactly does it.  I'll remember your warnings (which were also noted in the description of the focus property).

Thanks again!
spip

---

