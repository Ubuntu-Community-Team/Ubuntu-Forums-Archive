---
title: "WoW not working in Patch 2.0.12"
date: 2007-04-03
forum: Gaming &amp; Leisure
---

### Post by Galstaff on 2007-04-03
Well, new  WoW patch today, didn't seem like they we're changing much.  I download the patch and go to log on, and my screen freezes, can't alt tab/alt f4 or anything out of it and im forced to restart my computer, any ideas? I tried running WoW Repair and nothing =/

---

### Post by justin whitaker on 2007-04-03
> **Galstaff said:**
> Well, new  WoW patch today, didn't seem like they we're changing much.  I download the patch and go to log on, and my screen freezes, can't alt tab/alt f4 or anything out of it and im forced to restart my computer, any ideas? I tried running WoW Repair and nothing =/

That's not good news. (Crosses fingers and hopes Crossover does well). Did you look to see if there were any workarounds on WineHQ?

---

### Post by Galstaff on 2007-04-03
ill go take a look now

---

### Post by justin whitaker on 2007-04-03
No problems with Crossover.

---

### Post by caedz on 2007-04-03
I am having the same problem...

---

### Post by Mileeta on 2007-04-03
Not that I have anything to add to this discussion, other than "me too!"  I can clarify that I'm one of *them* that uses an ATI gfx card.  The game was working just fine last night at this time, but with the patch I got nothing.

Also, tagged for later.

-M

---

### Post by Drezliok on 2007-04-03
Upgrade went fine for me. I have an Nvidia card though I doubt that makes a large difference.

Did any of you make a backup of your WTF.config? If you did you could see if the patch changed something for you.

---

### Post by sedition on 2007-04-03
I was having some weird problems that I posted in an earlier thread with today's update as well. I seemed to fix my bug (different granted, but it may work for you as well) by changing winecfg to be NT 4.0 and everything cleared up. Also, on a side note, I experienced a lot of glitches everyonce in a while and I discovered that it usually happened after unrelated updates via Synaptic. I reinstalled the updates and this also cleared up the glitches.

---

### Post by Mileeta on 2007-04-03
thanks sedition!  Changing winecfg to NT 4.0 made me a very happy rogue :)

---

### Post by sedition on 2007-04-03
Right on. Glad it helped!

---

### Post by Praill on 2007-04-11
Changing the version to NT 4.0 worked for me as well, to the point that it runs fine; except for the sound.
Im experiencing really chopping sound with alot of static that I did not have prior to this new path and change to NT 4.0.

Has anyone else experienced this sound issue and found a solution?

---

### Post by Praill on 2007-04-11
It wasnt too hard to fix. I changed the sound driver to use EsounD in winecfg and it working perfectly. It will also now play nicely with other applications that want to use the alsa drivers to play sound at the same time. HOORAY!

---

### Post by Ferrat on 2007-04-12
allways update using "NT4" this minimizes the chance of corruption and you don't get the "waiting for files to close" but sometimes the updates corrupts the MPQ files, I got that problem, I could do everything but as soon as I entered Scarelt Monastary the game crashed, trying to log on to that Char resulted in game crash but making a new char worked without problems, I just replaced the corrupted MPQ file and then I could log on to that char again without any problems.

---

### Post by Tantalus90 on 2007-05-15
Thanks , the "waiting for files to close" message had me stumped too 

Any chance of this little tidbit being added to the howto ?

---

