---
title: "Becoming root(?)"
date: 2009-03-14
forum: General Help
---

### Post by blurt on 2009-03-14
I installed clam tk antivirus; tried to update virus signatures; got box
saying "must be root". So, I switched to root desktop, and clicked to update
signatures, and the same box "must be root". What gives?.--blurt.:(

---

### Post by SuperSonic4 on 2009-03-14
Try ```
gksu clamtk
``` from a terminal or by pressing alt+f2

---

### Post by lisati on 2009-03-14
> **blurt said:**
> I installed clam tk antivirus; tried to update virus signatures; got box
saying "must be root". So, I switched to root desktop, and clicked to update
signatures, and the same box "must be root". What gives?.--blurt.:(

I haven't tried the clam AV family on ubuntu so I'm not sure if something simimlar applies, but with AVG free for Linux you can save yourself a lot of hassles by adding your username to the AVG user group (see [here]("http://ubuntuforums.org/showthread.php?t=889552"))

---

### Post by SuperSonic4 on 2009-03-14
> **lisati said:**
> I haven't tried the clam AV family on ubuntu so I'm not sure if something simimlar applies, but with AVG free for Linux you can save yourself a lot of hassles by adding your username to the AVG user group (see [here]("http://ubuntuforums.org/showthread.php?t=889552"))

I'd use avast if you're running a 32bit system. AVG seems bloated and clamtk tends to report a lot of false positives

---

### Post by lisati on 2009-03-14
> **SuperSonic4 said:**
> I'd use avast if you're running a 32bit system. AVG seems bloated and clamtk tends to report a lot of false positives

Good point: it always pays to do some homework. I read on one of the AVG sites that support for the only version of AVG I've seen that comes in a Linux-friendly package is likely to be discontinued.

---

### Post by blurt on 2009-03-14
The 'gksu worked like a charm; thats good enough for me. As for false positives *better safe than sorry?* I dual boot XP and ubuntu, because
sometimes within minutes of letting windows on the internet, there is a 
problem! In fact, I removed the nic driver from windows!! Although I use clamwin on the windows side, so as not to import something, the clamtk
lets me scan before I even send the file over to XP, and so there is the
redundancy of two somewhat different scan-engines.--tnx,blurt.:cool:

---

