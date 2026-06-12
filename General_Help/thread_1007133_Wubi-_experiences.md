---
title: "Wubi- experiences"
date: 2008-12-10
forum: General Help
---

### Post by matth1j on 2008-12-10
In the past I've tried installing Ubuntu and failed miserably due to my PC's Abit SG-95 motherboard with (apparently) unsupported SATA hardware. However, someone mentioned Wubi, and as it didn't involve messing around with partitions (so no great loss if it failed), I thought I'd give it a go. Success \\:D/

Whether this is because Ubuntu 8.10 supports my SATA, or because of something Wubi does that Ubuntu on its own doesn't, I don't know. But I wouldn't have tried it if it wasn't for Wubi.

There were a couple of issues:

1. No sound. I followed [these]("http://ubuntuforums.org/showthread.php?t=205449") instructions, but they indicated that everything was fine. Then I tried going to youtube, where I was prompted to install the latest Flashplayer. When I attempted this, I got an error message that Flashplayer does not support my x86_64 architecture, which was news to me because I thought my Celeron was 32 bit :redface:

Anyway, I reinstalled Wubi using the --32bit option, and now the sound works fine. Apart from the sound (which I guess could be fixed by someone who knew what they were doing), what am I missing by not running the 64 bit version?

2. Constantly running graphics card fan. Easily fixed by following Ubuntu's suggestion to install the 'unsupported' Nvidia drivers for my 7900GS card.

So a big thank you to the Wubi team :cool:

John

---

### Post by razvanescu on 2008-12-10
Not all software/drivers developers ensure support for 64-bit architecture, so my advice is to stay for the moment under 32bit. It runs just fine!

cheers!

---

