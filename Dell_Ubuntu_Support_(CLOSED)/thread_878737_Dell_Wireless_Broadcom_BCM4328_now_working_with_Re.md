---
title: "Dell Wireless Broadcom BCM4328 now working with Restricted Drivers Manager"
date: 2008-08-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Vaun on 2008-08-03
Exciting news.  A recent update to linux-restricted-modules-2.6.24-20-generic in hardy-proposed has enabled the restricted driver for the BCM4328 (wl driver).  Working flawlessly as of now I was forced to used ndiswrapper for the last six months.  Signal strength has also increased from ndiswrapper.  I'm still testing as it's in proposed, but this seems very promising.

---

### Post by CloudFX on 2008-08-03
It's actually been there for a while now... I believe four or five months ago.  It's easier to enable on Gutsy than Hardy, last time I tried (which would be 3 months ago).

---

### Post by PinkFloyd102489 on 2008-08-03
Great news, now I can use promiscuous and monitor modes on my laptop for Aircrack.


EDIT: Seems a bit buggy. Keeps disconnecting and reconnecting, though not visibly. Network Manager shows signal drop but ifconfig says it's still up. I thought I broke something when I put it into Monitor mode (which enables, but doesnt support injecting, go figure) but it's still doing it.

---

### Post by TimDaniels on 2008-08-09
> **Vaun said:**
> Exciting news.  A recent update to linux-restricted-modules-2.6.24-20-generic in hardy-proposed has enabled the restricted driver for the BCM4328 (wl driver).  Working flawlessly as of now...

Exactly how did you install it and start it up?  I checked "Pre-release updates" on the "Updates" tab of the Software Sources admin utility, and then Update Manager said that there were 55 update files available - and I installed all of them.  But after a restart, there's still no Wi-Fi.  Wi-Fi on my XPS-M1330 had been working fine under Gutsy, but it's nowhere to be found with the Duck.  Are there some more procedures for getting Wi-Fi back?

*TimDaniels*

---

### Post by phanku on 2009-04-25
Hey, how did you get that bcm4328 to work in monitor mode?

---

### Post by dwouters on 2009-04-25
Tim Daniels: If you look under System>Administration>Hardware Drivers, you should see your restricted driver. Down at the lower right corner, look for a button that reads "Activate". If the active button is not green, click it to activate the driver. Tht should get you wireless again.

---

### Post by lakhvinderrayat on 2009-06-15
can anyone tell me how to use bcm4328 in monitor mode?

---

