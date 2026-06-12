---
title: "Gnome + Tiling Window Manager"
date: 2008-09-13
forum: Desktop Environments
---

### Post by puppyfarts on 2008-09-13
I was wondering if there is a way to use the Awesome Winodw Manager on Gnome. I saw that Xmonad and Gnome are compatible, but what about Awesome, and is there a guide like for Xmonad?

---

### Post by mbsullivan on 2008-11-21
I know this was an older post, but it seems nobody else had any bright ideas, so I'll give my (admittedly poor) input.

Strictly speaking, of course it is possible to run awesome under Gnome... simply replace Metacity with Awesome. If you're careful, you could probably follow the XMonad instructions (replacing XMonad with Awesome, of course).

However, that being said, to the best of my knowledge, there is no **real** support for Awesome WM under Gnome, so you may get some odd issues (gaps between windows, top of windows cut off, bad support for snapshot, applet that shows different workstations doesn't work with Awesome, etc). So, while it "works", it's not a real practical situation.

To be honest, I'm not a dev of either WM, so I could be wrong... but I used to use Awesome and currently use Xmonad (under Gnome, actually), and I don't ever remember seeing anybody running Awesome in a different DE.

If you want to try it out for yourself (without making any permanent changes), just boot into Gnome, open a terminal, and type:

```
sudo killall -9 -r metacity && awesome 
```

If you want a fully featured tiling WM under Gnome, why not use XMonad? You should be able to emulate any of the keybinds/tagging behavior of Awesome with little effort. The only real advantage I've found with Awesome is it's support for Conky-like eyecandy, but so long as you're using Gnome as a DE that really shouldn't matter.

Mike

---

