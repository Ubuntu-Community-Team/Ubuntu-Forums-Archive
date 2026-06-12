---
title: "Problems connecting wired connection - JJ"
date: 2009-05-15
forum: General Help
---

### Post by Roxlo on 2009-05-15
Whenever I try to connect to the internet in Ubuntu JJ, it says Wired Connection - You are now disconnected.

I have a Dynex DX-E102 10/100 Mbps PCI network card

Any suggestions? Thanks

---

### Post by fooey on 2009-05-15
Give us (copy & paste) output from:

```

lspci
lshw -class network
ifconfig

```
[I]
p.s. also try reseting your router & cable/dsl modem too.[/I]

---

### Post by Roxlo on 2009-05-15
Woops, 1 second

---

### Post by gamblor01 on 2009-05-15
Uhhh...what you pasted is just the usage statement for the lspci command -- that isn't going to help us much as all it does is describe the valid options that lspci accepts.

Maybe you thought you were supposed to type all of those commands on one line?  They are separate commands.  Type:

```

lspci

```

and then paste the output, and so on.  ;)

---

### Post by Roxlo on 2009-05-15
lspci

```
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
02:0a.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster


```


lshw -class network

```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:21:27:fa:58:9d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: e2:69:72:6e:8f:69
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


```


ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:21:27:fa:58:9d  
          inet6 addr: fe80::221:27ff:fefa:589d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

---

### Post by fooey on 2009-05-15
> **gamblor01 said:**
> Uhhh...what you pasted is just the usage statement for the lspci command -- that isn't going to help us much as all it does is describe the valid options that lspci accepts.

Maybe you thought you were supposed to type all of those commands on one line?  They are separate commands.  Type:

```

lspci

```

and then paste the output, and so on.  ;)

Uhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh...then you try & help little buddy then. =;
Bye.

---

### Post by gamblor01 on 2009-05-16
> 
Uhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh...then you try & help little buddy then. =;
Bye.


No problem...I am trying to help.  I was trying to get the correct output posted so that we can diagnose.  ;)

It looks like the kernel is detecting your card (as Realtek) and everything looks OK except that you don't have an IP address (per your ifconfig output).  Can I assume that you wish to obtain an IP address automatically (via DCHP)?  If you want to use a static IP then we'll have to do things differently but I'm just going to assume you want to use DCHP.  Here's what we can try:

Edit your /etc/network/interfaces file (you can use the command "sudo gedit /etc/network/interfaces" to do this).  Add the following lines:

```

auto eth0
iface eth0 inet dhcp

```

Now save and close the file.  At this point your system should be configured to use DHCP.  We just need to run a command to tell your system it needs to obtain an IP address from the DCHP server.  That is done like so:

```

sudo dhclient

```


Does it work now?



Alternatively you can go to System -> Administration -> Network.  After unlocking it you can click on the wired connection and click Properties.  Make sure you have the box checked to "Enable this connection" then set the Configuration to "Automatic configuration (DHCP)".  This will basically insert the 2 lines above into /etc/network/interfaces for you and should get an IP address for you.  In my experience this network applet is really slow/unresponsive most of the time so I prefer the command line -- it's orders of magnitude faster.  :D

---

