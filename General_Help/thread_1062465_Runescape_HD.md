---
title: "Runescape HD"
date: 2009-02-06
forum: General Help
---

### Post by AoA Linux on 2009-02-06
Hey guys, I am new to the forums, I have been using Ubuntu for about 6 months now and I am very very impressed. I am currently using Intrepid Ibex.  I have a question about HD graphics on Runescape if anyone can help.  I have an Intel X3100 graphics card and the HD worked when I had Vista.  Now when I go into HD mode the "game" itself is fine and plays the HD, but the menus and login thing glitches up/distorts.  Does anyone have any experience or advice to help with my problem? 

Thanks

---

### Post by Kezia on 2009-02-06
This can be fixed by right clicking on your desktop and selecting "change desktop backgrounds" , click on visual effects and choose "none".

Cheers from a fellow RSer.

---

### Post by AoA Linux on 2009-02-06
WOW thanks!!  I been trying to figure this out forever.  Nice to see some RSing linux users lol

---

### Post by Kezia on 2009-02-06
> **AoA Linux said:**
> WOW thanks!!  I been trying to figure this out forever.  Nice to see some RSing linux users lol

No worries.. New linux user myself :) The guide on RS forums was actually quite helpful.. just look for "linux" :)

---

### Post by AoA Linux on 2009-02-07
I really appreciate the help with my issue, but does anyone know if it is possible to keep my desktop effects and still play Runescape HD?

Thanks

---

### Post by AoA Linux on 2009-02-07
Just a friendly bump, I am off for the night.  Peace

---

### Post by Githlar on 2009-04-23
I upgraded to Jaunty and for some reason RS HD stopped working (granted I haven't been on in like a week, so it may not have been the Jaunty update that did it).

Anyway, with my crappy Intel i810 graphics I always had problems with RS HD menus and things not displaying correctly. I couldn't even log in because I couldn't see the panel to click my name or anything else. I saw the background, but the foreground objects were invisible. Anyway after a little tinkering on my part I found out that it's Compiz (the program responsible for desktop effects) that caused this behaviour for me. I haven't found a way to have it enabled and use RS HD at the same time yet.

On a side note, I've seen some stuff floating around with people actually modifying their Xorg binary using some sed script to replace all instances of XINERAMA to fix a fullscreen issue. This can be resolved by adding the following to your /etc/X11/xorg.conf:

```

Section "ServerFlags"
  Option "xinerama" "false"
EndSection

```

And then hitting Ctrl+Alt+Backspace to restart X (prior to Jaunty) or logging out and back in.

---

