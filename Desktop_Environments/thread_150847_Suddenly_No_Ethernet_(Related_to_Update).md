---
title: "Suddenly No Ethernet (Related to Update?)"
date: 2006-03-26
forum: Desktop Environments
---

### Post by n00buntu on 2006-03-26
Hello,

  I've installed 5.10 a couple of days ago, and was very pleased with how it works (thanks!). Unfortunately, suddenly my ethernet connection seems completely down. AFAIR, the last thing I did before it died was to upgrade (via that reddish-looking icon on the top bar of the desktop), then reboot the computer. 
  Now I have the following probelms:
1. When the computer starts up it reaches the point where it says "bringing up interface eth0" (or something like that), then switches to some text screen for a **very** long time, then returns to the graphical loading screen before I can see what it wrote.
2. There is no internet connectivity whatsoever. 
3. ifup -n eth0 outputs:
ifup: interface eth0 already configured
4. sudo dhclient eth0 ouputs:
There is already a pid file /var/run/dhclient.id with pid 1
...
...
<some lines>
...
...
send_packet: Network is down
...
No working leases in persistent databases - sleeping.
5. ping [www.yahoo.com](www.yahoo.com) outputs:
ping:unknown host [www.yahoo.com](www.yahoo.com)

(I don't know what any of this stuff means).

  Is there some way to fix this?

  Many Thanks!!

---

