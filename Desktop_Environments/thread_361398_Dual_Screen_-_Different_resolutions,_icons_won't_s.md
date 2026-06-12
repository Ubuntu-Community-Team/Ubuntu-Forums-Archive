---
title: "Dual Screen - Different resolutions, icons won't stay"
date: 2007-02-14
forum: Desktop Environments
---

### Post by jonty-comp on 2007-02-14
I just managed to set up dual X screens on my nVidia GF6200, and for the most part, it works OK.  The DVI port has my main 19" LCD attached to it running at 1280x1024 and the VGA port has my old CRT running at 1024x768.  The CRT is to the right of the LCD, and it configured in xorg.conf as such.
I've got a few little problems with this though:
[LIST]
[*]The primary screen appears to be the CRT, and no amount of fiddling with the ServerLayout in xorg.conf seems to change that.
[*]The icons on the LCD screen's Desktop seem to be bound to a 1024x768 area, if I try and drag them outside this area they just snap back in.  However, everything else utilizes the 1280x1024 area normally.
[/LIST]

Are there workarounds for these things? I think I can get used to the mouse being to the right of me whenever I turn my PC on eventually, but the icon thing is quite annoying.

Thanks in advance,
Jonty

P.S. I attach my xorg.conf

---

### Post by jonty-comp on 2007-02-15
I recently found out that the nvidia driver considers the VGA output as the primary and the DVI as secondary by default, for legacy or something I guess.  Does this mean it's hard-coded in or something?

I haven't had any progress with the bound-up icons. :(

---

### Post by veloce on 2007-02-15
Now that's a nice tidy xorg.conf file!

Are you using twinview?  I can't see any references to it in the xorg.conf file but you are using nvidia card.

I use xinerama so my help may not be much use.  However, a couple of things:

[LIST]
[*]The i810 driver for Intel graphics has the command Option "FlipPrimary" "boolean" check the nvidia man page for something similar.

[*]Gnome remembers some settings that kills things!  Try deleting the ~/.gconf/desktop/gnome/screen folder and reboot. Before I did this, I couldn't drag items to certain bits of the screen.
[/LIST]

---

### Post by jonty-comp on 2007-02-15
> **veloce said:**
> Now that's a nice tidy xorg.conf file!
Thanks!  I like to keep things organised, then I can find things easier. :p 

> Are you using twinview?  I can't see any references to it in the xorg.conf file but you are using nvidia card.
No, I have two separate X screens, although I might try TwinView. ;)

> [LIST]
[*]The i810 driver for Intel graphics has the command Option "FlipPrimary" "boolean" check the nvidia man page for something similar.

[*]Gnome remembers some settings that kills things!  Try deleting the ~/.gconf/desktop/gnome/screen folder and reboot. Before I did this, I couldn't drag items to certain bits of the screen.
[/LIST]
Thanks, I'll check on both these things and report back on whether they fix anything! :D

EDIT: Apparently there's no option like that, and I can't find a screen folder in that path. :(

---

