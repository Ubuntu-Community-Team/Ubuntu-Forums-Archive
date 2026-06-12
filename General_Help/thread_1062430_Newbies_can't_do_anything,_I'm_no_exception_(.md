---
title: "Newbies can't do anything, I'm no exception :("
date: 2009-02-06
forum: General Help
---

### Post by el canadiano on 2009-02-06
Hey guys,

I have two issues. The two are that I cannot connect to the internet, nor can I change my screen resolution past 800x600. I've been eager to switch OUT of Windows Vista for the past year now, and this is the chance. I'm already impressed by the speed of Ubuntu, by the way. I use Ubuntu 8.1 I think, along with GNOME.

1.) My internet connection is broadband, and it connects to my computer via an Ethernet cable. Somehow, it recognizes my MAC address, and it automatically tries to connect, but can't do anything. I have viewed previous support topics similar to this with no help. I cannot ping, I cannot do scoot.

2.) Do I need Wine or other products to install cards for windows?

If I could get a reply, that would be fantastic, please do let me know what I could do to further help you. Thanks guys.

---

### Post by andrewc6l on 2009-02-07
For connection to the net, try:

sudo dhclient

If you're lucky, it will do the right sort of DNS request and get you online. If it doesn't, it might give you an error which could lead to a diagnosis of your problem. You might have a nonstandard ISP which requires you to make edits to /etd/dhcp3/dhclient.conf. (Try a Google search of Linux +site:whatever-your-isp-is.com.)

To install cards, you'll need to make sure they have a Linux driver. You probably won't have to install a Windows driver if it's supported under Linux. (Most of the time. Some wireless drivers make you install the Windows driver and use a Linux wrapper around it.)

---

### Post by Peter09 on 2009-02-07
can you post the output of the following terminal commands.

```
lshw -C network
```

and 

```
lshw -C display
```

---

### Post by el canadiano on 2009-02-07
That's in Applications, something, right?

---

### Post by el canadiano on 2009-02-07
If I break a double-post rule, sorry. Anyways, my runs of the requested programs.

ISHW -C network/display:
```
awpoon@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:04:07.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:83:2a:54
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network
       description: Ethernet interface
       physical id: 4
       logical name: pan0
       serial: 46:f6:6b:9a:4f:66
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
awpoon@ubuntu:~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: C51 [GeForce 6150 LE]
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=0

```

sudo dhclient
```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No buffer space available
Listening on LPF/pan0/46:f6:6b:9a:4f:66
Sending on   LPF/pan0/46:f6:6b:9a:4f:66
Listening on LPF/eth0/00:18:8b:83:2a:54
Sending on   LPF/eth0/00:18:8b:83:2a:54
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
send_packet: Message too long
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
send_packet: Message too long
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
send_packet: Message too long
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Message too long
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
send_packet: Message too long
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
send_packet: Message too long
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by sigurnjak on 2009-02-07
1. Have you try via terminal sudo pppoeconf .That should get you to configure your internet assuming you are not going via router . It is same as configuring new network connection in xp .

2. Re. your resolution , is your video card recognized ? If you are unsure run from terminal lspci and look for vga adapter . Once you find it go to a synaptic and choose proper drivers . 

Good luck .

P.S. I am using  nvidia glx  new drivers from synaptic .

---

### Post by el canadiano on 2009-02-07
> **sigurnjak said:**
> 1. Have you try via terminal sudo pppoeconf .That should get you to configure your internet assuming you are not going via router . It is same as configuring new network connection in xp .

2. Re. your resolution , is your video card recognized ? If you are unsure run from terminal lspci and look for vga adapter . Once you find it go to a synaptic and choose proper drivers . 

Good luck .

P.S. I am using  nvidia glx  new drivers from synaptic .

Yeah, it always prompts me for installing drivers, then I click it, enter my password, then has a percentage load thingy and then does nothing, so I doubt it =/

---

### Post by sigurnjak on 2009-02-07
So can i assume you have internet going and now just your resolution is a problem ?  Have you tried just updating your system via synaptic ?

If you cannot get synaptic to work via gui you may try terminal  sudo apt-get update.  I also reboot after major update just because i like  to make sure all is applied .

---

### Post by andrewc6l on 2009-02-07
The network issue appears to be a bug in 8.10:

[https://bugs.launchpad.net/bugs/291449](https://bugs.launchpad.net/bugs/291449)
[https://bugs.launchpad.net/bugs/293446](https://bugs.launchpad.net/bugs/293446)

You might want to add your comments to the first link.

---

### Post by sigurnjak on 2009-02-07
That is one reason  to start with long term release !

---

### Post by el canadiano on 2009-02-07
A bug? damn. Any solutions though?

EDIT: I uninstalled Ubuntu 8.10 and installed 8.04, it works now for both errors :D. Thanks to anyone who helped or tried helping.

---

### Post by sigurnjak on 2009-02-08
Glad all is well now ! Enjoy Ubuntu !:D

---

### Post by el canadiano on 2009-02-08
Thanks, you guys are great. Better than Microsoft :P

---

