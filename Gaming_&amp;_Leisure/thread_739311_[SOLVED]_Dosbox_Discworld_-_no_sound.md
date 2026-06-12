---
title: "[SOLVED] Dosbox Discworld - no sound"
date: 2008-03-29
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2008-03-29
Hi,
I installed Discworld on DosBox. There is no sound. Does anyone know how to get the sound to work? 

I have sound in all other dos box games.

:confused:

---

### Post by FranMichaels on 2008-03-29
In the Discworld folder (in DOSBOX) run config.bat. Choose soundblaster 16 or sound blaster compatible for sound and midi. 
Then run discbat. Any sound?

---

### Post by Rytron on 2008-03-30
> **FranMichaels said:**
> In the Discworld folder (in DOSBOX) run config.bat. Choose soundblaster 16 or sound blaster compatible for sound and midi. 
Then run discbat. Any sound?

Hi, I ran config.bat under dosbox. I tried the various soundblaster options (there was no option to exit and save, just esc to exit). No luck.

When you said run 'discbat' did you mean to say discworld?

---

### Post by Rytron on 2008-04-11
I found this solution:

To save and have sound, do like so:
After installing to folder DISCWLD, make a folder titled SAVE
Run Config.bat and configure your sound and audio to Soundblaster Pro if you have it
Open Disc.bat and choose Soundblaster Pro.

The above steps must be done each time prior to playing Discworld on DosBox.

---

