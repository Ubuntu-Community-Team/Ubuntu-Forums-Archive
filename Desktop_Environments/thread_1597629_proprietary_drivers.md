---
title: "proprietary drivers"
date: 2010-10-15
forum: Desktop Environments
---

### Post by hoboboot on 2010-10-15
so i have a desktop without ethernet access to the internet, i have ethernet, and thats how i got 9.04 to download the drivers proprietary drivers for nvidia gfx card aswell as DWL-G122 rev A2 USB wifi adapter, which then allows my desktop to connect to the internet wirelessly, without ethernet...

i was wondering if theres a way to get the DWL-G122 driver into 10.10 maverick meerkat without using ethernet... can i download drivers via the wifi in windoze and then install them via maverick meerkat?

thanks -hobo

---

### Post by hhh on 2010-10-15
Yes, put the driver in /lib/firmware and you should almost immediately see your wireless connection in network manager.

---

### Post by hoboboot on 2010-10-27
where would i find the driver though?

---

### Post by Frogs Hair on 2010-10-27
I had no trouble finding that driver on the internet but I could only find a Windows version.

---

### Post by hhh on 2010-10-27
> **hoboboot said:**
> where would i find the driver though?
I'm sorry, I thought you said in your 1st post that you had wifi working on Ubuntu 9.04. 

Here is the Windows driver...
[http://www.dlink.ca/products/?tab=3&pid=DWL-G122&rev=DWL-G122_revA2](http://www.dlink.ca/products/?tab=3&pid=DWL-G122&rev=DWL-G122_revA2)

You can then use ndiswrapper to activate it for Linux...
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

This document says that in Feisty you need to first blacklist prism54usb (it's an old USB)...
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)
To do that, open a terminal and enter```
gedit /etc/modprobe.d/blacklist.conf
```, scroll to the bottom and add```
blacklist prism54usb
``` then log out and back in (or reboot).

---

