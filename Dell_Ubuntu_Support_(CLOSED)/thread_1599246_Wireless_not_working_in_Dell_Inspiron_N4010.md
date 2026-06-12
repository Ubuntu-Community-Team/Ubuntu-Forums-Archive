---
title: "Wireless not working in Dell Inspiron N4010"
date: 2010-10-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by thameera on 2010-10-17
Hello,

I installed Ubuntu 10.10 64-bit version in my new Dell Inspiron N4010 laptop. But the wireless is not working. Mobile broadband works though. 

I tried reinstalling bcmwl-kernel-source but it doesn't help. And, yes, I've turned on wireless by pressing F2, it doesn't work either. Bluetooth works though.

"lshw -C Network" command gives the following output.

udaya@udaya-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c1
       serial: b8:ac:6f:76:63:ff
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 multicast=yes
       resources: irq:46 memory:f0400000-f043ffff ioport:2000(size=128)
udaya@udaya-laptop:~$

Please help!

---

### Post by nlsthzn on 2010-10-24
Hi,

I know this might be a silly question but it is a good place to start, I believe the F2 key toggles your wireless on and off... have you made sure it is active, maybe try toggling it off and back on and then seeing if you can connect via the Network Manager Applet...


Cheers
Neil

---

### Post by priyeshkv on 2011-05-06
if ur wireless is disabled, try the following commands

sudo ifconfig wlan0 up

if not able to do that, first give the command,

rfkill unblock wifi

---

### Post by computerandu on 2011-05-07
Hi,
The reason what I think is some  compatibility issues (its probably a bug in 11.04) with this version of  Ubuntu and the restricted driver because same driver was working quite  well in previous versions of Ubuntu. **Solution:** Here is what  you need to do. Use other Broadcom drivers. Download these drivers (from  Windows or through wired network or a friend’s computer or from  wherever you are reading this article [IMG]http://s2.wp.com/wp-includes/images/smilies/icon_smile.gif?m=1221158731g[/IMG]  ).
 For 32 bit: [http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb)
 For 64 bit: [http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb)
 Now remove the previous drivers in Ubuntu 11.04 by using: *sudo apt-get remove bcmwl-kernel-source*
 Now install the appropriate driver (you  have downloaded from the above links). Restart your computer. If  restarting doesn’t work try shut down and then start it (strange…but  works). Enjoy [IMG]http://s2.wp.com/wp-includes/images/smilies/icon_smile.gif?m=1221158731g[/IMG] 


Source: [http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

Please mark th thread as solve if it solves your problem.....

---

### Post by K-Sub on 2011-05-07
I am having the same problem and want to try this but I'm not sure how to install the appropriate driver once I have downloaded it.  Do I copy it from my thumb drive to the computer?  To where?  Then what?

BTW, I have a Broadcom BCM4312 80211.b/g.  LP-PHY (rev 01) adapter.  

In the past I have just gone to System -> Administration -> Additional Drivers and have been able to load the correct driver (BM3?).  Now it only shows the STA driver, which doesn't work with this adapter.

Thanx!

---

### Post by K-Sub on 2011-05-07
Well, I just double-clicked on the file and installed it, but now when I shut down my computer and restart it, I do not get any wireless at all.  Thought?  Thanx.

---

### Post by K-Sub on 2011-05-07
OK, I repeated the process and I see the problem.  This is the STA driver, which doesn't work with the adapter in my computer, I think I need the BM3 driver, or something like that.  Can anyone point me in the right direction?  I hate to say this folks, but this has been an ongoing problem with each update and I'm real close to just installing Windows on this machine.

---

### Post by K-Sub on 2011-05-07
> **K-Sub said:**
> OK, I repeated the process and I see the problem.  This is the STA driver, which doesn't work with the adapter in my computer, I think I need the BM3 driver, or something like that.  Can anyone point me in the right direction?  I hate to say this folks, but this has been an ongoing problem with each update and I'm real close to just installing Windows on this machine.

Well, I don't know which of the many things that I tried fixed the problem, but I seem to once again have stable WiFi.

---

