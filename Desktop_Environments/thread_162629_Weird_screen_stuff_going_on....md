---
title: "Weird screen stuff going on..."
date: 2006-04-19
forum: Desktop Environments
---

### Post by DarkED on 2006-04-19
This also happens with Gnome, but it's more fluent in KDE.

First I'll give my laptop's specs:

Averatec 6130HS20 laptop
15.4" WXGA @ 1280x800
ATi Mobility Radeon 9600 64meg (using the fglrx driver from ATi's site)
512meg RAM
Pentium4 w/ HT @ 3000mhz

Okay, what happens is when I logout to the Ubuntu splash/login screen, sometimes it doesn't come up at all. I either get a white screen with a cursor, or a black screen with nothing. I can still hear the sounds, I can even type my user/pass/hit enter to login. It makes it about halfway through the greeter as far as I can tell, then just locks. A reboot and I'm good to go.

Also, the other half of the time I get these weird screen artifacts on logout/reboot. For instance, I'll have red and green garbage all over the screen when it's going through the shutdown sequence. Or, I get this REALLY weird thing where it looks like all the liquid in my LCD is going to the center of the screen, and it looks ... well ... liquidly and glowing :D I can actually SEE this happening, the first time I saw it I thought my LCD had sprung a leak or something. But after reboot, all was well.

Like I said, these problems happen in Gnome and KDE, and they happen alot, so it's obviously not the desktop environment. My ATi card isn't fried and I'm not running hot. It's been so long since I've seen shutdown screen I cant remember what it looks like :D

Any help would be appreciated, I read another post that said something about the power management but after a week or so of searching (on and off) I can't find anything about this problem.

---

### Post by towsonu2003 on 2006-04-19
do these happen when you do ```
sudo dpkg-reconfigure xserver-xorg
``` and choose "vesa" instead of "ati" or "fglrx" (whichever you're using)?

---

### Post by DarkED on 2006-04-19
Yep :(

I also discovered I can recreate the 'liquid' thing by doing a Ctr+Alt+F1 to a real terminal.

Oh Noes, what shall I do? :D

EDIT: It did the liquidy thing in Windows for the first time, and now I'm getting a little worried...

---

### Post by DarkED on 2006-04-21
Sorry for double posting, this DOES NOT happen in vesa! When I checked last time, i reconfigured xorg and forgot to reboot! I ran vesa and logged out / went to a terminal / various stuff and no problems. So, it DOES seem the ATi/fglrx driver is the problem...

Any sugguestions? I'm using the latest ATi driver (8.24.8 I think, from ati.com), and running it as fglrx in xorg.

Thanks again!

---

### Post by l8st-xit on 2006-04-27
I'm not sure if this is going to help or not (Actually I'm pretty sure it isn't) but I have the same problem on an ATI Radeon 8500.  This didn't happen on previous driver versions (or at least I never noticed it) so I'm going to have to downgrade and/or wait for the next version - hopefully those will be better.

---

### Post by cowmix on 2006-04-30
For me (on a Dell E510 with a X300) the 'radeon' driver works great.. the ATI driver suffers from weird screen artifacts.

[QUOTE=towsonu2003]do these happen when you do ```
sudo dpkg-reconfigure xserver-xorg
``` and choose "vesa" instead of "ati" or "fglrx" (whichever you're using)?[/QUOTE]

---

