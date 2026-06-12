---
title: "Totem has no volume control"
date: 2006-06-01
forum: Desktop Environments
---

### Post by 12quality on 2006-06-01
Like most of us, I just upgraded to Dapper and am having a problem.

The little speaker near the bottom right of totem doesn't do anything.  It is light grey like it is inactve.  The Sound menu is also inactve.

Anyway, everything else works, including the sound, but I can't control sound from totem.

any ideas?

---

### Post by Rackerz on 2006-06-01
Can you play things using totem? Also have you installed the w32codecs, etc?

---

### Post by 12quality on 2006-06-03
[QUOTE=Rackerz]Can you play things using totem? Also have you installed the w32codecs, etc?[/QUOTE]

Yes, like I said, everything else works fine.  I can play movies, songs, etc., but to control the volume, I have to use the volume control applet/program.  The little speaker icon used to allow me to control the volume from within the program, but is no longer active.

---

### Post by 12quality on 2006-06-04
I went into the configuration editor and under "/apps/totem/", the value for "audio_output_type" had been set at 5, which is invalid.  I changed it to 0 for stereo and it now works.  Maybe a legacy from having upgraded from Hoary-to-Breezy-to-Dapper.

---

