---
title: "World of Warcraft: 2 cursors in D3D mode?"
date: 2007-03-22
forum: Gaming &amp; Leisure
---

### Post by zaubara on 2007-03-22
Hey!

Now that I finally got Ubuntu 6.10 up and running, I wanted to use wine to play WoW without Windows.

Because the Direct3D mode has a way better performance than OpenGL for me, I am trying to get that up and running.

Everything works great so far, but I the original white gnome-cursor keeps staying over the "Hand" of WoW... and that's kinda annoying.
I did google for a while, but I was unable to find a usable answer :(

Any ideas?

Thanks!

---

### Post by hikaricore on 2007-03-22
Known issue since ever.  This will almost always happen in D3D mode.

You may want to change your cursor set to something smaller or semi-transparent if this bothers you as this is about your only option.

---

### Post by zaubara on 2007-03-22
Damn, i was hoping there's some kind of magic-bugfix ;)

Is it possible to make the cursor invisible via console? Maybe one could write a un/hide-script then...

BTW: I can't quit WoW like normal, it always crashes so I have to kill the wineserver... is that also a known bug?

Thanks

---

### Post by hikaricore on 2007-03-22
You could probably write a script to change your mouse pointer to nothing and run it as part of a WoW launching script.  Search around for this, I don't have time or I'd help ya.

Personally I only ever have WoW crash when I do something stupid, but it's possible it crashes on exit in d3d mode for some people, mine usually just hangs for about a minute then eventually closes.

---

### Post by kanton on 2007-03-27
Mine started crashing a couple of days ago (while quitting). It has worked (almost) flawlessly until now... Any ideas? I've tried both opengl and d3d.

---

### Post by hikaricore on 2007-03-27
Did you by any chance update wine?

I've noticed a drop in fps and stability between.

[http://wine.budgetdedicated.com/archive/ubuntu/edgy/wine_0.9.33~winehq0~ubuntu~6.10-2_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/edgy/wine_0.9.33~winehq0~ubuntu~6.10-2_i386.deb) (version 2=bad)

and

[http://wine.budgetdedicated.com/archive/ubuntu/edgy/wine_0.9.33~winehq0~ubuntu~6.10-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/edgy/wine_0.9.33~winehq0~ubuntu~6.10-1_i386.deb)  (version 1 = good)

I thought it was just my mind playing tricks on me, or my video card being stupid.

---

