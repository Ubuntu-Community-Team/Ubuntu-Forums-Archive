---
title: "Wireless won't work with new laptop Help!"
date: 2009-02-08
forum: General Help
---

### Post by muchdugan on 2009-02-08
Ubuntu Wireless Problem with new laptop, Please Help!:

I just got a *Compaq Presario CQ60*
I wanted to try Ubuntu so I decided to dual boot 2 OS's...
My Compaq laptop has a seperate wireless button right by the power button for turning the wireless on/off. When it's on, it's blue and off it's orange.
Under Vista it's blue(working).
Under Ubuntu it's orange(not working).

Under Ubuntu, it does not see any wireless networks.

Any ideas?

---

### Post by Tim Sharitt on 2009-02-08
It would help to have some information on you wireless card.

From a terminal run

```
lshw -C Network
```

Post the results here.

---

### Post by optimistique1 on 2009-02-08
Hi Buddy, I have the same machine and it has the Atheros AR5007 card.

Go to hardware drivers and disable the ATH5 driver.

Go into terminal and type 

'apt-get install linux-backports-modules-intrepid-generic'

make sure you are connected to the internet via a wired conenction.

reboot and then you should be up and running :-)

PS: The light will ALWAYS show orange in Ubuntu

---

### Post by muchdugan on 2009-02-08
> **optimistique1 said:**
> Hi Buddy, I have the same machine and it has the Atheros AR5007 card.

Go to hardware drivers and disable the ATH5 driver.

Go into terminal and type 

'apt-get install linux-backports-modules-intrepid-generic'

make sure you are connected to the internet via a wired conenction.

reboot and then you should be up and running :-)

PS: The light will ALWAYS show orange in Ubuntu

Thanks! it worked quite easily. So the problem was the driver.
 The orange light gives it a kinda 'ubuntu human' theme lol

---

### Post by kylesgirl138 on 2009-02-22
Hi there, I have the same problem as you have/had, but I think I have a different wireless card; when I go to disable the driver in "Hardware Drivers", the only driver on the list is "Support for Atheros 802.11 wireless LAN cards".  I disabled that, and entered the specified code into Terminal, but this is what I got:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I don't understand what this means...I restarted my PC after I got this message, thinking it might still work, but the wireless was still not working.  Did I do something wrong?

---

### Post by bgates on 2009-02-22
That message means that you are not currently acting as a user with enough privileges to complete the installation.  You would just need to put sudo in front of the command to run it as superuser.

If it installs but won't work, do the command from the second post in the topic and post the results.

---

### Post by eldragon on 2009-02-22
> **kylesgirl138 said:**
> Hi there, I have the same problem as you have/had, but I think I have a different wireless card; when I go to disable the driver in "Hardware Drivers", the only driver on the list is "Support for Atheros 802.11 wireless LAN cards".  I disabled that, and entered the specified code into Terminal, but this is what I got:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I don't understand what this means...I restarted my PC after I got this message, thinking it might still work, but the wireless was still not working.  Did I do something wrong?

you need to be a superuser in order to run that command.

try
```

sudo apt-get install linux-backports-modules-intrepid-generic

```

instead.

---

### Post by kylesgirl138 on 2009-02-23
I tried what you said, but I still am not able to connect to the internet.  I entered "lshw -C network" into Terminal and here's what I got:

```
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:5f:60:1e
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.70 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: be:e1:32:78:02:54
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

What does any of this mean?  Is there anything I can do?
I've also tried this using the first method:  [www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

Please help!! :(

---

### Post by kylesgirl138 on 2009-02-23
Nevermind, it's all fixed...I took the liberty of Googling my wifi card (Atheros 802.11 LAN) and here's what I found: [http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/)

It worked perfectly.  I think my problem was that I never added to the kernel boot modules list, so when I restarted my computer after fixing the wifi for the first time, I had no connection.

Thanks for all your help! :D

---

### Post by fipem on 2009-05-25
i have a presario c700 with atheros AR5007 and i cant connect to wireless

chaka@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:fc:ef:94
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.4 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 2a:03:da:48:64:5d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

pliz help me... on the wicd options, under preferences it says nothing next to wireless and next to cable it says eth0

chaka@ubuntu:~$ lspci | grep Wireless
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

