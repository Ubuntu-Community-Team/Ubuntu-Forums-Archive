---
title: "M1330 wireless adapter stopped working on reboot"
date: 2010-04-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Cincinnatux on 2010-04-17
[note:  I am leaving the below post in the forum on the off-chance that somebody else has a similar situation.  In my case, multiple reboots alone appear to have resolved the issue.  ('rfkill list' now shows that the Wireless LAN is unblocked.)  I am no closer to understanding what went wrong, but am unconvinced we could learn much by troubleshooting a problem that is not persistent.]

I had an odd problem surface today.  I powered down my Dell M1330 laptop (so I could boot into Windows and help a friend troubleshoot a Windows problem she was having) and when I booted back into Karmic-64, my wireless did not start up.  This is a first for me, and I'm really hoping one of you good people can give me some good advice.

What I know:
- upon booting yet again back into Windows, I was able to confirm that wireless still detects wireless signals in the area and can connect to them.  
- toggling the network switch on the side of the laptop no longer appears to have any effect in Ubuntu (though it enables/disables the WiFi as per normal in Windows)
- the blue WiFi indicator light above the keyboard no longer lights up at any time when I boot into Ubuntu

What I've tried (though I'll confess that I do not understand the outputs):

```
sudo lshw -C network
```

Which I think indicated that I have a working driver and that it is called 'iwlagn':

```
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:21:5c:52:9f:85
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f1ffe000-f1ffffff
```

Then ```
lsmod
``` indicated that the driver iwlagn was indeed loaded:

```
iwlagn                124896  0 
iwlcore               133600  1 iwlagn
mac80211              210040  2 iwlagn,iwlcore
```

Then ```
rfkill list
``` told me that the hardware is 'blocked', which I thought meant that the driver was loaded but the hardware wasn't responding.

```
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

What do I do now?  Is there a way for me to get Ubuntu to activate my wireless?

Thanks in advance!

---

