---
title: "powernowd  modes question"
date: 2006-07-18
forum: Desktop Environments
---

### Post by cptnapalm on 2006-07-18
I have a laptop and things are running pretty much fine, but I had a question about powernowd.  I noticed that when I am encoding stuff with iso2mkv, which is a cli to a bunch of other cli encoders like mencoder, the CPU is at 100% and it is running at 800 Mhz.  The CPU is a 2.0Ghz Intel Centrino.

My question relates to the modes which powernowd uses.  According to the man page, by default if CPU utilization exceeds 80%, the frequency ought to step up to full speed.  Since utilization stays at 98-100%, it ought to step up to the full 2.0Ghz.

Am I wrong about this?

(This may not really be a problem as I the first pass encoding is running steadily at about 22 fps.  Then again, I've never been one to encode a lot, so I really have no idea if this is typical behavior for a 2.0Ghz Centrino.)

---

### Post by mrbaz on 2006-07-18
I'm also curious.  I have a laptop with the modular extra battery.  Under Windows, I can get 5 hours of use before I need to plug it into the AC.  Under ubuntu, I get a 3 hours and change before it yells at me to plug it into AC.
Is this because ubuntu isn't properly throttling my processor?

---

### Post by cptnapalm on 2006-07-18
On the face of it, it would seem like staying at 800 Mhz would consume less power.

If you have a single core processor, have more than a few percentage points of CPU utilization when idle and are running a 686 kernel, this might do some good: [http://www.ubuntuforums.org/showthread.php?t=216442](http://www.ubuntuforums.org/showthread.php?t=216442)  Not sure how much it would help, but might help a bit.

---

