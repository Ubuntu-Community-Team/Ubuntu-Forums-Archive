---
title: "Installing Enemy Territory"
date: 2010-11-05
forum: Gaming &amp; Leisure
---

### Post by WG- on 2010-11-05
Well I want to install ET on ubuntu.

I was following this guide: [http://www.katanoon.nl/ubu-e/install.php](http://www.katanoon.nl/ubu-e/install.php)

In step two it says (other guides tell me the same [https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)):
> 
Step 2: Install RTCW: ET
sudo apt-get install libgtk1.2

Well I tried that and it didn't work. Well I then looked for the package in synaptic package manager and I found that I have installed libgtk2.0-0. Now my brain tells me that this is just a  upgrade of libgtk1.2. So no worries right?

I then tried just tried to install ET and it produces the following error:
> error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


So it has problems with it that I don't have libgtk-1.2... so what do I do now? (I still assume that libgtk-2.0-0 is a better version of libgtk-1.2) Should I install libgtk-1.2 from [https://launchpad.net/ubuntu/+source/gtk+1.2?](https://launchpad.net/ubuntu/+source/gtk+1.2?)

---

### Post by WG- on 2010-11-05
Hmmm I fixed the problem, apparently I could just continue the installation and disregard that problem I figured out. 

Only question left is if someone knows where the latest patch of ET can be downloaded?

---

### Post by Sticky_Bit on 2010-11-05
[http://www.planetwolfenstein.com/files/files.shtml](http://www.planetwolfenstein.com/files/files.shtml)

---

### Post by WG- on 2010-11-06
> **Sticky_Bit said:**
> [http://www.planetwolfenstein.com/files/files.shtml](http://www.planetwolfenstein.com/files/files.shtml)
Thanks for the link for some reason I didn't found that site with google.

---

