---
title: "Ethernet and wireless not working on dell mini 10v Ubuntu 9.10"
date: 2010-01-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aronszekely on 2010-01-06
Hi Everyone!

I did not find an answer to this and I have been looking for a while. I installed Ubuntu Karmic 9.10 on a dell mini 10v. I had UNR on it before but I had the same exact problems: no autodetection of wired connections, because of this I couldn't download the broadcom proprietary drivers.
 
when going to the ethernet connections I accidentally deleted eth0 and do not know how to put it back. 

Does anyone have any suggestions how to get first the wired connection working, detecting the ethernet card, then to get the wireless (though I think that issue I can solve based on previous threads)?

thank You!

Aron

---

### Post by manosx on 2010-01-06
if you are in a LAN you can open a terminal and 

```
dhclient eth0
```

eth0 will be the name of the interface normally but you can check it with

```
ifconfig
```

---

### Post by rberger on 2010-01-06
I just tried setting a Dell Mini 10v up two weeks ago for a friend and had the same problem. My fix was just to go back to 9.04. Worked great.

---

