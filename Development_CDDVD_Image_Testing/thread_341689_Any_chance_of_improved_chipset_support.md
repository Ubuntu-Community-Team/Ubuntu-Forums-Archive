---
title: "Any chance of improved chipset support?"
date: 2007-01-19
forum: Development CD/DVD Image Testing
---

### Post by ExploreMN on 2007-01-19
I'm curious if this version will expand chipset support to include more of the SiS chips - primarily 965L. The current 6.10 release can't seem to see any SATA or IDE controllers.

---

### Post by FLPCGuy on 2007-01-20
> **ExploreMN said:**
> I'm curious if this version will expand chipset support to include more of the SiS chips - primarily 965L. The current 6.10 release can't seem to see any SATA or IDE controllers.
As I understand it this may have something to do with SATA software RAID support in newer chipsets.

Here are some drive workaround ideas:
[http://linux.derkeiler.com/Newsgroups/comp.os.linux.hardware/2005-05/0707.html](http://linux.derkeiler.com/Newsgroups/comp.os.linux.hardware/2005-05/0707.html)

[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

I'm building a PC Chips A33G system with SiS 965L Southbridge and 761GX Northbridge with built-in SiS video.  They don't have Linux or Vista drivers.  The previous generation 741GX video worked fine with all Linux distros I tried, I hope the new video is usable.

---

### Post by ExploreMN on 2007-01-21
Well, actually if you go to SiS's website instead of PC Chips you can get the drivers...at least the source code. Then you need to compile it yourself.

Also, I don't know about the RAID stuff. I'm not using RAID...however, I gave up on Linux and just installed Windows XP Professional and MediaPortal instead.  No problems there...

---

