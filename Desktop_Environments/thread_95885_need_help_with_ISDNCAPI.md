---
title: "need help with ISDN/CAPI"
date: 2005-11-27
forum: Desktop Environments
---

### Post by HolgerAckermann on 2005-11-27
First of all: Hello to everyone in this forum, this is my first post here.


I'm using Fritz ISDN card, Ubuntu 5.10 and the packets:
avm-fritz-firmware
avm-fritz-firmware-2.6.12-9
capiutils
libcapi20-3
pppdcapiplugin

Blacklisted "hisax" for hotplug, added "capi" in /etc/moules and inserted my ISPs data for an isdn network connection (ppp0). So far so good, it worked. I added a modem watch to the panel with which I activated and deactivated the connection.

Later, I updated my Ubuntu with available security fixes and updates. It still worked but a connection was established when Ubuntu started. The first thing I usually did after logging in was closing the ISDN connection.

Today, I could not activate my ISDN connection with the icon in the panel or with the "Network" entry in the system menu respectively. I installed GKdial with which I can connect to my ISP but a connection speed of 0K/s is displayed and the displayed connection time remains "00:00:00" not matter how long I am connected.

What is going wrong? I would like to use the icon in the panel again, not being connected after login. What should I do? If anyone got an Idea, please tell me (in simple words, I'm using Linux for 10 days now...).

Thanks,
Holger

---

### Post by ranf on 2005-11-27
[QUOTE=HolgerAckermann]
I'm using Fritz ISDN card, Ubuntu 5.10 and the packets:
avm-fritz-firmware
avm-fritz-firmware-2.6.12-9

Later, I updated my Ubuntu with available security fixes and updates.[/QUOTE]
Did you also install the updated kernel (linux-image-2.6.12-10)? 
Then you will also have to update avm-fritz-firmware to 2.6.12-10.

You should be able to select the older kernel image in Grub (the boot menu). Then things should work as they did before the updates.

---

### Post by HolgerAckermann on 2005-11-27
[QUOTE=ranf]Did you also install the updated kernel (linux-image-2.6.12-10)? 
Then you will also have to update avm-fritz-firmware to 2.6.12-10.

You should be able to select the older kernel image in Grub (the boot menu). Then things should work as they did before the updates.[/QUOTE]

Thanks for the reply, ranf.

I updated both the kernel and the avm-fritz-firmware. I still could use the panel icon to connect/disconnect, but after the update I was connected after the login. Thats the difference between the 2.6.12-9 and the 2.6.12-10 image. I installed some packages after the update which should not interfere with my ISDN connection (xmms and inkscape packages). I also installed gnome-ppp during the last session (2.6.12-10) before I could not connect using the panel icon. I uninstalled the gnome-ppp again later but I think I did not uninstall all packages that were installe with gnome-ppp.

Well, I would like to use 2.6.12-10 and not 2.6.12-9...

---

### Post by ranf on 2005-11-28
[QUOTE=HolgerAckermann]
I updated both the kernel and the avm-fritz-firmware. [/QUOTE]
Ok, fine.

[QUOTE=HolgerAckermann]
I still could use the panel icon to connect/disconnect, but after the update I was connected after the login. Thats the difference between the 2.6.12-9 and the 2.6.12-10 image. I installed some packages after the update which should not interfere with my ISDN connection (xmms and inkscape packages).[/QUOTE]
No these two shouldn't have any effect on ISDN.

But I'm not familiar with ISDN.
My first guess was just a mismatch between new kernel and old firmware.

---

### Post by HolgerAckermann on 2005-11-28
I have no idea why, but I can connect again using the panel icon (-10 Kernel).

Still one thing to solve: I am connected at startup. As you can see in the syslog, the first thing during boot is to call my ISP. Where can that be configured?

FROM SYSLOG:
  localhost syslogd 1.4.1#17ubuntu3 restart.
  localhost pppd[7882] capiplugin: connected: "" -> "**ISPs number**" outgoing
  localhost pppd[7882] capiplugin: using /dev/capi/0: "" -> "**ISPs number**" outgoing
  localhost kernel Inspecting /boot/System.map-2.6.12-10
  ...

---

### Post by HolgerAckermann on 2005-12-01
[QUOTE=HolgerAckermann]Still one thing to solve: I am connected at startup. As you can see in the syslog, the first thing during boot is to call my ISP. Where can that be configured?[/QUOTE]

Found! 
in file "/etc/network/interfaces" remove the line "auto ppp0"

---

