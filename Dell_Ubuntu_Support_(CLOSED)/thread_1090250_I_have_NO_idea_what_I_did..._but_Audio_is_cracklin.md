---
title: "I have NO idea what I did... but Audio is crackling!! Help!"
date: 2009-03-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gavinfoxx on 2009-03-08
I have NO idea what I changed recently on my dell mini 9... but all of a sudden, the only noise the speakers make are a quiet crackling sound whenever some audio plays.  I'm not using dell's install, I'm using 8.10

*checks*

Okay..

it only happens with some sound options... but I dont think I changed anything about the HDA Alsa, or whatever it is.  Why would that break? How do I switch it back so everything is working? Do I have to switch to a different architecture? what do I choose?  How do I get hda alsa to work again? It seems to be the "main" audio playback thign I have... thanks!

---

### Post by Mr Fat Bat on 2009-03-09
Give this article a go: [http://ubuntuforums.org/showthread.php?t=789578&highlight=streaming+tv](http://ubuntuforums.org/showthread.php?t=789578&highlight=streaming+tv)

Probably Part C :)

---

### Post by gavinfoxx on 2009-03-17
Uhm... I tried to follow that advice but I still seem to be having some trouble.  Could someone maybe help diagnose my specific instance and maybe walk me through some of this stuff? Thanks! Maybe on aim or yahoo or something...?

---

### Post by ashwinhgtx on 2009-03-18
Have you tried disabling the onboard mic?

---

### Post by thomasboleyn on 2009-03-18
> **gavinfoxx said:**
> I have NO idea what I changed recently on my dell mini 9... but all of a sudden, the only noise the speakers make are a quiet crackling sound whenever some audio plays.  I'm not using dell's install, I'm using 8.10

*checks*

Okay..

it only happens with some sound options... but I dont think I changed anything about the HDA Alsa, or whatever it is.  Why would that break? How do I switch it back so everything is working? Do I have to switch to a different architecture? what do I choose?  How do I get hda alsa to work again? It seems to be the "main" audio playback thign I have... thanks!

I recently did a clean install of Xubuntu 8.10 and have been having this problem also. I use a Sony Vaio pcg-k215z. I had the exact same distro version installed before, just messed it up by trying to install xfce 4.6 so had to format and re-install. I'd be interested to know what causes this problem too!

---

### Post by 123456789123456789123456 on 2009-03-18
from one of your earlier replies I assume you read the steps provided in one post of the link.  If installing the upgrade did not work.

Possibility.

Somehow you have gotten the computer to use a differnt driver than it was originaly using, that driver may not and by looks of problem, is not 100% compatable with the sound device.  Causing problems.  Somehow we need to figure out what the original driver used was, and get it back to using it.

dell, has computers shipped with ubuntu.  I would hate to contact dell, but they may know of a more compatable driver.

---

