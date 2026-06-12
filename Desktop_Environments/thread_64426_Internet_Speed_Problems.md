---
title: "Internet Speed Problems"
date: 2005-09-11
forum: Desktop Environments
---

### Post by jlacroix on 2005-09-11
For the longest time, my wife and I have been having disconnects every day. Her and I both have an Ubuntu PC, hers 500mhz with 256MB of RAM, and mine 900mhz with 768MB of Ram. I also have a computer that runs Windows 2000 for wingames.

Anyway, we've been calling Comcast frequently about these disconnects. They've been acting like they don't know what we're talking about. When it happens, the internet speed gets slower, and slower, and slower, until its completely gone. At that point, I have to unplug my router and cable modem, reset them and plug them back in, then reboot the computers.

I just recently this week set up my Windows 2000 PC to play some games. I noticed recently that when the internet goes down, the Windows 2000 PC still has an extremely fast connection. The Windows 2000 PC hasn't been having any disconnects at all. In fact, a broadband speed report indicates that the Windows 2000 PC is getting a modest 2.2Mbit connection, while our Ubuntu computers are lucky to get 1.2!

Thinking a bit further, I've used a ton of distro's before, more importantly Redhat, Fedora, Suse, Mandrake, PC Linux OS, and even Linspire. None of them have had problems with the internet connection, only Ubuntu. The problem started when I switched from Fedora to Ubuntu several months ago.

When this problem started I was running Hoary (stable). Now I am running Breezy (unstable) and my wife is still running Hoary. We've had problems with Hoary through to more currently Breezy.

I still think Ubuntu is the greatest operating system on earth, don't get me wrong, but it has a very serious internet problem. Is there a fix for this yet?

---

### Post by cwaldbieser on 2005-09-11
[QUOTE=jlacroix]For the longest time, my wife and I have been having disconnects every day. Her and I both have an Ubuntu PC, hers 500mhz with 256MB of RAM, and mine 900mhz with 768MB of Ram. I also have a computer that runs Windows 2000 for wingames.

Anyway, we've been calling Comcast frequently about these disconnects. They've been acting like they don't know what we're talking about. When it happens, the internet speed gets slower, and slower, and slower, until its completely gone. At that point, I have to unplug my router and cable modem, reset them and plug them back in, then reboot the computers.

I just recently this week set up my Windows 2000 PC to play some games. I noticed recently that when the internet goes down, the Windows 2000 PC still has an extremely fast connection. The Windows 2000 PC hasn't been having any disconnects at all. In fact, a broadband speed report indicates that the Windows 2000 PC is getting a modest 2.2Mbit connection, while our Ubuntu computers are lucky to get 1.2!

Thinking a bit further, I've used a ton of distro's before, more importantly Redhat, Fedora, Suse, Mandrake, PC Linux OS, and even Linspire. None of them have had problems with the internet connection, only Ubuntu. The problem started when I switched from Fedora to Ubuntu several months ago.

When this problem started I was running Hoary (stable). Now I am running Breezy (unstable) and my wife is still running Hoary. We've had problems with Hoary through to more currently Breezy.

I still think Ubuntu is the greatest operating system on earth, don't get me wrong, but it has a very serious internet problem. Is there a fix for this yet?[/QUOTE]
Could you describe the physical connections of your home network in a little more detail?  And is your router wired or wireless?

---

### Post by jlacroix on 2005-09-11
Sorry. I'll try my best. I have a Belkin router. The cable modem is plugged into the cable modem port, and it has four ports that I have the three computers plugged into. All ethernet cabling, its a wireless router but the wireless portion is turned off, because it can do both.

Basically each computer has a network cable plugged into the network cards going into the router, which has the cable modem attached to it.

---

### Post by cwaldbieser on 2005-09-11
[QUOTE=jlacroix]Sorry. I'll try my best. I have a Belkin router. The cable modem is plugged into the cable modem port, and it has four ports that I have the three computers plugged into. All ethernet cabling, its a wireless router but the wireless portion is turned off, because it can do both.

