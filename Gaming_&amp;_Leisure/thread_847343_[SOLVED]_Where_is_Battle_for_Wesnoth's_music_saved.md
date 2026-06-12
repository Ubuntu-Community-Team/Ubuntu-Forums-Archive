---
title: "[SOLVED] Where is Battle for Wesnoth's music saved?"
date: 2008-07-02
forum: Gaming &amp; Leisure
---

### Post by ladr0n on 2008-07-02
Seriously.  Maybe I just need to go to sleep and let my tired brain reset itself, but I can't find it.  It isn't in ~/.wesnoth, and it isn't anywhere near the executable in /usr/games.  Where did they hide it?

---

### Post by geek_Man on 2008-07-02
wesnoth-music is a seperate package.

sudo aptitude install wesnoth-music

---

### Post by Steveway on 2008-07-02
> /usr/share/games/wesnoth/data/core/music
Didn't even need to search. It's pretty logical. (I didn't suspect it in he /data/core/ subdirectories but close enough.)

---

### Post by ladr0n on 2008-07-02
Thanks steveway, that's exactly what I needed.

---

