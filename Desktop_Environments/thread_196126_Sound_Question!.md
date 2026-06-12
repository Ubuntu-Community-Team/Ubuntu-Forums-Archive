---
title: "Sound Question!"
date: 2006-06-13
forum: Desktop Environments
---

### Post by DimitrisC on 2006-06-13
Well i installed Dapper Drake a few days ago and i think its perfect. I installed everything i wanted and i think with the dapper release i finally found an alternative to wind*ws.

I have a question about sound.  I have a Dell Inspiron 6000 laptop with an onboard sound card (as most laptops).  I use the alsa mixer (at least thats what is says when i use volume control).

My question is how do i enable full duplex?  I can't hear any sound when my sound card is used by another program.  e.g. i can't use skype when i listen to an mp3, i can't play an mp3 when i play a game with sound (frozen-bubble), i can't play an mp3 when i view a streaming video file from the net (metacafe) and a lot more.  I tried all of this in wind*ws and it seems that it can handle multiple sounds just fine.  I am listening to an mp3 right now while listening to an online radio station and can also hear the msn messenger notifications and sounds all together just fine.  When i try that in dapper and gnome i can only use one program with sound at a time.  Most applications either don't work (giving me an error that something is blocking the sound card and cant open device  /dev/dsp or they just work but with no sound).

Is this normal or am i doing something wrong?

Thanks in advance!

---

### Post by BitTorrentBuddha on 2006-06-13
It is normal, this stems from the fact that sound cards can only be used by one source at a time, ESD uses software to mix all audio into one source. Other sound cards have hardware mixing where they mix the sources into one source on the card. In order to fix this you'll probably have to fiddle with ESD, ALSA, and OSS, unfortunately I'm no expert on this :(. Good luck.

---

### Post by toros on 2006-07-26
Were you ever able to fix the full duplex problem?

---

### Post by DimitrisC on 2006-07-26
Well i kind of found a solution.  I try to set up all programms (at least those that support this feature) to use alsa.  Alsa can handle mutliple sounds just fine.  So i set up xmms, gaim, thunderbird and all the other applications that support alsa to use alsa as the default sound server.  Now i can hear the sounds of gaim while listening to mp3s.  I am still having problems with skype though since it doesn't have an option to use alsa (at least thats what i think).

---

