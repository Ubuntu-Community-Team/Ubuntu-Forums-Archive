---
title: "Ubuntu freezes after waking up from suspend and hibernation"
date: 2009-02-14
forum: General Help
---

### Post by cmwslw on 2009-02-14
I just installed Ubuntu, and I absolutely love it. I love the open source philosophy and the great support. I do have one problem that's really glaring though. Whenever my computer wakes up from a suspend or hibernation, it freezes. When waking up from a suspend, I only see my desktop background and my cursor, but I am unable to move it. When waking up from hibernation, I see the Ubuntu boot screen and it says "Ubuntu is waking up", but freezes after the progress bar gets a quarter of the way. Does anyone have any idea what is causing this problem? I have a new eMachines ET1161-03 upgraded to an ATI 4830 card. Would my RAM be the problem?

Thanks in advance,
-Cory Walker

P.S. This is my first time troubleshooting an Ubuntu problem, so please excuse the fact that I might not include enough information. Just ask if you need anything.

---

### Post by cmwslw on 2009-02-15
Sorry to bump so early but threads get buried so fast in the General Help section. Is there a better place to ask this?

---

### Post by sacredsunder on 2009-02-23
I have the same problem with an acer aspire 5515 laptop I bought yesterday.

---

### Post by sacredsunder on 2009-02-23
ah ha! I figured out a solution to my problem. The proprietary ATI driver was causing the problem for my hibernate and suspend. It was making the hibernate throw two errors:

ata1: softrest failed (device not ready)
ata3: softrest failed (device not ready)

and when I disabled the ATI driver suspend and hibernate both work and dont give any errors.

 Hope this helps someone else : p

---

### Post by joey-elijah on 2009-02-23
Suspend/ Hibernate is a bit of an issue in Ubuntu (and Linux) generally that's starting to be addressed in the kernel.

---

