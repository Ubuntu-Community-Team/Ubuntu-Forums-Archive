---
title: "How to get Unity?"
date: 2011-03-18
forum: Desktop Environments
---

### Post by Hatryst on 2011-03-18
Hi. How can I get the Unity Desktop Environment on my Ubuntu Desktop (10.10)?
DO I need to install Ubuntu 10.10 Netbook version?

---

### Post by ankspo71 on 2011-03-18
Hi,
You can install the package called "ubuntu-netbook" which will install everything required to have the Ubuntu Netbook Edition. Once "ubuntu-netbook" is installed, you will need to log out, then click on your name in the login screen, then choose "Netbook Edition" (or similar) in the session menu at the bottom of the screen, then enter your password and continue to login. 

Unity can also be installed separately by installing the package called "unity", but it won't have all of the settings and artwork of the Netbook Edition. You will also be missing the session menu entry and scripts needed to start the desktop automatically upon login, so a command like "unity --replace" will be needed to start the unity desktop.

Hope this helps.

---

### Post by kerry_s on 2011-03-18
> **Hatryst said:**
> Hi. How can I get the Unity Desktop Environment on my Ubuntu Desktop (10.10)?
DO I need to install Ubuntu 10.10 Netbook version?

if you want unity, the best version is on ubuntu 11.04, the 1 in 10.10 is very limited & feels incomplete, most just say it sucks.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by L'ami Francais on 2011-03-24
you can try unity-2d in 10.10. it is not as fancy as the one in Natty but still looks  good. it is the version design for lower spec machine.
you can find a tutorial here:[http://techie-buzz.com/foss/ubuntu-unity-2d-install.html](http://techie-buzz.com/foss/ubuntu-unity-2d-install.html)

the summary is in the terminal:
$ sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily
$ sudo apt-get update
$ sudo apt-get install unity-qt-default-settings

After the installation, log out from your current session. In the login screen, you will see &#8220;Unity 2D&#8221; in a drop-down menu. Pick that and login again. You should have the new UI now.

hope this helps
Nicolas

---

### Post by mysoogal on 2011-05-20
> **Hatryst said:**
> Hi. How can I get the Unity Desktop Environment on my Ubuntu Desktop (10.10)?
DO I need to install Ubuntu 10.10 Netbook version?


do not install Unity Desktop Environment, you will cry later

---

### Post by Frogs Hair on 2011-05-20
You can get Unity _2D_ via a PPA .

[http://www.omgubuntu.co.uk/2011/05/unity-2d-ppa-for-ubuntu-10-10-users/](http://www.omgubuntu.co.uk/2011/05/unity-2d-ppa-for-ubuntu-10-10-users/)

---

