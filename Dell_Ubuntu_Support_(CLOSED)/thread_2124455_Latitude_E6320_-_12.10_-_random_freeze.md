---
title: "Latitude E6320 - 12.10 - random freeze"
date: 2013-03-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ilcontegis on 2013-03-11
Dear all,

My Latitude E6320 randomly freeze since I bought it. (Ubuntu 11.04, 11.10, 12.04 and now 12.10).
I noticed that if I leave it on without using it (no screen-look, no screen saver etc) it would freeze after a couple of hours. Otherwise, the laptop freezes randomly even when I am using it.

Does any of you have any idea how could I try to solve this problem?

Thank you very much.
Regards

---

### Post by ibjsb4 on 2013-03-11
Considering you have had this problem for a long time, you have probably tried just about everything.  But ..

My first thought is a memory leak.  Or maybe bad ram.

---

### Post by ilcontegis on 2013-03-11
This happens only with Ubuntu. With windows 7 no problem at all.

---

### Post by ibjsb4 on 2013-03-11
Any chance of finding a better video driver?

---

### Post by ilcontegis on 2013-03-12
I already tried to change it :(

---

### Post by hkb41 on 2013-03-12
Without specs on the machine hardware it's gonna be next to impossible to figure out what's going on.

---

### Post by ilcontegis on 2013-03-13
Searching the name of the laptop on google I could find this information
[http://www.dell.com/us/enterprise/p/latitude-e6320/pd#TechSpec]("http://www.dell.com/us/enterprise/p/latitude-e6320/pd#TechSpec")
I hope it's sufficient.

Regards

---

### Post by jyris on 2013-05-16
I have the same laptop and the problem too. So far on 12.04 it has never frozen while working, only when idling. When frozen the system is fully stuck. It does not answer ping etc.

I have tested that turning screen off and locking does not usually freeze the system. I have set suspend when inactive to "Don't suspend" so it is not that either. After the freeze there is no hint what was happening in the syslog either, cron just running hourly tasks until the system freezes.

There is not much to go on here, but I'd love to wake in the morning knowing that I don't need start my day by rebooting.

At least it is good to know that upgrading to 12.10 does not help.

Knowing these issues, this link is a bit hilarious: [http://www.ubuntu.com/certification/hardware/201012-6925/](http://www.ubuntu.com/certification/hardware/201012-6925/)

Best regards,
Jyri

---

### Post by jyris on 2013-05-22
After ruling out the display driver I turned my suspicion to proprietary Broadcom STA wireles driver. I have now used my laptop in flight mode (the switch above DVD-drive) for several days and the laptop has not hang so far.

The laptop is now more that 2 years old and I wonder if there is an open-source driver available for the wireless-chip by now.

Best regards,
Jyri

---

### Post by wilburd on 2013-06-02
I also have a Dell e6320, ubuntu 12.04 64bit. System freezes radomly - but only when on battery. I never had any freezes when plugged in. I tried flashing BIOS, updating the kernel, some other things. After half a year I'm ready to give up and switch to a different OS.:cry:

---

