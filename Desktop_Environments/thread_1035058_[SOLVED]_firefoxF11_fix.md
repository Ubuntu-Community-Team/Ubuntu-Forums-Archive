---
title: "[SOLVED] firefox/F11 fix"
date: 2009-01-09
forum: Desktop Environments
---

### Post by jesse c on 2009-01-09
Forum help showed me that hitting f11 twice would restore the size of my firefox page so that it would not obscure my top task bar-the apps/place/sys bar.This works but there must be a more permanent solution so i dont have to do it every log in,and what is the f11 key anyway ?

---

### Post by adamlau on 2009-01-09
F11 = Fullscreen :) .

---

### Post by keithld on 2009-01-09
I had that happen to me only once after wtaching a 2-hour movie on HULU Full Screen, it also changed my theme...

What I did was open a terminal and run: firefox --safe-mode then surf around a bit and maybe make a few changes to your settings, then change them back and exit...  Now run Firefox in regular mode and see if it clears it up...

I think in my case a Preference file got corrupted...

---

### Post by jesse c on 2009-01-09
thanks for replies.Keithld i got the f11 cue from you a few days ago and i tried the safe mode thing that day and again today but no change.The problem seems to be firefox specific because other web browsers are ok.Oh and for my knowledge and future forum questions what is the correct term for that top bar (apps/place/sys etc.)?

---

### Post by Ludachrispeed on 2009-01-09
I'm not sure if this answers your question, but I think I had a similar problem which  was answered here: [http://ubuntuforums.org/showthread.php?t=1011999]("http://ubuntuforums.org/showthread.php?t=1011999")

The ansewr was:
> System->Preferences->CompizConfig_Settings_Manager->Utility->Workarounds->uncheck_Legacy_FullScreen_Support

---

### Post by jesse c on 2009-01-09
Thank you. The compiz settings route seems to have been the solution.

---

