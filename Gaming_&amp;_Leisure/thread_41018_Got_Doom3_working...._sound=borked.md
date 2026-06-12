---
title: "Got Doom3 working.... sound=borked"
date: 2005-06-11
forum: Gaming &amp; Leisure
---

### Post by Curlydave on 2005-06-11
I just got Doom3 working on Linux. The performance is well, low, as expected, but playable. I'm running at high settings at 1280x1024 (my LCD's native res) with no AA, no AF and I'm getting mostly 20-40 fps, with it going higher in narrow corridors. It's not great, but it's playable.

The sound is really screwed up. It's staticky, crackily and jumbled. Right from the menu sounds to sound in-game, the audio is horribly distorted and messed up; i'ts hard to describe. I don't intend to actcually play Doom3 on Linux as it runs infinitely better in Windows, but I'd still like to know what's wrong. Has anyone else experienced this?

---

### Post by tristan on 2005-06-11
Gday Curlydave

I have doom3 on my ubuntu box. The sound used to work fine, until I upgraded to libesd-alsa as per the ubuntuguide. After this the sound was distored and nasty. Turns out you just need to tell doom3 which sound backend to use.

If you look at the sound settings for doom3 you can select **best, alsa or oss**. You need to select oss (by default it's set to best). The sound should immediately change back to normal.

Hope this helps you.

PS Regarding your gameplay. I assume you're using an Nvidia FX card? Try upgrading to the latest 7664 Nvidia drivers. The immediately give you another couple of fps, and also allow you to overclock the card too, which can give you a 10%. Very smooth!

I have an FX5900XT and it's very playable (45+ fps) in 800x600 high detail.

---

### Post by meldroc on 2005-06-11
Yep.  I also have this problem.  I was able to fix the sound by switching to OSS instead of ALSA.

---

### Post by Krogen on 2005-06-12
I probably can't help you guys but I had it installed in Kanotix and it worked completely fine (sound, too). The framerate was about the same compared to Windows XP.

I didn't use cedega to run it, just the file(s) from id software.

---

### Post by Curlydave on 2005-06-13
Thank you very much, OSS fixed it!

As for the gameplay, I have a top-notch video card, but there's one catch: It's ATI, (x800pro) and therefore blows in Linux. It also won't let me turn on settings eg vsync, AA, AF etc, but those would totally crush my performance.

---

### Post by floyd27 on 2005-10-20
Where is the option to change the sound..
I looked everywhere and cant see anything to change the sound....\
thanx

---

### Post by edm00se on 2005-11-28
[QUOTE=floyd27]Where is the option to change the sound..[/QUOTE]

I've got to go in on this one. I've heard references to associating audio interfaces with specific app's in Ubuntu. I've been using Ubuntu since early-Warty and I have yet to stumble across this feature. If anyone can shed some light on this elusive beast, I'd be very grateful.

edit=
Okay, now that I'm done sounding like a complete n00b, for everyone's reference, you can change the audio settings once the game is loaded from the main menu. You can find it under the system options.

---

