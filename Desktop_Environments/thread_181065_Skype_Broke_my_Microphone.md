---
title: "Skype Broke my Microphone"
date: 2006-05-23
forum: Desktop Environments
---

### Post by deadyeti on 2006-05-23
I installed skype, and after I used it my microphone will only work in skype.  Teamspeak was working fine before I installed skype but now my Mic only works in skype. 

Anyone had this problem or any Ideas to help?  I tried messing with the mixer and nothing helped.

-Yeti

---

### Post by queenorych on 2006-05-25
Not sure, but Skype for linux doesn't properly release /dev/dsp.  See dsp_hijacker.  It provides a wrapper around dsp, and relaeses when not used.  This is probably your problem.

---

