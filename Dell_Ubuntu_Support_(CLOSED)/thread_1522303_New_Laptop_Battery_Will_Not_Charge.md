---
title: "New Laptop Battery Will Not Charge"
date: 2010-07-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jheylin on 2010-07-02
I have a Dell XPS M1530 running Ubuntu 10.04.  Recently the battery stopped taking a charge.  I figured, since it was a year old, that it was possibly dead.

I bought a new battery and put it into my laptop.  I left it to charge up until it was full (a whole day) and turned my laptop on.  It said it was at 72% charge (what it came to me at) and that I only had a few hours of charge time left.  I ran it to zero, plugged it back in, and the battery will not charge.

When I remove the plug, it reads the battery as zero and after a few seconds the laptop shuts down.

I'm wondering if this is a hardware problem or a software problem.  The laptop runs off the plug, but the battery will not charge.  Any ideas?

---

### Post by ptptaylor on 2010-08-29
It seems like you probably have some kind of motherboard problem. If it's under warranty it would be worth giving dell a phone call.

---

### Post by jheylin on 2010-09-23
I resigned myself to the fact it was a physical problem, but after the latest software update all of a sudden it's charging the battery again.  Motherboard?  Nope.  Software?  Yep.  Weird.

---

### Post by the.scarecrow on 2010-09-24
I had this problem on my Latitude 1750, Dell suport got me to flash the BIOS to the latest version which may have helped a bit but is not a full solution.

I duel boot Win7/10.04 and not charging was the same in either OS. 

My solution is to always power on using the battery. While booting I plug the power unit into the mains, then when startup is complete I finally connect the power unit to the laptop.

This process always kick-starts the charging circuit if the battery is below 95%.

If you Google this Dell charging problem, you will see it is a common issue.

---

### Post by togume on 2011-03-07
> **the.scarecrow said:**
> I had this problem on my Latitude 1750, Dell suport got me to flash the BIOS to the latest version which may have helped a bit but is not a full solution.

I duel boot Win7/10.04 and not charging was the same in either OS. 

My solution is to always power on using the battery. While booting I plug the power unit into the mains, then when startup is complete I finally connect the power unit to the laptop.

This process always kick-starts the charging circuit if the battery is below 95%.

If you Google this Dell charging problem, you will see it is a common issue.

Thanks for this tip!

Confirming that this is indeed the case for some people with Dell laptops. I have a Latitude E5410, and this happened to me today. I must have powered it up with the power cable plugged in, resulting in the battery not charging.

The fix was to start it up with only the battery, and that made it charge again. I only waited until it cleared the BIOS to plug it in.

---

