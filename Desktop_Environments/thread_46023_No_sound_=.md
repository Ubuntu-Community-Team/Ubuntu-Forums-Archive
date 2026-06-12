---
title: "No sound =\"
date: 2005-07-02
forum: Desktop Environments
---

### Post by filemanager on 2005-07-02
I just got a new computer and have installed Ubuntu 5.04 (amd64) on it.

The sound card I ordered with the computer was a:

Creative Sound Blaster Live! 4.1/5.1/6.1/7.1-channel 24-bit (SB0410) (OEM)

But in Device Manager it says it's "Creative SB Audigy LS"

But anyway, main problem: no sound! Of course the Creative website doesn't have any linux drivers, so what do I do?  :neutral:  :???:

---

### Post by filemanager on 2005-07-03
bump

---

### Post by BoyOfDestiny on 2005-07-03
Check all your connections and make sure volume isn't muted. ESD gives me problems, try opening a terminal and type sudo killall esd. If that solves it go to system -> preferences -> sound and uncheck start sound server. If that doesn't do it I guess you need to add the emu10k driver or something (too much of a newbie myself).

Good luck!

---

### Post by t2kburl on 2005-07-03
try the suggestions posted here 


[http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753)


worked for me, but I have onboard ac'97

---

### Post by filemanager on 2005-07-03
[QUOTE=t2kburl]try the suggestions posted here 


[http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753)


worked for me, but I have onboard ac'97[/QUOTE]


I did that and now my Linux OS won't boot!! (I'm using the LiveCD right now). How do I get it to boot?! ](*,)

---

### Post by t2kburl on 2005-07-03
uh oh

not sure how changing sound settings would make it fail to boot

try deleting the /etc/asound.conf file you created since it obviously didn't solve your problem

---

### Post by filemanager on 2005-07-05
[QUOTE=t2kburl]try the suggestions posted here 


[http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753)


worked for me, but I have onboard ac'97[/QUOTE]
 I have onboard ac'97 also, but I also have a Sound Blaster Live! 24-bit card.

I heard that you have to disable the onboard sound for Linux to use the soundblaster. I tried that but it didn't work =\

---

### Post by filemanager on 2005-07-08
[QUOTE=BoyOfDestiny]Check all your connections and make sure volume isn't muted. ESD gives me problems, try opening a terminal and type sudo killall esd. If that solves it go to system -> preferences -> sound and uncheck start sound server. If that doesn't do it I guess you need to add the emu10k driver or something (too much of a newbie myself).

Good luck![/QUOTE]
 Where would I get the emu10k1 driver?

---

### Post by varunus on 2005-07-08
It should come with ALSA.  Try "sudo modprobe snd-emu101k" in a terminal and see if that works.

---

### Post by varunus on 2005-07-11
filemanager, I just found the problem.  Go to [http://www.ubuntuforums.org/showthread.php?t=21211](http://www.ubuntuforums.org/showthread.php?t=21211)

It describes how to install the emu10k1 drivers.  Sorry for the inconvenience.   :-?

---

