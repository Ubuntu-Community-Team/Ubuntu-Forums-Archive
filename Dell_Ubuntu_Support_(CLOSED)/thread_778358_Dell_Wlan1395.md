---
title: "Dell Wlan1395?"
date: 2008-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by blankd3ckskat3r on 2008-05-02
i have bought an inspiron 1525 preinstalled with vista. i downloaded the 8.04 hardy iso and loaded it to the laptop. works great, no complaints besides my wlan isnt working. i have the dell wlan1395 card. ive searched everywhere, and cannot find anything. i tried installing the windows driver through ndiswrapper and it says it installed correctly but i still have no connections. can anyone help?

---

### Post by ticat85 on 2008-05-02
I'm having the same problem with 1395. And I'm lost as to how to work it... all I know is that the bcmwl6.inf is the driver and you can get it on the Dell Support website.

---

### Post by mpn22 on 2008-05-02
I used the bcmwl5.inf from here [http://ftp.us.dell.com/network/R174291.exe](http://ftp.us.dell.com/network/R174291.exe) with ndiswrapper and it works without any problems. just use unzip R174291.exe and run ndiswrapper on the inf file in the DRIVER_US directory. Got my solution from here: [http://ubuntuforums.org/showthread.php?t=704088](http://ubuntuforums.org/showthread.php?t=704088)

p.s. running it on hardy x64 on a XPS M1530

---

