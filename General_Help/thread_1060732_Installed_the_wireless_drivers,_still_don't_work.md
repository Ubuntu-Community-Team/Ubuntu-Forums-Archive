---
title: "Installed the wireless drivers, still don't work"
date: 2009-02-05
forum: General Help
---

### Post by anotherdrumdude on 2009-02-05
Hey guys. I've been fighting with this computer for over a week straight now. I am trying to get my wireless card to work. It's a Broadcom 4318 in a Compaq Presario V2000 running the new Hardy version 10.4

I have installed BOTH ndiswrapper and the fwcutter. I have installed the drivers other posts have said to install. My card still won't work. In SYSTEM-ADMINISTRATION-HARDWARE DRIVERS it only shows that my ATI/AMD graphics driver. If I run terminal and type in:

ndiswrapper -l

I get:

bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: ssb)
wmp54gs : driver installed
        device (14E4:4318) present (alternate driver: ssb)

What am I doing wrong? I've tried both ways and get nowhere!

Thanks.

---

### Post by Yellow Pasque on 2009-02-05
I don't have a Broadcom device, but I do use ndiswrapper for my Realtek 8180.

First, provide some basic info please:
```
sudo lshw -C network
cat /etc/network/interfaces
sudo iwconfig
```

Make sure the ndiswrapper kernel driver is loaded:
```
lsmod | grep ndis
```
If the ndiswrapper module isn't loaded, make sure it loads properly when you load it manually:
```
sudo ndiswrapper -ma
sudo depmod -a
sudo modprobe -v ndiswrapper
```

---

### Post by carml on 2009-02-05
To usse ndiswrapper you can also install the package Ndiswrapper-gtk,which provides a graphical interface,with you can check immediately if ndiswrapper loaded the driver and found the card.

---

### Post by anotherdrumdude on 2009-02-05
root@Mikes-Laptop:~# sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:1e:f3:49
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:6e:aa:9f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8e:4c:a0:28:ba:e0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
root@Mikes-Laptop:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback

root@Mikes-Laptop:~# sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

root@Mikes-Laptop:~# lsmod | grep ndis
root@Mikes-Laptop:~# sudo ndiswrapper -ma
module configuration information is stored in /etc/modprobe.d/ndiswrapper
root@Mikes-Laptop:~# sudo depmod -a
root@Mikes-Laptop:~# sudo modprobe -v ndiswrapper
FATAL: Module ndiswrapper not found.
root@Mikes-Laptop:~#

---

### Post by carml on 2009-02-05
I'm sorry that in my first post I committed an error,the GUI for ndiswrapper is the pakage ndisgtk:)

---

### Post by anotherdrumdude on 2009-02-05
ok so if I type in:

m-a a-i ndiswrapper 

i get this error message after a lot of script that disappears upon failing and erasure of the script:

module-assistant, error message

Installation of the ndiswrapper-source source failed.

Ignoring this package. Maybe you need to add something to sources.list, maybe the contrib and non-free archives.


what am i doing wrong? it won't install the driver in ndisgtk either. it was telling me that i should run the above script.

---

### Post by anotherdrumdude on 2009-02-05
Ok so I spent all night digging through the various forums and was unable to figure out what I am doing wrong. This is slightly aggravating... ugh...

---

### Post by abyssius on 2009-02-05
> **anotherdrumdude said:**
> Ok so I spent all night digging through the various forums and was unable to figure out what I am doing wrong. This is slightly aggravating... ugh...
Here's what I recommend before you go into endless CLI commands and get even more frustrated. Stick your installation CD into your CD drive. Browse the CD using Nautilus (double-click on the CD icon when it appears on the desktop). Open the [pool] directory. Open the [main] directory. Open the [n] directory. Open the [ndiswrapper] directory. First, double-click the ndiswrapper-commonXXXXX.deb file to install it. Next, double-click the ndiswrapper-utilitiesXXXXX.deb file to install it. Next, go up one level from the [ndiswrapper] directory, and you'll see the [ndisgtk] directory. Open that directory and double-click the ndisgtkXXXX.deb file to install it.

After doing this, you'll have as a new entry in your System/Administration menu called Windows Wireless Drivers. This is the graphic version of ndiswrapper. You'll have to know what and where your Windows wireless drivers are. You'll need two files *drivername*.inf and *drivername*.sys. Select your *drivername*.inf file. Once you've installed the driver correctly, you can click the [Configure Network] button to continue to get your adapter working.

---

### Post by anotherdrumdude on 2009-02-06
Abyssius,

Your info was far more helpful that any other i've found so far. However, when I get to the point where it asks me to click the Configure Network button, I get an error message saying it cannot find a network configuration tool. How would I go about getting a network configuration tool? The Hardware Drivers tool doesn't show my wireless card yet, and the other network tool installed already doesn't show anything for wireless. The only option that one has is Auto eth0 in the first tab.

---

### Post by abyssius on 2009-02-06
> **anotherdrumdude said:**
> Abyssius,

Your info was far more helpful that any other i've found so far. However, when I get to the point where it asks me to click the Configure Network button, I get an error message saying it cannot find a network configuration tool. How would I go about getting a network configuration tool? The Hardware Drivers tool doesn't show my wireless card yet, and the other network tool installed already doesn't show anything for wireless. The only option that one has is Auto eth0 in the first tab.

You will not be able to proceed until you have successfully installed the windows driver. Does the Windows Wireless Driver report that the driver and hardware is present? (see attachment). If your window looks similar, then we can proceed. The "can't find network configuration tool" is probably a bug. 

(a) If the driver is present, try clicking on the Network icon, to see if it lists wireless networks.

(b) If this doesn't work, we can still proceed as long as the windows driver was installed.

---

### Post by cpbrock3 on 2009-03-09
I got to the same point.  What was the fix for this?  I installed everything and got the Network GUI to show that it recognized it had a driver for it.  But when I clicked on configure I also got the error message.

Did you end up getting this thing fixed?

---

### Post by hoads123 on 2009-06-10
I am also having this problem. 
Have a wn111 wireless adaptor that is being difficult and after upgrading to Jaunty the network manager seems to have disappeared from the System menu.

any help would be great

---

### Post by hoads123 on 2009-06-10
> **abyssius said:**
> You will not be able to proceed until you have successfully installed the windows driver. Does the Windows Wireless Driver report that the driver and hardware is present? (see attachment). If your window looks similar, then we can proceed. The "can't find network configuration tool" is probably a bug. 

(a) If the driver is present, try clicking on the Network icon, to see if it lists wireless networks.

(b) If this doesn't work, we can still proceed as long as the windows driver was installed.


Apologies for cutting in... My screen does look like you say and clicking on the network icon doesn't show any wireless networks. (the version is NetworkManager Applet 0.7.0.100)

---

