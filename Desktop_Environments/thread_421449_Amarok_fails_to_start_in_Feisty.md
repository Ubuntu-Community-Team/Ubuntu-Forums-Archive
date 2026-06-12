---
title: "Amarok fails to start in Feisty"
date: 2007-04-24
forum: Desktop Environments
---

### Post by Sirkent on 2007-04-24
Since I've upgraded to Feisty, Amarok won't start for some reason. It worked perfectly before and I haven't changed anything in particular that should upset it.

I've tried re-installing Amarok and reinstalling quite a few of the kdelibs too without any success.

Here's what I get when I try to run amarok from the command line:
```
~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80960c0 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80960c0 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?
```

It never shows (in the notification area or as a window) and the process never quits. That's all I get.

Any ideas?

---

### Post by Sirkent on 2007-04-25
bump!

---

### Post by FuturePilot on 2007-04-25
I think you need to use the command ```
amarokapp
```

---

