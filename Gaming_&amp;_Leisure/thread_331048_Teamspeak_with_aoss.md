---
title: "Teamspeak with aoss"
date: 2007-01-04
forum: Gaming &amp; Leisure
---

### Post by radiation on 2007-01-04
Hi all,

I have a problem with using Teamspeak with aoss (in conjunction with World of Warcraft under wine.)

I have no problem with sound in wow. And I use it with the alsa-oss wrapper "aoss".

When I start TeamSpeak with the regular script, and thereby running it by oss, there is no problem. I can connect to servers and both hear and talk.

Then I thought that it would be nice to both play and talk with people at the same time, i therefore started up TeamSpeak with the "aoss". The problem is that both the speakers and the headphones becomes muted. I can connect to a server but neither hear or talk. (regardless if any other program using sound is running).

I don't use artsd.

The sound card is a Audigy 2 SE, and i'm running Ubuntu Edgy.

I have found many other people, across the web, having the same problem, but I haven't been able to find a soulution. And the WoW+TeamSpeak-HowTo at linux gaming isn't helping either.

All ideas are appriciated. Is there any alternative to the official TeamSpeak client?

Best Regards and thanks in advance

---

### Post by Sammi on 2007-01-04
You can take a look through the "voice chat" section of our community WoW with Wine howto:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Remember to also run WoW with aoss.

---

### Post by radiation on 2007-01-04
I used that excellent guide to get wow up and running. And im using aoss when starting wow.

The problem is that regarless of other programs, Teamspeak's mic and headphones are muted when starting teamspeak with aoss.

Going to try to purge all alsa packages when i get home and the reinstall them.

---

### Post by willskills on 2007-01-04
Having the same problem mate, although am using my onboard soundcard on a gigabyte mobo... I have also tried with my USB with headset
 no joy! :/

radiation - keep us posted!!

---

### Post by Sammi on 2007-01-04
Ok. This problem seems more soundcard related than game related. You should try another suppord room, like [Hardware & Laptops]("http://www.ubuntuforums.org/forumdisplay.php?f=135") or [General Help]("http://www.ubuntuforums.org/forumdisplay.php?f=131").

---

### Post by radiation on 2007-01-06
Unfortunately, I think Sammi is quite right.

I have ordered a new soundcard, I will keep you informed about the progress when it arrives.

Have a nice weekend

---

### Post by radiation on 2007-01-06
So i Installed my new Hercules Muse, and reinstalled the alsa-base and alsa-utils. And everything is working wonderfully.](*,)

---

### Post by Slalomsk8er on 2007-02-20
Well I have the same problem (symptom) but I think it is not a soundcard problem but a 64bit thing, as I get an error from ld.so :( 

```

$ LD_LIBRARY_PATH="/opt/TeamSpeak2RC2:$LD_LIBRARY_PATH" aoss /opt/TeamSpeak2RC2/TeamSpeak.bin
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
```

On 32bit systems I never had any problems with TS2 after I figured out that I need dmix AND dsnoop enabled on cards with drivers that don't handle hardware mixing.

---

### Post by vinboy on 2007-02-25
I have the same problem, aoss doesn't work on my Counter Strike game.

if I want to buy a soundcard, what should I look for?

---

### Post by Sammi on 2007-02-25
> **vinboy said:**
> I have the same problem, aoss doesn't work on my Counter Strike game.

if I want to buy a soundcard, what should I look for?
Go to your local computer store and see what soundcards they have, then find out how well they work with Ubuntu here:
[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards)

This also a good reference site: 
[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

---

### Post by specs10 on 2007-03-16
Sorry to post in what appears to be a dead-ish thread, but I have a hard time believing that it's a hardware issue.

I'm having the same problem as radiation had.  However, for me at least, Teamspeak is the only program that gets messed up using aoss.  I managed to unmute the microphone and speakers by launching Teamspeak without aoss, and Teamspeak runs perfectly fine without aoss.  But when I launch it with aoss again, there's no playback and it won't pick up my microphone.

But the reason I don't think it's a hardware issue is that I tried running skype simultaneously with WoW using aoss and I had no issues at all with my sound.  (I have a Soundblaster Audigy2 Gamer.)

Has anyone already submitted a bug report for this?

---

