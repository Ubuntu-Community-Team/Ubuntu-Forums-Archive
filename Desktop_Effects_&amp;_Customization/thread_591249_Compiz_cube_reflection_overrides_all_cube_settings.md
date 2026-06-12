---
title: "Compiz cube reflection overrides all cube settings and won't cut off"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by Damad on 2007-10-25
I installed the Compiz Config Settings manager and eneabled the cube. All works fine until I turn on cube reflection. When i turn on cube reflection, all of the settings set in my other cube settings (zoom, cube caps) are all ignored, and when i try to cut cube reflection off, it stays on, though it is shown to be off in the settings manager. Any clues?

---

### Post by Damad on 2007-10-26
bump

---

### Post by Damad on 2007-10-27
Bumpo

---

### Post by Damad on 2007-11-01
Bumporonomy!!!

---

### Post by Zorael on 2007-11-01
Upgraded from Feisty or a fresh Gutsy install?

Using Gnome/KDE Configuration Backend to save your Compiz settings, or Flat-file Configuration Backend? (Preferences in CompizConfig Settings Manager). Some are experiencing weird issues with settings not sticking etc with Gnome/KDE backends.

I'm not sure how much it helps, but I've been told adding 'ccp' as an argument when starting compiz will make it use its own format when saving configurations. (?)

```
$ compiz --replace --ignore-desktop-hints ccp &
```

---

### Post by Damad on 2007-11-03
the problem seems to have randomly fixed itself, however, now i have a hard time getting compiz to work, period. When I go to System>Preferences>appearance>visual effects>extra(or custom) it says something to the extent of Compiz failed to load, or just do nothing at all

---

### Post by Zorael on 2007-11-03
Try launching it from a terminal and post its output here. Likely it will be more specific than "err0r, did not werk!" :>

```
$ compiz
```

---

### Post by gluonman on 2008-01-01
Okay, Zorael. Your ccp suggestion just completely ruined everything. I want to know how to completely reverse the damage.

---

### Post by Zorael on 2008-03-12
> **gluonman said:**
> Okay, Zorael. Your ccp suggestion just completely ruined everything. I want to know how to completely reverse the damage.
Ouch! That never happened to me, but it sort of makes sense. As I said, it makes it use its own configuration format, so it may just have overwritten your previous one and created a new in an arguably better designed format.

So, there's likely no way to reverse it.

---

