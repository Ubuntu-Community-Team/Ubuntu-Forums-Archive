---
title: "Kontact causing X freezups (Kubuntu Feisty)"
date: 2007-05-02
forum: Desktop Environments
---

### Post by MagisterJoe on 2007-05-02
Kontact seems to be causing my X server to freeze up.  If I open Kontact at any point during a session, the session will inevitably freeze in a few hours.  It does not make a difference whether I close the application, kill it from the CLI, or anything else.  X will eventually just eat up all my processor time, rendering the desktop useless and requiring me to reboot from tty5 or something.

When I start kontact from the shell, I get the following:
```
joe@FREEZER:~$ kontact
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
joe@FREEZER:~$ WeaverThreadLogger: thread (ID: 1) suspended.
WeaverThreadLogger: thread (ID: 2) suspended.
WeaverThreadLogger: thread (ID: 3) suspended.
WeaverThreadLogger: thread (ID: 4) suspended.
```

When I close the program, I get:
```
Weaver dtor: destroying inventory.
WeaverThreadLogger: thread (ID: 1) destroyed.
WeaverThreadLogger: thread (ID: 2) destroyed.
WeaverThreadLogger: thread (ID: 3) destroyed.
WeaverThreadLogger: thread (ID: 4) destroyed.
Weaver dtor: done

```

However, I don't get a shell prompt.  It seems like Kontact is leaving something running that is eventually just eating cycles.  Anyone know what's going on?  Is this a bug that I should file?

---

### Post by TyphoonX on 2007-05-11
I have same exact problem & warning messages with Kontact (Kubuntu Feisty) with no freezeups

---

