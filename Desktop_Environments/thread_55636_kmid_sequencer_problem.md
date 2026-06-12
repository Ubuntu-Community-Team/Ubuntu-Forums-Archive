---
title: "kmid sequencer problem"
date: 2005-08-09
forum: Desktop Environments
---

### Post by retsel on 2005-08-09
I need a midi player, so I installed kmid. When I try to use it I get:

 "Error kmid - Could not open /dev/sequencer. Probably there is another program using it."

I checked in /dev and there is nothing called sequencer, but in /.dev there is.

In the /.dev directory I did a ls -l sequencer and got:

"crw-rw---- 1 root audio 14, 1 2005-04-01 07:37 sequencer"

Anyone have any ideas of what I need to do to get kmid to work?

Maybe an easier way out is to install a different midi player. Any suggestions?

---

