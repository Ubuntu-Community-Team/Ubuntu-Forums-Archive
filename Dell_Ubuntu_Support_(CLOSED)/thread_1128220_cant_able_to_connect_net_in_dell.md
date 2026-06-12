---
title: "cant able to connect net in dell"
date: 2009-04-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by suhaib1thariq on 2009-04-17
i am having inspiron 15 laptop ....i had vista..now dual booted with ubuntu ... i can able to connect net in ubuntu..while i can able to connect net in vista ...how can i do that ?

---

### Post by vigyani on 2009-04-17
I think the best way would be to call Dell and ask for help.

---

### Post by coffeeaddict22 on 2009-04-17
Hi,
There's a lot of things that cause network problems, and every network is a little bit different.
There's a ton of stuff on the 'net; most of it is good, but Linux has made huge strides in networking recently so some of it is getting a bit out of date.
To start, what network?  Are you trying to connect wired or wireless?
presuming it's a wireless network, a useful start is to open a terminal (applications/accessories) and type in ```
ifconfig
``` which tells you about your network configuration.
Post the results back here if you get more than a couple of lines.  If you don't, type in ```
lshw -C network
``` and post that back too.  That lists the hardware; the -C network limits the output to the network stuff (if you have interest and time just type in lshw and have a look).  
If ifconfig shows you a network is being seen, type in ```
sudo iwlist scan
```
which will tell you about the networks around, what encryptation is required, the signal quality, whether you have an address on the network and a few other things.
Post the results back here if you need more help.  You can also look in the wiki- [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") is an excellent and recently updated wireless network troubleshooter, although it's got a fair bit of detail.

---

