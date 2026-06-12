---
title: "Changing default network connection"
date: 2008-12-27
forum: General Help
---

### Post by yosubis on 2008-12-27
I have 2 ethernet cards, one onboard and one pci. The onboard is fine, the pci is not recognised properly. It's a realtek card, and it is recognised as one of Myson technology, and according to the network manager the driver is fealnx.

The card works, but only at 10 Mb/sec. This card is also the default connection. I need to change so that I'll still be connected to both networks, just that the default connection will be the onboard card.

How do I change the default connection?

also, how I make ubuntu recognise the card as it suppose to?

---

### Post by yosubis on 2008-12-27
A little bump, since only after 2 hours this thread found itself on the third page.

---

### Post by Wartender on 2008-12-27
i believe that in network connections (right-click the network symbol on the notification area of your panel), if you check the "system setting" box (when editing a connection) that will make it the defalt, so uncheck your 10mb connection and check the other one.

---

### Post by Iowan on 2008-12-27
What model Realtek?  There are (or were) several threads about driver upgrades, etc.

---

### Post by yosubis on 2008-12-28
> **Wartender said:**
> i believe that in network connections (right-click the network symbol on the notification area of your panel), if you check the "system setting" box (when editing a connection) that will make it the defalt, so uncheck your 10mb connection and check the other one.

I tried this, but when I rebooted the computer both were still marked as "system setting".

---

### Post by yosubis on 2008-12-28
> **Iowan said:**
> What model Realtek?  There are (or were) several threads about driver upgrades, etc.

It has the Realtek RTL8139D chip

---

### Post by yosubis on 2008-12-28
A small nudge since after 3 hours it found itself at the bottom of the second page.

---

### Post by yosubis on 2008-12-28
Another nudge, since after 3 hours it's back to the third page.
This will be my last bump, If no one answers I'll assume that nobody knows the answers to my questions.

---

### Post by zoffix on 2010-04-12
Even though the issue is old, I'll post the way I fixed the same problem on my box.

I have a wi-fi connection on network 192.168.0.0/24 and Ethernet on 10.0.0.0/24. My problem was that Ubuntu would always choose the 10.0.0.0/24 network as the "default"

This command made my wi-fi interface the default:

```
sudo route add default gw 192.168.0.1
```

Cheers!

---

