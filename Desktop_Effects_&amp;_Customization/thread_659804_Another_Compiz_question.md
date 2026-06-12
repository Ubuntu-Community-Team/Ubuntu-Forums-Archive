---
title: "Another Compiz question"
date: 2008-01-06
forum: Desktop Effects &amp; Customization
---

### Post by ferus on 2008-01-06
Hi, 

please don't hate me but I have to ask this question. I read through other posts on this topic but some of them are very confusing or irrelevant.

I installed Compiz-Fusion on my Kubuntu 7.10. The installation went OK (as far as I can tell) but anytime I start Compiz it only works partially.
I get the new animations when minimizing/maximizing/closing windows, I have the Super+E (I can't remember the name of this effect) working, also alt+tab is giving me a different animation that it used to..
However, I don't have the cube desktop or painting fire and other effects
In addition, I cannot start ccsm - when I try to start it it seems like it's working but nothing happens.

I have a nVidia 8800 card and the latest drivers (nvidia x.org driver ('new driver') installed.

Can anyone help me with this? I would really appreciate any suggestions.
Thanks in advance.

PS: I did post my question also on kubuntuforum but I didn't receive any answer there.

---

### Post by rune0077 on 2008-01-07
ccsm is not preinstalled, so you need to install it first (but I assume you have done that). Maybe try reinstalling it.

You need to be able to open the ccsm manager to activate the desktop cube and the fire-thingy. In Gnome you can alternative open Apperances and access the Advanced Desktop Settings there - I'm sure there's something similar in KDE but I wouldn't know the name of it.

---

### Post by Princey on 2008-01-07
Try pasting this > sudo apt-get install compiz compizconfig-settings-manager  in the terminal and when it's done, try typing ccsm after pressing ALT + F2 again. That did the trick for me.

---

