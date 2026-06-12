---
title: "wireless as well as the ethernet driver not working"
date: 2010-02-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by renjumace on 2010-02-22
hi,
   i have installed ubuntu 9.10 karmic on my dell 1525 inspiron. the wireless and the ethernet drivers are not working (i suppose!). i tried to get the broadcom driver (BCM4312 802.11b/g) from the broadcom site for linux, but the output from the steps explained on the site didnt match with mine. also when i connected the ethernet cable, the message shown was, the default option for the wired network came showing that the connection has been established but i wasn't able to open any site even after the message showed connected. please help me in this regard. i used ubuntu 9.04 and it was perfect. but i kinda liked the appearance of karmic thats why i want to use it. And by the way my ethernet port driver is that of marvel (88E8040 PCI-E Fast Ethernet Controller). since i dont have either the wireless or wired access to the internet, i am finding it hard to sit on other computers and find the solutions. Please help me in this regard.

---

### Post by wankel786 on 2010-02-22
When you go wired, type in a terminal

sudo dhcpcd

See if that works for you.

---

### Post by gibbylinks on 2010-02-24
Just in case, have you looked at the restricted drivers. All I had to do was activate that on my 1501 and it works no problems.

---

### Post by lethalrhymezz on 2010-03-01
go to your admin setting in the system menu. there is smth like user acoount settingz which is kind of similar to windows. Browse the guest account settings and tick the box - access internet, wifi etc. The problem is that usulally u r logged as a guest not as a root and there are some restrictions. There is also an option to enable your ethernet adapter if u use wired connection.

---

