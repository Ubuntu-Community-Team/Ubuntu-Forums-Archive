---
title: "Confused about pulseaudio and alsa mixer"
date: 2009-04-27
forum: General Help
---

### Post by sonicb00m on 2009-04-27
I am running an HDA Intel chipset for my sound using the digital output. It's been a tenuous experience in the past but as since settled down a lot but things are not perfect yet.

The main thing bugging me now is that after a reboot there is never any sound and the culprit is the main sound channel in the gnome alsa mixer being muted.

The only possible way for me to hear sound is to uncheck this mute option and all is good with the world. Now, pulse is definitely being used because I can control the volume within the pulse volume manager. Plus all the usual benefits and signs prove it is running through pulse.

So how can I rectify the problem? I either need to somehow stop also muting the master track or something else.

Lastly, there is no source input for the card. There are always used to be but no it has disappeared. This isn't a big problem because I rarely, if ever, record audio with it...but all the same!

---

### Post by Sam Lars on 2009-04-28
Try running
```
alsactl store
```
when you have it how you want it.

---

### Post by sonicb00m on 2009-04-29
thanks will see if it helps

---

### Post by sonicb00m on 2009-04-30
unfortunately, that didn't help.

The mixer is muted again after reboot.

The volume slider is all the way down though but as soon as i uncheck mute i can hear sound.

---

### Post by sonicb00m on 2009-04-30
I tried this command to see if it was worth putting in a startup script in gnome

amixer set -c 1 Master 70 unmute
amixer: Unable to find simple control 'Master',0


But i just get that error message

---

