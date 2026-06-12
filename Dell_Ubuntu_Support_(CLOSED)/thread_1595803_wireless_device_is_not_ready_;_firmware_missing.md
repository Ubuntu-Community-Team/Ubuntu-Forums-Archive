---
title: "wireless device is not ready ; firmware missing"
date: 2010-10-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aminulete on 2010-10-13
Hi,
my laptop is DELL vostro 1510..wireless lan card driver automatically loaded after installing ubuntu 9.04 and connect wifi network. but today i install ubuntu10.10 and wireless doesnot work. the same problem was when i installed ubuntu9.10.few hours ago i again installed 9.04 and wifi works...

i have got this following by run 'lshw' in terminal on ubuntu 10.10 :

network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:68:d3:12:55
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg

So please anybody tell me the way to enable wireless on ubuntu 10.10

---

### Post by MartijnV on 2010-10-13
You'll need the firmware for your card. It's usually automatically installed when you enable the proprietary driver, using a wired connection.

---

### Post by aminulete on 2010-10-13
sorry my earhernet port damaged and i am unable to connect wire connection,,,,,pls another way? on ubuntu9.04 the firmware automatically load without wire or any other internet connection,,,,,i am so much disappointed at ubuntu10.10

---

### Post by MartijnV on 2010-10-14
what do you see in /lib/firmware/b43 ?

---

### Post by gibbylinks on 2010-10-14
Could you put the driver on a USB stick or CD ?

---

### Post by breadbin on 2010-10-14
pity your ethernet is not working:( i just had the same problem and installed fw-cutter and used the eth cable to get the firmware automatically, maybe someone can tell you where it gets the firmware in this program?? i thought it was from the broadcom dell drivers but maybe i'm wrong. think they are saved in /lib/firmware

here is a link that helped me and might give an insight into how and where to get the firmware

[http://wireless.kernel.org/en/users/Drivers/b43#firmwareinstallation]("http://wireless.kernel.org/en/users/Drivers/b43#firmwareinstallation")

good luck

---

### Post by latras on 2011-03-06
Hi, 

If you do not the possibility to fetch the firmware via the ethernet, the use the steps described in this guide. 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

Good luck.

---

### Post by seyekuyinu on 2011-06-02
This worked like magic for me on Ubuntu Linux 11.04!!!

---

### Post by dasking on 2011-08-20
> **latras said:**
> Hi, 

If you do not the possibility to fetch the firmware via the ethernet, the use the steps described in this guide. 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

Good luck.
  
awesome bro thanx a bunch my ethernet was working but there is also one for that to just to let any1 else know :o:o:o:o

---

### Post by Yogotiss on 2011-11-25
> **latras said:**
> Hi, 

If you do not the possibility to fetch the firmware via the ethernet, the use the steps described in this guide. 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

Good luck.
Thanks a bunch for this! Lately I've been dumb founded and now my eyes are open.

---

### Post by ccwillrun on 2011-12-03
Awesome, quick and easy fix. 

Thanks a lot!

---

### Post by paul_doughty on 2012-01-05
**Ubuntu 11.10 getting wireless BCM4311 working**

                                      
                                       I have an Dell Vostro 1500 with a Broadcom BCM4311  wireless card.  After installing Ubuntu 11.10, I find that my wireless  doesn’t work.  The reason, Ubuntu detects the wireless but then loads  the incorrect driver for this card.


 I use the lspci command to display the details about my hardware. It  will display all of your PCI connected hardware. I edited the output to  show only the relevant information.  The important information here for   matching your hardware with mine is this indentifier [14e4:4312].
 $ sudo lspci -v
 
30:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)
        Subsystem: Hewlett-Packard Company Broadcom 802.11a/b/g WLAN
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at c8000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 2
        Capabilities: [58] MSI: Enable- Count=1/1 Maskable- 64bit-
        Capabilities: [d0] Express Legacy Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [13c] Virtual Channel
        Kernel driver in use: b43-pci-bridge
        Kernel modules: ssb
 
$ sudo lspci -nn
30:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)




 _**The Solution**_
 I am  going to install the correct driver for this wireless card.  Then I will remove the “incorrect” driver (bcmwl) which Ubuntu installed  by default.
 $ sudo apt-get update
$ sudo apt-get install firmware-b43-installer
$ sudo apt-get remove bcmwl-kernel-source
$ sudo reboot


 

Hopefully you found this useful.

---

