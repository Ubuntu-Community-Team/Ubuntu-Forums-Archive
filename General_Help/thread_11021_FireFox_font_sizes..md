---
title: "FireFox font sizes."
date: 2005-01-13
forum: General Help
---

### Post by node on 2005-01-13
On my notebook I get a 1024x768 resolution.
When I fire up everyones favourite browser, the fonts are pretty big.
This can be controlled by ctrl+ or ctrl- , however, I'm looking for a way to make my change (2x ctrl-) default.
Can anyone help out ?

---

### Post by wallijonn on 2005-01-13
I had to play around from with FF. Edit -> Preferences -> General -> Fonts & Colours -> 

My config is:
Westsern
Serif 16
Verdana
Verdana 14
monospace
Use My Fonts (checked on).

You would end up working with the size 14 & 16 and increasing or decreasing accordingly.

---

### Post by nocturn on 2005-01-13
You could check if your display resolution and font rendering resolution are in sync.

You get the display resolution in a termianl with:
xdpyinfo |grep -i resolution

It should give something like 75x75 or 100x100.

Then go to the fonts settings in gnome, I think there's an advanced button.
Correct the resoltion there to match the display.
Logout and restart X (CTRL-Backspace).

---

