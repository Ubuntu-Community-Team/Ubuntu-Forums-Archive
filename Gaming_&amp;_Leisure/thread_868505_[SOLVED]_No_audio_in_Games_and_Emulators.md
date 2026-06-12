---
title: "[SOLVED] No audio in Games and Emulators"
date: 2008-07-23
forum: Gaming &amp; Leisure
---

### Post by GSZX1337 on 2008-07-23
Whenever I play a game or run an emulator, I don't get sound. I don't know anything about Linux sound trouble shooting, so please explain things as I might not even know the simplest things.

EDIT: I have audio in Flash games.

---

### Post by GSZX1337 on 2008-07-24
Bumpy.

---

### Post by FranMichaels on 2008-07-24
Does going to System -> Preferences -> Sound

Clicking the sounds tab, and un-ticking the box next to Enable Software Mixing, then rebooting fix the problem (you wouldn't need to reboot, but not sure how to kill pulseaudio or what not...)

---

### Post by GSZX1337 on 2008-07-24
It did fix the problem. Is that all there is to it, or is this just the first step in troubleshooting?

---

### Post by FranMichaels on 2008-07-24
No worries, mark your thread as solved, and happy gaming :KS

---

### Post by GSZX1337 on 2008-07-28
I actually found out that the problem was that I had Banshee minimized and that's what was keeping the sound from working. Thank you for helping though. :)

---

### Post by eragon100 on 2008-07-28
> **GSZX1337 said:**
> I actually found out that the problem was that I had Banshee minimized and that's what was keeping the sound from working. Thank you for helping though. :)

Yep, that can be a problem :(

Long live ubuntu's moronic default pulseaudio setup!

(My 5.1 speakers only gave stereo sound. Turned out that when you have surround speakers, the default is to play stereo, not surround. And the only way to change: editing a config file in the terminal, YEAH!)

---

