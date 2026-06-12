---
title: "Broadcom BCM4401-B0 100Base-TX Issues"
date: 2010-11-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by franzalex on 2010-11-26
I installed Ubuntu 10.10 on my Dell Inspiron 1521 and the LAN/Ethernet card was working perfectly but Ubuntu was displaying a message about not installing the Wireless drivers because it was restricted or something along that line.

I then went to the Synaptic Package Manager, searched for all Broadcom packages and installed them. So far so good.

I restarted my computer and to my surprise, my wireless works but my lan isn't! What the heck could be wrong?

I then uninstalled/removed all the packages I installed earlier hoping my ethernet would start working again but hey, nothing changed. My wireless card works and the ethernet still doesn't.

Is there any way of getting this fixed?

I checked and found my network devices were:

[LIST]
[*]Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
[*]Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
[/LIST]

---

### Post by franzalex on 2010-11-26
After a lot of sweat I figured it out.

Apparently, installing the new wlan drivers blacklisted the ethernet drivers.

I opened the file **/etc/modprobe.d/broadcom-sta-common.conf** and commented out the line blacklisting the ethernet adapter.

The file now looks like this:
[FONT=Courier New][SIZE=2]# wl module from Broadcom conflicts with ssb
# We must blacklist the following modules:
#blacklist b44
blacklist b43legacy
blacklist b43
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS[/SIZE][/FONT]

End result, the ethernet works like expected. As a matter of fact, I'm replying over ethernet.

---

