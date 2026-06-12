---
title: "pulseaudio and dell optiplex gx1"
date: 2009-01-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by adreignsss on 2009-01-10
I have installed all the pulseaudio and its playing but there is no sound coming from speakers.I tried to add  the snd card to ect/modules snd-cs4236, but nothing. Im using 8.10 and tried everything from: [http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578") and from 

[http://ubuntuforums.org/showthread.php?t=997506]("http://ubuntuforums.org/showthread.php?t=997506")

Can anyone help.  Thank you.

---

### Post by kr1z on 2009-01-14
I recently installed 8.04 on a GX1.  Initially I had no sound at all.  Putting snd-cs4236 in /etc/modules (as you've done) gave an audible pop sound during startup, and a sound at login, but nothing afterward.  Subsequently I tried preferences -> sound and got sound for playing CDs, MP3s (but not system sounds for login/logout) by changing settings from "autodetect" to "Alsa mixer" and pushing the test button to see if there was sound after changing the setting.  If 8.10 has a similar mechanism in preferences -> sound you might be able to get some sound, at least.

---

