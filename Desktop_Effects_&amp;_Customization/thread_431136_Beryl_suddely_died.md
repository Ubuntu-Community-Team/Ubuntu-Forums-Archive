---
title: "Beryl suddely died :/"
date: 2007-05-02
forum: Desktop Effects &amp; Customization
---

### Post by forsaken_pariah on 2007-05-02
This is a really interesting problem... 

For about a week I've had a problem with Firefox crashing about three out of ten times I tried to type in the little search box at the top. But usually it just freezes for a second and closes and I can just reopen it and try again. But this time it wasn't so simple.... I opened Firefox and started typing in the search box and it made X freeze altogether. With nothing left to try, I pressed ctrl+alt+esc to restart X and it came back up in 640x480 resolution. I soon discovered that it erased everything in the "Modes" line of the screen section in xorg.conf except 640x480@60Hz. I changed this and restarted X and everything worked fine except Beryl. I still can't figure out why it doesn't work. The desktop cube works just fine but I'm not getting any window decorations anymore. I can tell it to use KWin and it works just fine but when I use the Beryl window manager I get nothing, not even with aquamarine.


Any help would be very greatly appreciated...



Kory X.

---

### Post by forsaken_pariah on 2007-05-02
Never mind. I fixed it. It seems it also deleted the "AddARGBGLXVisuals" part too. But I'd still like to know how Firefox could possibly cause a problem this severe....

---

