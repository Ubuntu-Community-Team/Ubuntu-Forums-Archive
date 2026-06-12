---
title: "XPS M1330/Wireless-N question"
date: 2008-09-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pimbeto on 2008-09-05
Hi everyone,

I am considering buying an XPS m1330 and I will most likely be dual booting, so I would like to know if the wireless-n cards offered by Dell (either Intel Next-Gen Wireless-N Mini-card or the Dell Wireless 1505) work with Ubuntu 8.04. 

I noticed that preloaded Ubuntu systems are only offered with the Intel 3945, however I think it would be a shame these days to get a new laptop with a wireless-g card. 

Also if it does not work out of the box, then is there a way to make wireless-n work? ndiswrapper maybe?

Thanks in advance.

---

### Post by pimbeto on 2008-09-08
up

---

### Post by thorcik on 2008-09-08
hi there,
I don't know about the dell card but I assure You, Intel one works perfectly out of the box, even the LED turns on ;o) However, I don't know about the N-speed as I have no possibility of checking it.

---

### Post by Mau on 2008-09-08
Intel wireless works out of the box.

Everything else works for me as well (suspend, etc) in integrated graphics.

---

### Post by cjawcrusher512 on 2008-09-09
[[size=2][color=#006699]How to buy a ball mill with quality at reasonable price in China  ?[/color][/size]](http://answers.yahoo.com/question/index?qid=20080826203448AAVEOrl)

---

### Post by avpap on 2008-09-10
Ndiswrapper is your only choice! Install ndisgtk the gui of ndiswrapper and after that the bcml5.inf driver from the Dell website. After the driver is installed and the hardware is present I suggest to uninstall network-manager and install wicd. It's amazing and easy to use. This setup works like a charm in my XPSM1330 wit N-Wireless.

---

