---
title: "No Wireless Connection in Jaunty - Dell Inspiron 1501 w/ BCM4311 802.11b/g WLAN"
date: 2009-05-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by barivocalist on 2009-05-14
I just upgraded to Jaunty Ubuntu 9.04, and I have spent hours trying to get my wireless connection to work. At present, no wireless networks register (despite their being some available in the area). I have tried using ndisgtk, but it claims that it can't recognize the hardware.

I can use a wired ethernet connection, but at home I don't have such a luxury, so I really need to get my wireless to work.

When I check the network specs using the command line lshw -C network, I get the following:

*-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:9b:06:ef
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=10.0.1.241 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 86:2d:38:32:b6:4f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

My computer model is a Dell Inspiron 1501

PLEASE HELP!

---

### Post by coffeeaddict22 on 2009-05-14
Hi,
Driver problem of some sort.  You've not got a logical name for the network.
First, the really simple fix: check you've got the wireless switch turned on.  My LT has it on the left side; for some Dells it was Fn-F2.
Then restart.
If that doesn't work, Have a look in System/Administration/Hardware drivers (you'll need to have a wired connection for this; no wire = no chance of this helping); if there's a Broadcom driver in there, enable it.
After that, some fishing for problems.  Post back the output of  ```
lsmod
``` if you get this far with no joy.

---

### Post by barivocalist on 2009-05-15
Wow, do I feel like an idiot. Of course I didn't think of the fact that when I loaded Jaunty from a disk, my wireless trigger might not be on. I spent hours in terminal yesterday working with every app and command I could try with no success...

I'm hanging my head a bit in shame, but at least it works now.

If anybody else is having this issue, turn your wireless on... it works.

---

### Post by coffeeaddict22 on 2009-05-15
Don't worry, you aren't the first... mea culpa. 
To quote: "the only real mistake is one from which we learn nothing..."

---

