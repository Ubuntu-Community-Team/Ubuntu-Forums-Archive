---
title: "CrossfireX refuse to work 11.04"
date: 2011-07-29
forum: Gaming &amp; Leisure
---

### Post by rootfairy on 2011-07-29
Hello,
 im trying to get a 5770 and 5750 to run in CrossfireX in Xubuntu and Ubuntu 11.04 as well.
 Official AMD drivers cannot be used, because they are bugged. The bug  is that when you move your mouse cursor to the lower right section of  the screen you will get a 3 second frame freeze.
 Proprietary drivers dont show this malfunction.
 Aticonfig and AMDCCCLE are not able to set up a CrossfireX configuration.
 Upon using aticonfig --initial the following message appears:
 Fail to link to fglrx-libglx.so, please check whether driver is installed correctly
 Upon using aticonfig properly to set up a CrossfireX configuration --lscs reports:
 Candidate Combination: 
    Master: 1:0:0 
    Slave: 2:0:0 
    CrossFire is disabled on current device
    CrossFire Diagnostics:
    CrossFire can work with P2P mapping through GART
    Dongle Capabilities: support PASSTHROUGH |INTERLINK_SW_AFR | INTERLINK_AUTO_AFR | INTERLINK_BLACKING | INTERLINK_SUPERAA
 No matter how i try, CrossfireX remains disabled.
 In AMDCCCLE the second device 5750 remains as an unknown adapter,  while the active display and device are properly used and displayed.


help1!!!!!

---

### Post by rootfairy on 2011-09-11
this is actually solved. hd 5770 and hd 5750 cant work in linux with all drivers currently available. it adds up, that crossfire perfomance on hd 5770 and hd 5750 is PURE ******** and a single card is faster, than the two combined.

GTFO ATI

---

### Post by holastickboy on 2011-09-15
This has been the case with ATI stuff since I started using Linux back in 2000, not much has changed (though it is a little better now).  I wasn't aware that you could crossfire different Radeon cards eh?  Thought you had to have 2x 5750s or 2x5770s eh.

---

