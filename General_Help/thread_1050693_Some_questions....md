---
title: "Some questions..."
date: 2009-01-25
forum: General Help
---

### Post by hjehkj34h on 2009-01-25
I am getting close to uninstalling Windows XP, and trying out Ubuntu.  Before I do, I have a few questions...

1.  Unrelated, but when I uninstall Windows XP from my computer, I plan on using Darik's Boot and Nuke to format my hard drive, and plan on using the Government standard (, or whatever it is), which is something like thirty-two writes.  My hard drive is at least five years old, and I was simply wondering if this could cause any problems with it?

2.  I have a Lexmark X5435 Printer that I just recently bought.  I have looked at some lists, and I do not see any drivers for this printer.  Would there be any chance of getting this printer to work?  I would prefer not to have to buy another one, as again, I just got this one.

3.  I have Verizon DSL, along with a Westell 6100 router.  On Windows XP, everything is running on it except for Ethernet.  When I booted Ubuntu from the LiveCD, I was not able to access the internet.  I am guessing that the CD that came with it will not work for Ubuntu.  What would the recommended instructions be for getting it to work?

4.  Going back to question three, should the internet work on the LiveCD?

Thanks in advance for any help with these questions!

---

### Post by 50words on 2009-01-25
If you are going to keep using the drive, then using DBAN seems unnecessary. If the drive dies, it won't be from DBAN, but because its time has come.

I had to do some Googling to find a PPD file for my Lexmark e120n printer, but it works pretty great for everything except when printing image-based PDFs. I would guess you can get similar results from yours if you look around.

If the internet does not work when you use the LiveCD, I would not expect it to work from an install. However, if it is not working, the problem is more likely related to your ethernet or wireless card than your router.

---

### Post by caro on 2009-01-25
> **hjehkj34h said:**
> I am getting close to uninstalling Windows XP, and trying out Ubuntu.  Before I do, I have a few questions...

3.  I have Verizon DSL, along with a Westell 6100 router.  On Windows XP, everything is running on it except for Ethernet.  When I booted Ubuntu from the LiveCD, I was not able to access the internet.  I am guessing that the CD that came with it will not work for Ubuntu.  What would the recommended instructions be for getting it to work?



