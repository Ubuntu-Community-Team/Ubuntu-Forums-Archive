---
title: "RAID disaster - please help!"
date: 2008-12-15
forum: General Help
---

### Post by bilbat on 2008-12-15
Used 'live' CD, & tried 'run without making ANY changes to system', to run it off the CD - broke my RAID0 & blew away 65Gb of Vista64 (not so bad as it sounds - at that point, was a test install anyways...); went to raid BIOS, fixed the array, and alternate installer broke it *AGAIN*, before I was given an option to do _anything_. I'm obviously not seeing SOMETHING here, but IBD if I can figure out what it is...  Was especially amazed by attempt to run direct from CD breaking the array!

---

### Post by robobot on 2008-12-15
With a raid array, you can't just install straight from the CD. Ubuntu doesn't have drivers for RAID devices installed by default, so you need to install those before you can install the OS.

Here's a link with instructions:
[https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")

---

