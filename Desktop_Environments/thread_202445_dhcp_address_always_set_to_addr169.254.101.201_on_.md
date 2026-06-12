---
title: "dhcp address always set to addr:169.254.101.201 on boot - server sends IP 10.1.1.194"
date: 2006-06-23
forum: Desktop Environments
---

### Post by hanasaki on 2006-06-23
eth0 is set to auto dhcp in /etc/interfaces

on boot the IP is always 
eth0      Link encap:Ethernet  HWaddr 00:01:6C:3F:58:DE
          inet addr:169.254.101.201  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::201:6cff:fe3f:58de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1009 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1045 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:491896 (480.3 KiB)  TX bytes:209125 (204.2 KiB)
          Interrupt:169 Base address:0xe800There is a dhcp server on the subnet that is delivering 10.1.1.194 for this MAC.  The syslog says the IP is being set and renewed correctly as 10.1.1.194 however after boot the IP is always 169.254.101.201

---

### Post by ayoli on 2006-06-23
i had this strange pb but only with dcp on wifi device. curious to have an advice  on this subject ;)

---

### Post by hanasaki on 2006-06-23
No : for now i just restart the dhcp clent daemon manually after reboot.  Not a godo work around :(

---

### Post by Ocxic on 2006-06-23
check that your routers/switches have DHCP disabled, it could be interfering with you're server.

---

### Post by hanasaki on 2006-06-23
There is nothing else on the subnet that is providing DHCP.
The really odd part is that the dhcp client is reporting setting the IP to the correct address of 10.1.1.194  but ifconfig shows the 169.... IP

there is something in the /etc/network/... up script that sets the IP to some 169.254 subnet if an IP has not already been set.  could there be some race condition between the setting via dhcpc and this script at boot time?

---

### Post by dbott67 on 2006-06-23
The 169.254.xxx.xxx subnet is reserved for APIPA.  

[APIPA]("http://www.webopedia.com/TERM/A/APIPA.html") is short for Automatic Private IP Addressing, a feature of later Windows operating systems. With APIPA, DHCP clients can automatically self-configure an IP address and subnet mask when a DHCP server isn't available. When a DHCP client boots up, it first looks for a DHCP server in order to obtain an IP address and subnet mask. If the client is unable to find the information, it uses APIPA to automatically configure itself with an IP address from a range that has been reserved especially for Microsoft. The IP address range is 169.254.0.1 through 169.254.255.254. The client also configures itself with a default class B subnet mask of 255.255.0.0. A client uses the self-configured IP address until a DHCP server becomes available.

The APIPA service also checks regularly for the presence of a DHCP server (every five minutes, according to Microsoft). If it detects a DHCP server on the network, APIPA stops, and the DHCP server replaces the APIPA networking addresses with dynamically assigned addresses.

As to why it's happening, I cannot say, but on MS platforms this is normal whenever the DHCP server cannot be reached or is unavailable.  I was not aware that Ubuntu utilized it.

A few things you can try:

1.  Give your DHCP client a static IP address from the same range that the DHCP server is supposed to provide. See whether you can ping the DHCP server. If you cannot, double-check your cabling and your NIC cards.

2. DHCP uses the BOOTP protocol for its communication between the client and server. Make sure there are no firewalls blocking this traffic. DHCP servers expect requests on UDP port 67 and the DHCP clients expect responses on UDP port 68.

The fact that you can get it working by restarting the dhcp daemon leads me to believe that #2 is not the problem, however, by setting a static IP you can see if your network connection is working after every re-boot.  If not, then it could be something related the the NIC driver or maybe a hardware issue.

Can you post what type of ethernet card you have and which driver it's using?  Post the output of the following commands:
```
sudo lshw -C network
```
and 
```
lsmod
```

-Dave

---

### Post by hanasaki on 2006-06-23
set the ip to the correct 10.1.1.194 by restarting the dhcpclient daemon
able to ping the dhcpd server host on 10.1.1.254 by IP and by hostname
able to ssh to the dhcpd server host

FYI built the kernel with kernel-package
Linux deskstation 2.6.16.20 #1 SMP PREEMPT Mon Jun 19 10:05:28 CDT 2006 i686 GNU/Linux

lshw -C network
  *-network
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:01:6c:3f:58:de
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=sis900 driverversion=v1.08.09 Sep. 19 2005 duplex=full ip=10.1.1.194 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:e800-e8ff iomemory:ea022000-ea022fff irq:169
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: bond0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bonding driverversion=3.0.1 firmware=2 master=yes multicast=yes

---

### Post by hanasaki on 2006-06-23
lsmod
Module                  Size  Used by
rfcomm                 40532  0
l2cap                  27712  5 rfcomm
ppdev                  10564  0
ipv6                  277760  14
vfat                   14336  0
fat                    55260  1 vfat
it87                   21604  0
hwmon_vid               3200  1 it87
i2c_isa                 5312  1 it87
i2c_sis96x              6084  0
parport_pc             28908  1
lp                     12608  0
parport                40840  3 ppdev,parport_pc,lp
ide_cd                 41888  0
usb_storage            43012  0
nvidia               4553428  12
snd_intel8x0           33884  3
snd_ac97_codec         97184  1 snd_intel8x0
snd_ac97_bus            2688  1 snd_ac97_codec
serio_raw               7812  0
evdev                  10432  1

---

### Post by dbott67 on 2006-06-24
[QUOTE=hanasaki]set the ip to the correct 10.1.1.194 by restarting the dhcpclient daemon
able to ping the dhcpd server host on 10.1.1.254 by IP and by hostname
able to ssh to the dhcpd server host[/QUOTE]

After re-booting, are you still able to ping/ssh to the DHCP server?  Does the network appear to function properly?

-Dave

---

### Post by hanasaki on 2006-06-24
yes.  there is even a route in the route tables for the 169 subnet.

---

### Post by Paulo79 on 2006-12-14
Well, although the discussion above occurred quite a while ago, I found myself having the same problem on Ubuntu Dapper and Edgy:

The DHCP client would tell me that my computer was bound to a valid IP address, but then ifconfig would show me "inet addr:169.254..." I need the valid address since I'm running sshd and apache in this computer.

I didn't want to spend a lot of time on this (so there might be a better solution to solve this problem). I just edited /etc/default/zeroconf and uncommented the line DISABLE=yes.

Now both ifconfig and the DHCP client show me the same (valid) IP address.

---

### Post by Fenix-TX on 2007-02-10
Hi! i have this problem too with zeroconf, but i want to use zeroconf and samba (my router give me a valid ip addres, but in ifconfig i see 169.x.x.x, but i can surf trough internet...).

Is there any way to resolve that problem with zerconf? I'm using it, and i want to use it, but this causes me problems with samba...

---

### Post by gradedcheese on 2007-02-10
zeroconf uses the 169.254/ prefix when a DHCP or static IP isn't available.  This something very neat called "IPv4 Link Local" (or IP4LL).  It should not, however, be happening when you have an IP address already.  Assuming your network interface is eth0, you could ask for a DHCP address:

sudo dhclient eth0

do you get an address that way?

Or, if you are on a static IP:

sudo ifconfig eth0 put_the_ip_here

---

### Post by Fenix-TX on 2007-02-11
> **gradedcheese said:**
> zeroconf uses the 169.254/ prefix when a DHCP or static IP isn't available.  This something very neat called "IPv4 Link Local" (or IP4LL).  It should not, however, be happening when you have an IP address already.  Assuming your network interface is eth0, you could ask for a DHCP address:

sudo dhclient eth0

do you get an address that way?

Yes i get an address now, but then, zeroconf will work too?
And i have to do that always or can i edit some file to put that line?
Will it happen on Feisty too or on Feisty this not happen?

---

### Post by gradedcheese on 2007-02-11
Yes, zeroconf will work just fine with a regular IP address.  Edit /etc/network/interfaces so that (for example, for eth0) you have:

iface eth0 inet dhcp

---

### Post by Fenix-TX on 2007-02-12
> **gradedcheese said:**
> Yes, zeroconf will work just fine with a regular IP address.  Edit /etc/network/interfaces so that (for example, for eth0) you have:

iface eth0 inet dhcp

Yes i have that:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```
 i need to add dhclient eth0?

---

### Post by Fenix-TX on 2007-03-06
Well i resolve my problem uncommenting this line on /etc/default/zeroconf

```

FALLBACK=yes

```

Now i always have the IP address that router assign to my computer.

---

