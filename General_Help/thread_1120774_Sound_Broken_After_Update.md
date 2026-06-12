---
title: "Sound Broken After Update"
date: 2009-04-09
forum: General Help
---

### Post by joeyknuccione on 2009-04-09
Last night's update broke my sound, how do I fix it?

---

### Post by chriskin on 2009-04-09
which update?
what ubuntu release are you using?
what audio system (alsa? pulse? oss?)

tell as some details please..

---

### Post by joeyknuccione on 2009-04-09
> **chriskin said:**
> which update?
what ubuntu release are you using?
what audio system (alsa? pulse? oss?)

tell as some details please..
Intrepid, latest.
Sound, I'm not sure. How do I know?

---

### Post by chriskin on 2009-04-09
you don't know which ubuntu release you have?
you can find it at system->about ubuntu

also, about the sound system, it's at system->preferences->sound

now about which update you made and screwed up everything, i have no idea , you either checked before giving the ok or not

---

### Post by joeyknuccione on 2009-04-09
> **chriskin said:**
> you don't know which ubuntu release you have?
you can find it at system->about ubuntu

also, about the sound system, it's at system->preferences->sound

now about which update you made and screwed up everything, i have no idea , you either checked before giving the ok or not
System>Preferences> No About Ubuntu listed
System>Preferences>Sound = I can't tell if its Alsa or Pulse Audio. Nothing works.

---

### Post by chriskin on 2009-04-09
1) i wrote "system/about ubuntu, not system/preferences/about ubuntu"

2) all i asked was what is written as default, not what works, obviously since you are asking here, none works. 


how come and you do not know your ubuntu release's name though?

---

### Post by joeyknuccione on 2009-04-09
> **chriskin said:**
> 1) i wrote "system/about ubuntu, not system/preferences/about ubuntu"

2) all i asked was what is written as default, not what works, obviously since you are asking here, none works. 


how come and you do not know your ubuntu release's name though?
Sorry, my noobness is profound.

I'm on Ubuntu 8.10, Intrepid, with the linux kernel updated last night to:

2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux


The sound is set to autodetect, and I can't tell or remember, but it is either Pulse or Alsa. Sorry, noobitis.

---

### Post by chriskin on 2009-04-09
it is most probably alsa that causes the problem 
updating to the last version of alsa will (probably) make every problem disappear

if you do not know how to do this from alsa's site, search the forums for a script that does it for you. i knew one some time ago about it is definitely older than your version 

_i might have to add that if you feel adventurous, jaunty beta's sound is perfect, both alsa and pulse. upgrading is a good option, the one i took since alpha version. _

---

### Post by joeyknuccione on 2009-04-09
> **chriskin said:**
> it is most probably alsa that causes the problem 
updating to the last version of alsa will (probably) make every problem disappear

if you do not know how to do this from alsa's site, search the forums for a script that does it for you. i knew one some time ago about it is definitely older than your version 

_i might have to add that if you feel adventurous, jaunty beta's sound is perfect, both alsa and pulse. upgrading is a good option, the one i took since alpha version. _

Will try, I'll update with results.

And sorry for not saying thank you sooner.

---

### Post by rage9 on 2009-04-09
Same happened to me, you'll have to reinstall your ALSA drivers.

There is a thread here: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

Download the script, unpack it, run it, reboot.  Should do the trick.

---

### Post by chriskin on 2009-04-09
cool, the script i talked about found you by itself

thanks rage9 for taking the job off my shoulders, i was almost about to go searching :P

---

