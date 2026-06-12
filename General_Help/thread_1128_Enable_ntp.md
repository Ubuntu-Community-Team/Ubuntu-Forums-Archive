---
title: "Enable ntp?"
date: 2004-10-18
forum: General Help
---

### Post by mark on 2004-10-18
Okay, stupid question #437 - how do I enable *ntp* support?

I had assumed (I know, I know...) that *ntp* was enabled out-of-the-box, so to speak.  Well, I just brought up *Adjust Time &amp; Date*, tried to select *Synchronize clock with Internet servers:* and got this message:```
NTP support is not running - Please run NTP support in the system to enable synchronisation of your local time server with internet time servers
``` Having found no handy *Enable ntp support* setting anywhere, I guess I need some CLI help.  Is there a config file somewhere that I need to edit (or create)?  Or is there something more esoteric involved?

*Thanks,*

Mark

---

### Post by mark on 2004-10-19
Sorry, should have done my homework.  I started *Synaptic*, searched for *ntp*, installed everything pertinent that I was missing, rebooted and there it was.  The key element seems to have been *ntp-simple*.

I'll try to investigate a little more thoroughly before posting in the future.

---