3.  Before you begin your Ubuntu installation, check the settings on your router and write them down.  More than likely the Verizon CD won't have a Linux version, but if you know the network settings you won't need it.  (You actually don't need it for Windows either; it just helps some people set up their DSL more easily.)  The DSL modem shouldn't need anything done to it if it is already running.

---

### Post by perlluver on 2009-01-25
I am using Verizon DSL on Ubuntu through a Linksys router, and an ethernet cable, and before that I had the modem plugged directly into my computer and it always worked.  So I am wondering if you are using Wireless or USB?

---

### Post by hjehkj34h on 2009-01-25
> **50words said:**
> If you are going to keep using the drive, then using DBAN seems unnecessary. If the drive dies, it won't be from DBAN, but because its time has come.

I had to do some Googling to find a PPD file for my Lexmark e120n printer, but it works pretty great for everything except when printing image-based PDFs. I would guess you can get similar results from yours if you look around.

If the internet does not work when you use the LiveCD, I would not expect it to work from an install. However, if it is not working, the problem is more likely related to your ethernet or wireless card than your router.

Since I was putting a new operating system on the computer, I figured that I would "start clean".  Would it be recommended that I not format the drive?

Regarding the printer, I just recently read something about installing the drivers through WINE, and printing through Notepad.  Would this work for other Windows applications?  If I can't get it to work, that would at least be better than nothing..

> **caro said:**
> 3.  Before you begin your Ubuntu installation, check the settings on your router and write them down.  More than likely the Verizon CD won't have a Linux version, but if you know the network settings you won't need it.  (You actually don't need it for Windows either; it just helps some people set up their DSL more easily.)  The DSL modem shouldn't need anything done to it if it is already running.

Yeah, when I start the computer, the "Internet" light on the router is green.  If I remember correctly, on XP, I would use "192.168.1.1" to get to the network settings.  That does not work for me on Ubuntu.

> **perlluver said:**
> I am using Verizon DSL on Ubuntu through a Linksys router, and an ethernet cable, and before that I had the modem plugged directly into my computer and it always worked.  So I am wondering if you are using Wireless or USB?

I have an Ethernet cable, but for whatever reason, I never connected it.

I am using USB.  The router that I am using does not have wireless capabilities.

---

### Post by perlluver on 2009-01-25
> **hjehkj34h said:**
> Since I was putting a new operating system on the computer, I figured that I would "start clean".  Would it be recommended that I not format the drive?

Regarding the printer, I just recently read something about installing the drivers through WINE, and printing through Notepad.  Would this work for other Windows applications?  If I can't get it to work, that would at least be better than nothing..



Yeah, when I start the computer, the "Internet" light on the router is green.  If I remember correctly, on XP, I would use "192.168.1.1" to get to the network settings.  That does not work for me on Ubuntu.



I have an Ethernet cable, but for whatever reason, I never connected it.

I am using USB.  The router that I am using does not have wireless capabilities.

I don't believe you can connect through the USB cable in Ubuntu, you will have to use the ethernet cable.  You have to use the software that Verizon supplies to use the USB cable, and it will not install in Ubuntu.

---

### Post by caro on 2009-01-25
> **hjehkj34h said:**
> 
Yeah, when I start the computer, the "Internet" light on the router is green.  If I remember correctly, on XP, I would use "192.168.1.1" to get to the network settings.  That does not work for me on Ubuntu.


You probably need to set/modify your network configuration.  Check your settings on System > Preferences.  The IP address of your router won't change under Ubuntu but your computer probably isn't seeing or connecting to the router.  Check your IP address and if it is not in the same range as your router, you won't be able to connect.

---

### Post by mb_webguy on 2009-01-25
Regarding DBAN... The only reason you'd want to use something like that is if you were giving or selling the drive to someone else, and wanted to make absolutely sure they couldn't read any of your personal information from the disk.  If you are personally going to continue using the drive, then there's no reason for this.  Surely you're not so paranoid that you don't trust yourself not to steal your own data? ;)

When you install a new operating system, the partitioner will format the drive, anyway.  It won't do as thorough a job as DBAN, but it doesn't have to.  The purpose of the installer's partitioner is to prepare the drive for the new operating system, and not to protect national security.

---

### Post by hjehkj34h on 2009-01-25
> **perlluver said:**
> I don't believe you can connect through the USB cable in Ubuntu, you will have to use the ethernet cable.  You have to use the software that Verizon supplies to use the USB cable, and it will not install in Ubuntu.

I'll try that out.  I guess I should get the internet working before I switch over to it.

> **caro said:**
> You probably need to set/modify your network configuration.  Check your settings on System > Preferences.  The IP address of your router won't change under Ubuntu but your computer probably isn't seeing or connecting to the router.  Check your IP address and if it is not in the same range as your router, you won't be able to connect.

I'll check this out as well.

> **mb_webguy said:**
> Regarding DBAN... The only reason you'd want to use something like that is if you were giving or selling the drive to someone else, and wanted to make absolutely sure they couldn't read any of your personal information from the disk.  If you are personally going to continue using the drive, then there's no reason for this.  Surely you're not so paranoid that you don't trust yourself not to steal your own data? ;)

When you install a new operating system, the partitioner will format the drive, anyway.  It won't do as thorough a job as DBAN, but it doesn't have to.  The purpose of the installer's partitioner is to prepare the drive for the new operating system, and not to protect national security.

LOL, that's true.  I guess I'll go without doing this.

One more question for now, but with the printer, could the drivers be installed through WINE?  If so, could I then print through different Windows applications?  I read this on another thread...

Thanks again for all of the help!

---

### Post by mb_webguy on 2009-01-25
As to your printer...  That particular Lexmark isn't currently supported under Linux (which, by the way, is entirely Lexmark's fault).  HP is much more Linux-friendly, so if you can get your hands on an HP printer you'll be much better off.  And for those printers which do have Linux support, setup is pretty easy in Ubuntu.

An no, you can't install printer drivers under Wine.  Wine is just an application interface.  Think of it like... dressing a man in drag.  People who wouldn't have anything to do with a strange man might be willing to stop and talk to a beautiful woman -- but he/she still has the same equipment underneath, regardless of how he/she looks on the outside.  Wine makes Linux look like Windows to Windows applications, but you're still dealing with the Linux operating system, and it's the operating system that interfaces with hardware.  So nothing you do in Wine is going to have any effect on your ability to access hardware.

---

### Post by 3rdalbum on 2009-01-25
Wine is a **last resort**, and the majority of drivers do not work in Wine. Only if there is absolutely no native way should you try installing the Windows drivers.

---

### Post by hjehkj34h on 2009-01-26
Okay, I checked some things, and I forgot that I didn't have an Ethernet port on my computer, which is why I don't have Ethernet on.

> **caro said:**
> You probably need to set/modify your network configuration.  Check your settings on System > Preferences.  The IP address of your router won't change under Ubuntu but your computer probably isn't seeing or connecting to the router.  Check your IP address and if it is not in the same range as your router, you won't be able to connect.

Sorry, but where would I go once I am at Preferences?  I went to Network Connections, and I still couldn't get it to work.  Also, my router is an NAT router.  Sorry if that would have helped.

Thanks for the advice and information on the drivers and WINE.

---

### Post by caro on 2009-01-26
A couple of things to get you started:

System > Administration > Network > Devices
Click on the drop down box and select your ethernet device and check your IP address.  This will help you see which devices are recognized and working.  If the IP address isn't in the same range as your router's network, then something is configured incorrectly.

System > Preferences > Network Connections
Select the tab for the wired or wireless network interface you see from the steps above. Click on the device (or one of them if you have multiple) and then click on Edit at the right.  Make sure you have "connect automatically" enabled, and on the IPv4 tab make sure your settings there are correct (most likely DHCP).   If you are wireless, then make sure the SSID is correct, etc.

---

### Post by albinootje on 2009-01-26
> **hjehkj34h said:**
>  2.  I have a Lexmark X5435 Printer that I just recently bought.  I have looked at some lists, and I do not see any drivers for this printer.  Would there be any chance of getting this printer to work?  I would prefer not to have to buy another one, as again, I just got this one.

Just did a search, on [http://linuxprinting.org](http://linuxprinting.org) amongst others, .. nothing.
Lexmark is not very pro Linux is my impression, you're better off with HP or Epson, but first do a little research.
Linux hardware support is getting better and better, but it will take some time before all hardware vendors will see the light and start being more supportive towards Linux.
> 
4.  Going back to question three, should the internet work on the LiveCD?

Normally yes.
Perhaps you need to restart your router, or fill in specific network settings first.

---

### Post by hjehkj34h on 2009-01-27
I don't have an Ethernet port, so I have to use USB.  I believe that I found some instructions on this page...

[https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch]("https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch")

Am I on the right track, and if so, would this driver work with a Westell 6100 router?  Also, is it possible to test this on the LiveCD without actually "installing" anything?

---

### Post by albinootje on 2009-01-28
> **hjehkj34h said:**
> I don't have an Ethernet port, so I have to use USB.  I believe that I found some instructions on this page...

[https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch]("https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch")

Am I on the right track, and if so, would this driver work with a Westell 6100 router?  

I don't know. Did you search for :
```

"Westell 6100" router ubuntu

```
.. Does that router support wifi ?
> 
Also, is it possible to test this on the LiveCD without actually "installing" anything?
With the "try without installing" you can install software into the RAM memory just for that session.

---

### Post by hjehkj34h on 2009-01-28
> **albinootje said:**
> I don't know. Did you search for :
```

"Westell 6100" router ubuntu

```
.. Does that router support wifi ?

With the "try without installing" you can install software into the RAM memory just for that session.

I found a page similar to this when accessing help through the Ubuntu LiveCD...

[https://help.ubuntu.com/community/UsbAdslModem]("https://help.ubuntu.com/community/UsbAdslModem")

It seemed to list that link as the main one to use.  I checked the other ones, and did not see any Westell router listed as being compatible.

The router does not support WiFi.

According to some instructions that I have, it mentions about a firmware.  Would that be placed onto the RAM, or the router?

---

### Post by albinootje on 2009-01-28
> **hjehkj34h said:**
> I found a page similar to this when accessing help through the Ubuntu LiveCD...

[https://help.ubuntu.com/community/UsbAdslModem]("https://help.ubuntu.com/community/UsbAdslModem")

It seemed to list that link as the main one to use.  I checked the other ones, and did not see any Westell router listed as being compatible.


Right. I've searched again, now for :
```

"Westell 6100" usb linux

```
and the results were not very helpful :(

Here are driver for MS-Windows, no Linux drivers there :
[http://www.fastaccess.drivers.bellsouth.net/#westell](http://www.fastaccess.drivers.bellsouth.net/#westell)

Can you post the output of :
```

lsusb

```
with your modem + usb cable attached ?

---

### Post by hjehkj34h on 2009-01-30
Sorry for the delayed responses...

Anyway, here is what I got when I ran "lsusb" in the Terminal...

> Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0781:b2b5 SanDisk Corp. 
Bus 001 Device 002: ID 06a9:000b Westell WireSpeed Dual Connect Modem
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I had my SD card connected, so that is what the SanDisk line is for.

---

### Post by albinootje on 2009-01-30
> **hjehkj34h said:**
> here is what I got when I ran "lsusb" in the Terminal...

Thanks.
Can you post the output of :
```

sudo lshw -C network
ifconfig -a
route -n
cat /etc/resolv.conf

```

---

### Post by hjehkj34h on 2009-01-30
Okay...

sudo lshw -C network...

> ubuntu@ubuntu:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: 00:0f:db:c5:33:b1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device link=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 86:9e:32:73:0f:13
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

ifconfig -a

> ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0f:db:c5:33:b1  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:133 dropped:0 overruns:0 frame:133
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1544 (1.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13536 (13.5 KB)  TX bytes:13536 (13.5 KB)

pan0      Link encap:Ethernet  HWaddr 86:9e:32:73:0f:13  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

route -n

> ubuntu@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

cat /etc/resolv.conf

> ubuntu@ubuntu:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: No such file or directory

---

### Post by albinootje on 2009-01-30
> **hjehkj34h said:**
> sudo lshw -C network...


Thanks. Please post the output of this :
```

lspci
sudo dhclient eth0

```

And do you know the ip address of the router ?

---

### Post by hjehkj34h on 2009-01-30
Okay.  I'll be right back.

I use 192.168.1.1 to access the settings of the router on Windows.  This does not work on Ubuntu.  If this isn't what you mean, then sorry, I do not know the IP address.

---

### Post by albinootje on 2009-01-30
> **hjehkj34h said:**
> Okay.  I'll be right back.

I use 192.168.1.1 to access the settings of the router on Windows.  This does not work on Ubuntu.  If this isn't what you mean, then sorry, I do not know the IP address.

Good.
In case "dhclient" doesn't work, can you do the following, and post the output here :
```

sudo ifconfig eth0 192.168.1.100 up
sudo route add default gw 192.168.1.1
ping -c3 192.168.1.1
ping -c3 62.108.1.66

```

---

### Post by hjehkj34h on 2009-01-30
lspci

> ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:08.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax/Voice/Spkp Modem (rev 01)
02:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
02:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)

sudo dhclient eth0

> ubuntu@ubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0f:db:c5:33:b1
Sending on   LPF/eth0/00:0f:db:c5:33:b1
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Sorry, but I'll have to try the commands that you just posted a little later.

---

### Post by albinootje on 2009-01-30
Thanks for the output.
I'm getting confused though. First you talked about ethernet in a few comments, then you wrote that you don't have an ethernet port, and you have to use usb, which does fit with the output of lspci and lsusb (which does show your router and not an ethernet interface).
But why are you not getting an ip address through dhcp ?

I assume your ISP delivered the modem/router with a MS-Windows support cdrom ?
Would it make sense to phone your ISP about this ?
What about finding a pcmcia based ethernet card for your laptop (I assume it's a laptop) ?

---

### Post by hjehkj34h on 2009-01-30
Yes, my ISP sent the router along with a CD for Windows.  As for Ethernet, I forgot that I didn't have an Ethernet port on this computer, and I was hoping to get it to work without having to buy an Ethernet card.  I guess I could try calling them, but I'm not sure if they support this operating system.  Also, no, I do not have a laptop.

Anyway, the first two commands that you gave me did not do anything.  These are the results of the last two...

ping -c3 192.168.1.1

> ubuntu@ubuntu:~$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.100 icmp_seq=1 Destination Host Unreachable
From 192.168.1.100 icmp_seq=2 Destination Host Unreachable
From 192.168.1.100 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2014ms
, pipe 3

ping -c3 62.108.1.66

> ubuntu@ubuntu:~$ ping -c3 62.108.1.66
PING 62.108.1.66 (62.108.1.66) 56(84) bytes of data.
From 192.168.1.100 icmp_seq=1 Destination Host Unreachable
From 192.168.1.100 icmp_seq=2 Destination Host Unreachable
From 192.168.1.100 icmp_seq=3 Destination Host Unreachable

--- 62.108.1.66 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2014ms
, pipe 3

---

### Post by albinootje on 2009-01-30
> **hjehkj34h said:**
> As for Ethernet, I forgot that I didn't have an Ethernet port on this computer, and I was hoping to get it to work without having to buy an Ethernet card.

It is gonna be soooooo much easier to get you internet in Linux if you do have a network card. 
Cheapest network cards here are 5 euros and they do work with Linux (very often they have a Realtek chipset, which is supported).

---

### Post by hjehkj34h on 2009-01-30
Okay.  I guess I'll consider looking for one.  Just curious, but would a USB to Ethernet adapter work, or would I need an Ethernet card?

---

### Post by albinootje on 2009-01-30
> **hjehkj34h said:**
> Okay.  I guess I'll consider looking for one. 

Cool! :)
> 
Just curious, but would a USB to Ethernet adapter work, or would I need an Ethernet card?
Go for the ethernet card.

I've seen one usb wifi stick from a friend which worked fine for Linux, but I can imagine that buying a random usb-2-ethernet converter is perhaps not gonna work in Linux.

And it's also pretty likely that the computer shop people can tell you whether the cheapest ethernet card works in Linux or not. 
I would be surprised if it didn't.

---

### Post by hjehkj34h on 2009-01-30
Okay, thanks for the help!

I'm just asking on that because I've never opened the computer up before.  I figured that the card would probably be the better alternative.

---

### Post by ajboesch on 2010-03-08
Verizon tech support does not support linux....only winblows and mac

---

