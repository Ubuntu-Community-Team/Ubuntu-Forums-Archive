---
title: "followed the &quot;1390 wireless configuration tutorial&quot; but just got worse"
date: 2007-07-12
forum: Dell  Ubuntu Support
---

### Post by ashrafabdeljaber on 2007-07-12
Ok, so i have a fresh installed ubuntu 7.04. I'm a noob in linux so please bear with me.
At first, when I click on the network icon it showed two links "enable networking", which was checked and "enable wireless" which was also checked

I followed this tutorial [http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html) to try to get my broadcom 1390 wireless to work. Now the "enable wireless" isnt shown and I still have the problem of not being able to use my wireless card.

All help is much appreciated.

---

### Post by apjjr on 2007-07-12
I did this and it worked fine.  ndiswrapper is a program that privides an environment to run a windows device driver.  After installing ndiswrapper you must use ndiswrapper to install the windows driver.
Please post the output of ndiswrapper -l.  You should see something like the following:
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

Make sure you followed the steps carefully.

-Alex

---

