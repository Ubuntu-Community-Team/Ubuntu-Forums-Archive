---
title: "DeVeDe is way slow compared to ConvertXToDVD"
date: 2009-05-20
forum: General Help
---

### Post by Mirge on 2009-05-20
I've google'd around and seen a few other threads regarding this issue, but they all basically said get better hardware or deal with it.

Well, on this exact same computer with the exact same hardware.. ConvertXToDVD would convert a 750MB - 800MB .avi file into a burned DVD in ~45 mins. DeVeDe is going on 2 hours now... and is only 74% complete and says 1/4 on the top progress bar.

Is there a faster alternative to DeVeDe? I tried using ConvertXToDVD in wine (latest trial version of ConvertXToDVD), but it says it can't find a DVD burner.

---

### Post by Mirge on 2009-05-20
From DeVeDe's website:

DeVeDe is very slow compared to Mencoder alone!

By default, Mencoder uses fast options, but DeVeDe uses high quality options.
If you want speed, just go to the tab Quality options (in the
Advanced options section) and there disable Trellis and choose Use MBCMP. Now DeVeDe
should be as fast as Mencoder with default options.


---


So out of curiousity, I tried it using the exact same video file... the one I was complaining about was at 93% and had been at 93% for a few minutes. I used the above suggestion, and in addition checked the box that said: "Use optimizations for multicore CPUs"... before it got to 94%, the new one was already at 3%. It just reached 95%... and the 2nd one is at 6% before it made it to 95%. I can only "guesstimate" that it's about 3x faster now using the method explained above.


Hope it helps someone else experiencing the same issue.

---

### Post by Miljet on 2009-05-20
Thanks for sharing. That is "nice to know" information.

---

### Post by Mirge on 2009-05-22
Follow-up: Don't know if it was DeVeDe's ISO that was created, or K3B (never had issues with K3B before)... but the audio was out of sync with the video. I ended up using ConvertXToDVD with Wine, and it created an ISO just fine... 40 mins roughly. Burned with K3b and watched the video in my DVD player without any issues. I'm going to stick with that method, especially since I actually purchased ConvertXToDVD.

---

### Post by rulet on 2009-06-23
So have you succesfully installed ConvertXtoDVD 3 on Wine?

---

### Post by digger95 on 2009-07-01
Rulet, 

I use ConvertXtoDVD 3 with WINE.  It installs without a hitch and produces exactly the same quality output as it does under Windows.  On my system there are two options unavailable when running it under WINE in Linux:

1.  There's no video preview.
2.  It doesn't find a DVD burner.

Both of these are non-issues for me because I never have the preview up while encoding (hogs resources) and I never burn straight to DVD because I like to check the output first.

I did give DeVeDe a good try because I wanted an open-source alternative, but the quality wasn't as good and it would never produce a DVD larger than 1.6 GB.

Dig

---

