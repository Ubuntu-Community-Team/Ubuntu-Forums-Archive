---
title: "Laptop - No sound from speakers, headphone jack works fine"
date: 2005-04-16
forum: Desktop Environments
---

### Post by vtrac on 2005-04-16
I downloaded, patched, and installed vanilla kernel 2.6.11-5 from kernel.org, edited the default ubuntu kernel config file so that my kernel compile would be shorter.  Everything seemed to work fine, and I'm currently using kernel 2.6.11-5, but I just noticed that I can't hear anything out of my laptop's built-in speakers, however the headphone jack works fine.  Any ideas?

---

### Post by mirons on 2005-04-16
Generally it's enough to change some settings via alsamixer. Button 'm' turns on/off options.

---

### Post by vtrac on 2005-04-18
[QUOTE=mirons]Generally it's enough to change some settings via alsamixer. Button 'm' turns on/off options.[/QUOTE]
 weird.. I rebooted into my previous kernel and it was still broken.. then I rebooted to windows to make sure that it wasn't a hardware issue, and windows played the sound find through the builtin speakers.  Then I rebooted back to 2.6.11-5 and the speakers were fine as if nothing happened.  ?  Oh well.. hope it stays like this.

---

