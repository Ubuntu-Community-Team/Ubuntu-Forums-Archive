---
title: "Strange Gnome Problem--"
date: 2005-11-11
forum: Desktop Environments
---

### Post by autocrosser on 2005-11-11
Was changing the desktop theme & the Theme panel "crashed"--didn't think too much about it, but right after that almost every Gnome preference app would crash during opening--GDM & almost every preference panel--GDM crashed if I try to log-out. Rebooted & forced a fsck--no change--This only is happining in my main uses directory--I created another user & everything works fine in that directory--Question is--I know the problem will be in a .file--which one? Have looked at .gnome-.gnome2-.gnome2_private & .gnome_private--I'm not sure I'm looking in the right places---Ideas anyone?

---

### Post by bvc on 2005-11-11
.gconf

---

### Post by autocrosser on 2005-11-14
Well--the answer was a "corrupted" theme--I went back & traced my steps leading to the prob--I had just changed themes (not one that I had designed) & removed it from .themes---did a "killall gnome-panel" & all was happy--

---

