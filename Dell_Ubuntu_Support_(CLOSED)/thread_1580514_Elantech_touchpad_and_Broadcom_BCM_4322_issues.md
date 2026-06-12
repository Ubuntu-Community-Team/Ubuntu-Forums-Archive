---
title: "Elantech touchpad and Broadcom BCM 4322 issues"
date: 2010-09-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lxlv01 on 2010-09-23
I have recently got a new old stock inspiron 11z. machine seems to be perfect with 10.04 except from two issues.

1. Touchpad: it is one of those that had the Elantech touchpad. I know some people didn't like it, but i am not peculiar in this, just need to be able to condigure it the way i want. ubuntu doesn't recognize it, no touchpad options, and it appears as a logitech PS/2 mouse in the configuration files. The touchpad works, but i cannot change anything on its configuration like disabling tap to click or anything else. Is there any solution for this?

2. Broadcom 4322. while the card is recognized, and i have installed the proprietary drivers, wifi seems ultra-slow at random times, and disconnects. reboot helps but after a while the same thing happens. with iwconfig i found that there is no wlan0 interface but it is displayed as eth1. I did some search on launchpad and the forums and realize the issue with various other symptoms is common but found no definite solution. has anyone solved the problem installing wicd on this machine? it has helped me in the past to solve me some wireless problems on other machines and i guess that wireless should work on such an ultra-portable thing. 

i am running 10.04.1, clean installation from usb stick as a sole OS, no dual boot, updated until today, through an ethernet connection.  

thank you

---

### Post by lxlv01 on 2010-09-28
just an update in case someone faces anything similar, i have installed wicd and tested wireless with a thomson 585v7 router over a fair distance. it seems that wicd solves the issue and i can have a stable and fast connection with signal at 30%-40%. For a couple of days this configuration has lasted and i have had no issues with disconnects or very limited speeds as with the network manager. I really hope this solution is permanent and lasts and that it is helpful for someone else.

i haven't done anything for the touchpad, because most suggestions seem to consume more time to implement, than actually get used to it. i am also using a usb mouse when i can. perhaps in the future i will deal with it.

---

