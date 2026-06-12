---
title: "Once applications crash once, they no longer work..."
date: 2009-01-27
forum: General Help
---

### Post by primus454 on 2009-01-27
...without a restart. This has been happening for a while now. Mostly with Amarok and Swiftfox. Even if I kill them, they will crash shortly after re-opening without a restart. Any fix?

---

### Post by Crafty Kisses on 2009-01-27
You can try running Amarok in the Terminal so when it crashes it will give you an error, then you can post it back here on the forums.

---

### Post by primus454 on 2009-01-27
I forgot to mention this also happens with terminal.

---

### Post by Crafty Kisses on 2009-01-27
Try doing the following then, press Alt-F2, then from there run this:```
xterm
```Then run **gnome-terminal**, then see if xterm gives you any errors.

---

### Post by primus454 on 2009-01-27
Terminal froze up but I could run it through Terminator and i got this:

Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809bed0 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809bed0 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )


Then I get a popup: "Xine was unable to initilize any audio drivers.

I dont get any error message when I run terminal through terminator.

---

### Post by primus454 on 2009-01-27
Another thing to add, I cannot log out or power down with X. I end up restarting through TTY1.

---

### Post by primus454 on 2009-01-27
Bump =)

---

### Post by primus454 on 2009-01-28
Nobody?

---

