---
title: "ubuntu audio to low"
date: 2009-05-09
forum: General Help
---

### Post by yon2501 on 2009-05-09
i cant seem to figure out why but for some reason my ubuntu install's audio is way to quiet, to even be able to hear anything i have to have volume up in the 70-80% range any lower and it acts like its muted, by default im using the HDA intel alsa mixer, but ive also tried sigma tel stac9205 oss mixer with the same problem. sigma tel is the same driver i use under the windows partition and it works fine there so i know it isnt a hardware issue, so does anyone know how to boost ubuntu's audio?

EDIT: under hda intel i have pcm and front maxed out as well and i can still only get audio around the 70-80% range.

---

### Post by Hobgoblin on 2009-05-09
This worked for me.

Open volume control.

Select pulseaudio from the dropdown.

Turn it down then back up to full.

Switch back to default device.

---

### Post by yon2501 on 2009-05-09
that seems to have helped a little but i still cant hear anything until its about at 60% now, and i know my speakers are louder then this, on windows with one click up from mute its like what ubuntu is right now around 80%

---

### Post by yon2501 on 2009-05-10
no one knows a way to fix this?

---

