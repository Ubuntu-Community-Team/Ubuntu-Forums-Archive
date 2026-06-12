---
title: "Dell Mini 9, Ubuntu 8.04.1LPIA, Broadcom 4312, b43 Driver..."
date: 2009-05-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Arndtwe on 2009-05-06
I have a Dell mini 9 running Ubuntu 8.04.1 LPIA. The wireless card thatI have in it is the Broadcom 4312. The current driver I am using, which is also the latest is the STA driver. The driver prior to this one was the b43. I would like to get and install the b43 driver... Why you may ask? Because the latest driver does not support monitor mode. This means that if I want to use say, the Kismet suite, I am out of luck!! Why on earth would the developers of a new driver remove features rather than add them??

Anyway. I have search for hours, Google, here, other forums and I just cannot find a solution to this!!! No where is there a place to download and install the b43 driver. I need help. Any information on the topic would be greatly appreciated

---

### Post by Arndtwe on 2009-05-09
BUMP - No one has any input, at all?

---

### Post by Brandon Williams on 2009-05-09
I suspect that if you run 'locate b43.ko' on the command line, you will discover that you already have the b43 driver, since it is part of the stock kernel. I also suspect that you will find that it in fact does not work with the wireless card in the mini 9. My experience suggests that this wireless card only works with the STA driver. I would be happy to be proven wrong, though.

---

### Post by snowpine on 2009-05-10
Broadcom 4312 is not well supported by Linux; the only methods that have ever worked for me are 1) Broadcom STA driver (wl.ko) or 2) ndiswrapper. I've tried b43 and it just doesn't work.

---

