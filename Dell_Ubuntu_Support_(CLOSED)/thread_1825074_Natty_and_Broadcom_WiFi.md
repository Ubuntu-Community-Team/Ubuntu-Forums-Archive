---
title: "Natty and Broadcom WiFi"
date: 2011-08-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MARP1961 on 2011-08-14
Why does Natty not offer the b43 Broadcom Driver in 'Additional Drivers' as it did in Lucid? The STA driver is not working correctly with certain Broadcom wireless cards despite being listed in Additional Drivers.

I eventually 'forced' b43 to install on my son's Inspiron 6400 and we've had no problem with Natty since. It seems mad that Ubuntu can't get this right (a recent installation of Fedora 15 worked 'out of the box').

---

### Post by MARP1961 on 2011-08-26
Does anyone know why this is?

---

### Post by followurdrmz on 2011-08-27
I also have a problem with dell 1390 wlan card.. mine is a inspiron 1520. Driver is listed in additional drivers but device is not listed in network manager to configure. I use a dsl connection via ethernet so i stopped looking for the solution for time being.

---

### Post by bkratz on 2011-08-27
> **followurdrmz said:**
> I also have a problem with dell 1390 wlan card.. mine is a inspiron 1520. Driver is listed in additional drivers but device is not listed in network manager to configure. I use a dsl connection via ethernet so i stopped looking for the solution for time being.



The Dell 1390 corresponds to the BCM4311. Here is the correct means of getting it to work.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by MARP1961 on 2011-08-28
I wish I'd read this installation fix back in April when Natty was released. Many thanks!

---

### Post by followurdrmz on 2011-10-21
Works just perfect on 11.10. Wish i have seen it back in august. Thank you bkratz..

---

