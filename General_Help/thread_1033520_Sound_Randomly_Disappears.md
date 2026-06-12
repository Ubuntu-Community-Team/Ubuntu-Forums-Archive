---
title: "Sound Randomly Disappears"
date: 2009-01-07
forum: General Help
---

### Post by bc90021 on 2009-01-07
Hi,

I'm having an issue with sound in 8.10.  If I start the machine from the powered-off state and log in, I have sound.  It'll work in all capacities (movies, music, internet) for a few days, and then I'll come back to the machine after being at work and it will not work in any capacity.

A reboot fixes the problem.  However, since this is not Windows, I am not keen to be rebooting my Linux box every few days so that I can have sound.

When I go to System | Preferences | Sound, and test the sound instances, I get the error that's attached in the screenshot. (gconfAudio sink: failedto connect: connection refused)

Does anyone have any idea of what's going on and how I can fix it?  Restarting PulseAudio and/or ALSA has no effect whatsoever.

Thanks.

---

### Post by bc90021 on 2009-01-08
I don't think I can mark this as solved, but there is a workaround...

I have to kill -9 any process that contains "gconf" and "audio" in it.
Then I have to kill all web browsers* that are open.
Then I have to restart alsa-utils.
Then I have to restart pulseaudio.

Once I do all that, audio works in all capacities again.

However, this royally sucks.  There is something seriously wrong with sound in 8.10 in my experience.



* This process didn't work until I killed Epiphany as well as Firefox.  Very strange.

---

### Post by bc90021 on 2009-02-22
Bump... anyone?

---

