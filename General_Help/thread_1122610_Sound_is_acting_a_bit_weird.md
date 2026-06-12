---
title: "Sound is acting a bit weird"
date: 2009-04-11
forum: General Help
---

### Post by dudeeh on 2009-04-11
I have ubuntu 8.10 64 bit on this computer. It has been running just fine for quite a while, but day before yesterday my sound started acting up a bit.

I came home from work, and my sound was just dead. Music wouldn't play, video's played but with no sound, stuff like that, no sound _at all_.
I rebooted, everything was fine.

Today, i was playing a bit of music, suddenly amarok just dies on me, so i restart amarok and about five minutes later, my sound hangs. A continuous stutter could be heard, even though amarok was definatly dead (had to kill it though). A quick ctrl+alt+backspace did not fix the problem, so i rebooted once again. This second time around, i did a quick check of dmesg and the like to see if there were any warning flags before rebooting, but didn't see anything that struck me as being the problem.

So what i'm wondering is: how can i 'debug' my sound card? 

$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfa100000 irq 22

---

