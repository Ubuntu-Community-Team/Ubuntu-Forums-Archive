---
title: "No Sound"
date: 2006-08-24
forum: Desktop Environments
---

### Post by RexInTheCity on 2006-08-24
I've been running ubuntu full time for over a month now with no problems. I just had the x server update problem and got it fixed. Now my sound isn't working. I checked all the volume settings and they are all the way up, I tried switching speakers and still nothing.

I tried a couple different media players and got a couple errors:
Audacity: There was an error initializing the audio i/o layer. You will not be able to play or record audio. Error: Host error.

Beep Media Player: Couldn't open audio. Please check that: 1. You have the correct output plugin selected. 2. No other programs is blocking the soundcard. 3. Your sound card is configured properly.

MPlayer: Couple not open/initialise audio device -> no sound

Rythmbox just plays the file with no sound.

VLC player just crashes.

Anyone have some ideas?

PS: Won't be able to reply to any posts untill tomorrow evening.

---

### Post by catalasan on 2006-08-24
i have the same problem after updating the x server.  my system is a toshiba m45-s331 running ubuntu 6.06
[IMG]http://ubuntuforums.org/images/smilies/confused.gif[/IMG]

---

### Post by hraposo on 2006-08-24
Try:
sudo alsamixer

---

### Post by MilesDavis on 2006-08-24
Once again, how do you save your alsamixer settings?

---

### Post by MilesDavis on 2006-08-24
Got it!

"sudo alsactl store 0" makes it save i think?

---

### Post by catalasan on 2006-08-24
i tried the steps in the following link and it worked for me.  hope it works for you too.[IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

[http://www.ubuntuforums.org/showthread.php?t=189276]("http://www.ubuntuforums.org/showthread.php?t=189276")

---

### Post by RexInTheCity on 2006-08-24
Thanks for the replies, I tried the suggestions but my sound still isn't working.

---

### Post by avtolle on 2006-08-24
I'm sure there is much more involved than what this tip does, but... in a terminal, type killall esd. (don't type the period) Then return to the desktop and see if anything has changed.

---

### Post by RexInTheCity on 2006-08-26
> **avtolle said:**
> I'm sure there is much more involved than what this tip does, but... in a terminal, type killall esd. (don't type the period) Then return to the desktop and see if anything has changed.

no help

---

### Post by CassioBunana on 2006-08-26
Hi guys...I guess I've the same problem as you! I've tried so many solutions with no success...well for me the problem seems to be applications can't access (write) on the alsa resources but I don't know what this exactly means..

---

### Post by RexInTheCity on 2006-08-26
Well, I just restarted again and my sound is magicly working... but now it sounds distorted when the sound gets to loud.

---

### Post by RexInTheCity on 2006-08-28
bump

---

