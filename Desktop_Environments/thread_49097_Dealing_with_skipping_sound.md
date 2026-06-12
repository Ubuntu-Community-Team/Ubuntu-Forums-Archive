---
title: "Dealing with skipping sound"
date: 2005-07-15
forum: Desktop Environments
---

### Post by f1dave on 2005-07-15
I figured I might just share my experiences with this problem, one that certainly comes up a bit at linuxquestions.org anyway. Basically, you're in kde, you're listening to music, you have other apps running and bam, your sound starts skipping or playing extra fast.

Now, as far as I know it's a mixer problem, or an ALSA problem, and it seems to affect anyone who doesn't have a decent soundcard like an audigy 2. In my case, i'm using onboard sound on the A7N8X mobo. My problem was encounterd by simply running juk or amarok with amsn, firefox and thunderbird running.

What would happen is the music would skip, and upon stopping, all sounds from amsn that had 'built up' in the previous time period would be played- this could last for a very long time! All I did was turn amsn's sound off, as I figured it would stop building up. So far, so good. It's a bit of a cheat way to fix it though, and i'm interested to know of any real solution much smarter linux users have come up with to fix this annoying bug. 

PS- please don't say buy an audigy :P

---

### Post by TheOtherShoe on 2005-07-15
Have you tried using enlightened sound daemon to fix this? Or is this with ESD?

---

### Post by SWAT on 2005-07-20
Did you try to compile your own version of ALSA (from the newest stable source)? 
I have an audigy 2 and don't have your problems (but I also ain't got aMSN running)

---

