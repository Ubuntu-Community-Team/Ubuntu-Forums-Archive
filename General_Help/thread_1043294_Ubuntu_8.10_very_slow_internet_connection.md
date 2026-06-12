---
title: "Ubuntu 8.10 very slow internet connection"
date: 2009-01-18
forum: General Help
---

### Post by MangoAbacus on 2009-01-18
I have searched on this and have done the following:

Disabled ipv6
added in /etc/dhclinet.conf the addresses for opendns
disabled wireless in network manager (although it does not stick)

the problem is that downloading updates takes a very long time. the package manager will display "Download speed: unknown" also surfing with firefox is extremely slow. Tried the tweaks described in other threads (network.http.pipelining set to true...etc) 

this is a brand new 8.10 install. during install it hung configuring apt and I unplugged network and alt-f2 and killed http process and completed install. I had downloaded the image on 1/17/2009 and verified that no errors on CD. 

it is a compaq presario v4000 laptop with 1.7 Ghz processor and 1 Gb or RAM... Otherwise Gnome works beautifully. 

other machines in network are connecting to internet normally. I use a smoothwall router with all latest updates.

I am about to try reinstall, but do not want to go thru hassle if issue will reoccur. Any help would be appreciated

---

### Post by Rainstride on 2009-01-18
try changing servers, go to software sources and in the "download from" drop down list select "other" and click the botton that says "select best server".

---

### Post by MangoAbacus on 2009-01-18
I am sorry I forgot to mention that i did do this...(I have been working on this since Friday and have done several searches) it did find a server (ubuntu-rocks or something like that) and that did not speed the process up any....I should mention that in what apt-get update returns I saw a lot of 302 found... so I changed it back to main...

---

### Post by Rainstride on 2009-01-18
i had this problem the other day, the ubuntu-rock server wasn't working at all for me so i just manualy set it to a close by server, and i got my updates fine.

---

### Post by zekica on 2009-01-18
I had similar problem with new NetworkManager when it enabled both network interfaces (wired and wireless). Can you right-click and deselect "Enable Wireless" it may help...

Can you post the output of: route -n ?

---

### Post by linux_tech on 2009-01-18
If you are using firefox, this may help
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

---

### Post by MangoAbacus on 2009-01-18
network -n returns

Kernel IP routing table
Destination   Gateway   Genmask        Flags Metric Ref Use Iface
192.168.0.0   0.0.0.0   255.255.255.0  U     0       0   0  eth0
169.254.0.0   0.0.0.0   255.255.0.0    U     1000    0   0  eth0
0.0.0.0       192.168.0.1 0.0.0.0      UG    100     0   0  eth0

not sure if the formatting will remain legible, but here goes.

linux_tech - I have already tried tweaking Firefox...

---

### Post by MangoAbacus on 2009-01-19
I am convinced it was the drivers to the nic card.

documenting here for future reference. 

I actually installed again and the same thing...so I knew it was not Ubuntu...I was surprised since I have installed Ubuntu several times without issues....never with an HP/Compaq laptop though.

i did rmmod 8139too and modprobe 8139too but that did not help either.

I slapped a PCMCIA nic card into it and now internet is flying. 

Laptop -> Compaq Presario V4000

---

