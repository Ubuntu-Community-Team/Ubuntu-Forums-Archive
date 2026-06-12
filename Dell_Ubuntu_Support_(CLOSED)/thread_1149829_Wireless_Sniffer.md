---
title: "Wireless Sniffer"
date: 2009-05-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by omid1979 on 2009-05-05
Hi all , 
I was install ubuntu 9.04 on my new dell Vostro 1310 Notebook , I also install wireshark for network monitor and sniffer , but it can't detect my wireless card , how I can configure it to enable me to work with my wireless ? my notebook wireless is "Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)" as linux driver ( it was Dell mini wireless on windows vista "

any one can help me how to solved it ?

P.S : wireless network work fine on ubuntu but I can;t use it for  wireshark network sniffer

---

### Post by icdelg on 2009-06-02
I was having the same problem and found out that on linux systems you need to be root to capture any data. 
You just have to run:```
sudo wireshark
```

The wireshark wiki has lots of helpful information
[http://wiki.wireshark.org/]("http://wiki.wireshark.org/")

---

### Post by tyroeternal on 2009-06-03
> Not all operating systems support capturing non-data packets and, even on operating systems that do support it, not all drivers, and thus not all interfaces, support it. Even on those that do, monitor mode might not be supported by the operating system or by the drivers for all interfaces.  -[Wireshark FAQ]("http://www.wireshark.org/faq.html#sec10")

More than likely this is an issue with your card's/driver's ability to capture packets.  While running it as root user is the first step, you also need a compatible card.  I'm not sure what card you have, but the card in the Mini 12 I have does not support it.

---

