---
title: "Question about Wargus"
date: 2007-03-01
forum: Gaming &amp; Leisure
---

### Post by disturbedite on 2007-03-01
i downloaded stratagus 2.2.2 since this version isn't in the repos yet.  i downloaded wargus, compiled it, and installed the warcraft2 data without error.  wargus runs fine, except some audio (& all music) is missing.  here is the log:

[http://www.pasteserver.net/320](http://www.pasteserver.net/320)

if anyone could post some possible solutions it would be much appreciated.  thanks

---

### Post by Kimm on 2007-06-09
> **disturbedite said:**
> i downloaded stratagus 2.2.2 since this version isn't in the repos yet.  i downloaded wargus, compiled it, and installed the warcraft2 data without error.  wargus runs fine, except some audio (& all music) is missing.  here is the log:

[http://www.pasteserver.net/320](http://www.pasteserver.net/320)

if anyone could post some possible solutions it would be much appreciated.  thanks

You probably have something that blocks Stratagus from accessing the soundcard. Try "killall esd" in your terminal.

Could you please also describe how you got it working (cant seem to do it myself)

---

