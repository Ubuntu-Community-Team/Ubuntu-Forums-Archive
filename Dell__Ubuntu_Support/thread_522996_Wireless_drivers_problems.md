---
title: "Wireless drivers problems"
date: 2007-08-11
forum: Dell  Ubuntu Support
---

### Post by ghostandmachine on 2007-08-11
So, I had the drivers working at one time when I had Ubuntu Studio on my Dell Inspiron 1150 but I uninstalled, then reinstalled Feisty. Anyway, followed the instruction for installing on the Help pages. It says it's installed but it's not seeing any of my wireless points.

Driver is a BCM4309. I don't even know if I have the right drivers. Dell's website is stupid.

thanks in advance.

---

### Post by erichill on 2007-08-11
This page should help you. It certainly works for my Inspiron 1501.

Good luck :KS

Eric

---

### Post by saru411 on 2007-08-11
i think it would help if you posted the link to "this page"

---

### Post by erichill on 2007-08-11
Whoops, sorry. :oops:

Here is the url. 

[http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated](http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated)

 now that it refers to a different computer, but the wireless card is the same. It works or me.:)

---

### Post by michael37 on 2007-08-12
There are actually two ways of implementing the driver:
[LIST]
[*]using ndiswrapper and Windows wireless driver
[*]using native Linux driver
[/LIST]

I posted [a poll](http://ubuntuforums.org/showthread.php?t=516118) on this subject and got an overwhelming support for the ndiswrapper method.

The FAQ quoted above implements an unusually interesting way for a Linux native driver which is **already outdated**.  So, my recommendation is against this method.

Instead, follow this FAQ for the Linux driver.  [https://help.ubuntu.com/community/WifiDocs/Driver/1390](https://help.ubuntu.com/community/WifiDocs/Driver/1390)
This Howto can be found by going to [http://help.ubuntu.com/community](http://help.ubuntu.com/community) and searching for *1390*.  Your wireless card is also known as Broadcom 1390.

---

### Post by jeremy1138 on 2007-08-12
> **ghostandmachine said:**
> So, I had the drivers working at one time when I had Ubuntu Studio on my Dell Inspiron 1150 but I uninstalled, then reinstalled Feisty. Anyway, followed the instruction for installing on the Help pages. It says it's installed but it's not seeing any of my wireless points.

Driver is a BCM4309. I don't even know if I have the right drivers. Dell's website is stupid.

thanks in advance.

I used NDIS Wrapper to get my broadcom wireless adapter going and it works fine but it's range is VERY limited.  This may be your problem?

---

