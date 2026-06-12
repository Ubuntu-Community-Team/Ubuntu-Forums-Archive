---
title: "Seriously weird X display"
date: 2005-03-12
forum: Desktop Environments
---

### Post by Chuk on 2005-03-12
This is a problem that's followed me through a Debian install, Warty Warthog and now it's still here in the Hoary preview.  (It does NOT happen when I use the Live CD, though, which makes me think it's probably not the hardware -- I also had an older Debian install on the same hardware that worked.)

Basically, once it goes to gdm, the screen just goes crazy, with a giant square (usually white) for the mouse cursor, and the screen filled with dark black static/snow. I'm using an older video card, an S3 Trio 3D/2X, but as I say it worked before. Text mode is fine, even the Hoary install in the FB worked fine. It's just X.

Any suggestions? I've tried dpkg-reconfigure xserver-xfree86 about 30 times, and xf86config about a dozen times (trying different settings), as well as xf86cfg (didn't even display properly). Also, Alt-Ctrl-F# doesn't do anything, and sometimes Alt-Ctrl-+/- changes things, but never fixes them. Alt-Ctrl-Backspace either does nothing or gives me a black screen.

One thing that might be interesting is the fact that it does work with the Live CD. Is there some difference in the hardware detection or X server files that might give me a clue there?

thanks in advance for any help you can give,

---

### Post by valadil on 2005-03-12
Hmmm.  I'm not sure about the Ubuntu live CD, but I know other live cds such as knoppix default to a 2.4 kernel instead of 2.6.  That would potentially explain why your old debian install worked too.

My advice is to try a knoppix cd.  Boot into 2.4 as default and if that works reboot and try 2.6.

---

### Post by Chuk on 2005-03-13
Of course! That's definitely a possibility. Hmm...I like the 2.6 kernel, though. Right now I'm just using the vesa driver, so there's a bit of a performance hit but it does work. Thanks for the suggestion, though.

---

