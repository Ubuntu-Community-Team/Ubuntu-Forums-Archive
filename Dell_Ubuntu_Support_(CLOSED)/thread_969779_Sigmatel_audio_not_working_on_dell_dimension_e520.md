---
title: "Sigmatel audio not working on dell dimension e520"
date: 2008-11-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by deathsshadow77 on 2008-11-03
I have installed ubuntu 8.10 on a dimension e520 and everything works except the audio.
The name of the card according to the mixer is a sigmatel STAC9227. If anyone has any info on how to get this card to work I would greatly appreciate it.

---

### Post by deathsshadow77 on 2008-11-04
bump

---

### Post by deathsshadow77 on 2008-11-05
bump again

---

### Post by WiFi Ed on 2008-11-05
I don't have any definite answers for you, the audio on my E520 is working fine in 8.10. When I rightclick on the speaker icon and choose Preferences this is what I have.

---

### Post by ianhowells on 2009-01-23
Sorry for the bump of an old thread, but I'm having this exact issue. My preferences window looks just like the image WiFi Ed had posted.

I would *greatly* appreciate any ideas

---

### Post by ianhowells on 2009-01-26
Hah - I feel incredibly stupid. 

For anyone else having issues with a Dell Dimension E520 and sound in ubuntu, my solution was incredibly simple - hopefully you missed this as well.

I had my speakers plugged into my sound card, which is not supported by ALSA. All I had to do was unplug from my unsupported sound card, and plug into the on-board sound instead. ](*,)

---

### Post by sumit.kalra999 on 2009-01-27
Hi,
i also faced same kind of problem with my Sigmatel sound drivers, but after performing the hardware testing,  sound came back with its 75% of its maximum level

just perform "Hardware testing"

---

### Post by stevetor on 2009-01-27
So hey...I'm the new guy here.
and not very savy, I'm afraid.  Running windows xp...lame I know.

anyhow, I'm having this same issue and i'm stumped.  I have re-installed the drivers, gone through all the settings...nothing's working.  even tried sigma tel website...can't get it to load  (?curious?)
any help?

how do I do the hardware testing?

please / thanks!

p.s  i have ubuntu 8.10 recently installed on my system, but can't run it, as my bluetooth keyboard/mouse won't recognize...

---

