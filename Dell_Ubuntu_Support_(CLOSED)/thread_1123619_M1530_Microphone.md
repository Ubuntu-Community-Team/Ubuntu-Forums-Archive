---
title: "M1530 Microphone?"
date: 2009-04-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by spongypants23 on 2009-04-12
Is there a way to get the built-in microphones on the XPS M1530 to work?

---

### Post by khelben1979 on 2009-04-12
I don't know, but have you tried all the settings in [alsamixer]("http://en.wikipedia.org/wiki/Alsamixer")? (see wiki link)

In some sound configuration programs such as Kmix, you have the possibility to mute/unmute the sound and this has been a way to fix this problem on other laptops which I have come in contact with.

---

### Post by spongypants23 on 2009-04-12
Alsamixer only shows one mixer each for Playback and Capture, seems to have something to do with PulseAudio.

(See attached screenshot)

I don't have much to mute and unmute.

---

### Post by khelben1979 on 2009-04-12
Hmm... Maybe [the pulse audio IRC]("http://www.pulseaudio.org/wiki/Community#IRC") can answer this, then? (see link)

---

### Post by spongypants23 on 2009-04-12
Solved. I feel stupid now. It was simply choosing "Digital Mic 1" for Digital Input source in the Volume Control panel.

---

