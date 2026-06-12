---
title: "Inspiron 8100 - Ubuntu - ESS Maestro 3i record issue"
date: 2007-06-08
forum: Dell  Ubuntu Support
---

### Post by tk471 on 2007-06-08
Hello!  I've been a Debian sarge/etch user for about a year now on an old HP Pavillion 7850, and recently installed Ubuntu Studio (Feisty Fawn 7.04) onto a Dell Inspiron 8100 (Geforce2go 16MB, 1Ghz PIII proc, Maestro ESS 3i sound card, 512MB RAM).  

Ubuntu (and then Ubuntu Studio later on) installed flawlessly, and the only thing that doesn't seem to like to work (and it's the only thing I really wanted to work), is recording audio.   I don't think this is so much an 'Ubuntu' issue as just a driver/Linux kernel item, I've been googling and researching for some time, looking at ALSA driver pages, OSS driver pages, finding older pages of other distros, but nothing seems to say 'this is the fix'.  I have a feeling that with the exception of buying a PCMCIA sound card (and I have to do a little research on that), I might have to put Windows XP back on.  Which really isn't a problem... I'd just rather been able to use Ubuntu, cause I rather like it.

Has anyone else been able to record audio with Linux on an Inspiron 8100 of this nature?  Audio playback is fine.     

Thanks very much for any advice, and thanks to everybody out there who writes all this code for all this stuff!

-Pete

---

### Post by tk471 on 2007-06-09
I think I've sorted it out... between checking 'alsamixer' from command line (enabling the microphone and levels), and tweaking JACK audio a bit, I've managed to sort out the microphone as well as recording internal sounds, and playing back correctly too (using Audacity).  I've got to try the external microphone and line in next, not to mention sort out some issues with JACK (XRUNs, I need to read up on what those are).  I think I'll be able to manage it (and keep Ubuntu Studio installed!).

---

### Post by tk471 on 2007-06-13
Just a final note, we recorded a number of sets last night during practice (nothing fancy, just used Audacity to record rough audio just to track ideas), but no problems.  I'm considering some sort of multi-input card (hammerfall?  I see apps for is installed), but not sure if the Inspiron 8100 is up to the task of multitrack recording.  Anyway it goes, Ubuntu Studio is staying on!

---

