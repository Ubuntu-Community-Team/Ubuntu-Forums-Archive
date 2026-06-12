---
title: "Ubuntu Noob: No Sound In KDE At All"
date: 2010-05-18
forum: Desktop Environments
---

### Post by curtisjwong on 2010-05-18
I'm pretty new at this stuff.  Anyway I'm running Ubuntu 10.04 and I  just installed the kubuntu-desktop plasma program and ran it.   Everything works perfectly except the sound.  I tried the suggestion of  going to "multimedia>audio output" and setting pulseaudio at the top  of the list but I'm still not hearing anything.  Oddly when I test "HDA  Intel (AD198x Analog)" it will occasionally successfully play a test  sound but when I set it to the top of the list yet again nothing  happens.  Any advice on what I can do?

---

### Post by Zorael on 2010-05-18
Pop up the sound mixer (KMix, or alsamixer in a terminal) and make sure volume channels aren't muted or at 0%. You may have several that all affect output (like Master, PCM and Front), which would all need to be at greater than 0% for sound to output.

PulseAudio silences them and imposes its own single volume slider instead, and they remain muted even when pulse isn't running.

To play a continuous test sound, enter this in a terminal.
```
$ speaker-test -twav -c2
```
(Ctrl+C to break the loop.)

---

### Post by curtisjwong on 2010-05-18
Thanks for the quick reply.  I opened kmix and unmuted pcm and raised the sliders on everything to maximum.  I can hear background fuzz but the sound still doesn't work at all.

---

### Post by Zorael on 2010-05-18
Even from the speaker-test command?

Is PulseAudio running when you're attempting this? Ctrl+Esc to open up a list of processes, do a textual search for 'pulse'.

Do you get the same behavior even if you specify a device?
```
$ speaker-test -twav -c2 -Dhw
$ speaker-test -twav -c2 -Ddefault
```

---

### Post by curtisjwong on 2010-05-18
Pulseaudio is running.

I got sound when I tried 

speaker-test -twav -c2 -Dhw

but the other one didn't work.  I tried installing mp3 codecs and stuff after Amarok prompted me to and the sound still doesn't work.  Rhythmbox and youtube and any video file played on vlc also don't produce any sound

---

### Post by dabl on 2010-05-18
Try installing pavucontrol and paman, then Alt-F2 "pavucontrol" to run Pulse Audio volume control.

Take a look at the "sinks" -- your audio channels. Note the tiny "mute" button and make sure it is not depressed. While you have that open, also open KMenu > System Settings > Multimedia and look at the sequence of devices.  Use the "test" button to test each device.  The one that works needs to go to the top of the list.  Working back and forth between pavucontrol and the multimedia device list, you can usually come up with a setup that will work repeatedly.

(of course if your next move is to plug in headphones, .... can't guarantee what happens then.  :) )

---

### Post by curtisjwong on 2010-05-18
It Works!

pavucontrol did the trick.  Thank you so much for all your help guys now I can finally start learning how to use kde.

---

