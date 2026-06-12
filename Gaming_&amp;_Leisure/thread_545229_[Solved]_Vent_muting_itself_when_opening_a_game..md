---
title: "[Solved]_Vent muting itself when opening a game."
date: 2007-09-07
forum: Gaming &amp; Leisure
---

### Post by weezerisrock on 2007-09-07
As far as I can tell from searching thru the forums is no one else had the problem with vent that I did.  So I found the fix, and I thought it would be good to document it somewhere.  This way I can find it later if I need it, or someone else may be able to find it useful.

The guide I used to install vent was here: [http://www.eqjunkies.com/?p=125](http://www.eqjunkies.com/?p=125)
from section 6 on.  (I already had wow installed.)  For the ventriloctrl-0.3 I used another guide, I'll have to see if I can find it again and post it here.

When I opened vent I had it working just fine.  I was also able to get the ventriloctrl to work.  However when I would start a game, all of a sudden vent would go quiet.  Other people could hear me but I couldn't hear them.

The fix I found for this for me, was to go hit alt+F2 and at the run prompt run 

```
winecfg
```

under the audio tab I only had OSS selected (what one of the guides told me to do.)  changing it to only ALSA cause the noise to go crazy in the game.  Selecting both ALSA and OSS fixed the problem!  I can now hear people in vent and they can hear me while ingame.

---