Basically each computer has a network cable plugged into the network cards going into the router, which has the cable modem attached to it.[/QUOTE]
Are you using dynamic IP addresses for your PCs or static IP addresses or a mix?

The first thing I would try is to see what the basic differences are between the networking configurations for your Ubuntu and Windows 2000 machines.

For the Ubuntu machines, you can provide the interface configuration and routing information by posting the output of these two commands:
```

$ ifconfig -a
$ route

``` 
For the Windows 2000 machine, the commands are:
```

C:\> ipconfig
C:\> route print

```
It might be useful to issue the commands when the symptoms are manifesting themselves, especially in the case of "ifconfig" which may show collision error information.

Once we have that information available, it may provide insight into other possible lines of inquiry.

---

### Post by jlacroix on 2005-09-11
Ubuntu ipconfig -a:
```

eth0      Link encap:Ethernet  HWaddr 00:05:5D:36:C2:6E
          inet addr:192.168.2.62  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::205:5dff:fe36:c26e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5341214 (5.0 MiB)  TX bytes:2172364 (2.0 MiB)
          Interrupt:10 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

route:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

```


Windows 2000 ipconfig:
```

Windows 2000 IP Configuration

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : Belkin
        IP Address. . . . . . . . . . . . : 192.168.2.41
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.2.1

```
Route Print:
```

===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x1000003 ...00 c0 4f 2d b4 26 ...... 3Com EtherLink PCI
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.2.1    192.168.2.41	  1
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1	  1
      192.168.2.0    255.255.255.0     192.168.2.41    192.168.2.41	  1
     192.168.2.41  255.255.255.255        127.0.0.1       127.0.0.1	  1
    192.168.2.255  255.255.255.255     192.168.2.41    192.168.2.41	  1
        224.0.0.0        224.0.0.0     192.168.2.41    192.168.2.41	  1
  255.255.255.255  255.255.255.255     192.168.2.41    192.168.2.41	  1
Default Gateway:       192.168.2.1
===========================================================================
Persistent Routes:
  None

```

---

### Post by cwaldbieser on 2005-09-12
[QUOTE=jlacroix]Ubuntu ipconfig -a:
```

eth0      Link encap:Ethernet  HWaddr 00:05:5D:36:C2:6E
          inet addr:192.168.2.62  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::205:5dff:fe36:c26e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5341214 (5.0 MiB)  TX bytes:2172364 (2.0 MiB)
          Interrupt:10 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

route:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

```


Windows 2000 ipconfig:
```

Windows 2000 IP Configuration

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : Belkin
        IP Address. . . . . . . . . . . . : 192.168.2.41
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.2.1

```
Route Print:
```

===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x1000003 ...00 c0 4f 2d b4 26 ...... 3Com EtherLink PCI
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.2.1    192.168.2.41	  1
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1	  1
      192.168.2.0    255.255.255.0     192.168.2.41    192.168.2.41	  1
     192.168.2.41  255.255.255.255        127.0.0.1       127.0.0.1	  1
    192.168.2.255  255.255.255.255     192.168.2.41    192.168.2.41	  1
        224.0.0.0        224.0.0.0     192.168.2.41    192.168.2.41	  1
  255.255.255.255  255.255.255.255     192.168.2.41    192.168.2.41	  1
Default Gateway:       192.168.2.1
===========================================================================
Persistent Routes:
  None

```[/QUOTE]
Well, that was a bust.  Looks like the settings are pretty much identical.  The only weird thing I can see is the 224.0.0.0 route on the Windows machine.  I can't quite figure out what that is for.  The all the PCs seem to have 192.168.2.1 ((your router) set as their default route.  The ifconfig statistics don't seems to show anything weird, either.

Have you tried switching what ports they are plugged into on the router?  Is there any kind of configuration in the router that might be causing a conflict.  From a network perspective, your provider really only knows your router exists, so I can't see that it is somehow singling out your Ubuntu machines.  If you plug one of the Ubuntu machines directly into the cable modem, does it experience the same problem after some time?

---

