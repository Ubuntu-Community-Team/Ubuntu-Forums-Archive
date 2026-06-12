---
title: "AppArmor Module Failed"
date: 2009-06-16
forum: General Help
---

### Post by Entropy_Sam on 2009-06-16
Okay, I'm pretty certain I've got to the root of the crashes I experienced a while back in 9.04. Since disabling Flash in Firefox and using Opera, I haven't experienced a full-system crash in Ubuntu once.
 
Thing is, while most people complained of firefox-only crashes, I was experiencing the whole shebang.
 
Since isolating the cause, I've noticed that the AppArmor module is failing at startup.
 
I can't find any posts on this, but having read up a little (amongst other things, it restricts applications' access to system resources), i'd say it sounds like the system is likely to be considerably less stable without.
 
That's just peculation on my part, and I have absolutely no idea how critical this failed module is likely to be. Can anyone advise on what steps I should take, if any to restore AppArmor to full functionality?
 
(one thing I want to investigate is whether or not it runs if I uninstall my nVidia drivers, as I only started exeriencing full system crashes after installing those - before, the offending windows were just automatically closed... I'll post a bug report on launchpad if i notice the problem)

---

### Post by nolliecrooked on 2009-06-16
retry?

---

### Post by Entropy_Sam on 2009-06-16
> **nolliecrooked said:**
> retry?
 
 
Heh, thanks, but ths is a persistent occurrance. I can assure you "turned it off and switched it back on again" :-p
 
Fair enough though - I work in IT support, so I know how many people DO call for help before trying the obvious...
 
But still, AppArmor is not loading, and being new to Ubuntu, I'm not really sure whree to turn to find out why. All I get is a FAILED message at startup.
 
Any advice? :-)

---

