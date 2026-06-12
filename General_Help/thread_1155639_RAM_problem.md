---
title: "RAM problem?"
date: 2009-05-11
forum: General Help
---

### Post by Benjamin_Lebsanft on 2009-05-11
Hi there,

I have 4GB of RAM, running the 64bit version of ubuntu, until yesterday I had swap enabled and ubuntu began swapping when reaching around 1.3 or more GB, when over 2 were still free. Performance  really went down when swapping began, sound stuttered etc. Now I disabled swap in fstab and now my system freezes hard when reaching the same amount of RAM. Is this a ubuntu setting or do I have faulty RAM?

Thanks
Ben

---

### Post by sandy8925 on 2009-05-11
Could be faulty RAM as you said. Are you sure you have 64 bit Ubuntu ?  And a 64-bit system ? Also instead of completely removing the swap from fstab i recommend that you reduce the swappiness. This can be done by lowering the value of vm.swappiness 

Here's a link to an optimization guide where you can find out how to change swappiness:

[http://www.goitexpert.com/entry.cfm?entry=ubuntuguide](http://www.goitexpert.com/entry.cfm?entry=ubuntuguide)

---

### Post by Benjamin_Lebsanft on 2009-05-11
Well I run ubuntu since warty, so I guess I know which version I install :) At the moment it is:

Linux benni-desktop 2.6.30-2-generic #3-Ubuntu SMP Fri May 1 01:37:37 UTC 2009 x86_64 GNU/Linux

but this happened on jaunty as well. I have an intel quad core q9500. I changed swappiness before but can't remember if it helped, I'll try again, thanks :)

---

### Post by ckonestroh on 2009-05-11
> **Benjamin_Lebsanft said:**
> Well I run ubuntu since warty, so I guess I know which version I install :) At the moment it is:

Linux benni-desktop 2.6.30-2-generic #3-Ubuntu SMP Fri May 1 01:37:37 UTC 2009 x86_64 GNU/Linux

but this happened on jaunty as well. I have an intel quad core q9500. I changed swappiness before but can't remember if it helped, I'll try again, thanks :)

Others are have trouble with Ati Radeon Cards and 4 gig memory problems...

Most users removed 2 gigs and where able to get there ati radeon cards to aleast respond in a two de graphics but would not support 3d graphics.....

Hopefully your not using a Ati graphics card...

---

### Post by Benjamin_Lebsanft on 2009-05-11
I use intel onboard graphics. Setting swappiness to 0 allows me to get at least 2.7GB of RAM without system freezes, hopefully it will stay this way.

---

