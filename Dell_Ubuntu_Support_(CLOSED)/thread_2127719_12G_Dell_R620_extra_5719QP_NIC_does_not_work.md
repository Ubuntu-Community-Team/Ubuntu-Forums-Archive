---
title: "12G Dell R620 extra 5719QP NIC does not work"
date: 2013-03-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by create123 on 2013-03-20
Hi I have 6 x R620 with both the integrated Broadcom 5720 QP and an additional 5719 QP.  The integrated one works fine but the additional 5719 does not.  It appears to work, link lights are on, switch recognizes it, ifconfig thinks there are packets that have gone through, but I can't get any communication to go through it.

I am on 12.04.2 LTS with xen installed:
# uname -a
Linux ubuntu 3.2.0-39-generic #62-Ubuntu SMP Thu Feb 28 00:28:53 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


Anyone else run into this?

---

### Post by create123 on 2013-04-12
Just wanted to let you all know I resolved this by moving the 5719 card from slot 1 (where Dell pre configured it) to slot 3.

I am a bit pissed that they caused me all this wasted time.

---

