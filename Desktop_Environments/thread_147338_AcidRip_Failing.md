---
title: "AcidRip Failing"
date: 2006-03-20
forum: Desktop Environments
---

### Post by WamBamBoozle on 2006-03-20
Hi

Totem was complaining that it couldn't read the dvd menu so I thought I'd try EasyUbuntu, which fixed that. But now I can no longer rip DVD's. AcidRip has been my freind. Now it says

[INDENT]...
==========================================================================
Building audio filter chain for 48000Hz/2ch/ac3 -> 0Hz/0ch/??...
Building audio filter chain for 48000Hz/2ch/ac3 -> 48000Hz/2ch/s16le...
[format] Sample format big-endian AC3 not yet supported 
[libaf] Reinitialization did not work, audio filter 'format' returned error code -2
Couldn't find matching filter/ao format!

Exiting...
AcidRip message - Playlist completed
AcidRip message - Mencoder interrupted by user[/INDENT]

---

### Post by WamBamBoozle on 2006-03-21
What should you do? I will tell you: it means that you should select the codec "copy"

What does it mean? It means that the audio format AC3 can't be decoded by AcidRip at present but it isn't a big deal because you can just copy it instead. Ok, I'm not sure what it means but I'm not sure I care anymore.

Incidentally -- the "copy" codec results in the audio being better synchronized.

---

