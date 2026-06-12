---
title: "Ubuntu can't see PDA connected via USB"
date: 2009-04-09
forum: General Help
---

### Post by jcorden on 2009-04-09
I have been given a HTC TYTN 2 mobile phone as part of my job that runs Windows mobile 6.1.

I would like to transfer all my mp3 files on my home PC that runs Ubuntu (v7 I think) to this device. I am not bothered about synchronising all my e-mail and contacts.

I have connected the phone to the PC via USB but Ubuntu does not recognise it. Any idea how I can solve this?

Thanks

---

### Post by Wayne_V on 2009-04-09
If you want to just access the phone as a USB storage device look in the phone settings for 'USB connection' and change from 'ActiveSync' to 'Mass Storage'.

If you do need to sync contacts take a look at msynctool - seems to work fine for me (with phone in ActiveSync mode.

---

### Post by jcorden on 2009-04-09
Wayne - thanks for taking the trouble to reply but I can't find that option on my phone. If I go to Settings - USB to PC the only option is a checkbox titled Enable advanced network functionality (which is currently checked). If I uncheck it nothing happens.

---

### Post by Wayne_V on 2009-04-09
I would check your device manual to see if it supports USB storage mode.

Otherwise, you are probably looking at some sort of ActiveSync replacement (see [http://www.synce.org/moin/](http://www.synce.org/moin/)).   That could be a lot more involved.

---

