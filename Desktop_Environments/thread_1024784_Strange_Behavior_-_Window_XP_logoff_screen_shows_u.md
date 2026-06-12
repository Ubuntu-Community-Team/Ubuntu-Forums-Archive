---
title: "Strange Behavior - Window XP logoff screen shows up just before GNOME Login screen"
date: 2008-12-29
forum: Desktop Environments
---

### Post by harry000 on 2008-12-29
Hello,

I have observed a very strange thing with Ubuntu on my system. It is however does not cause any issue, but it is strange.

I have dual booting with WindowXP and Ubuntu 8.10.

While booting into Ubuntu, and just before the Gnome Login page, I see "Window XP" logging off screen.

The "Window XP" screen shows up for less than a sec and also, its all covered with horizontal lines (but one can still easily see that its XP screen)

Now this is really strange because it have happened before (with clean install of Ubuntu 8.04 and also with a clean install of 8.10)

I cannot come up with any logical explanation for this behavior.

---

### Post by bgerlich on 2008-12-29
Not updated graphics card memory buffer is flushed in X screen buffer during card driver module init, causing this strange effect (i think). Nothing to worry about.

Ask in the Xserver IRC channel if you want a proper and exact explanation, those guys know better :).

---

