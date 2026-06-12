---
title: "Wireless-Network with WG111"
date: 2005-10-30
forum: Desktop Environments
---

### Post by Mikulcak on 2005-10-30
Hello together,
I have a strange problem with my NetGear WG111.
I installed the driver with ndiswrapper 1.4, everything worked fine: I see my Access - Point and it receives and responses on 'ping'. This means, in my eyes, that the driver is correctly installed and browsing the internet also should work fine.
But it doesn't. This means: FireFox tries to connect a very long time and then stops. The weird fact: 'apt-get update' in the terminal works fine, it downloads the list of updates after some time.
The stick (and the access - point) work fine with WinXP,
thank you,
Mikulcak

---

### Post by jkr on 2005-10-30
If you can verify networking is working ok with ping, and likewise confirm dns is working too ( which it would have to be to get apt-get working) 

maybe problem is with Firefox - I have solved a problem with similar symptoms turning off ipv6  - search for about:config and ipv6 to turn it off.

hth
;)

---

