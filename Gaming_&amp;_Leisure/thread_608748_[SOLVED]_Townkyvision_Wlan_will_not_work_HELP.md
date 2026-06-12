---
title: "[SOLVED] Townkyvision Wlan will not work HELP"
date: 2007-11-10
forum: Gaming &amp; Leisure
---

### Post by djcla on 2007-11-10
HI,,

I have installed Twonkyvision and got it to work fine over ethernet but just cannot get the 360 to see it over wlan and do not understand why.  I have tried running 
sudo route add -net 224.0.0.0 netmask 240.0.0.0 dev wlan0 but this does not help .   I just do not understand why my xbox cannot see the media server while on wireless yet it works fine on fixed LAN.  Anyone help?

---

### Post by djcla on 2007-11-11
working now, not sure what i did, could be one of 2 things changed the wireless channel on my netgear router to auto and added the following 2 lines in a teminal session.

sudo iptables -A INPUT -i wlan0 -p tcp -m tcp --dport 9090:9091 -j ACCEPT
sudo iptables -A INPUT -i wlan0 -p udp -m udp --dport 9020:9021 -j ACCEPT

---

