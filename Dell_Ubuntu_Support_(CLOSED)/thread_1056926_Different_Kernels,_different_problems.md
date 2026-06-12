---
title: "Different Kernels, different problems"
date: 2009-02-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by WhaleWolf on 2009-02-01
Ok, starting my own thread as suggested.
My internet problem all started by moving the wireless modem-router from the bedroom to the living room.

I can no longer connect to the internet with the Ubuntu 8.10 kernel 2.6.27-11-generic (64-bit btw). My ISP is Tiscali btw, but I am sure the problem isn't there, because internet does work in Windows Vista. Wired with ethernet I can also connect to internet. And when I use the Ubuntu 8.10 kernel 2.6.22-15-generic, internet works wireless too, but now my screen resolution is not working here. o_O

Now I am not really interested in fixing the screen resolution in kernel 22, but I would just like to fix the internet problem in kernel 27 instead.

I am going to spam the requested terminal data here now, gathered in the kernel 22, where wireless internet DOES work:


 lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7950 GTX (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

 lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 009: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 001 Device 008: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 001 Device 007: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 046d:c049 Logitech, Inc. G5 Laser Mouse
Bus 003 Device 001: ID 0000:0000  

 lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1f:3c:4f:2c:63
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp firmware=14.2 1:0 () ip=192.168.1.3 latency=0 module=ipw3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:2b:a5:40
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 firmware=5752-v3.19 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

Do you need the terminal data of the kernel 27 too?
I hope you can help me out here. If you need more information, please ask. Also if you need more information on the virus. I am new to Ubuntu btw, so step-to-step instructions please. Thank you in advance. :)

EDIT: I tried disabling and enabling the connection by unchecking and checking the boxes...

---

### Post by ugm6hr on 2009-02-01
Looks like you have a 3945 Intel wifi chipset, that is using the ipw3945 driver.

Perhaps check what the output from "lshw -class network" suggests the driver being used in the -27 kernel is.

Perhaps the new iwlwifi driver ( [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/) ) has been added?  It should work OK.

