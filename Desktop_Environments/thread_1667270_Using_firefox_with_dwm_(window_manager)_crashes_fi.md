---
title: "Using firefox with dwm (window manager) crashes firefox"
date: 2011-01-14
forum: Desktop Environments
---

### Post by yezariaely on 2011-01-14
I have installed dwm as window manager and whenever I start firefox it crashes after a few seconds. When I use the gnome window manager everything works fine.  Anyone has a hint for me what I can do?

---

### Post by Spice Weasel on 2011-01-14
What is the output in the terminal when you launch Firefox? Are there any error messages?

---

### Post by yezariaely on 2011-01-15
Thank you for your answer. In fact there was an error message which I missed. My bad.

Error message was "Attempting to load system libmoon". So I removed the libmoon package (which I do not need) from my system and everything works fine.

Problem solved! :) Thanks!

Why this problem does not occur when not using dwm (it is a different user, too) still confuses me...

---

### Post by Spice Weasel on 2011-01-15
Heh. Libraries can be crazy things.

---

