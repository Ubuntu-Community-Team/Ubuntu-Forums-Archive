---
title: "[SOLVED] compiz tray icon won't load on boot-up"
date: 2007-12-29
forum: Desktop Effects &amp; Customization
---

### Post by Cammy on 2007-12-29
If I go to System -> Preferences -> GL Desktop and click "Show tray icon", it appears on my top panel, but the next time I boot the machine, it's gone.

Any tips for making it hang around?

---

### Post by thymox on 2007-12-29
Find out what command *System -> Preferences -> GL Desktop* runs, then go to *System -> Preferences -> Sessions* and add a new Startup Program that runs the command you just discovered.  If it needs sudo rights, then just do it via:```
 gksudo -S "command you found"
``` and it'll use the nice GUI sudo thingy.

---

### Post by Cammy on 2007-12-29
Well I'm not trying to run the GL Desktop dialog at bootup.  I'm just trying to get the tray icon for it to stick around.  If I run the GL Desktop app, and check the "Show tray icon" option, the check disappears on next bootup, and I have to re-check it.  It's like it's not saving the settings.

What I need is a command line option to add to sessions that kicks off the tray icon.

---

### Post by Cammy on 2007-12-30
Ok, I'm gonna mark this as solved.

I asked over on the compiz forums, and found I was running an ancient version of compiz.  I've installed the new version, and I'm good to go (although I have a few new bugs to replace the old ones, heh).

---

