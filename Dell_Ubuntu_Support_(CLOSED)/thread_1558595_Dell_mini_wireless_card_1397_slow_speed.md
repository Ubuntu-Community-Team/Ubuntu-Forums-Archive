---
title: "Dell mini wireless card 1397 slow speed"
date: 2010-08-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by morefeo on 2010-08-22
Hi all, first of all I was searching around and found that peolpe with the same or similar card are using the broadcom sta driver for 43xx (mine is bcm4312), but if I try to use it, wifi does not work (selecting it from the hardware drivers window).

Then I use the b43 drivers suggested by Ubuntu, and it works, but at low speed (1.5 ~ 2 mbps), while Windows7 reachs my internet's top speed (6 mbps).

So, is broadcom sta driver better than b43? Is there any way I could use it or is better to use b43? b43 driver can be speed up?

Thanks in advance, for the help, and sorry for my english.

---

### Post by mikewhatever on 2010-08-24
If you want to use the sta driver, you'll need to remove the backports wilreless modeles, which are needed on Karmic to make b43 work. I'd also recommend removing the b43 driver.

---

### Post by morefeo on 2010-08-25
> **mikewhatever said:**
> which are needed on Karmic to make b43 work

On lucid too?

---

