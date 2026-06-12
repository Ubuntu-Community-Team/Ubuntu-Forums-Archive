---
title: "Studio 1749 - wireless not working"
date: 2010-07-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by piratemari on 2010-07-10
I recently got a new Dell Studio 1749 and installed Lucid Lynx alongside Windows 7 (which, unfortunately, I need for school). I'm not that new to Ubuntu, and used it on an older dell, and loved it so much. (by used it I mean used only Ubuntu on that laptop) Once I installed Lucid on this laptop in a partition I had an issue with the whole "no module found" which I fixed by getting rid of dell's backup and mcaffee. Then it seemed good after that. Everything worked fine except for one thing. The wireless doesn't show any connections.

I installed ndiswrapper and downloaded the proprietary drivers for my laptop - didn't work. I made sure that my wireless is actually turned on - still nothing.  I'm not sure what to do now, I can connect using my wired network but that's really annoying and it means that I can basically only use Ubuntu while being at home, in the living room. When I installed the driver it shows that the hardware is not present. I still have the driver installed. The wireless IS turned on, and it works perfectly on Windows 7. I used my service tag to get the drivers, so that is also the correct driver. 

lspci brought up that my wireless device is a Broadcom Corporation Device 4727. dell calls it a Wireless WLAN 1397/1520 Half MiniCard. Yes both numbers, two different cards but it shows them both in my drivers list when I use my service tag. I downloaded the drivers and they were the exact same driver for both card types. Iunno what's up with that. 

I would really, really appreciate some help getting this to work. Thank you!

~Mari

---

### Post by simosx on 2010-07-10
Did you try the steps from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) ?

You mentioned you installed ndiswrapper. I am not sure if you installed manually in contrast to the updated way in the current version of Ubuntu.

---

### Post by piratemari on 2010-07-11
They don't have my device on the list, we already looked it over. Also, I manually installed it.

---

