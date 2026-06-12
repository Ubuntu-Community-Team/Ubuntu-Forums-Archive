---
title: "Firefox recently freezes, but only if started from XFCE"
date: 2013-03-20
forum: Desktop Environments
---

### Post by cornstalk on 2013-03-20
I have Ubuntu 12.04 (factory installed) running on a Zareason laptop that I recently purchased.  Default desktop was Unity.  Because I like XFCE, I installed it and used it for a month or two, with complete satisfaction.  

Now just recently, for no obvious reason, Firefox 19.0.2 totally freezes when started from XFCE.  No response from any part of the Firefox interface.  Requires a kill -9 command to remove the dead Firefox screen.

Firefox 19.0.2 works just fine when started from Unity, from which I deduce that this is NOT a Firefox add-on issue.

I noticed when updating, not to long ago, that some updates were being installed that jointly concerned Firefox and Unity.  My suspicion is that either this or some other update (I always update everything recommended) has broken Firefox for use with XFCE.  

I googled on this issue before posting, but I could find nothing.  I would appreciate any help.  

Note: I do not actually want Unity, and it has occurred to me that deinstalling both it and Firefox, then reinstalling Firefox, might be a plausible step toward fixing my problem.  But I am loath to do that, because it is such a radical step.  Ideally I would like a more precise fix.

---

### Post by cornstalk on 2013-03-20
Fixed this, noting that xfwm4 was not starting with xfce.  Remedy: start xfce, start xterm, go 'xfwm4' in xterm, save xfce session upon exit.  Later sessions will work.

---

