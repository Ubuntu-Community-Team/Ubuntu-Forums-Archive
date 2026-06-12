---
title: "Tower Toppler (aka Nebulus) Crashes on first level"
date: 2011-05-27
forum: Gaming &amp; Leisure
---

### Post by hilz on 2011-05-27
I recently upgraded from 8.04LTS to 10.04LTS. Tower Toppler (AKA Nebulus) was working fine on 8.04LTS. But after the upgrade I can only get as far as the start of the first level. The Sub opens and the character hops out, but when the Sub goes back into the water the game stops. Anyone found a solution?

Edit: I noticed this while searching with Google:
Package: toppler
Version: 1.1.4-2
Severity: important

After upgrade to squeeze toppler has begun to freeze at start of any mission, just after immersion of hero's sub.
Re-installing and deleting didn't help.

Debian Release: 6.0
APT prefers oldstable
APT policy: (500, 'oldstable'), (500, 'testing')
Architecture: i386 (i686)

This is the same fault that I am getting. However the version of toppler with Lucid is 1.1.4-1.

I tried doing as suggested "press numlock or caps lock" when the game starts. But that didn't work.

Is there a way of downgrading to the older version of Toppler? Or will I still have the same problem?

---

### Post by Gh0stDog on 2011-10-07
No solution so far I have the same problem since Karmic Koala and I just try again with Tower Toppler on latest Oneiric Ocelot 11.10 .... same freeze when the level starts.  Turn Capslock On/Off works as a temp fix  ( [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=612127](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=612127) )

You must try different combination of capslock on/off with or without numlock ( one time I had to enable them both than disable them to leave the frozen state ) on the freeze screen itself where the level starts and looks like frozen.

---

