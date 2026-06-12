---
title: "wifi not working on inspiron 1525"
date: 2008-08-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by davidmiller252 on 2008-08-15
I just got a brand new dell inspiron 1525 preinstalled with windows vista. Of course I installed ubuntu 8.04. Now for some reason my wireless is not functioning at all. I set internet connection to roaming and everything, but it still doesn't work. I have vista installed on it as well, and it works fine under windows.

---

### Post by wallas on 2008-08-16
My brother's laptop has got the same problem, but we are just running the LiveCD...

---

### Post by bigbrovar on 2008-08-16
can u please state the type of wireless card ur laptop uses .. some wireless crads dont have native drivers for ubuntu .. but there are work arounds that would make them work .. also u can go to Hardware driver under system/administration/Hardware Drive ..its the utility that displays the drivers for your system that as not been installed and offers to install them .. if u see any driver they u just enble the driver by ticking the check box .. and ubuntu would download and install the driver .. 

to see the type of wireless card u are using just open terminal Application/Accesssories/Terminal  and run this ```
lspci
```
this would display all the drivers u have on ur system .. read through and check for anything about your wireless

---

### Post by Minipalmer on 2008-08-16
Hey there Dave. I, too, am using an Inspiron 1525. I had a buddy help me set up Ubuntu, and we installed every update we could find for Ubuntu, and it updated the driver for the wireless card and sync'd it with Ubuntu.

Have you done all the updates? Try System > Administration > Update Manager

---

### Post by cpetercarter on 2008-08-16
At a guess,your Inspiron 1525 has an Intel 3945abg wireless card. If so, have a look at [http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/]("http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/"). Make sure that you have the linux-backports-modules-hardy-generic packageinstalled.

---

