---
title: "Using /dev/shm on Mini 9"
date: 2008-12-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Rallg on 2008-12-01
I upgraded my Dell Mini 9 to 2Gb memory. Ubuntu 8.10 is the standard version, not the Dell remix. No linux-swap.

After looking around for what other have done, I have used /dev/shm for temporary files in certain programs (such as Gimp or Audacity). Apparently, this is a system-managed RAM partition included with Linux. I hope that it saves writes to SSD and also runs faster.

So far, no problem. But I have no idea whether it is beneficial. Would anyone more knowledgeable care to comment?

---

### Post by iggykoopa on 2008-12-01
it sounds like your using it correctly for your intents. It will save you writes and it will run faster. I wouldn't be too worried about the writes on your drive though, they have good wear leveling algorithms and from what I've read around you'll get something like 5-10 years off those drives anyway(probably longer than you'll use the laptop for).

---

