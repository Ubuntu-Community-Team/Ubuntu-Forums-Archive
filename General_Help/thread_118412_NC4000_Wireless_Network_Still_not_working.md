---
title: "NC4000 Wireless Network Still not working"
date: 2006-01-16
forum: General Help
---

### Post by kuosion on 2006-01-16
Please review this forum:
[http://ubuntuforums.org/showthread.php?t=117914](http://ubuntuforums.org/showthread.php?t=117914)


So basically i have tried many things to fix this wireless network. Nothing is working so I am hoping for this one last chance to fix it before i go back to XP pro :(

---

### Post by hbush on 2006-01-20
following the instructions on: [http://ubuntuforums.org/showthread.php?t=52223&highlight=wireless+nc4000](http://ubuntuforums.org/showthread.php?t=52223&highlight=wireless+nc4000) I managed to fix the problem the very first days :) Its not peace of cake. Waht I did is: 

did a backup of /etc/network/interfaces and edited the same file 

> sudo pico /etc/network/interfaces 

which now looks like this: 

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
# mapping hotplug
# 	script grep
# 	map ath0

# The primary network interface
iface ath0 inet dhcp
wireless-essid yourESSID
wireless-key yourwepkey

iface eth0 inet dhcp

auto ath0

auto eth0


then rebooted ... it worked

if it doesn't (cose the first time I installed didn't worked ... bthw I installed ubuntu 3 times  :???:  but now it works) I typed the following:
 
> sudo ifdown ath0
sudo ifdown eth0
sudo iwconfig ath0 channel URchannel
sudo iwconfig ath0 essid UR_ESSID
sudo iwconfig ath0 key URWEPKEY
sudo iwconfig ath0 mode managed

(see all commands by typing iwconfig --help and before I entered the last command I did a right clik on the network icon and on properties I changed the network name to ath0 then)

sudo ifup ath0 


if still not working (keep calm) reboot. 
one more thing, the wireless button on the tuchpad is functioning so do not tuch it in between. 
if still doesn't work please let us know.

---

