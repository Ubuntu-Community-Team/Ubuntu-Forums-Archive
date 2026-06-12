---
title: "Help needed, perhaps driver stuff / games"
date: 2007-10-31
forum: Gaming &amp; Leisure
---

### Post by tempusfugit on 2007-10-31
I installed morrowind in ubuntu and it starts, but its way too slow, now i installed prince of persia t2t and it said me that 64 mb video memory is needed and i have only 16. But that is wrong, i have a ati driver working in my restricted driver area and dont know what to do now. please help me.
I have a ati radeon 1200 chipset and my pc is running on ubuntu gutsy.
i tryed some strange configurations following a guide on the net but it doesnt solve my problem. also the sound is messed up
Thanks alot!

---

### Post by acoustibop on 2007-11-01
"I have a ati radeon 1200 chipset" - I presume you mean an embedded chip, tempusfugit?  So how much system memory and how much memory assigned to the videocard card do you have?

If you have an embedded chip, it probably has no dedicated memory at all.  Most embedded chips  use system memory; sometimes there's a fixed amount, and sometimes the amount can be allocated in the system BIOS.  AFAIK some manufacturers of computers with embedded chips will set this figure quite low, so that plenty of memory remains avalable for system use, leaving the user to increase it if they want more videocard memory for gaming etc.

This may be what's happening.  Otherwise, the games may not be detecting your video chip's memory.  Since you haven't given us any system specifications whatsoever, apart from the type of your embedded video chip, it's impossible to form an opinion on how those games should be running on your system.

If your sound is "messed up," you need to sort that out before trying to install and play games,as well.

---

### Post by tempusfugit on 2007-11-01
Sorry for missing system specs i was very tired yesterday.

I have a packard bell pc
512mb ddr ( in windows it shows i have only 448 )
intel celeron d processor 356

Tell me if you need more to know, the point is in windows xp i can play all my games i have san andreas morrowind prince of persia t2t etc.
and my sound is normal also, i have an ati driver and adaptek driver and everything works fine. somehow its a ubuntu thing.

---

### Post by tempusfugit on 2007-11-04
nobody?

---

### Post by acoustibop on 2007-11-05
Well, it does look like your video chip is using enough system memory, tempusfugit - that's why, in Windows, it only reads that you have 448 MB system memory.

Which fglrx driver are you using - what's the output of fglrxinfo?

I'm not familiar with the games you're trying to play; are they Linux versions or are you trying to play them in Wine or an equivalent?

---

