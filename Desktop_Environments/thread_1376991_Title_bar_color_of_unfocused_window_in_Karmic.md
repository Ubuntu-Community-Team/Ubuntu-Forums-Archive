---
title: "Title bar color of unfocused window in Karmic"
date: 2010-01-09
forum: Desktop Environments
---

### Post by jis on 2010-01-09
It is so dark I can't see the details, if I don't use very high contrast in my monitor. The color did not change even if I changed Style in Settings > Appearance. Is there any way I can change the colors of the uncofused title bar?

---

### Post by morgengenuss on 2010-01-09
title bars are part of the window manager and therefor only change when you change the window manager theme.

(of course that's not exactly the truth since xfwm4 themes can pickup the gtk theme's colors, but as far as i know albatrosse's xfwm4 theme doesn't do that.)


so, to answer your question: edit the theme in /usr/share/themes

---

### Post by jis on 2010-01-10
It is odd that no theme I tried has changed this setting (at least effectively). I like Raleigh theme, but its gtkrc is empty; well there is a comment telling it is the default theme if no other theme is selected.

---

