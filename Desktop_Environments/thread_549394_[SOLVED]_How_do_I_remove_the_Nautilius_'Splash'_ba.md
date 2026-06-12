---
title: "[SOLVED] How do I remove the Nautilius 'Splash' bar from startup?"
date: 2007-09-12
forum: Desktop Environments
---

### Post by chrome307 on 2007-09-12
Is it possible to remove this so I just start with my desktop?

---

### Post by SoundFriend on 2007-09-12
Curiously, testing Gutsy, I don't get the Nautilus splash, and wondered why. I just get a long pause before the desktop appears.

SF

---

### Post by mcduck on 2007-09-13
It's not a Nautilus splash, it's Gnome splash.

Anyway, press Alt-F2 and run 'gconf-editor'. Then browse to apps/gnome-session/options and disable 'show_splash_screen'. :)

---

### Post by chrome307 on 2007-09-13
Thanks :)

---

