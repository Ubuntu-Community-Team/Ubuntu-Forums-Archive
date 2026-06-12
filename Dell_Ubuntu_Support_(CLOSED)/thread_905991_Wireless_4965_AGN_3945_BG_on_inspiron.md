---
title: "Wireless 4965 AGN 3945 BG on inspiron"
date: 2008-08-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xtracool_protik on 2008-08-30
Hey guys I purchased Inspiron with 4965 wirelessN capability card and all, however my System->Administration->Network doesn't show any wireless device
First of all I installed ndiswrapper which took drivers very well and installed them without problem However still there was no connection.
 So I read this thread where in it was said intel 4965 is supported by ubuntu linux so I removed ndiswrapper restarted PC and still the problem is same. Can anybody look into it 
One more thing I'm not looking for N compatibility just G is fine 
I've also tried lshw and it shows h/w but no driver present
 Thank you very much

---

### Post by elctb on 2008-08-30
No help here, because I have the same problem. I have a Dell Inspiron 1525 with the 4965 chip and I can't see any wireless networks, let alone connect to them.

I even tried kernel 2.6.26.3 and still have the same problem. iwlist scan doesn't show any networks.

---

### Post by xtracool_protik on 2008-09-18
Well buddy if u have intel network device just go to system->administration->network and u'll find an option of wireless there if not instead of upgrading ur kernel try reinstalling 8.04 hardy 2.6.24-19 kernel or even default i.e. 2.6.24-16 and the wireless is there. This method worked for me. If u have card with some other made u'll have to dig a little

---

