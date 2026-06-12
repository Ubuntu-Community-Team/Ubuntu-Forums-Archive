---
title: "white screen of death :("
date: 2009-03-11
forum: General Help
---

### Post by sandyd on 2009-03-11
i just got KDE 4.2 installed on Intrepid for a trial run and the only thing i got when i logged in was a white screen.

The only i problem is with the white screen. I can press Control + Alt + Delete and get the shutdown/logoff/suspend/hibernate options, but i cannot simply see the desktop. IN fact, ANY apps i start (using krunner, autostart) can be seen, but the desktop can't be seen. kickoff and the task bar are also covered by this weird square.

tried kwin --replace from krunner.
no such luck either.

Compositing is diabled. 

any ideas?

---

### Post by LegendofTom on 2009-03-11
First, push CTRL-ALT-F1 - this will get you to the command line. Now, as root, run dpkg-reconfigure xserver-xorg. This will reconfigure xorg for you, amd should fix that white screen.  (White is still better than Blue.)

---

### Post by sandyd on 2009-03-12
no such luck
 
it doesn't show up in kde-neon, only the normal KDE packages, so there should be a workaround for whatevers wrong with it.

---

