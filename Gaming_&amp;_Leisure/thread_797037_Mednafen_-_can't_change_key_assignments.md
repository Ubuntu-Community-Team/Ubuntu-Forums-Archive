---
title: "Mednafen - can't change key assignments"
date: 2008-05-16
forum: Gaming &amp; Leisure
---

### Post by purplenite on 2008-05-16
I'm running Hardy 64 and I'm having trouble with Mednafen. Pressing Alt+Shift+1 does not start the usual input configuration process. I've tried deleting my configuration file, but that did nothing. All other keyboard commands appear to work fine.

Any suggestions?

---

### Post by csi_ on 2008-05-17
Maybe you are not running a qwerty charset. If so try:

setxkbmap us; mednafen <*somegame*>

---

