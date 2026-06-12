---
title: "Newbie alert, very weird networking problem"
date: 2006-06-19
forum: Desktop Environments
---

### Post by armadillo on 2006-06-19
Hello people, I have just tried switching from Debian Sarge to Ubuntu 6.06. I got a really strange problem which I cannot get my mind around.

I am writing this from XP so I don't have access to copy paste command results.

I am connecting to the internet through the ethernet plug of a Thomson Speedtouch 530 ADSL modem. My dual boot (XP and ex-Debian, now Ubuntu) machine uses static IP (10.0.0.1). The router lives at 10.0.0.138.

Booting into Gnome from the Live CD, I go to System->Administration->networking and enter the settings. This changes the appropriate line in my /etc/network/interfaces file to:

auto eth0
iface eth0 inet static
address 10.0.0.1
netmask 255.255.255.0
gateway 10.0.0.138

The internet works fine.

When I proceed to install to HD, the installation seems to work fine. The /etc/network/interfaces file is as above. The result of ifconfig seems to be identical. However, the internet is down. Pinging the router returns "Destination host unreachable".

It sounds too weird to be true. I can understand a network that fails to work in general, but it works when booting from CD only(!?). How can this be? Is there anywhere else that the network is configured except from /etc/network/interfaces? Any help will be greatly appeciated.

---

### Post by cskeide on 2006-06-19
Try configuring from System->Administration->networking again. Also, do you have more than one network card? Wireless? Could be that the interfaces changed name? Could you paste the output of "ifconfig -a"?

---

### Post by armadillo on 2006-06-19
OK, I have tried configuring the net both from the Gnome GUI and manually through /etc/network/interfaces and ifdown/ifup. In all cases, I succeed (I get net) when using either method having booted from the CD whereas I fail when booting from the installation.

Output of ifconfig -a using the CD is below:

eth0      Link encap:Ethernet  HWaddr 00:08:A1:19:76:64  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe19:7664/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:901 (901.0 b)  TX bytes:7968 (7.7 KiB)
          Interrupt:193 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1744 (1.7 KiB)  TX bytes:1744 (1.7 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Output of ifconfig -a using the HD installation is below:

eth0      Link encap:Ethernet  HWaddr 00:08:A1:19:76:64  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe19:7664/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:2 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:3156 (3.0 KiB)
          Interrupt:193 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4253 (4.1 KiB)  TX bytes:4253 (4.1 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Also, in case it's needed, output of lspci:

0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
0000:00:01.0 ISA bridge: nVidia Corporation MCP2A ISA bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation MCP2A SMBus (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation MCP2A USB Controller (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation MCP2S AC'97 Audio Controller (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation MCP2A PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation MCP2A IDE (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)
0000:02:08.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 40)


The ethernet card is the Davicom one at the very end, there is also an onboard one but that has been disabled from the BIOS.

---

### Post by imsmith on 2006-07-08
Install tcpdump on your hard drive install and look at outbound traffic:
[INDENT]
ping your router then open a new terminal and start the tcpdump

sudo tcpdump -ni eth0 

(ctl-c to exit)[/INDENT]

If you aren't seeing outgoing packets, then the card isn't installed or configured properly.  If you are seeing outgoing packets but not return packets, then the card is installed and setup, but something else is wrong.  

If you see "ICMP echo reply" in the tcpdump then the router is receiving your traffic and returning it back to the linux box.  If you don't then the problem isn't on you PC, its on the network.

If it is a problem on your PC, start by making sure that there isn't a firewall turned on, that eth0 is your default NIC, that you have ethernet address resolution, and that your default route is set:

firewall:

[INDENT]check to see if there are any rules in iptables:

sudo iptables -L

by default there aren't any rules.
[/INDENT]

ethernet address resolution:

[INDENT]verify that you have an arp table entry for the router:

arp

you should have something like this:

Address             HWtype  HWaddress             Flags Mask         Iface
10.0.0.138          ether   <6 hexidecimal pairs> C                  eth0

if you don't have an entry in the arp table for the router but you do know the hardware address of the router, you can manually enter it:

arp -s <hostname> <hw_address>

if that change works, understand that you've just treated the symptom and there is an Ethernet address resolution problem (which often means a bad NIC, hub, or switch on the network)

[/INDENT]


default nic & default route:

[INDENT]use the route command:

route

and you should see something like this:

Kernel IP routing table
Destination   Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0      *               255.255.255.0   U     0      0        0 eth0
default       10.0.0.138      0.0.0.0         UG    0      0        0 eth0

if the default gateway is missing, add it:

sudo route add default gw 10.0.0.138 eth0

if the Iface is wrong, then you can change it on the GUI: 

System >> Administration >> Networking >> "Default Gateway Device"
[/INDENT]

That will fix most network problems.  

Good Luck.

---

### Post by armadillo on 2006-07-15
Thank you very much for your help. However, I am afraid the problem still remains. Here is what I did (I am writing this from a laptop next to the sick machine so cannot directly copy paste from the terminal):

Output of "tcpdump -ni eth0" when pinging the router behaves in (what I find) a strange way. I did it ten minutes ago when arp was manually set and indeed got a screenful of "ICMP echo reply" as you predicted.

However, I am doing it again now (and arp seems to have cleared my manual entry) and I am getting instead a load of (manually copied example of single line):

13:37:55.263876 arp who-has 10.0.0.138 tell 10.0.0.1

(10.0.0.138 is the router, 10.0.0.1 the sick machine)

The pinging terminal always gets a "Destination Host Unreachable".
(more on arp further down)

-------------------------------------------

Next, looking at "iptables -L" I am informed that:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

and this is repeated for FORWARD and OUTPUT as well. I presume this is as it is supposed to be.

-------------------------------------------

arp seems to be blank if no ethernet activity has happened for a while. If  I bring it up after an usuccesful ping I get:

Address         HWType        HWAddress         Flags    Mask     Iface
10.0.0.138                    (Incomplete)                        eth0


Giving the following command:
arp -s 10.0.0138 00:0E:50:63:D2:98 (my router's HW address)

I get:

Address         HWType        HWAddress            Flags    Mask     Iface
10.0.0.138      ether         00:0E:50:63:D2:98    CM                eth0

and the tcpdump output changes to ICMP echo request as pointed out above but still no joy from the pinging terminal.
-------------------------------------------

Route seems to be doing fine:

Destination  Gateway     Genmask        Flags   Metric   Ref  Use Iface  
10.0.0.0     *           255.255.255.0  U       0        0    0   eth0
default      10.0.0.138  0.0.0.0        UG      0        0    0   eth0

I presume this is as it is supposed to be.



So, this is it. No idea what the bloody problem might be, sounds very very strange indeed.

---

