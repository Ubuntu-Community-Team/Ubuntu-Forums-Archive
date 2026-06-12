---
title: "half life 2 choppiness"
date: 2007-08-10
forum: Gaming &amp; Leisure
---

### Post by forrestcupp on 2007-08-10
I have seen that many people are successful in running Half Life 2 in wine, so I thought I would give it a shot.

My specs are Athlon 64 3500+ (running 32 bit ubuntu), 1.5 Gigs RAM, geforce 7600, Audigy 2 Platinum 

First let me say that HL2 runs flawlessly in Windows XP on my system.  I have the latest Wine installed, and I was able to get HL2 installed and running with no problems.

But when I run the game, it's so slow and choppy that it's unplayable.  Also the sound stutters and skips.

Because of how well it runs with all of the settings turned up in Windows, and because of the fact that many others don't have problems, I think there should be a way for it to work for me.

Does anyone have any ideas on how I can get this playable?

---

### Post by Daveth on 2007-08-10
I assume your graphics drivers are up to par? Your specs are fairly similar to mine and it plays well for me, though I will downgrade my wine version from 42 which I have found to be a little flaky.

---

### Post by forrestcupp on 2007-08-11
Yeah, I'm using the latest nvidia binary drivers in Gutsy.  The Gutsy repos have Wine version 42, so I guess I'll have to track down a lower version.

---

### Post by forrestcupp on 2007-08-11
I stopped Compiz and used Metacity, and now it runs smoothly.  It looks nice.

Now I have a different problem, though.  My keyboard doesn't work in the game.  I can look around with my mouse, but the keyboard won't work.  I tried to change the bindings in the options, but it just sat there waiting on a key while I was pressing keys.  It's weird because the keyboard works just fine in Steam.

Any ideas?

---

### Post by forrestcupp on 2007-08-11
If anyone cares, I got it working.  In winecfg, I set everything to Windows XP mode instead of 2000, and I checked the box that says "Allow the window manager to control the windows."

Now everything works perfectly.  It actually runs better than it did in XP.  I guess that's one less reason for me to boot XP.

BTW, I didn't downgrade wine; I'm using version 42.

---

