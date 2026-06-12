---
title: "UT2004 black bars in widescreen"
date: 2008-05-03
forum: Gaming &amp; Leisure
---

### Post by WiFlag on 2008-05-03
I have recently installed UT2004 (native linux) and I am running into problems with the displaying the game in widescreen (Samsung SyncMaster 906BW monitor, and a Radeon X800SE graphics card with the proprietary driver)

I have been able to get 1440x900 (my monitor's native resolution) to work by editing ~/.ut2004/System/UT2004.ini, but my computer is showing it's age, and even with the graphical fluff turned down it is still slow, so I want to run it at 800x500. And this is where I hit a problem - all the lower widescreen resolutions display as an especially stretched image with black bars at the top and bottom.

My guess is that UT (which has 800x500 as an option) is showing it in an 800x600 resolution and blacking out 50 pixels above and below. However 1440x900 it did not have as an option, so it just did what I told it.

Has anyone found a way around this, or seen a similar issue?

---

### Post by WiFlag on 2008-05-03
Update - nothing called out in UT2004.ini helps
Every valid 4:3 resolution pops up stretched but with no black bars
Every 16:10 widescreen resolution in the list gives these black bars, with the exception of the 1440x900, which I had to manually put in. 

Any ideas?

---

### Post by WiFlag on 2008-05-09
I ended up just changing my FOV to 108 to compensate for the difference. Quite the hackjob - I'm still all ears if anyone has any ideas.

---

