---
title: "Display Problem :S"
date: 2009-05-18
forum: General Help
---

### Post by max4242 on 2009-05-18
Installed ubuntu a few days ago and A wierd thing happens,
Whenever I go to system- preferences- display my screen flickers with a black line across it and completely freezes untill I can try to exit the display window.

This also happens with wine, when I try and run anything the same black line flickers across the screen for a good min or two and then it runs.

I never tryed a native linux game yet so I cant tell you if I get the same thing.

I have a radeon hd 3600 with the ati/amd proprietary FGLRX graphics driver installed.

Anyone else have this? or can help?

anytime I try to change resolution it also flickers and freezes up

---

### Post by Legace on 2009-05-18
Remove the monitor.xml file in ~/.config

Or, alternatively, you can open the monitor.xml file and make sure the values (resolution/refresh rate) are correct.

---

### Post by max4242 on 2009-05-18
I tried this in terminal rm ~/.config/monitor.xml
but it says no such folder

Sorry kinda new

---

### Post by max4242 on 2009-05-18
Bump.
anyone I cant have this happening on my primary PC
Ive searched my entire PC for monitor.xml and theres nothing

---

