---
title: "Dell PS M1710 fan going crazy"
date: 2008-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Guruji on 2008-04-28
hi,
from time to time (seems to happen randomly, no specific app used or same action done) the fan of the laptop (or the one of gpu?), goes crazy, start to go super fast...and at the same time the system starts to run very slow.
This problem already appeared under 7.10, and is still there now with 8.04.
I suspect it to be a gpu problem, but changing the nvidia driver didn't seem to solve anything.
I tried powerTop, who shows me the biggest power waster was nvidia.. tried some tuning... but no change (i would say it's worst after the tuning).
The system slows down until it becomes unusable (gutsy & hardy), firefox quit inexpectedly (only hardy).
I can't test it under windows...cause i finally got ridd of it after not using it for some months.

any idea?

System:
Dell XPS M1710, Core2Duo 2Ghz, 1gb ram, 80gb HD, nvidia GoForce 7900gt 512 (driver 169.12)

---

### Post by mac.ryan on 2009-06-09
Same computer, same problem.

For me the problem started quite recently in 8.10 and it is still there in 9.04.

Did you find any solution to the problem? The funny thing is that all sys monitor I tried report CPU usage absolutely in the norm, but the computer still seems to clog up and the temperature of the processors drops dramatically (given the fan being on all time). It normally reach 25 celsius indeed.

My best guess is that it is something in relation with teh power manager module kernel: it probably get tricked to believe the system is way too hot and scales down cpu clock while firing up the fans at their top speed...

Any feedback welcomed, especially since i have been unable to find relevant bugs on launchpad.

---

### Post by Guruji on 2009-06-09
yes i fixed it! that was a year ago hehe.
The problem is ... dust.. getting around the copperplate cooling the cpu and gpu. I had to open all the computer, clean everything close back.. and no more crazy fan. It wasn't that dirty.. just a tiny bit of dust .. but that was enough. Never happened again since i cleaned it.

you can find on dells website in the support sectinon they show you how to open the computer.

---

### Post by mac.ryan on 2009-06-09
Thank you for the quick reply...

however it must be a different problem then, as I completely opened and cleaned the laptop less than 10 days ago. :-/

My problem seem to happen randomly and - luckily for me - not that often (yet still often enough to annoy me). One of the things I noticed is that it seems to occour more often when the computer resumes from stanby or hibernate...

Anyhow... thanks for quick answer! :)

---

