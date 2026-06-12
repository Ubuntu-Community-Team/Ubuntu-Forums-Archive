---
title: "no mix and mix mono in voume control"
date: 2009-05-09
forum: General Help
---

### Post by spacegypsy on 2009-05-09
Simple question;

Why is it that I don't have Mix and Mix Mono in my Volume Control Preferences?

Any ideas?

I have an Intel soundcard.

---

### Post by LexLuthor08 on 2009-05-10
same problem here. Trying to record audio from the desktop. I have no mix under Alsa mixer. 
You might wanna try kmix (but I had no mix switch there either)

---

### Post by LexLuthor08 on 2009-05-10
**[color="red"][size="5"]solved[/size][/color]**

I followed the instructions here from the beginning:
[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

Basically you switch from ALSA to Pulse Audio which is a far better tool anyway (lets you control audio level for each program separately).
Recording every sound on the desktop works now!

---

### Post by spacegypsy on 2009-05-10
Thanks, but still no go for me:(.

I can see all the playback devices in the playback tab but when i try to record a stream with gnome sound recorder or audacity nothing is recorded. I also cannot see those applications in PulseAudio Volume Control.

Weird.

---

### Post by LexLuthor08 on 2009-05-11
> **spacegypsy said:**
> Thanks, but still no go for me:(.

I can see all the playback devices in the playback tab but when i try to record a stream with gnome sound recorder or audacity nothing is recorded. I also cannot see those applications in PulseAudio Volume Control.

Weird.

did you go unter the tab Recording, then right click on the microphone?
If you then chose **Move Stream ->  Monitor of **.... 
it should record the output.

---

### Post by spacegypsy on 2009-05-13
I've been looking over and over it, just don't know..
I redid the install procedure without result.

You're talking about a recording tab in the PulseAudio Volume Control.
But I don't have it:icon_frown:.

Yet, I see that there's some audio going through the PulseAudio Volume Meter (Recording).

---

