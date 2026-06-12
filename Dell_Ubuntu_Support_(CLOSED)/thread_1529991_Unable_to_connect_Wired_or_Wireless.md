---
title: "Unable to connect Wired or Wireless"
date: 2010-07-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mceven on 2010-07-13
I just installed Ubuntu 10.04 LTS using Wubi.  I am unable to connect to the internet either way, wired or wireless -- neither connection is recognized.  

I have a Broadcom wireless card, and browsing around it seems like that's the problem with the wifi.  lspci prints out:
> 
Ethernet controller: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe (Rev 10)
Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

I have no idea why the wired connection is not recognized.  I unplug the cable from this computer, plug it into my laptop (Dell Latitude E5400 running Windows XP on the other partition), and nothing is recognized -- a ping returns nothing at all, so I'm guessing it has something to do with the DNS server and IP addresses needing to be entered manually?  

I'm just grasping at straws here.  If I can get Ubuntu online tonight, I'll keep it and try to master the fabled learning curve.  If I can't, I'll probably just go back to XP.  

Thanks in advance for any help.

---

### Post by jarviser on 2010-07-13
First and main problem is Broadcom...
example  [http://ubuntuforums.org/showthread.php?t=1505697](http://ubuntuforums.org/showthread.php?t=1505697)

Canonical and Broadcom need to get together big-time.

Secondly Wubi will always be more risky that dual boot

Finally, always reboot after swapping ethernet cables (although there are other command line remedies). Plug-n-play it is not. Manual IP address may fix it but auto is just fine if you reboot.

---

