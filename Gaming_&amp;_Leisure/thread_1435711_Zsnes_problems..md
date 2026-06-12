---
title: "Zsnes problems."
date: 2010-03-21
forum: Gaming &amp; Leisure
---

### Post by WayWick on 2010-03-21
Alright my problems where solved.

---

### Post by eksasol on 2010-03-22
To fix the sound issue, open the file zsnesl.cfg is located in the ".zsnes" folder. Or access directly to it by typing in Terminal: [B]gedit .zsnes/zsnesl.cfg
[/B]
Under the Sound section, look for the line: **libAoDriver="sdl"**. Try changing "sdl" to another driver such as "oss" or "alsa".

I have no idea about the issue with full screen, try all the different video options, could be your video card driver. I use windows mode with HQ Filter and Bilinear and it looks great.

As for sound in Wine, go to Configure Wine ->Audio tab, try changing between the drivers (ALSA, OSS, PULSE) and click on the Test button. Also if you have more than two sound cards, you'll need to specify which one will be the main output in Ubuntu's Sound Preferences.

---

### Post by WayWick on 2010-03-22
Alright thanks ill be sure to try those!

---

