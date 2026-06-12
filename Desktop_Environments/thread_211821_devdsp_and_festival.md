---
title: "/dev/dsp and festival"
date: 2006-07-08
forum: Desktop Environments
---

### Post by nkassi on 2006-07-08
I'm trying to use Festival to pull some pranks but everytime I start festival it returns an error saying the it can't open /dev/dsp. I notice that my sound card is map as /dev/audio and I tried making a symbolic link from /dev/dsp to /dev/audio but it did not solve my problem. Also I can't write anything to /dev/audio because it always returns a error saying that the ressource is busy. 

Any thing I can do to fix this.

Nic

---

### Post by Hypatia2 on 2006-07-24
Try using **esddsp **to re-route your audio output to the correct device. It allowed me to install and use several stubborn audio apps:
> echo "Hello." |/usr/bin/esddsp festival --tts
Have you tried espeak for speach synthesis? I'ts a lot simpler and sounds pretty good.

---

### Post by magabriel on 2007-07-29
Seen in a Fedora Community Portal post: [https://fcp.surfsite.org/modules/newbb/viewtopic.php?topic_id=41200&start=0]("https://fcp.surfsite.org/modules/newbb/viewtopic.php?topic_id=41200&start=0") 

> You need to use Alsa output. Put this in your ~/.festivalrc

(Parameter.set 'Audio_Command "aplay -q -c 1 -t raw -f s16 -r $SR $FILE")
(Parameter.set 'Audio_Method 'Audio_Command)

I was desperately looking for a solution when I found this. It worked for me.

---

### Post by everdred on 2007-12-15
> **magabriel said:**
> Seen in a Fedora Community Portal post: [https://fcp.surfsite.org/modules/newbb/viewtopic.php?topic_id=41200&start=0]("https://fcp.surfsite.org/modules/newbb/viewtopic.php?topic_id=41200&start=0") 



I was desperately looking for a solution when I found this. It worked for me.


Works for me too. Thanks for posting!

---

