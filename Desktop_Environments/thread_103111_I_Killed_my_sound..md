---
title: "I Killed my sound."
date: 2005-12-13
forum: Desktop Environments
---

### Post by Valhalla on 2005-12-13
I haven't the faintest clue what I did, but my sound just stopped working after I did an update through synaptic.  Poof, everything is gone.  I checked alsamixer, and nothing is muted, esd is running, and gstreamer has esd set as the audio sink, but nothing is working.  Anyone know what went wrong?

---

### Post by stozka on 2005-12-13
welcome to the club,I've also killed my sound, last thing I remember, was modifying startup process.
:(

---

### Post by stozka on 2005-12-13
well, I was without sound for one week(lazy mf), but after reading your post here's my solution:

first I installed

sudo apt-get update
sudo apt-get install sysv-rc-conf

then I messed up

sudo sysv-rc-conf

after running configurator again, I've noticed that alsa was not checked,

after reboot I had to enable PCM also,

apps, sound&video, volume control, PCM

and now, I'm sounded again

:)

---

