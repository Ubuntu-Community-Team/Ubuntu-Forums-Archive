---
title: "Internet/WiFi Problem?"
date: 2010-07-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Breath! on 2010-07-08
Hi,

After I fixed my display, I found out I couldn't connect to the internet via an external Netgear dongle or by Ethernet. The WiFi icon in the top panel shows a red exclamation point and when I click it it says 'No Network Devices...'  Any suggestions? 

Thanks

---

### Post by bobcollard on 2010-07-08
> **Breath! said:**
> Hi,

After I fixed my display, I found out I couldn't connect to the internet via an external Netgear dongle or by Ethernet. The WiFi icon in the top panel shows a red exclamation point and when I click it it says 'No Network Devices...'  Any suggestions? 

Thanks
You might right click the wifi icon, open  Edit Connections and click the wireless tab, then add your information manually.  I have a Netgear dongle and have no trouble getting this to work.

---

### Post by Breath! on 2010-07-09
I tried that and it didn't work either. 

I searched around and ran some commands I found, and it seems that Ubuntu doesn't see my ethernet card at all or at least according to lspci. And ideas?

I'm hoping I can get wired internet to work so I can use apt-get to install the wireless drivers (the manual install is posing multiple difficult dependency issues...)

---

### Post by bobcollard on 2010-07-09
> **Breath! said:**
> I tried that and it didn't work either. 

I searched around and ran some commands I found, and it seems that Ubuntu doesn't see my ethernet card at all or at least according to lspci. And ideas?

I'm hoping I can get wired internet to work so I can use apt-get to install the wireless drivers (the manual install is posing multiple difficult dependency issues...)
Have you thought of installing a different system like Xubuntu?
You might install WICD if you ever get the Ethernet to work, but, without some kind of connection you are not going to even update or upgrade.  lspci shows the following for me, (Does not see Dongle):
bob@Dell-Laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)

---

### Post by ugm6hr on 2010-07-10
> **Breath! said:**
> After I fixed my display

Was this a hardware fix?

If lspci does not list any Netork Devices - this is a hardware problem. Perhaps a loose connection?

Maybe post output from:
```
lspci
lshw -class network
```

So we can confirm.

---

### Post by bobcollard on 2010-07-10
> **ugm6hr said:**
> Was this a hardware fix?

If lspci does not list any Netork Devices - this is a hardware problem. Perhaps a loose connection?

Maybe post output from:
```
lspci
lshw -class network
```So we can confirm.
If you are asking me and not the OP then yes, my Broadcom 4312 card burnt out and I am using a Netgear WG111v3 USB.  You can see my lspci above and here is lshw -class network:
bob@Dell-Laptop:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:31:ba:93
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes
       resources: irq:28 memory:f69fc000-f69fffff ioport:de00(size=256)
  *-network:0
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:22:3f:eb:13:70
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.102 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by ugm6hr on 2010-07-10
> **bobcollard said:**
> If you are asking me and not the OP
Useful info to compare with Breath's output.

---

