---
title: "Mouse Scrolling Lines"
date: 2009-03-05
forum: General Help
---

### Post by joeyknuccione on 2009-03-05
So I'm getting a handle on the mouse deal, here's my xorg.conf:

Identifier "Mouse0"
Driver     "mouse"
Option     "Protocol" "auto"
Option     "Device"   "/dev/psaux"
Option     "Emulate3Buttons" "no"
Option     "ZaxisMapping"  "4 5"

So, do I add another option, or do I adjust one of the ZaxisMapping numbers? I'm too noob and too scared to experiment myself. 'Preciate any help.

---

### Post by NT4usB on 2009-03-05
Scrolling in terminal, Open Office, Firefox, or ??? 
Lemme guess, all of the above.
Only one I've figured out is Firefox.
about:config in the location bar
Search for mousewheel.withnokey
Can't recall if I changed action but numlines was 25, iirc. You can open another tab and switch back and forth to see what changes when you tweak action and numlines.

ZaxisMapping is direction. 4 is up and 5 is down (or 5 us up and 4 is down... or something.) 
Doesn't control how much it scrolls, only which way.

---