The latest driver should be in the [http://packages.ubuntu.com/intrepid-updates/base/linux-backports-modules-2.6.27-11-generic](http://packages.ubuntu.com/intrepid-updates/base/linux-backports-modules-2.6.27-11-generic) package.

---

### Post by WhaleWolf on 2009-02-02
> **ugm6hr said:**
> Looks like you have a 3945 Intel wifi chipset, that is using the ipw3945 driver.

Perhaps check what the output from "lshw -class network" suggests the driver being used in the -27 kernel is.

Ok, logged into the 27kernel, did the "lshw -class network" in the terminal, and got this:
 lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:4f:2c:63
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:2b:a5:40
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5752-v3.19 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5a:d5:77:ac:2e:1b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


> **ugm6hr said:**
> Perhaps the new iwlwifi driver ( [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/) ) has been added?  It should work OK.

The latest driver should be in the [http://packages.ubuntu.com/intrepid-updates/base/linux-backports-modules-2.6.27-11-generic](http://packages.ubuntu.com/intrepid-updates/base/linux-backports-modules-2.6.27-11-generic) package.

I haven't added anything special, except updates. In the June 2008 my ex-gf added Ubuntu 7.10 on my laptop with Vista for me. I upgraded it to 8.04 in July 2008 and in November 2008 I upgraded 8.04 to 8.10. In December 2008 I changed btw my userpassword and since then I log into Ubuntu with the new password, but before it connects to the internet I have to typ the OLD userpassword to unlock some keyring... o_O maybe it has something to do with this, maybe not... anyway... what do you want me to do with the links you gave me? Should I install something? If so... how? (feel really dumb here :P)

---

### Post by WhaleWolf on 2009-02-02
I see now I forgot to add the ifconfig and iwconfig data, my apologies, I must have overlooked that. I will give you the config data of the 22kernel first:

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:2b:a5:40  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:1f:3c:4f:2c:63  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe4f:2c63/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1835 errors:0 dropped:78 overruns:0 frame:0
          TX packets:1806 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2574921 (2.5 MB)  TX bytes:151846 (151.8 KB)
          Interrupt:17 Base address:0xe000 Memory:ecfff000-ecffffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:342 errors:0 dropped:0 overruns:0 frame:0
          TX packets:342 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27320 (27.3 KB)  TX bytes:27320 (27.3 KB)

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Tiscali123C4B"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:21:04:12:3C:4B   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=90/100  Signal level=-43 dBm  Noise level=-113 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:80   Missed beacon:0

pan0      no wireless extensions.
______________________________________________________________________
And now the 27kernel:

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:2b:a5:40  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:1f:3c:4f:2c:63  
          inet6 addr: fe80::21f:3cff:fe4f:2c63/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:208 (208.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:342 errors:0 dropped:0 overruns:0 frame:0
          TX packets:342 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27320 (27.3 KB)  TX bytes:27320 (27.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-4F-2C-63-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"BTOpenzone"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 02:18:F6:0B:23:4E   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=45/100  Signal level:-82 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
_______________________________________________________________________
I see that it says BTOpenzone in the 27kernel, but I have been trying to connect to Tiscali123C4B in the 27kernel as a hidden network, since it doesn't show up on the list of wireless networks. I have tried to connect to BTOpenzone once, maybe it's because of that it shows in the iwconfig data...

---

### Post by ugm6hr on 2009-02-02
OK.  I see the problem...

The new (-27) kernel uses the (new) iwl3945 driver, while the old (-22) kernel uses the (apparently) outdated ipw3945 driver.

It is unfortunate that the new driver apparently doesn't work :(

Try each of the following in succession (with a reboot between each to see if has worked).  You will have to connect with a wire in the -27 kernel to install the various packages.

I would try installing the [linux-backports-module]("apt:linux-backports-modules-intrepid-generic") to see if the latest update fixes things for you.

If that is already installed (or even if you have just installed and it doesn't work) - make sure that the wifi channel is appropriate.

> I see that it says BTOpenzone in the 27kernel, but I have been trying to connect to Tiscali123C4B in the 27kernel as a hidden network, since it doesn't show up on the list of wireless networks. I have tried to connect to BTOpenzone once, maybe it's because of that it shows in the iwconfig data...

So do you get *some* wifi network options in -27 kernel?  If so - I think this is probably the problem:
[http://www.ubuntu.com/getubuntu/releasenotes/810#Only%20US%20wireless%20channels%20enabled%20by%20default%20on%20Intel%203945](http://www.ubuntu.com/getubuntu/releasenotes/810#Only%20US%20wireless%20channels%20enabled%20by%20default%20on%20Intel%203945)

> The iwl3945 wireless driver defaults to the US regulatory domain for wireless, so wireless networks on channels forbidden by US regulations but permitted by European or Japanese regulations will not work out of the box. This affects IEEE 802.11b/g channels 12 (Europe and Japan), 13 (Europe and Japan), and 14 (Japan only), as well as all 802.11a channels. (Some other wireless drivers may be affected; this is the only one we are sure of so far.)

To work around this, add the following line to the /etc/modprobe.d/options file if you use this driver and need to use European wireless channels:

```
options cfg80211 ieee80211_regdom=EU
```

Alternatively, add the following line if you use this driver and need to use Japanese wireless channels:

```
options cfg80211 ieee80211_regdom=JP
```

If it still doesn't, you could roll back to the old driver by uninstalling it:
```
sudo apt-get remove linux-backports-modules-2.6.27-11-generic
```

If that still doesn't work, you could blacklist the iwl3945 driver to ensure that (hopefully) the ipw3945 driver is loaded instead:
```
sudo echo "blacklist iwl3945" >> /etc/modprobe.d/blacklist
```

---

### Post by WhaleWolf on 2009-02-03
I have installed wired the linux-backports-module, rebooted it, but no donut.
Then I tried step2, which is I think is the solution, since other wireless connections do show up (even other wireless Tiscali networks, which is strange, but maybe the neighbours are using different modems), but I cannot add the code 'options cfg80211 ieee80211_regdom=EU' to that file in text editor. How do I get access to edit this and also where do I add the code or doesn't it matter? Do I have to type something in the Terminal like 'sudo add options cfg80211 ieee80211_regdom=EU bladibla'? I really have no clue how to edit files like those. I will copy and paste my /etc/modprobe.d/options file here below btw, just in case:

# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

# Stop auto-association.
# LP: #264104
options ipw2200 associate=0

# XXX: Ignore HPA by default. Needs to be revisted in jaunty
options libata ignore_hpa=1

I hope you can help me out again. :)

---

### Post by ugm6hr on 2009-02-03
```
gksudo gedit /etc/modprobe.d/options
```
Type your password when asked.

Add the following to the bottom of the file:

```
#Edit for iwl3945 wifi driver to use European wireless channels
options cfg80211 ieee80211_regdom=EU
```

Save the file and reboot.

PS:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) explains gksudo use
The # at the start of the first line makes the OS ignore it - but it useful to put it in there in case you forget what it does in the future.

---

### Post by WhaleWolf on 2009-02-04
Okay, when I tried to edit via terminal i got the following error:

Error: no "edit" mailcap rules found for type "application/octet-stream"
ation/octet-stream"

Anyway, I managed to get my wireless connection to work through a different route. I turned off the BTHomeHub-2961 (which is my phone, which has also a wireless modem) and the Tiscali123C4B modemrouter and then I just turned on the Tiscali123C4B modemrouter and leave the BTHomeHub-2961 turned off. Then I checked the list of wireless networks and now the Tiscali123C4B does show up on the list and is no longer hidden and now it does connect to the internet. I turn on the BTHomeHub-2961 and reboot and it is working all normal again. I have no explanation for why this is happening...

Ughm6hr, you probably want to shoot me now, but I still want to thank for all the effort you put in. If you want some extra information, like config-data etc., please let me know.

---

### Post by ugm6hr on 2009-02-04
Anyway - it's working.... That's the main point.

Don't worry about anything now.

It sounds like the problem was interference between the 2 routers, I suspect since they were broadcasting on the same channel.

As for the error you got when trying to edit in Terminal - I suspect you typed it wrong, since that error makes no sense whatsoever.

---

### Post by WhaleWolf on 2009-02-04
> **ugm6hr said:**
> Anyway - it's working.... That's the main point.

Don't worry about anything now.

It sounds like the problem was interference between the 2 routers, I suspect since they were broadcasting on the same channel.

As for the error you got when trying to edit in Terminal - I suspect you typed it wrong, since that error makes no sense whatsoever.

DOH! I did type it wrong, I wrote with pen and paper edit instead of gedit... that's so annoying with Terminal, why isn't it possible to edit in Text Editor? Last and more serious question: I have to type my old password to unlock the default keyring constantly after I log in Ubuntu. Is it possible to change this and where and how do I do this?

---

### Post by ugm6hr on 2009-02-04
> **WhaleWolf said:**
> DOH! I did type it wrong, I wrote with pen and paper edit instead of gedit... that's so annoying with Terminal, why isn't it possible to edit in Text Editor?

You can edit in "Text Editor".  That is the menu name for Gedit!  But to edit system files, you need to launch gedit with "sudo" privileges.

Not sure about the keyring issue.  I recall a thread about deleting your keyring, so you have to then manually re-enter the various passwords, but it should recreate a keyring password to match your user login.  I'll try and look for it some other day.

---

