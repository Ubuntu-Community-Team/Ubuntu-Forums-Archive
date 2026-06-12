---
title: "Unreal Tournament won't run fullscreen"
date: 2007-10-06
forum: Gaming &amp; Leisure
---

### Post by Zeikcied on 2007-10-06
I have the original Unreal Tournament, from Unreal Anthology.  (Thanks to a custom installer found on Epic's forums.)  It seems to use the v436 binaries from the original version, though.

Anyway, UT ran perfectly several months ago (I'm talking around February or March).  I haven't played it since.  I tried starting it tonight, and it won't work.  I changed the settings in the UnrealTournament.ini to make it start in a window, and it started just fine.

So, to sum things up, UT starts just fine when in a window.  But it won't start fullscreen.  And I don't know how to make it go fullscreen from it being in a window.

UT2004 runs perfectly fullscreen, so I know it isn't necessarily an OpenGL problem.  Everything is the same, except I believe it was installed in Edgy, and I used the Adept Upgrader in Kubuntu to upgrade to Feisty.  I don't know if the upgrade changed any crucial packages or not, but I don't know why it won't start fullscreen.

When I try to start it fullscreen, it flashes for a very brief moment, and my mouse gets reset to the top-left corner of the screen, but the game immediately crashes upon startup.

Does anyone know why that is?

---

### Post by gwoodard on 2007-10-16
Okay... If you go to winecfg to "Graphics" to "Emulate Virtual Desktop" and "Allow the Window Manager to control the windows" If the game is crashing due to full screen then try these instructions and see what happens...If it works say so but if it doesn't work then either talking to me or google "Unreal Tournament+Fullscreen+Wine+Crash"

---

### Post by Zeikcied on 2007-10-16
> **gwoodard said:**
> Okay... If you go to winecfg to "Graphics" to "Emulate Virtual Desktop" and "Allow the Window Manager to control the windows" If the game is crashing due to full screen then try these instructions and see what happens...If it works say so but if it doesn't work then either talking to me or google "Unreal Tournament+Fullscreen+Wine+Crash"
I'm not running it via Wine, though.

There is an installer script that someone wrote that extracts the files from Unreal Anthology, and then uses the old Loki binaries (version 436 of the binaries, as far as I can tell).  So it's native Linux, not Wine.

---

### Post by gwoodard on 2007-10-16
Nevermind on that... here try this

[http://ubuntuforums.org/archive/index.php/t-363783.html](http://ubuntuforums.org/archive/index.php/t-363783.html)

---

