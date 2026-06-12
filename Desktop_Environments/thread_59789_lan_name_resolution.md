---
title: "lan name resolution"
date: 2005-08-25
forum: Desktop Environments
---

### Post by soonindallas on 2005-08-25
hi all,  I've noticed a few posts about networking problems over the last few days.  here's my take, and my problem:

for as long as I have been using Ubuntu on my laptop, my ethernet NIC has been called "eth0" and my IPW2200 interface has been called "eth1".

on August 19, synaptic suggested I update my kernel and kernel headers which I did.  I found myself without WLAN, so I followed the procedure to update the IPW2200 driver and firmware.

Subsequently I noticed that gnome-related apps (network connection applet, gnome network tools and network settings) now refer to my WLAN as eth0 and the NIC as eth1.

This is also the way I need to refer to these interfaces when I use the command sudo ifup or sudo ifdown.

This is however at odds with /etc/network/interfaces that puts all the wireless tools options after "iface eth1"

I am having LAN name resolution problems - I can ping another computer on the LAN by IP but not by name, I can also ping hosts on the internet, my guess is the ISPs DNS is correctly resolving these hosts for me - I cannot ping other hosts on the LAN by name.

I'm wondering if the two things are related ??

Thanks for your suggestions.

Peter

---

### Post by soonindallas on 2005-08-25
[QUOTE=soonindallas]hi all,  I've noticed a few posts about networking problems over the last few days.  here's my take, and my problem:

for as long as I have been using Ubuntu on my laptop, my ethernet NIC has been called "eth0" and my IPW2200 interface has been called "eth1".

on August 19, synaptic suggested I update my kernel and kernel headers which I did.  I found myself without WLAN, so I followed the procedure to update the IPW2200 driver and firmware.

Subsequently I noticed that gnome-related apps (network connection applet, gnome network tools and network settings) now refer to my WLAN as eth0 and the NIC as eth1.

This is also the way I need to refer to these interfaces when I use the command sudo ifup or sudo ifdown.

This is however at odds with /etc/network/interfaces that puts all the wireless tools options after "iface eth1"

I am having LAN name resolution problems - I can ping another computer on the LAN by IP but not by name, I can also ping hosts on the internet, my guess is the ISPs DNS is correctly resolving these hosts for me - I cannot ping other hosts on the LAN by name.

I'm wondering if the two things are related ??

Thanks for your suggestions.

Peter[/QUOTE]
 wierdness... my eth0 and eth1 came back into line after a reboot - no chages made by me to anything.

now samba and hance nautilus can browse shares on the XP box that were perviously unavailable, but my NETBIOS resolution issue remains for the ping command.

more wierdness: samba can connect to the XP box by name eg smb://isabelle BUT i cannot 'ping isabelle': I have to ping 192.168.0.5...

any ideas on NETBIOS resolution ?  please post to this thread [http://ubuntuforums.org/showthread.php?t=59782](http://ubuntuforums.org/showthread.php?t=59782) as the networking forum seems more appropriate.  thanks!

---

