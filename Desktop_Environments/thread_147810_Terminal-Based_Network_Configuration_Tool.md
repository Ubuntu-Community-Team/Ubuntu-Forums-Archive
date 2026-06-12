---
title: "Terminal-Based Network Configuration Tool"
date: 2006-03-20
forum: Desktop Environments
---

### Post by tom purl on 2006-03-20
Hi, I'm having problem with ndiswrappers right now, and more than once I've accidentally blown away *all* of my network settings (/etc/hosts, /etc/hostsname, etc.).  Right now, everything is so foobared that I can't even use some gui apps that require sudo access.

Is there a terminal-based app that I can use to set up my networking?  Any help would be greatly apprecaited.

Thanks again!

Tom Purl

---

### Post by dbw on 2006-03-21
I have typically used the commands iwlist, ifconfig, and iwconfig.  Here's the way I role (for completeness, and assuming that my wireless is on ath0) :

sudo ifconfig ath0 up                #this activates  ath0
iwlist ath0                                  #lists all networks that ath0 sees
sudo iwconfig ath0 ESSID "networkname"
sudo iwconfig ath0 key 0a:0a:0a:0a:0a

this should set you up, but sometimes you have to recycle the up/down status of ath0 afterwards:

sudo ifconfig ath0 down
sudo ifconfig ath0 up

then rock on:
ping [www.some_random_site.com](www.some_random_site.com)

---

### Post by tom purl on 2006-03-21
Thanks dbw!  That fixed my problems.

---

