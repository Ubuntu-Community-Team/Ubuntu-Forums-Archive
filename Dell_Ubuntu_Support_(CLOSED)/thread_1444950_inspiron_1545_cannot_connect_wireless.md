---
title: "inspiron 1545 cannot connect wireless"
date: 2010-04-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jduane on 2010-04-02
i recently download the latest version of ubuntu on my inspiron1545 but i cant seem to connect wireless can someone PLEASE HELP ME I AM NEW TO UBUNTU and really like it when i am connected via ethernet cable,i am very stressed out and been trying to figure this out. I have no clue on what to do from here i tryed checking to see if i had wireless signal and there is none i cant tell if the antenna is working again PLEASE HELP ME

---

### Post by coffeeaddict22 on 2010-04-04
Hi,
Welcome.
Can you open a terminal (Applications/Accessories/Terminal), type in ```
nm-tool
lshw -C network
sudo iwlist scan
```
and post back the output?  It'll help clarify things a little.

---

### Post by Megaptera on 2010-04-04
Hi,
I've used this fix with both Ubuntu 9.10 and 10.04 (Alpha & Beta) sucessfuly with my Dell 1545. I know it says Dell mini but it works for me!

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

Hope it helps?

---

### Post by mikeeey on 2010-04-05
> **Megaptera said:**
> Hi,
I've used this fix with both Ubuntu 9.10 and 10.04 (Alpha & Beta) sucessfuly with my Dell 1545. I know it says Dell mini but it works for me!

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

Hope it helps?

I'm having the same problem on my girlfriend's Dell Inspiron 1525. I've followed many guides and just now tried the link you've provided. After activating the driver again I check in the Hardware Drivers and it says it's actived but not currently in use. The problem is I can't figure out how to turn it on. It seems like I'm so close..


Here's my results from the terminal when I tried the code posted by coffeeaddict22:

```
*-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:3c:93:c5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 multicast=yes
       resources: irq:28 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:fe7fc000-fe7fffff

```

---

### Post by gibbylinks on 2010-04-05
> **mikeeey said:**
> I'm having the same problem on my girlfriend's Dell Inspiron 1525. I've followed many guides and just now tried the link you've provided. After activating the driver again I check in the Hardware Drivers and it says it's actived but not currently in use. The problem is I can't figure out how to turn it on. It seems like I'm so close..


I know I'm stating the obvious here..but is it turned on. Have you tried the Fn key with the wireless key, then see if your wi-fi light goes on and off.

Apologies if you think I'm treating you like an idiot. But sometimes we don't see the obvious.

---

### Post by Megaptera on 2010-04-05
After I've followed that guide I reboot and then click on the wireless icon and my connection is shown
In addition to gibbylinks suggestion, have you tried reboot?

---

### Post by mikeeey on 2010-04-05
> **gibbylinks said:**
> I know I'm stating the obvious here..but is it turned on. Have you tried the Fn key with the wireless key, then see if your wi-fi light goes on and off.

Apologies if you think I'm treating you like an idiot. But sometimes we don't see the obvious.
lol don't worry about it, I completely understand.

yes this is the problem, I don't think it's turned on, and I can't figure out how to turn it on. I've tried sliding the switch on the side (which would normally turn it on in windows), and I've tried holding the fn key and sliding it, but it doesn't turn on.

In the hardware drivers I have the Broadcom STA wireless driver installed and activated, however, "not in use." I assume it becomes "in use" when you turn the wifi on. Are there any commands in the terminal or alternative ways to turn the wifi on?

---

### Post by Megaptera on 2010-04-05
I don't think it's Fn + F2 .... I think it's just F2.
See #3 here:
[http://www.linuxquestions.org/questions/linux-laptop-netbook-25/wireless-stopped-working-dell-inspiron-1545-using-ubuntu-9-04-a-754951/](http://www.linuxquestions.org/questions/linux-laptop-netbook-25/wireless-stopped-working-dell-inspiron-1545-using-ubuntu-9-04-a-754951/)

Hope this works?

---

### Post by mikeeey on 2010-04-05
> **Megaptera said:**
> I don't think it's Fn + F2 .... I think it's just F2.
See #3 here:
[http://www.linuxquestions.org/questions/linux-laptop-netbook-25/wireless-stopped-working-dell-inspiron-1545-using-ubuntu-9-04-a-754951/](http://www.linuxquestions.org/questions/linux-laptop-netbook-25/wireless-stopped-working-dell-inspiron-1545-using-ubuntu-9-04-a-754951/)

Hope this works?

I have not yet tried this, I'll do so when I get home (on my iPod touch right now), as well as holding the f2 button to see what happens.

---

### Post by mikeeey on 2010-04-05
Well, everything else failed, but upgrading to Ubuntu 10.04 fixed it! It's working perfectly now, and I'm typing this on her laptop using WiFi.

From here on out I deem every problem fixable by upgrading to Ubuntu 10.04 lol.

---

### Post by jduane on 2010-04-05
thank you mega i did it and its working great i am in LOVE with the software and amazed at all the **** you can do.  Thanks to everyone for all your help i greatly appreciate it guys

---

### Post by Megaptera on 2010-04-06
You're welcome!!

---

### Post by sussa on 2010-04-30
Hello!

I'm having connection problems with Inspiron 1545 on Ubuntu 10.04. However, I don't have a Broadcom card, but an Intel instead.

Here's the topic with my laptop's configuration: [http://ubuntuforums.org/showthread.php?t=1466892]("http://ubuntuforums.org/showthread.php?t=1466892")

Thanks for your attention :)

---

