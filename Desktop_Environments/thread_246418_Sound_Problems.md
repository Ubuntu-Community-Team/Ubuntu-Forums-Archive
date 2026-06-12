---
title: "Sound Problems"
date: 2006-08-29
forum: Desktop Environments
---

### Post by benclinch on 2006-08-29
Hi,
I would like to be able to use my microphone with Audacity, but every time I launch it says:
"There was an error initializing the audio i/o layer. You will not be able to play or record audio
Error: Host Error"

What does this mean and how can I fix it?

---

### Post by atomkarinca on 2006-08-29
if you have alsa, you may try:

sudo aptitude install aoss
aoss audacity

this may help.

(jeez, i almost forgot) you can also use:

artsdsp audocity

---

### Post by galileon on 2006-09-01
hey, thats usually when you have another program using /dev/dsp ie the old OSS device...best bet is to close all other sound programs, and maybe issue a killall esd in a terminal.

---

