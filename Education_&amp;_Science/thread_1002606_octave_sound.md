---
title: "octave sound"
date: 2008-12-05
forum: Education &amp; Science
---

### Post by aci016 on 2008-12-05
i use octave for school, anyway i recently installed the sound package through: sudo apt-get install octave-sound, the version of octave installed is 3.0 and the audio package is 1.1.1

i tried playing a sinusoid signal by using: sound(signal)

and i got this message:
sh: ofsndplay: not found

is there anyway to fix this? i really need the sound function to be able to do my homework thanks. :)

---

### Post by jpkotta on 2008-12-13
Install alsa-utils or pulseaudio-utils.  Then put the following in your ~/.octaverc
```
global sound_play_utility = 'aplay';
```
OR
```
global sound_play_utility = 'paplay';
```

---

