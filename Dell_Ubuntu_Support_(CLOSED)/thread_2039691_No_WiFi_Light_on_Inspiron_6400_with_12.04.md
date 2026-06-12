---
title: "No WiFi Light on Inspiron 6400 with 12.04"
date: 2012-08-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by carve111 on 2012-08-09
Help. I can't get the wifi light on, on my laptop( Inspiron 6400). It was fine when I had 10.10.  I get this with additional drivers:
[COLOR=Red]This package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware[/COLOR].
and this: [COLOR=Red]0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)[/COLOR] when I  [COLOR=Red]lspci -vvnn | grep 14e4

[COLOR=Black]I think I have the right drivers, I just can't get the bloody light on.
Sorry to be a pain in the ****. Total newby.  :confused:
[/COLOR][/COLOR]

---

### Post by wildmanne39 on 2012-08-11
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/netscript.sh && chmod +x netscript.sh && ./netscript.sh
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.

Also please change the red font back to black.
Thanks

---

### Post by Tobeus on 2012-08-13
There are a couple of basic things to check on Dells first off.  Some sound silly, but check them anyway, it could save you a ton of aggravation, and often times are the culprit.

1.  Check to see if your wifi is turned off by pressing Fn + F2 (not sure if this works in Ubuntu, but it's so easy to try).
2.  Check in the bios (f2 on Dell boot logo screen when you first power up) and see if the wifi is disabled.

Otherwise, it is probably driver related, and I'm not good enough to help if that is the case.  Either way, good luck!

-Tobeus

---

