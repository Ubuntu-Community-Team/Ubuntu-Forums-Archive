---
title: "totem, dvd playback broken"
date: 2006-08-04
forum: Desktop Environments
---

### Post by stairwayoflight on 2006-08-04
hi all,

i have been using ubuntu since 5.10. now i have 6.06, and though i don't play dvds often, totem won't start now. i get that dialog that says "totem quit unexpectedly."

when i insert a dvd, totem starts up, the window reads "DVD Menu" but nothing happens. the window doesn't appear to respond properly when i try to maximize, etc. i had to close it.

in mplayer, the dvd spins up for a couple of minutes, the led is on on the drive. every time after a few minutes it has crashed.

my only guess is that my version of libdvdcss or whatever kills css is buggy or not getting along with my dvd/players.

actually for a second or two i saw some crap on screen. it looked almost normal, kind of like when the ol' nintendo screwed up.

perhaps its my dvd? i have tested one dvd with mplayer, it works perfectly but contains no css encryption. i am upgrading totem to the new one with the gstreamer backend.

---

### Post by kostkon on 2006-08-04
I don't know what causes your problem but I want to let you know that Totem with gstreamer is not suppposed to support DVD menus neither subtitles.

Try Xine (apt-get install gxine), which has the best DVD support of all the players to see if you get the same error.

---

### Post by Jjohn on 2006-08-05
Hi All,
      I have the same problem as stairwayoflight I installed the libdvdcss2 also libreaddvd Installed/uninstalled/reinstalled most of the "dvd" players even reinstalled the dapper os after partioning my home folder to save losing data. Still no play back and lots of dfferent errors. Please if anyone knows. Share the knowledge](*,) 
Regards John

---

### Post by scott_b on 2006-08-05
I was having the exact same problems last night.  I got up this morning and restarted.  Now, everything works fine.  I followed the instructions here [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) .  But again, it only worked after a restart.

---

### Post by cantormath on 2006-08-05
> **scott_b said:**
> I was having the exact same problems last night.  I got up this morning and restarted.  Now, everything works fine.  I followed the instructions here [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) .  But again, it only worked after a restart.

This totally works for me and has alot more then just dvd playback codec...
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

---

### Post by stairwayoflight on 2006-08-05
> **cantormath said:**
> This totally works for me and has alot more then just dvd playback codec...
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

yep, that did it. for some reason synaptic wouldn't let me install totem and totem-xine since i upgraded totem a day or two ago.

totem wouldn't even start!

yes, automatix fixed it. even my junky dvd seems to be playing just fine :-)

---

### Post by asplode on 2006-08-05
Yeah, the very latest Totem is being held back from automatic updates because it only supports totem-gstreamer right now.  Try regressing to v1.4.1

---

### Post by tribaal on 2006-08-10
To fix this issue follow the directions given [here]("http://ubuntuforums.org/showthread.php?t=230002"). It worked for me.

Hope this helps...

- trib'

---

