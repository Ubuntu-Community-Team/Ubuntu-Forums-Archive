---
title: "wine firefox flash and sound"
date: 2006-09-13
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-09-13
It's not possible to get sound through flash (and possible other ways) in firefox used through wine unless I close amarok and reopen firefox.  Is there a way I can fix this, like for example telling firefox to use a different sound system or something?

---

### Post by CatKiller on 2006-09-14
Have you tried turning off ESD? Either System -> Preferences -> Sound and untick "Enable software sound mixing" or **killall esd**.

Or you can use **winecfg** to change the sound system used by Wine, if you wanted Wine to use a different sound system to everything else. They both have to use the same thing eventually though, to get out of your speakers ;)

---

