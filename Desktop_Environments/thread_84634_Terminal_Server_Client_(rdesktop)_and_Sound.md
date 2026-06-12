---
title: "Terminal Server Client (rdesktop) and Sound"
date: 2005-10-31
forum: Desktop Environments
---

### Post by rtidd on 2005-10-31
I have a mixed network at work.
Windows 2003 servers and some linux boxes I am switching from RHES to Ubuntu.
My personal workstation is set up for beta testing and everything works reasonably well.

I can connect to my windows servers and it works great EXCEPT that sound does not seem to work.

The rdesktop config shows settings for exporting local (windows) sounds to the linux rdesktop client but this does not seem to work.

Anyone run into (and hopefully solved) this issue yet?

---

### Post by SlowJet on 2005-10-31
I just tried on two pc's with the same sound system and it worked fine.
They are both 5.1 same brand.
It does not work and never has on the other linux box which has a basic sound system.

Keyborads are simular as is video but that is dynamically adjusted.

It stopped playing, like it was hung, but it was the window media asking to be updated to version 10.
Those messages didn't show on the linux screen.
Another setting to send windows movements, etc, I suppose.

Also be sure to use RDPv5 (vs. RDP) on Win XP.

SJ

---

### Post by rtidd on 2005-10-31
Interesting..
My work box is an HP/Compaq with built in sound on the motherboard.
Device manager shows an Intel 82801DB/DBL/DBM (AC'97) Audio controller.
Sound works just fine on the system but not in rdesktop.
I am running ALSA

You said this never worked on stock audio?
What sound system are your two boxes running that work?
Any clue why the standard embedded M/B sound will not work?

---

### Post by SlowJet on 2005-10-31
All I'm saying is that the sound system (sound card, drivers, ability, setup?) has to be either the same or (at least very simular)

The windows box is an intel onboard 6 channel - 3 plugs 5.1
One Linux is the same.
They both have  Creative Inspire T5400 speaker system.

The other linux box has Sound Blaster Live value and basic 2 speakers setup.

I'm using ALSA on both Linux but the settings are way different.
Both are running Ubuntu 5.10 with all the Dapper updates.

That's all I know. :)

SJ

---

### Post by rtidd on 2005-10-31
damn.    well at least I have a better idea of what's up.
the computer hardware is very different between my desktop (ubuntu) and my W2003 server.

Worked ok in Windows->Windows.
Not sure why this should make any difference but thanks for the input.
I'll play with windows drivers to see if I can get it to play nice.

---

