---
title: "Automatic connceted to bsnl broadband"
date: 2011-02-11
forum: Delhi Team
---

### Post by ishtvibhu on 2011-02-11
Recently I have installed wine to use barahdirect software which is a roman to devanagari unicode software which works wonder in windows. but after installing wine, I see that each time I boot my system and switch on my broadband modem, I am automatically connected to internet although I had to run following script to connect to internet previouslly
sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1 eth0
sudo pppoeconf
sudo pon dsl-provider
sudo /etc/init.d/networking restart
plog
.......................
A googling has frightened me about installing wine with root privileges. I am unable to know whether the wine has root priveleges or not. THis is the MOST FRIGHTENING THING for me at this moment.
Also, rhythmbox goes out after a selection of file is made to open.
Is this related to wine anyway?
I desperately seeks help

---

