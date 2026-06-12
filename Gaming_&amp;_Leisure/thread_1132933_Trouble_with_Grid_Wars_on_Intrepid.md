---
title: "Trouble with Grid Wars on Intrepid"
date: 2009-04-22
forum: Gaming &amp; Leisure
---

### Post by ollec86 on 2009-04-22
I've been trying to get Grid Wars working on Intrepid, but I'm having a great deal of trouble with it.  I've been using the .deb file from [http://www.getdeb.net/app/GridWars+2]("http://www.getdeb.net/app/GridWars+2") (the 32-bit one) and the installation goes fine.  Every time I try to open it from the Applications menu, though, nothing happens.  When I open up Terminal and type "gridwars", **I get the appstub.linux signal handler 11 error immediately (nothing opens when I do this either).**

From what I've read, others with this error found that it was occuring because they were playing music using Rhythmbox (or some other music-playing software) in the background and that there was an inconsistency between the two programs.  In my case, however, I don't have music players open and Grid Wars 2 doesn't open at all, so I don't have the option of messing with the sound settings.

I love this game and I've been trying to get it working for a couple days now.  Any help would be appreciated.

Thanks,
Ollec

---

### Post by Bölvaður on 2009-04-22
I get a different version of this bug. When I got other programs open that use Alsa (I think gridwars is... oss?) then like 1 minute into the game it crashes. And of course there was never any sound coming from gridwars.

you could try enable only OSS and try again.

---

### Post by ollec86 on 2009-04-22
Only OSS?

What does that mean and how would I do that?

~ Ollec

---

### Post by Vadi on 2009-04-22
OSS is one of the sound systems available in Linux. ALSA is the prominent other one.

Go to system - preferences - sound, and for the playback stuff, try setting it to 'OSS'. I'd try 'PulseAudio' too if it's not already chosen.

---

### Post by ollec86 on 2009-04-22
When I set the sound playback to all OSS or all PulseAudio, I got the same error message.

~ Ollec

---

### Post by Bölvaður on 2009-04-22
what release of ubuntu are you running? I have a hunch...

---

### Post by ollec86 on 2009-04-22
I'm running Ubuntu 8.10.

~ Ollec

---

### Post by jdunn on 2009-04-23
I think that pulseaudio, which runs at a higher layer than ALSA, includes OSS emulation.  However, I've found that any games using PA's OSS emulation (on Intrepid) intermittently crackle, loose sound completely or crash.  The solution I've found works is to pkill pulseaudio.  You can restart the pulseaudio daemon after closing the game...ALSA also has OSS emulation, I think and that's what the OSS game uses when you kill pulseaudio.

---

### Post by ollec86 on 2009-04-23
I've read that killing pulseaudio causes the system to fail when booting.  Wouldn't that cause issues?

~ Ollec

P.S. - I'm still interested in hearing your hunch Bölvaður ^_^

---

### Post by MyR on 2009-04-27
I did not use any .deb

1. install libstdc++5 from the repo
2. download the linux version from [http://gridwars.marune.de/](http://gridwars.marune.de/)
3. extract the files
4. open the game ;]

peace

---

