---
title: "window manager for TV?"
date: 2011-01-19
forum: Desktop Environments
---

### Post by forcotton on 2011-01-19
Hello ubuntu users!:popcorn:

I'm setting up a HTPC to hook up with TV. I'll mostly use xbmc full screen, however I'll need to run a browser or some other app from time to time. Full screen is better I guess.

So I'm looking for a window manager that:
 - can be setup to full screen by default, no window titles, no decorations.
 - light weight
 - good compatibility, e.g. pop-up windows / notifications should be correctly handled.
 - provide visual aid when switching between windows; something like Expose effect or even big window title list should be fine.

I don't mind a little configuring. It's best if the package is in ubuntu; I can go compile if it's really good. :D

---

### Post by Krytarik on 2011-01-19
What about simply setting up Compiz that way?:

"System -> Preferences -> CompizConfig Settings Manager"
- "Windows Decoration", in the field "Decoration windows" enter "!any"
- "Window Rules", in "Fullscreen" enter "any"

**EDIT:** > good compatibility, e.g. pop-up windows / notifications should be correctly handled.
If "Fullscreen" doesn't work good enough, since I know some notifications don't get displayed then, you could instead just choose "Maximized", if there is a different at the end depends on the application.

---

### Post by Kalimol on 2011-01-20
And the Ring Switcher or Shift Switcher is expo-y.

That's actually a pretty neat trick. I wish I'd done that with my HTPC (I'm between televisions.)

---

### Post by Krytarik on 2011-01-20
> **Kalimol said:**
> And the Ring Switcher or Shift Switcher is expo-y.
Yeah, forgot about that, in the "Window Management" section of CCSM you can choose one or more switcher:
- Application Switcher (old style)
- Static Application Switcher (new style)
- Scale
- Shift Switcher
- Ring Switcher

---

