---
title: "Wireless Internet problem"
date: 2005-10-18
forum: Desktop Environments
---

### Post by MrPolo on 2005-10-18
Hello,

I installed Ubuntu Hoary a week or 2 ago and my Wireless internet still doesnt work :(

I got some help from some friends, but no result...

I have an Acer Aspire 1692 with an 802.11b/g wireless Lan.

Thx 

Greetz
MrPolo

---

### Post by ksousa on 2005-10-18
I,v the same problem with an Acer Aspire 1800...and i think that Ubuntu and acer is not a good marriage...sorry

---

### Post by MrPolo on 2005-10-19
:(:(

Dont tell me there is no solution plz :)

---

### Post by mrmarco on 2005-10-30
Here it works, with :
[LIST]
[*]Ubuntu Breezy
[*]This setting for the ipw2200 wlan driver :
```
echo "options ipw2200 led=1" > /etc/modprobe.d/ipw2200
```
[*]These settings for the acerhk driver :
(download it from [http://www.informatik.hu-berlin.de/~tauber/acerhk](http://www.informatik.hu-berlin.de/~tauber/acerhk) here it works with version 0.5.28 )
In /etc/modprobe/acerhk, put :
```

# module parameters for acerhk
options acerhk usedritek=1 autowlan=1 force_series=1690
# reset transceiver on load
install acerhk /sbin/modprobe -r ipw2200  && modprobe --ignore-install acerhk && /bin/echo 1 > /proc/driver/acerhk/wirelessled

```
[*] Be warned : the ipw2200 driver has to be reloaded before use. Therefore, I use a script like this one in order to use wlan (example for fixed ip configuration, use dhclient instead of ifconfig/route if needed) :
```

#!/bin/sh
ifconfig eth1 down
modprobe -r ipw2200
modprobe -v ipw2200
iwconfig eth0 essid "my_essid_name"
iwconfig eth0 key restricted  XXX-XXX-XXX-XXX-XXX-XX
iwconfig eth0 ap YY:YY:YY:YY:YY:YY
ifconfig eth0 inet up 10.0.0.7 netmask 255.0.0.0
route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.0.0.1 dev eth0

```
[*] It is even possible to bind the orange button to bring the wlan interface up, but it is trickier than it looks like, because the above script has to be run by root, see the "super" package and /or [http://lea-linux.org/cached/index/Dev-suid_scripts.html](http://lea-linux.org/cached/index/Dev-suid_scripts.html) (in french) for explanations and solutions.
[/LIST]

Hope It Helps,

Mrmarco

---

### Post by chatuser on 2005-11-23
- edit /boot/grub/menu.lst
- change acpi=off to noapic
- reboot your computer

Everything works now, damn ACPI !!

---

