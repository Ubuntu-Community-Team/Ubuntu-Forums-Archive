---
title: "Dell inspirion 1721 7.04, wireless Broadcom 1505 card working, cant bring up Wlan"
date: 2007-09-06
forum: Dell  Ubuntu Support
---

### Post by slim shady on 2007-09-06
OK, I have everything working; DVD, touch pad, screen resolution and my wireless card. A Dell 1505 Wlan card. I am using the  1.47.2 Ndiswrapper and  the Broadcom driver.

Compiled from the Ubuntu forum how to fluffy method. Wireless light comes on but I cant bring up the network interface for the Wlan. 

I need help, this is beyond my expertise, I don't have a clue where to start

---

### Post by bobdole211 on 2007-09-09
Wow, hey, what Broadcom driver did you use with ndiswrapper?

I too have the 1721 with the Broadcom 1505 wireless-n card.  Happen to have a link for which driver you used?

Sorry I didn't answer your question.  That's beyond my expertise as well.

---

### Post by slim shady on 2007-09-22
Sorry for the long time between posts, i used the driver supplied for vista and installed it in NDiswrapper. Works at times and doesn't work other times. I have never been able to get the network manager to recognize it though. So it still isn't working.

---

### Post by bobdole211 on 2007-10-02
So I'm using Debian Unstable (which is similar to Ubuntu, considering it's based on Debian) and I've gotten open networks to work on my Dell Inspiron 1721.

Below is my lscpi info:

0b:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 03)

I am using the Dell R151517.exe driver with ndiswrapper, which is located here:

[http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R151517&formatcnt=1&libid=0&fileid=202136](http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R151517&formatcnt=1&libid=0&fileid=202136)

This is the tutorial I used (it's for Debian, but I'm sure it's similar to Ubuntu (or can be modified to work in Ubuntu):

[http://www.debian-administration.org/articles/401](http://www.debian-administration.org/articles/401)


The highlights of the article are (just in case the page disappears):

apt-get install module-assistant

module-assistant prepare

apt-get install ndiswrapper-source

module-assistant build ndiswrapper

apt-get install ndiswrapper-utils-1.9 (the article says 1.8 but that's no longer in the repisitory)

module-assistant install ndiswrapper



Now go to the location of the inf file for the Broadcom driver and type:

ndiswrapper -i bcmwl5.inf

depmod -a
modprobe ndiswrapper


Now at this point if you type ifconfig you should see a wlan0 (or something similar, something new for wireless.  At least I did when I used this driver vs. the R151520.exe that comes with Vista 32bit.)



At this point you need to type:

iwconfig wlan0 essid any
iwconfig wlan0 mode auto
dhclient wlan0

If you're in range of an open network after typing iwconfig wlan0 essid any, you should see the open network you're connected to when typing "iwconfig wlan0".  I'm not entirely sure if the "iwconfig wlan0 mode auto" is necessary, but /shrug.  After typing that I saw that I was given an ipv6 address (I'm currently at a public library), so I typed in the dhclient wlan0 as the tutorial suggested and this gave me an ipv4 ip.  I was then able to connect and type this out!

Later I will try to set up encryption using a secured router but for now I'm happy that this works!

---

