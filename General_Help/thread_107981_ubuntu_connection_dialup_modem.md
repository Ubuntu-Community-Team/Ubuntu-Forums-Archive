---
title: "ubuntu connection dialup modem"
date: 2005-12-24
forum: General Help
---

### Post by Doc504 on 2005-12-24
I installed ubuntu 5.10 on my old win98/2ed (which I wiped)--it looks like a great os but how do I connect to the internet by dialup modem?  Is there some step by step instructional webpage that explains this for a linux newbie?
Thanks.:confused:

---

### Post by towsonu2003 on 2005-12-24
Check whether you see your modem in System>Administration>Networking. If you don't see it (probably so): Try reading through the links in my signature, except the first one. The wiki is the most easy one (good to start with that)... good luck.

---

### Post by Doc504 on 2005-12-27
If you are trying to determine the type of modem your computer( which now has Ubuntu)  and you are not able to connected to the internet with this computer (because I have wiped it out) would I need to reinstall the old wins 98 in order to do this?  Seems likely?

---

### Post by towsonu2003 on 2005-12-27
Installing Win98 won't help you if you want to connect to internet using ubuntu / linux. 

If you dont see your modem in System>Administration>Networking, then you probably have a winmodem (a modem type that is hard to make work in linux), in which case you will have to read those links... 

Steps to follow (briefly) are: 

1. This description: > A Winmodem is a combination of hardware known as chipset (much less than in a true pure hardware modem) and software  (written for the infamous Windows operating systems family).
A Linmodem is a Winmodem working under the famous Linux operating system. from [http://132.68.73.235/linmodems/index.html#linmodems](http://132.68.73.235/linmodems/index.html#linmodems)

2. Go to linmodems.org and download scanModem and use scanModem tool 

3. Read output of the tool and use the info to get drivers, if available... 

This links seems to cover this info very nicely: [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

---

