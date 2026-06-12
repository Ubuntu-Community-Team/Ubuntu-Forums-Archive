---
title: "[SOLVED] catch up time"
date: 2008-11-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by armandh on 2008-11-13
ONE LINE OF TYPING IS ALL IT TOOK FOR SOUND
see below post #3  DON'T FORGET TO SAVE THE EDIT

desktop effects solved with one line of code in dell ubuntu
see the other post

I have the dell mini (and I have demonstrated to my satisfaction that if I boot 8.04 or 8.10 from an external HDD the enhanced desktop effects will work. they wont on the dell 8.04. however with external HDD and regular 8.04 or 8.10 the sound does not work. I suspect I need a driver.

---

### Post by Rallg on 2008-11-14
Yep. My XP model (with 8.10 installed as dual boot) doesn't have sound working in Ubuntu. Tried various fix-it attempts found elsewhere on this forum, but they didn't work. The closest I got was some Terminal code that seemed to indicate a missing driver. Couldn't find any such driver anywhere.

I'll just wait for a fix. No doubt one exists, since sound does work for the native ubuntu models.

---

### Post by ytsejam1138 on 2008-11-14
In a terminal type:
sudo gedit /etc/modprobe.d/alsa-base

At the end of alsa-base file add:
options snd-hda-intel model=dell

[IMG]http://farm4.static.flickr.com/3219/2948064770_bff5f58e0a.jpg[/IMG]

Reboot your Mini
In a terminal type:
sudo reboot

After logging in, double click the volume icon and turn your speaker volume up.

[IMG]http://farm4.static.flickr.com/3187/2947208861_0c9695e696_o.png[/IMG]

All Credit goes to [www.ubuntumini.com](www.ubuntumini.com)

---

### Post by armandh on 2008-11-15
wow that just works

one short line typed in to the right place is all it took to get sound

---

### Post by armandh on 2008-11-16
bumped so you can easily get the sound from your mini 9

---

### Post by jaavaaguru on 2008-11-30
This fix works fine on my Dell Mini 9 with 8.10 until I put it into standby. Once it comes out of standby, I need to reboot again to get sound working. Does this happen for anyone else?

---

### Post by armandh on 2008-11-30
> **jaavaaguru said:**
> this fix works fine on my dell mini 9 with 8.10 until i put it into standby. Once it comes out of standby, i need to reboot again to get sound working. Does this happen for anyone else?

SAME PROBLEM I have no clue

---

### Post by wolkes on 2008-12-18
Great post....thx so much for the info.:KS:KS:KS:KS:KS

---

### Post by peterwh on 2009-08-01
This worked for me as well, thanks for the tip.:KS

---

