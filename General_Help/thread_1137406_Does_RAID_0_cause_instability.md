---
title: "Does RAID 0 cause instability?"
date: 2009-04-25
forum: General Help
---

### Post by Lateforgym on 2009-04-25
Just wondering it Linux users have crashes while muti-tasking in a RAID 0 environment. This is my attempt to reduce system instability in an non-linux environment by seeing if linux has the same problems. 


When I RAID 0 on my ASUS in XP I get periodic crashes at startup and while loading my 40 gigs of music, while usign my scanner, while loading 3 webpages, while updaing my feeds, while plugging in my USB drive and burning a CD. 

I just dont see why I should be getting periodical BSOD after spending $1,000 on a Windows box after 5 years of technology advancements I was lead to belive that a multi-core CPU, super fast system with tones an RAM would help me with my problems but appearantly its still 1999. 

My 5 year old MSI was more stable then this. But the one was no a RAID system.

THanks

---

### Post by fjgaude on 2009-04-25
Can't say if your problems are caused by raid0 or not. raid0 is only used for speed and not reliability... one drive failure takes all your data with it.

From what you say though it may be something else. In linux few of us use raid0, lots use raid1, raid5/6, and raid10. Make sure all your drive connections are tight... don't have any other suggestions.

You are likely using BIOS raid... or is it a card? You would have to have the correct driver if it is a card.

It would be difficult to install Ubuntu on your raid0 array. You might be able to use a liveCD with Ubuntu on it and install **dmraid**. From there you could continue to use the CD and mount your Windows raid0 and see how it works. But, you have lots of learning to go through to get all this to happen.

---

