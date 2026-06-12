---
title: "VBA Express 1.2 beta emulation too fast."
date: 2010-04-15
forum: Gaming &amp; Leisure
---

### Post by meanburrito920 on 2010-04-15
After upgrading to the 10.04 beta, I have found that VBA Express runs at around 200% at the exact same settings I had previously. Under 9.10 it ran normally at 100%. 

In a previous thread, I found that someone solved this issue by turning up the quality on the sound. This solution did not work for me. 

My VBA Express version is 1.2, and my VisualBoyAdvance version is 1.8. 

I also can confirm that the version of VBA Express did not change between 9.10 and 10.04. VisualBoyAdvance also did not change over this time period. The problem also occurs using the VisualBoyAdvance GTK+ interface.

---

### Post by dominus_sapiens on 2010-05-06
I can confirm this: this problem affected me on my upgrade to 10.04 also.

All I have been able to do so far, after lengthy searching, is what is described here:

[http://ubuntuforums.org/showthread.php?t=299206](http://ubuntuforums.org/showthread.php?t=299206)

In effect, all you can do is go to options -> frameskip -> throttle and select "100%".

This makes things run at around the right speed, though the audio will still be ridiculously choppy, and for this I have not found a solution, though boosting the process' priority helps somewhat.

This shall have to do for now...

---

### Post by clicker4721 on 2010-06-16
I tried that, and it worked for slowing the video, but screwed the sound over. I changed the settings to make it better and it still sucks. Also, gvba won't configure to my joypad, unlike VBA Express. It would be much better if one could slow down the express version.

---

### Post by ljg_3 on 2010-08-07
Same here... Tried altering the .cfg, but no luck :') However, thanks for the link [dominus_sapiens]("http://ubuntuforums.org/member.php?u=671766"), the best solution so far! not perfect, but far better than the choppy sound that would have kept me from playing all together :-)

---

### Post by Bhamid on 2010-08-08
The Visualboy Advance packages in the repository are out of date and aren't being developed, so it would be better not to use them.  The best solution I have found is to use [this]("http://sourceforge.net/projects/vbam/files/Win32%20-%20MFC/VisualBoyAdvanceM947.7z/download") through wine.

---

