---
title: "Suddenly no sound"
date: 2006-07-16
forum: Desktop Environments
---

### Post by ahlt on 2006-07-16
I've been using Ubuntu 6.06 since the official release, and I have never had any troubles with the sound driver. Everything just worked at once.

But for a couple of days ago, my sound just ran away ;p
There was no sign of life from my speakers. I didn't know what to do, so in panic I formated my ubuntu hardrive and installed Kubuntu 6.06. 
And everything worked again. I could once again hear sound from my speakers.

But then, after installing several applications and codecs with Automatix, the sound dissapeard again.

I do not think the solution is to reinstall ubuntu everytime this happens.
So do anyone got any ideas what might be wrong?

Thank you

---

### Post by jordilin on 2006-07-16
run alsamixer in the command line and check all the channels, just to see if there's no one muted.

---

### Post by ahlt on 2006-07-20
no, that didn't work.
I've also reinstalled alsa-base and linux-sound-base with no result...

---

### Post by mikemn84 on 2006-07-20
I was having a similar problem and alsamixer worked for me.  I had to arrow over all the way to the right and press M to active the external channel, which for some reason had been shutoff.   Thanks.

---

### Post by meastp on 2006-07-20
alsamixer -> DAC worked for me.

---

### Post by ndrake on 2006-07-20
I'm also having this problem.  Sound worked great initially, then after an update (not sure exactly when) sound stopped working.

I've made sure everything is unmuted with alsamixer.  "aplay -l" lists my sound card.

Not sure what else could be wrong.

---

