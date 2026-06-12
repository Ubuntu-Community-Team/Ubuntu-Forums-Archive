---
title: "No sound in savage either..."
date: 2006-09-14
forum: Gaming &amp; Leisure
---

### Post by rokknroll on 2006-09-14
Ive tried all the usual remedies, such as ps au | grep xxx and killing esd (running dapper gnome), etc, even disabling alsa altogether.  alas, still no sound in ET or Savage, UT2k4 works a dream(as it always did), and desktop sound apps run well too(aside from the volume wandering up and down at whill...)
anyone else encountered this or is it likely an issue with my install?
My mobo is Nvidia Nforce2 chipset...

---

### Post by Casey on 2006-09-14
try this in a game:

type in the chatbox
/setsave sound_output alsa

This makes it use ALSA.

/setsave sound_output oss

will bring you back.

You also can't use other apps that play music at the same time (sometimes this works, sometimes it doesn't -- i haven't figured out the cause yet).

---

### Post by rokknroll on 2006-09-17
Thanks, ill try that later today.  fingers crossed, i bought savage when it first came oyt and fell away from it on windows.  Hopefully the spark gets lit again.

---

