---
title: "Can't access network on new install"
date: 2006-06-10
forum: Desktop Environments
---

### Post by jflash on 2006-06-10
I just finished installing Breezy Badger on my sister's computer using a CD I ordered through ShipIt. I have every intention of upgrading her to Dapper Drake, but first I need this issue resolved.

When I was going through the installation (for what it's worth, I did a fresh install - formatted the disk and installed Ubuntu as the only OS), I ran it in expert mode. When I got to the point where it tried to configure the network, it said it couldn't connect to the network. At that point, I checked all of the obvious things, such as cables being connected, router on, etc., and retried. Still no luck. At that point, I chose to not configure the network at that point and figure it out later. And thus I finished installing Ubuntu.

After I finished the installation, I tried to figure out the network issue again. I know it isn't a problem with the network itself because my computer (which formerly ran Breezy Badger and has since been upgraded to Dapper Drake) connects to the network just fine. I have manually configured her computer using the settings from my computer, but still to no avail. As I said, I have checked the obvious things. If anyone can help me, I would really appreciate it. Thanks!

---

### Post by alamba on 2006-06-10
Post outputs of the following:
1. ifconfig
2. netstat -rn
3. ping <gatewayip>
4. ping 4.2.2.2
5. ping oracle.com

A

---

### Post by jflash on 2006-06-10
[QUOTE=alamba]Post outputs of the following:
1. ifconfig
2. netstat -rn
3. ping <gatewayip>
4. ping 4.2.2.2
5. ping oracle.com

A[/QUOTE]

1. ifconfig
```
sarah@sarah:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8B:34:95:03
          inet6 addr: fe80::250:8bff:fe34:9503/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:270 dropped:0 overruns:0 frame:0
          TX packets:0 errors:25 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:195312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:195312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:17488858 (16.6 MiB)  TX bytes:17488858 (16.6 MiB)
```

2. netstat -rn
```
sarah@sarah:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
```

3. ping 192.168.1.1 (gateway)

```
sarah@sarah:~$ ping 192.168.1.1
connect: Network is unreachable
```

4. ping 4.2.2.2

```
sarah@sarah:~$ ping 4.2.2.2
connect: Network is unreachable
```

5. ping oracle.com

```
sarah@sarah:~$ ping oracle.com
ping: unknown host oracle.com
```

Hope this helps.

---

### Post by jflash on 2006-06-11
*bump*

---

### Post by jflash on 2006-06-12
*bump* *again*

---

### Post by jflash on 2006-06-13
PLEASE help me on this! I am getting increasing pressure from both my sister and now my dad to get this fixed.

---

### Post by jflash on 2006-06-14
I would really like some help on this. I am leaving for three weeks on Saturday and would like this figured out beforehand. Please post if you can help.

---

### Post by Erik6543 on 2006-06-15
I can see in the results of ifconfig that your card has not received any inet adress, no broadcast adres and no netmask.

There are 2 situations:
1) you have a router that is capable of DHCP, make sure these line are in your /etc/network/interfaces file:

auto eth0
iface eth0 inet dhcp

2) you have a modem/router with a static address (gateway address depends on your hardware/ISP provider, see your documentation)

auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

more info on [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

Hope this helps!

---

### Post by jflash on 2006-06-15
I checked, and those two lines are already in her interfaces file. We do have a router that serves as a DHCP server. Anything else?

---

### Post by jflash on 2006-06-23
Anything? Please?

---

