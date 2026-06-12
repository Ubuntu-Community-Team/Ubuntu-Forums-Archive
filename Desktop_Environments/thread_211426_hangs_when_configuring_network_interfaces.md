---
title: "hangs when configuring network interfaces"
date: 2006-07-08
forum: Desktop Environments
---

### Post by AudioMove on 2006-07-08
Just installed a new wireless card on my Kubuntu desktop and it now hangs when cofiguring network interfaces. Ctr-c no longer works either. I also have commented out all references to eth0/eth1 in /etc/network/interfaces.

It eventually loads a bunch of text saying:

Fixing recursive fault but reboot is needed!
scheduling while atomic: usplash/0x00000001/846
.
.
.

I could post the entire text if i could get into my system and check the logs as im posting this from my laptop. Can anyone suggest a solution to this problem and a means of getting through this stage a booting up my desktop.

Thanks in advance,
Cathal

---

### Post by lawngn0mex on 2006-07-08
> **AudioMove said:**
> Just installed a new wireless card on my Kubuntu desktop and it now hangs when cofiguring network interfaces. Ctr-c no longer works either. I also have commented out all references to eth0/eth1 in /etc/network/interfaces.

It eventually loads a bunch of text saying:

Fixing recursive fault but reboot is needed!
scheduling while atomic: usplash/0x00000001/846
.
.
.

I could post the entire text if i could get into my system and check the logs as im posting this from my laptop. Can anyone suggest a solution to this problem and a means of getting through this stage a booting up my desktop.

Thanks in advance,
Cathal

what wireless card? did you check for linux support? is it an atheros or intel chipset card?

---

### Post by AudioMove on 2006-07-08
Its a netgear WG311 v3. I had it installed and working its only when I shut down my computer and booted it up later it hung at this stage. 

I tryed in recovery mode also and it got stuck and its last lines where:

COde: Bad EIP Value
note: udevd[3494] exited with preempt_count 1
udevd-event[3494]: run program 'lib/udev/iftab_helper' abnormal exit

Whether this has anything to do with my problem or because I've had to do alot of hard reboots, i dont really know.

---

### Post by AudioMove on 2006-07-08
I've now noticed an error while loading hardware drivers.

firmware_helper[2920]: main: error loading 'lib/firmware/mrv8k-b-fw' for device 'class/fireware/0000:00:0a.0' with driver 'mrv8k'

looks like the driver for the wireless card.

Still unable to boot into the desktop or too command line. Can anyone give me suggestions on how to get past these errors, at least on to command line so i can do something about them?

Edit: pluged out the wireless card, which allowed me to boot back into the desktop. Allowed auto eth0 and it boots fine now. Now just to get WEP working :-)

---

### Post by a.estrada.111680 on 2006-08-08
> **AudioMove said:**
> 
Edit: pluged out the wireless card, which allowed me to boot back into the desktop. Allowed auto eth0 and it boots fine now. Now just to get WEP working :-)

How did you allow "auto eth0" ?

Thanks

---

