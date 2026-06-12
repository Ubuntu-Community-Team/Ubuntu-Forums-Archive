---
title: "Beryl: missing minimize, maximize &amp; close buttons"
date: 2007-06-02
forum: Desktop Effects &amp; Customization
---

### Post by kris2pe on 2007-06-02
Yes I already added this to /etc/X11/xorg.conf

Option "AddARGBGLXVisuals" "True"

I need help!!!

---

### Post by silent1643 on 2007-06-02
i had this happen when i used envy to install the latest drivers, i uninstalled those drivers and my menu's came back..

---

### Post by bodhi.zazen on 2007-06-02
:lolflag:

While I have been called "beryl-zazen" by some who know me, we need some additional information here.

First as you are aware Beryl is almost ready for prime time and I would echo the caution that you should expect and accept some bugs :)

Otherwise stay with gnome.

Second, check a few themes. Some themes have no buttons.

Third, sometimes the buttons do seem to disappear. float your mouse along where they should be and them may appear :)

Or maybe not.

In that case, video card, driver (say nvidia version, open source or which driver), monitor, and a copy of your xorg.conf will be helpful.

---

### Post by zero244 on 2007-06-03
I had the missing title bars too.....I added the above line to my xorg and it fixed the problem.
If your getting Freeze Ups.....try disabling the crash handler pluggin...........I think it was the culprit to freezing me solid.

---

### Post by kris2pe on 2007-06-03
Got mine working already!!! 
goto selection window manager & then select beryl!!!

---

### Post by brainformat on 2007-06-03
i have the same problem
i have kubuntu 7.04 and beryl works just fine. exept the problem with title bar.

help pls

---

### Post by chronic88 on 2007-06-06
open the beryl settings manager and select "visual effects"
make sure that the window decoration option on the left side is selected (check marked)
I've also got "mipmap" selected under the main tab in window decoration, if that means anything/helps

that's how I got mine working anyways (after editing xorg.conf as well)

---

### Post by brainformat on 2007-06-06
it is checked....

---

### Post by MonkeyZiggurat on 2007-08-19
I'm having the same problem. It's not just the close/minimize etc. buttons that are gone, it's the entire top bar above each window and the borders as well.

I added the following lines to the "devices" section of my xorg.conf file:

Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True"

.....No change.

I'm using ubuntu 7.04 feisty fawn, with an nVidia 7800 GS.

Any help with this would be greatly appreciated.

---

### Post by Beaster on 2007-10-08
do we have any news on this?Still not having buttons..

---

### Post by adza on 2007-10-09
**bump**

---

