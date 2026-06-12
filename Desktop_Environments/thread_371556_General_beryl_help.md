---
title: "General beryl help"
date: 2007-02-27
forum: Desktop Environments
---

### Post by Jphenow on 2007-02-27
When I setup beryl the first time i was using an nvidia gefore mx 440; 64 bit, 64mb, I, just today, switched to an ATI radeon 9250 in which I just got my drivers working. How will have to change beryl configurations to meet my new card, because at the moment beryl will not function with it. Is there a way to avoid a complete re-install? 

P.S.
I'm still essentially a n00b so detailed help would be appreciated a lot!

thanks in advance!

---

### Post by halfvolle melk on 2007-02-27
You'll need direct rendering. Find out with **glxinfo | grep direct**. If you haven't, install the appropriate driver:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

