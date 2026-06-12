---
title: "LANG, rxvt, and nonsense characters in man pages"
date: 2006-06-16
forum: Desktop Environments
---

### Post by Nobber on 2006-06-16
Just wondering if anyone can explain why man pages viewed in the rxvt terminal emulator contain nonsense characters, but the same man pages viewed in gnome-terminal don't.

I've discovered that if I change the LANG environment variable from "en_GB.UTF-8" to "en_GB", then rxvt no longer displays nonsense characters in man pages, but presumably LANG is "en_GB.UTF-8" and not "en_GB" for some good reason? Or perhaps not. Anyone?

---

### Post by Nobber on 2006-06-16
So it's just a Unicode compatibility issue. Just tried **urxvt** (from the rxvt-unicode package) and man pages show up just fine with LANG="en_GB.UTF-8".

---

