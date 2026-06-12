---
title: "Inspiron 530, Ununtu and LG Flatron W2242S"
date: 2009-04-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Penfold73 on 2009-04-22
Took a while but I finally managed to get my new monitor to work with Ubuntu. It's an LG W2242S.  I needed to edit the /etc/X11/xorg.conf file to add a Modeline to the Section "Monitor" like this:

Section "Monitor"
    Identifier    "W2242S"
    Horizsync    28.0-83.0
    Vertrefresh    56.0-75.0
    Modeline    "1680x1050_60"    147.14    1680 1784 1968 2256    1050 1051 1054 1087 -Hsync +Vsync
    Option        "PreferredMode" "1680x1050_60"
EndSection

It now displays fairly well with a small exception. There is some blurry banding every 10cm or so, such that text is a little fuzzy. I have read that this may be due to Horizontal and Vertical sync rates being slightly off, but I'm not entirely sure how to continue. Does anyone have any suggestions for tweaks to lose the banding?

Many thanks,

P

---

### Post by Penfold73 on 2009-04-24
I eventually solved this issue by adjusting the "Phase" and "Clock" settings on the monitor itself. Blurred bars now gone.

---

