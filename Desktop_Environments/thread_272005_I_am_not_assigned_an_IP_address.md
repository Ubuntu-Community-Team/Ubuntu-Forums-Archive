---
title: "I am not assigned an IP address"
date: 2006-10-05
forum: Desktop Environments
---

### Post by Chozabu on 2006-10-05
hey yall since ive got to uni i can no longer access the network from linux (however windows still works!)
well, for starters, im running kubuntu dapper64 and i have the same problem when booting from a livecd...

anyhow, i boot up, login - and the internet dont work
so, i check in kcontrols connection settings, where my ip aint listed

---The output of ifconfig is:

eth0      Link encap:Ethernet  HWaddr 00:13:8F:A4:1B:52
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:98 Base address:0xc800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7988 (7.8 KiB)  TX bytes:7988 (7.8 KiB)
---


---the output of netstat -rn is:
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
---

---the output of sudo dhclient is:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:13:8f:a4:1b:52
Sending on   LPF/eth0/00:13:8f:a4:1b:52
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
---

i've tried copying the working info from windows too, but with no luck

---i don't know if its relevant, but the uncomment lines of /etc/dhcp3/dhclient.conf are
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
---

well, i'm rather stumped, if anyone has any ideas, id love to know!

---

### Post by louieb on 2006-10-05
First I don't know what could be the problem. But I would like to know a couple of things. In windows right click on my computer and select manage > services. Find the DHCP entry and see if it is started. If not then Windows is setup to use a static IP address.
 You said you tried to copy your windows setting over to linux. Where did you get them from? Again on windows open a command prompt and enter ```
ipconfig -all
```
Use the the info found here to setup linux to use a static IP.

---

### Post by Chozabu on 2006-10-05
yep, Windows is setup to use DHCP
---output of ipconfig -all
Windows IP Configuration

        Host Name . . . . . . . . . . . . : godd2
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : aber.ac.uk

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : aber.ac.uk
        Description . . . . . . . . . . . : ULi PCI Fast Ethernet Controller
        Physical Address. . . . . . . . . : 00-13-8F-A4-1B-52
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 144.124.97.20
        Subnet Mask . . . . . . . . . . . : 255.255.248.0
        Default Gateway . . . . . . . . . : 144.124.103.254
        DHCP Server . . . . . . . . . . . : 144.124.103.254
        DNS Servers . . . . . . . . . . . : 144.124.16.12
                                            144.124.16.11
        Primary WINS Server . . . . . . . : 144.124.0.10
        Secondary WINS Server . . . . . . : 144.124.0.9
        Lease Obtained. . . . . . . . . . : 05 October 2006 19:46:00
        Lease Expires . . . . . . . . . . : 06 October 2006 19:46:00

Ethernet adapter Local Area Connection 4:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : TAP-Win32 Adapter V8
        Physical Address. . . . . . . . . : 00-FF-9C-EC-04-D2
---
the info i tried connecting with in linux (as a static IP) was using:
        IP Address. . . . . . . . . . . . : 144.124.97.20
        Subnet Mask . . . . . . . . . . . : 255.255.248.0
        Default Gateway . . . . . . . . . : 144.124.103.254
        DHCP Server . . . . . . . . . . . : 144.124.103.254
        DNS Servers . . . . . . . . . . . : 144.124.16.12
                                            144.124.16.11
but no luck that way either!

---

### Post by Chozabu on 2006-10-14
a dmsg|grep eth0 returns
[   51.851360] eth0: ULi M5263 at pci0000:00:12.0, 00:13:8f:a4:1b:52, irq 98.
[   55.184095] uli526x: eth0 NIC Link is Down

afaik this means it really is not even aware its plugged in?

still i am very stuck, and would love to hear anyones ideas, even if its only got a tiny chance of helping

---

### Post by louieb on 2006-10-14
I just looked at a Slackware KDE desktop and could not find a form for network settings. To bad you don't have Ubuntu. in the Gnome desktop you go to System > Network setting. and tell it to use dhcp. You might try goind to a terminal window and try running dhclient-script. This is the DHCP configuration script. I found this by clicking the help icon and doing a search for DHCP. Who know?

---

### Post by Chozabu on 2006-10-15
well, in kubuntu its kmenu>system settings>network settings
it is set up to use dhcp, and works for both my dhcp routers at home (in kubuntu and windows)

when i try and run
dhclient-script
it complains that the command is not found...
ill check that out mroe asap though!

also, booting my box from a plain ubuntu live cd has the same problem
but a friends laptop does not!

so i guess the problem may be an oddity between my particular network interface driver and the unis network system?

---

### Post by Chozabu on 2006-10-17
well, its been 3 weeks or so since this problem came up
and ive given up, im borrowing a friends network card

which is working fine :)

---

### Post by Iowan on 2006-10-17
It's probably just me, but I'm having a hard time understanding:> Interrupt:[COLOR="Red"]98[/COLOR] Base address:0xc800I've seen Interrupt> 16 in other places, but is still seems odd to me...

---

### Post by nixios on 2006-10-17
Chozabu, try to use the command line ifconfig.

ifconfig up < makes your network card up>

or try to put static ip address on your interface.

ifconfig *interface_type* *ip_address* *netmask* 

then issue,

route add *ip_address* for routing.

hth.

---

### Post by Chozabu on 2006-10-19
ifconfig up wont bring my old card up
ill try a static again some other time, but for the min im just enjoying having the working net (upgraded to edgy etc)

oddly enough, this network cark im using now seems to cause windows to BSOD instantly after login... no worries though!

---

### Post by louieb on 2006-10-19
Found this in the Gentoo installation handbook it might help.

DHCP (Dynamic Host Configuration Protocol) makes it possible to automatically receive networking information (IP address, netmask, broadcast address, gateway, nameservers etc.). This only works if you have a DHCP server in your network (or if your provider provides a DHCP service). To have a network interface receive this information automatically, use dhcpcd:



```
# dhcpcd eth0
Some network admins require that you use the
hostname and domainname provided by the DHCP server.
In that case, use
# dhcpcd -HD eth0
```

---

