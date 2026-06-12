---
title: "Terminal command to change window manager"
date: 2007-05-07
forum: Desktop Effects &amp; Customization
---

### Post by Matthaeus on 2007-05-07
HI, i'm making a script which runs the game warcraft 3 through wine + a few other things.

Wine crashes if you try to start warcraft while you have 3d effects enabled. So to get around this i click the berly icon and change my window manager to metacity.

What are the appropriate commands to swap windows manager from berly to metacity? Also, what would be the appropriate command to start berly again?


Many thanks, Matt.

---

### Post by Rinzwind on 2007-05-07
It's the same kind of change you made to include Gnome with XGL in your session menu.

**metacity** should starts the usage of metacity. I think you might need **-- replace** behind it as a parameter to make it switch from beryl/emerald to beryl/metacity.
**emerald** invokes beryl/emerald.

(if I type metacity from CLI the GUI changes to metacity).

---

### Post by Matthaeus on 2007-05-07
metacity --replace works to change it to metacity,
but emerald --replace doesn't switch it back.

Matt.

---

### Post by Matthaeus on 2007-05-09
Bump.

---

