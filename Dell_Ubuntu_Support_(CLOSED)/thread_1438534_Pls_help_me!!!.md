---
title: "Pls help me!!!"
date: 2010-03-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by molykkutti on 2010-03-25
I installed ubuntu 9.04 as dual booting after Windows XP  . when I restarted the PC I could login properly once with ubuntu . But when I started it after some time the following message came after selected ubuntu 

   ata1 :SRST faied (errno=-16)
I really don't know what to do  Pls help me ....!

---

### Post by quixote on 2010-03-26
Apparently, you're not alone in not knowing what to do. :)  If you google that error message, there are hundreds of bug reports.  Apparently it's some quirk to do with adding an IDE drive.  Unfortunately, in your case, it looks like the first drive, which is the one with your OS on it.

Later kernels are supposed to not have this problem.  So one thing you could do, assuming you haven't got data you want on the ubuntu partition, is install a newer version of ubuntu to that same partition.  Karmic, or Lucid once it comes out Apr 29th.

---

