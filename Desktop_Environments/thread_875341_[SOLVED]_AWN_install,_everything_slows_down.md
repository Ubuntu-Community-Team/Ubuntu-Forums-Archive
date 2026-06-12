---
title: "[SOLVED] AWN install, everything slows down"
date: 2008-07-30
forum: Desktop Environments
---

### Post by blind0wl on 2008-07-30
Hi,

I installed AWN a couple of days ago and everything was running smoothly, I had to reboot due to enabling my LPT port in BIOS, once Ubuntu came back up the bar for AWN slowly slid to the centre of the screen...and I mean slowly...when mousing over the icons everything is very sluggish.  I checked out 'top' and found Xorg is using 90% CPU constantly.  It's likely due to the 90% CPU that everything is sluggish...anyone have any suggestions on how to rectify?

Cheers

Blindy

---

### Post by blind0wl on 2008-07-30
I checked out what happened when AWN wasnt running...xorg dropped back down to 1% CPU...started AWN...back it went up to 90% usage.  I've read that the recent updates have made xorg go through the roof, but no mention of it being due to AWN...so I'm kinda ruling that out.

---

### Post by blind0wl on 2008-07-30
Its ok.  The slowness occured from me changing the width of my monitor in the AWN config files....as soon as the value went over a certain width, it all became sluggish...by going back to default everything is ok.  AWN doesnt really support dual screens just yet, so the bar sits on my other screen.

Cheers

Blindy

---

