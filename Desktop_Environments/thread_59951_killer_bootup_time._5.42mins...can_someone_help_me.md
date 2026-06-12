---
title: "killer bootup time. 5.42mins...can someone help me here"
date: 2005-08-25
forum: Desktop Environments
---

### Post by byen on 2005-08-25
hey guys,
My bootup time sucks! it takes forever to boot and Im tired of rebooting again and again.and since hibernate and standby are not supported....the least i wanna do is boot faster....can some one help me here.....here is the summary that my Boot Up Manager shows:

> syslogg -system logging service
klogd-logs system events
alsa-sound arch services
gdm-gnome disp.manager
ppp-manages internet access via modem
cupsys-manages print jobs
makedev-creates special files that interact with hardware
systemimage-server - upgrades over the network
inetd-manager for incoming internet connections
systemimage-server-flamethrowerd-systemimager boot binaries for 1386 client nodes
pppstatus-console based ppp status monitor
netbootmond-automate gnu/linux installs and upgrades over network
powernowd-controls cpu speed and voltage
postfix-high performance mail server
rsync-fast remote file prog
flamethrower-multicast file distribution util
pcmcia-manages insertion/removal of laptop cards
emifreq-applet - cpu scalling applet
apmd-monitors battery status for old laptops
dbus-1 - delivers messages between applications
acpid-perform intelligent power mgmt
firestarter- firewall
kdm-kde disp manager
mdadm-manages multiple disk devices for fault tolerance
cron-runs system house keepin chores
atd-enables scheduling of jobs
binfmt-support - support for extra binary formats
fetchmail - mail retrieval and forwarding utility
acpi-support - for laptops...saves power

PS- just a note: most of the bootup time is being spent on " loading ndiswrapper"...i guess it is trying to find a network or something,,,, but i wish i could get it down as my ATiand linux standby dont get along well so its kind of a drag to have a restart and wait.....oh well...!

by the way I have a AMD 2800+768Mb, ati radeon U1 using the 7500 chipset!

Any help here would be greatly appretiated.

---

### Post by amohanty on 2005-08-26
> loading ndiswrapper 

ndiswrapper is mostly used for wireless network cards that are not as yet fully supported by linux or for other network cards. From ndiswrapper.sf.net:

> Some vendors do not release specifications of the hardware or provide a linux driver for their wireless network cards. This project implements Windows kernel API and NDIS (Network Driver Interface Specification) API within Linux kernel. A Windows driver for wireless network card is then linked to this implementation so that the driver runs natively, as though it is in Windows, without binary emulation. 

If you have a network card that does not need it remove it from the bootup menu using BUM.

For the rest:

ppp-manages internet access via modem
- remove if you do not use a modem to connect to the internet

inetd-manager for incoming internet connections
- I would suggest replacing with xinetd but  thats your choice.

pppstatus-console based ppp status monitor
- see ppp comment

netbootmond-automate gnu/linux installs and upgrades over network
systemimage-server-flamethrowerd-systemimager boot binaries for 1386 client nodes
- remove if you the machine does not server as a remote boot server

postfix-high performance mail server
- remove if you do not need a mail server

flamethrower-multicast file distribution util
- see comment for netbootmond

pcmcia-manages insertion/removal of laptop cards
- remove if machine is not a laptop or does not use PCMCIA cards

apmd-monitors battery status for old laptops
- remove if machine not old laptop

kdm-kde disp manager
- WAIT a sec why do you need kdm AND gdm?? 

mdadm-manages multiple disk devices for fault tolerance
- remove if you do not use raid, remove anyway

atd-enables scheduling of jobs
- remove if you already have cron

fetchmail - mail retrieval and forwarding utility
- remove if you do not use a mail server

HTH
AM

---

### Post by nad on 2005-08-26
Not knowing how you connect to the network or use your computer, I could only surmise as to which services you do not need.

There are several you may be able to do without. I haven't looked at bum yet. Is it able to edit your init scripts or will you need instructions to not start services?

---

### Post by byen on 2005-08-26
[QUOTE=nad]Not knowing how you connect to the network or use your computer, I could only surmise as to which services you do not need.

There are several you may be able to do without. I haven't looked at bum yet. Is it able to edit your init scripts or will you need instructions to not start services?[/QUOTE]
 I only connect to the internet using my wireless card which i have configured using the ndiswrapper. the deal is...when booting the ndiswrapper stalls and looks for a preferred network....and then resumes bootup.this takes abt 70% of my boot time... wonder if there is any way i could jut load the ndiswrapper and connect to the preferred network later....

-thank you for your help..

PD- BUM lets be edit bootup services without any problems..all i have to do is uncheck the program....pretty simple

---

### Post by nad on 2005-08-26
In that case, uncheck networking. I seem to recall, however, that you may need to edit /etc/network/interfaces to remove the hotplug ability of the network subsystem.

As the previous post described, there are several more services that you may disable.

In addition, you may wish to disable cupsys (the printing subsystem) if you will not be using it, as well as ppp and if you are behind a hardware firewall (router) you can probably do without firestarter.

---

