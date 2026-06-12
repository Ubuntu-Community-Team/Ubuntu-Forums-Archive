---
title: "Soundless Diablo 2 expansion?"
date: 2007-05-10
forum: Gaming &amp; Leisure
---

### Post by DiJEH on 2007-05-10
Yesterday I installed Diablo 2 and it worked fine, all sound worked and everything. Then I installed LoD (without any problems) and now all the sound has gone.

Even the sound setting inside D2 are blacked out and I can't do anything with them. So how do I get wine to play nice and give me sound?

---

### Post by lerchedahl on 2007-05-10
You are most likely running it with the "-ns" argument. Check your launcher/loader whatever and remove the "-ns" part if it's actually there.

---

### Post by DiJEH on 2007-05-10
All that's there is -w for windowed.

---

### Post by smutch on 2007-05-12
Have you tried running winecfg and changing the settings under the audio tab to a different Sound Driver? I had the same problem. I was using the OSS driver and I switched it to ALSA Driver and it then worked.

---

