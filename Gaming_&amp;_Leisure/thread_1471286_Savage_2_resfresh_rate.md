---
title: "Savage 2 resfresh rate"
date: 2010-05-03
forum: Gaming &amp; Leisure
---

### Post by maurodi on 2010-05-03
Hi all. I installed Savage 2 recently and I set the game resolution to "Desktop" which says 1280x1024 @50Hz. This is wrong as in nvidia-settings I selected 75Hz. I don't really feel anything different watching the game, but I'm worried it may harm my eyes or my monitor (can it?).

Perhaps it's just a bug and the game is showing a wrong value.

Any ideas?

I'm using Ubuntu 10.04 32bits with a GeForce 8600GT with 195.36.15 drivers.

---

### Post by P4man on 2010-05-03
If the game is running fullscreen, it can change resolution and refresh rate. You should be able to change both in the game. If its running windowed mode, then its just misreporting the refreshrate. Possibly because you are running compiz/desktop effects and compiz may not do more than 50FPS?

---

### Post by maurodi on 2010-05-03
I'm running fullscreen yes. But the only possible refresh rates are 50-59Hz.
I have the desktop "extra" effects, but nothing else installed.

---

### Post by Somberlain on 2011-07-22
refresh rate of savage 2 can be set through ~/.savage2/game/startup.cfg

SetSave vid_refreshRate "75"

---

