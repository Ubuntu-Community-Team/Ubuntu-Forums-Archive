---
title: "Wireless card problems"
date: 2011-10-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Michael Blowers on 2011-10-15
Hey guys, I recently installed ubuntu 11.04 on my Dell Inspiron 1525 and I can't get my wireless card to work. It is showing that the firmware is missing, I have looked around a bit for info but havn't come up with much.

I ran *lspci -v* and here is the output:
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe7fc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

If anyone could point me in the right derection that would be great thanks :D

---

### Post by Kai Summers on 2011-10-15
Have a look at System -> Administration -> Additional Drivers... You should be able to install a third party driver from there. If there is no driver in there then it might also be worth plugging up Ethernet cable so that you have a route to the repository then try an update... and then return to the Additional Drivers section.

Please keep us updated on progress.

---

### Post by Michael Blowers on 2011-10-15
I already gave the additional drivers a shot while connected to the net, but ill do some updates and give it another shot.

Cheers

---

### Post by varunendra on 2011-10-17
This guide should be able to help: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

**_EDIT_:**
Preferred method: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by Michael Blowers on 2011-10-17
Cheers for that, worked a treat to install the driver. But i have come across one more little problem because I have been using Ethernet I disabled wireless networking and now after I installed the driver the option the enable wireless networking has    	 	 	 	 	disappeared, is there a command to enable it in terminal, would be a lot easier than mucking around with the GUI

---

### Post by garvinrick4 on 2011-10-17
> Cheers for that, worked a treat to install the driver. But i have come  across one more little problem because I have been using Ethernet I  disabled wireless networking and now after I installed the driver the  option the enable wireless networking has                            disappeared, is  there a command to enable it in terminal, would be a lot easier than  mucking around with the GUIDoes a reboot bring up the new driver and make network manager accessable for you in wireless.

There is a way to restart network-manager if needed at anytime.
```
sudo /etc/init.d/network-manager restart
```below to ever reinstall anything you want, not that you need to reinstall now: Welcome to the Forums [Michael Blowers]("http://ubuntuforums.org/member.php?u=1468970").
```
sudo apt-get install --reinstall [COLOR=Red]network-manager[/COLOR]
```Just above change the package name you want to reinstall, in red.

---

