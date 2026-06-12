---
title: "Dell a860 after last update wireless not work"
date: 2009-03-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by alarikh on 2009-03-22
After last update wireless not worked. I tied to fix this problem every update. Somebody can help?

---

### Post by coffeeaddict22 on 2009-03-22
Hi,
A little more information would help.  Find a terminal, and type lspci into it.  One of the lines will start with "Network Controller"; the info after that will help you find the right answer.  
Also, once you've got that info, type in lshw.  The product info there will tell you more about whether the card has a driver, and whether it's active.  If there's no logical name you'll need a driver.

---

### Post by alarikh on 2009-03-22
> **coffeeaddict22 said:**
> Hi,
A little more information would help.  Find a terminal, and type lspci into it.  One of the lines will start with "Network Controller"; the info after that will help you find the right answer.  


0c:00.0 Network controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by coffeeaddict22 on 2009-03-22
OK, so the card is recognised.  Now have a look for how the wireless is set up:  
lshw
If you can't find the bit you want in the output, reduce it with 
lshw | grep network -A15
This should give you a bit more info; what you want to see is the logical name, and down in the stuff at the bottom of the output there should be a driver.

In case you wondered,
 lshw lists hardware known to the OS (Linux) on your PC. 
| is a pipe (look above the enter key) that redirects the output of the previous command into the new one. 
 grep looks through a file- or in this case some output- and pattern matches; network is the parameter we want it to match, 
and -A15 is an option for grep that gets it to list not only the line you found but the next 15 lines as well.

---

### Post by yrelle on 2009-05-12
Almost encountered the same problem.... After re-install Ubuntu 8.04, the wireless network adapter did not work.

With the instruction from coffeeaddict22, lshw |grep network -A15,  the following information listed:


:~$ lshw |grep network -A15
WARNING: you should run this program as super-user.
           *-network UNCLAIMED
                description: Network controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:0c:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
--
           *-network
                description: Ethernet interface
                product: RTL8101E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 02
                serial: 00:21:70:82:27:46
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1

Well, there seems at the bottom no driver "appears"....

---

### Post by yrelle on 2009-05-13
I read the [document]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check") [coffeeaddict22]("http://ubuntuforums.org/member.php?u=636580") mentioned times, tried finding the way to solve the wireless problem.
By lshw,  the wireless card could be found.

```
 *-network UNCLAIMED
                description: Network controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:0c:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
[COLOR=Red]                configuration: latency=0[/COLOR]

```Well, as the doc indicated, the driver should not be ready yet.

Afterward, doing as the instruction, the model could not be recognized by the command "modprobe"....
"
[LIST=1]
[*]run the command [lsmod]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lsmod") to see if driver is loaded. (look for the driver name that was listed in the output of lshw, "configuration" line). If you did not see the driver module in the list then use the [modprobe]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#modprobe") command to load it.
[/LIST]
"

```
heyi@heyi-laptop:~$ modprobe AR242x 802.11abg Wireless PCI Express Adapter
FATAL: Module AR242x not found.
heyi@heyi-laptop:~$ modprobe AR242x
FATAL: Module AR242x not found.

```

---

