---
title: "How can I get Ubuntu to stop reading AUTORUN.INF files?"
date: 2009-06-01
forum: Desktop Environments
---

### Post by darthpenguin on 2009-06-01
I hope I am posting this in the right place.

I noticed that when I insert a DVD in Ubuntu that has InterVideo on it then Nautilus (or GNOME?) reads the AUTORUN.INF which usualy looks something like this

[autorun]

open=install.EXE id= ver=1.0.0.0

icon=win\setup\iPlayer.ico

notice that it points to the iPlayer.ico. That means that I loose the pretty "CD" icon and get the infamous (and VERY ugly) InterVideo icon.

I don't thing Ubuntu should be reading any AUTORUN files ever for various reasons not just cosmetic. :)

How can I stop ubuntu from reading the AUTORUN.INF files on my media?

---

### Post by glotz on 2009-06-01
```
gconf-editor /desktop/gnome/volume_manager/autorun
```

---

### Post by darthpenguin on 2009-06-01
I checked media_autorun_never under apps/nautilus/preferences in the gconf-editor and that stoped VLC from opening on DVD insert but the Intervideo Icon still shows up. So Ubuntu is still reading the AUTORUN.INF

I looked for /desktop/gnome/volume_manager/autorun in gconf-editor as suggested but there is no volume_manager sub folder. I think were on the right track by looking in the gconf-editor but I just can't find the preference I need to toggle.

Any other suggestions? Thanks

---

