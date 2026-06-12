---
title: "WIDESCREEN - Desktop resolution works fine, GDM doesnt"
date: 2007-11-18
forum: Desktop Environments
---

### Post by adieb on 2007-11-18
Hallo,

i am running Gutsy with 22" widescreen plugged into a intel 3100 graphiccard. everything is fine. now (while iam writing) i have a perfect image @ 1680X1050. 
The Grapgiccrad is working fine (Compiz works, etc...)

The Problem is:

1.GDM
The resolution seems to be the same, but the image is shifted to the right.. Or better it just starts at the first third from the left side.  so i can login though the login area is still in the visible part of the image.
After I am logged in it just renews the image (format) and everything is in right place.

2. TOTEM
When I watch a video file an switch to fullscreen i get the same shifted view as seen with the GDM login.
When I switch back this problem remains, so that i have to logout an login again to get a normal view.


What to do?
I tried to dpkg-reconfigure xserver-xorg, I´ve looked into the xorg.conf but the best result i can get is the described.

Maybe a helpful hint:
I plugged in a friends screen, also a 22" Widescreen, same problem, but his screen tried to stretch the image so that its "starts" at the left border...
didn´t look that cool ;-)


if anybody knows this problem or better how to solve it....

---

### Post by blueturtl on 2007-11-18
Hi adieb,

are you using a monitor with a DVI connection or with the old VGA connection?

---

### Post by adieb on 2007-11-19
Ah sorry i forgot to mention that! I am using VGA since my monitor has no DVI... (I wanted to save some money)

---

### Post by blueturtl on 2007-11-19
Since you're using VGA the image can become misplaced not because there's something wrong with the settings on your system but due to the settings of your monitor. You should try fixing the picture with your monitors controls first (horizontal placement, vertical placement, horizontal size, vertical size). There should be a menu on your monitor or dedicated buttons to do this. Once you have adjusted the picture, wait for the monitor to memorize it (some blink a led or something to let you know the settings have been saved) before you change display modes. In the old days (before DVI) monitors had dedicated memory for remembering the positioning of the picture at different resolutions and refreshrates. 

With DVI you don't need to adjust the picture (ever) because the picture is transferred digitally and thus the monitor can automatically place the picture correctly.

---

