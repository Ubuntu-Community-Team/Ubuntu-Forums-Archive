---
title: "libpcap0.8-dev error install ?"
date: 2011-10-29
forum: Egypt Team
---

### Post by fairbird on 2011-10-29
&#1581;&#1575;&#1608;&#1604;&#1578; &#1578;&#1579;&#1576;&#1610;&#1578; &#1576;&#1575;&#1603;&#1580; [B]libpcap0.8-dev &#1608;&#1604;&#1603;&#1606; &#1581;&#1583;&#1579; &#1604;&#1610; &#1582;&#1591;&#1574; &#1603;&#1605;&#1575; &#1607;&#1608; &#1605;&#1576;&#1610;&#1606; &#1575;&#1587;&#1591;&#1585; &#1575;&#1604;&#1582;&#1591;&#1574; &#1601;&#1610; &#1575;&#1604;&#1578;&#1610;&#1585;&#1605;&#1610;&#1606;&#1604;
[/B]
**> **fair@ubuntu:~$ sudo apt-get install libpcap0.8-dev Reading package lists... Done
Building dependency tree 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
libpcap0.8-dev: Depends: libpcap0.8 (= 1.0.0-6) but 1.1.1-6 is to be installed
E: Broken packages****
 
**&#1608;&#1601;&#1610; &#1575;&#1604;&#1600; source.list &#1601;&#1602;&#1591; &#1587;&#1591;&#1585;&#1610;&#1606; &#1603;&#1605;&#1575; &#1607;&#1608; &#1605;&#1608;&#1590;&#1581;**

> deb [[COLOR=#38659d]http://archive.ubuntu.com/ubuntu[/COLOR]]("http://archive.ubuntu.com/ubuntu") lucid multiverse restricted universe main deb-src [[COLOR=#38659d]http://archive.ubuntu.com/ubuntu[/COLOR]]("http://archive.ubuntu.com/ubuntu") lucid multiverse restricted universe main #Added by software-properties 
 
**&#1575;&#1587;&#1578;&#1582;&#1583;&#1605; ubuntu 10.04**

---

### Post by thelinuxer on 2011-10-31
&#1571;&#1592;&#1606; &#1573;&#1606;&#1578; &#1605;&#1581;&#1578;&#1575;&#1580; 

sudo apt-get update
sudo apt-get install libpcap0.8-dev

---

### Post by ashams on 2011-10-31
[RIGHT]&#1605;&#1605;&#1603;&#1606; &#1578;&#1580;&#1585;&#1576; &#1578;&#1606;&#1601;&#1584; &#1575;&#1604;&#1571;&#1605;&#1585; &#1583;&#1607; &#1605;&#1606; &#1575;&#1604;&#1591;&#1585;&#1601;&#1610;&#1577;:
&#1604;&#1601;&#1578;&#1581; &#1575;&#1604;&#1591;&#1585;&#1601;&#1610;&#1577; &#1575;&#1590;&#1594;&#1591; Ctrl+Alt+T
 &#1579;&#1605; &#1575;&#1603;&#1578;&#1576; &#1575;&#1604;&#1571;&#1605;&#1585; &#1575;&#1578;&#1575;&#1604;&#1610;:
sudo apt-get install -f

&#1575;&#1604;&#1605;&#1589;&#1583;&#1585;:
[http://askubuntu.com/questions/34431/ubuntu-software-centre-fails-with-package-catalog-error](http://askubuntu.com/questions/34431/ubuntu-software-centre-fails-with-package-catalog-error)
&#1608;&#1576;&#1593;&#1583;&#1610;&#1606;

sudo apt-get update
sudo apt-get install libpcap0.8-dev
[/RIGHT]

---

