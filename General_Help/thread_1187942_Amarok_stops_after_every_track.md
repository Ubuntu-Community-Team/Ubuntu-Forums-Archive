---
title: "Amarok stops after every track"
date: 2009-06-15
forum: General Help
---

### Post by tomane on 2009-06-15
Hi all,
Maybe this is some stupid bug (on the user side) but I can't just figure it out. :(
I'm using amarok 2.1 on kde4.2.4 (jaunty kde ppa). I'm stumbled that amarok stops playing after every single track.
Repeat and random are off.
If I check on the playlist, "stop after this track is also disabled"
Dynamic playlist is turned on.

Any clue on what may be going wrong here?

Any hints would be truly appreciated as having to hit "play" at every 3~4 min. is makes amarok unusable for me.

Cheers,
--to

---

### Post by knichel on 2009-06-15
I was experiencing the same behaviour.  A restart of Amarok cleared it up for me.

--
JuJuBee

---

### Post by tomane on 2009-06-15
Yup, it did the trick for me too. I'm still trying to figure out why this happens.
Seems related to the fact that some tracks are deleter during playback, but I couldn't still reproduce it.

Cheers,
--to

---

### Post by DeMus on 2009-06-15
> **tomane said:**
> Yup, it did the trick for me too. I'm still trying to figure out why this happens.
Seems related to the fact that some tracks are deleter during playback, but I couldn't still reproduce it.

Cheers,
--to

I sometimes have the same with Rythmbox but only when I use the CPU for 100% with another program. It does play one song and then stops. Never had that with Banshee, which I use now to avoid this problem.

---

### Post by biodiesel-bri on 2009-11-30
This worked for me, but you'll lose any Amarok configuration you had:

Quit Amarok
Delete the entire directory ~/.kde/share/apps/amarok
Restart Amarok

---

### Post by tomane on 2009-12-01
Well, that was quite some time ago.
Eventually I made a clean install of kubuntu 9.10 amd64, but maintained my /home partition.
In order to get amarok to behave I had to wipe all its data under ~/.kde and it worked.

Cheers,
--to

---

### Post by Qazzian on 2010-08-19
I found that i only needed to remove the amarok config files 

mkdir ~/.kde/share/config/backup
mv ~/.kde/share/config/amarok* ~/.kde/share/config/backup/

---

