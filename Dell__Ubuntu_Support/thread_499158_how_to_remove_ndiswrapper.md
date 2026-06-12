---
title: "how to remove ndiswrapper??"
date: 2007-07-12
forum: Dell  Ubuntu Support
---

### Post by ashrafabdeljaber on 2007-07-12
First of all, Im a noob in linux so please bear with me.

Ok, so I have a fresh install of ubuntu 7.04 on my dell inspiron 1501. All the drivers were installed except for my broadcom wireless 1390 card. So I went to follow this tutorial [https://help.ubuntu.com/community/WifiDocs/Driver/1390](https://help.ubuntu.com/community/WifiDocs/Driver/1390)

But, Im stuck on the first step

$sudo rmmod ndiswrapper
$sudo apt-get remove ndiswrapper-utils
$sudo su
$sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
$sudo shutdown -r now

When I type in the first line at the terminal, it gives me this error

'ndiswrapper does not exist in /proc/modules'


What do I do??

---

### Post by Ek0nomik on 2007-07-12
> **ashrafabdeljaber said:**
> First of all, Im a noob in linux so please bear with me.

Ok, so I have a fresh install of ubuntu 7.04 on my dell inspiron 1501. All the drivers were installed except for my broadcom wireless 1390 card. So I went to follow this tutorial [https://help.ubuntu.com/community/WifiDocs/Driver/1390](https://help.ubuntu.com/community/WifiDocs/Driver/1390)

But, Im stuck on the first step

$sudo rmmod ndiswrapper
$sudo apt-get remove ndiswrapper-utils
$sudo su
$sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
$sudo shutdown -r now

When I type in the first line at the terminal, it gives me this error

'ndiswrapper does not exist in /proc/modules'


What do I do??

Don't worry about getting that error.  Assuming you have never installed ndiswrapper before this, that is the error you are supposed to get.  A lot of the wireless tutorials carry that step just to double check that you don't have ndiswrapper installed (or maybe an older version) before following their tutorial.

---

