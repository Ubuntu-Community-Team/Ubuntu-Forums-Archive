---
title: "Canadian Can't get wifi working on Dell D810 Lucid"
date: 2010-05-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bevboy0223 on 2010-05-08
Hi, everyone.  

I am trying not to biff the computer out the window, but it's hard to resist.  I installed 10.4 this evening, on my Dell Latitude D810 laptop.  Ethernet connection works just great.   The wifi doesn't work at all.  I checked the bios, and the wireless is turned on.  I right click on the wifi icon on the desktop, and it says wireless is connected.

I have been trolling the forums over the last few minutes and have seen numerous problems with wifi.  I have tried many of the things suggested, and there's been no relief for me whatever.

I am in Canada.  I hear there has been a problem with the Canadian repositories.  I downloaded 10.4 from a Canadian server.

I ran lscpi | grep -i network

It says:

Broadcom Corporation BCM4318 [Airforce One 54G] 802.11g wireless lan controller (rev 02)


What information do you want me to provide you?  

Thanks for your help!

Bev

---

### Post by sandyd on 2010-05-08
install b43-fwcutter

---

### Post by bevboy0223 on 2010-05-09
And how does one install that?

---

### Post by dernier_recours on 2010-05-09
Have you activated the proprietary driver?

System>Administration>Hardware drivers

Make sure the wifi is activated (my Dell has a green light on the dash - to switch on and off wifi, hold the Fn key and hit F2).

If you think you need to install b43-fwcutter, open a terminal and paste the following command.

```
sudo apt-get install b43-fwcutter
```

---

