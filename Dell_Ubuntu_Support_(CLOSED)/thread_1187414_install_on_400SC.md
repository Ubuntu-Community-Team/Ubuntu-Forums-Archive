---
title: "install on 400SC"
date: 2009-06-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fryek on 2009-06-14
I may just be inadequate in my skills, but are there any issues known with 400SC installs?

I am having an issue with the install hanging during copying files from CD to hd... after partition is finished (am wiping windows off entirely)....

I have an NEC DVD/CDROM, 3gig memory, nothing special... same CD worked fine on an older Dell (2300)... but keeps locking up before finishing.

Ideas?

Thanks.

K.

---

### Post by ugm6hr on 2009-06-14
Try giving more detail...

Which version of Ubuntu?

Does the LiveCD work OK?

Have you run a diagnostic on the HD?

---

### Post by fryek on 2009-06-14
sorry... more details...

> **fryek said:**
> ...issue with the install hanging during copying files from CD to hd... after partition is finished (am wiping windows off entirely)....

I have an NEC DVD/CDROM, 3gig memory, nothing special... same CD worked fine on an older Dell (2300)... but keeps locking up before finishing.

VERSION 9.04 using the CD created from ISO... 

Ran the diagnostic on the ISO CD (9.04) on the Drive also on the memory - all OK.

Not sure what LIVE CD you're asking about - but the answer would be No.

Other questions that might help diagnose issues?

Thanks.

K.

---

### Post by ugm6hr on 2009-06-15
> **fryek said:**
> Not sure what LIVE CD you're asking about - but the answer would be No.

The LiveCD is the main desktop iso for Ubuntu.  In order to get to the partitioning stage, the LiveCD must run (unless you are using the AlternateCD).

The Ubuntu CD has no utilities for HD diagnostic tests (only RAM, and to test the CD itself).

Which option are you choosing on booting the Ubuntu CD?

Are you using the "Guided" or "Manual" install option?

How are you choosing to partition?

If you are unsure, a few screenshots might help.

The most likely options, if the problems occur during copying of files:
1. A hardware problem with HD.
2. Incorrect partitioning (too small for Ubuntu).

A complete hardware list might help too (e.g. processor, HD size, graphics etc).

---

### Post by fryek on 2009-06-15
> **ugm6hr said:**
> The LiveCD is the main desktop iso for Ubuntu.  In order to get to the partitioning stage, the LiveCD must run (unless you are using the AlternateCD).

The Ubuntu CD has no utilities for HD diagnostic tests (only RAM, and to test the CD itself).

Which option are you choosing on booting the Ubuntu CD?

Are you using the "Guided" or "Manual" install option?

How are you choosing to partition?

If you are unsure, a few screenshots might help.

The most likely options, if the problems occur during copying of files:
1. A hardware problem with HD.
2. Incorrect partitioning (too small for Ubuntu).

A complete hardware list might help too (e.g. processor, HD size, graphics etc).

hmm... "live CD," "alternate CD?" ...well... I downloaded the ISO image at this location (no mention of anything called "live CD"):

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

... then burned the image according to instructions found there ....

The resulting disc DOES have both a memory and HD test option on initial GUI... so I guess this is the LIVE CD?  It does also have a partitioning option (which I chose each time I tried to run setup)... (maybe the leading graphics say "LIVE CD" - I would not have paid any attention to such graphics... so this may be the issue here).

The HD is a 40gig drive... I have another old drive around and I'll try that one tonight after work and see if i have better luck with that one.

Don't remember what graphics card I am using, but I'll get that too (will just put in all hardware stuff - after I make sure the other HD doesn't solve the problem).

Thanks.

K.

---

### Post by ugm6hr on 2009-06-15
Apologies.

The "Desktop" CD is a Live CD, as in you can boot into Ubuntu from it directly.

When you boot from this CD, it should give you an option to "Try without making any changes" - have you tried this option?

If yes, does it boot to a usable desktop?

If yes, then with 3GB RAM and 40GB HD, there should be no issue.  What I am unclear on is how you chose to partition the HD, since the default setting now is to preserve any existing partition rather than over-writing.

---

