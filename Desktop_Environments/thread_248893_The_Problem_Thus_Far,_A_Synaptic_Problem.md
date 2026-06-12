---
title: "The Problem Thus Far, A Synaptic Problem"
date: 2006-09-01
forum: Desktop Environments
---

### Post by randomcode on 2006-09-01
Hi everybody, this is the problem thus far... I installed Ubuntu Dapper but nothing internet related was working though I could see the network so I used another computer (on the same network) to come here and look for solutions. Its a wired network of laptops that are constantly being plugged and unplugged (The computer with Dapper is a Dell Inspiron 6400). Well either way I got firefox working via this thread [http://ubuntuforums.org/showthread.php?t=188033]("http://ubuntuforums.org/showthread.php?t=188033")
But I still cant get synaptic to work though(And I want to update)...

Here are outputs that my computer is doing (they seem to be the average that everyone asks about)

ping 85.133.25.8
```
PING 85.133.25.8 (85.133.25.8) 56(84) bytes of data.

--- 85.133.25.8 ping statistics ---
13 packets transmitted, 0 received, 100% packet loss, time 11997ms
```

ping archive.ubuntu.com
```
PING archive.ubuntu.com (195.248.90.54) 56(84) bytes of data.
64 bytes from archive.ubuntu.com (195.248.90.54): icmp_seq=1 ttl=48 time=344 ms
64 bytes from archive.ubuntu.com (195.248.90.54): icmp_seq=2 ttl=48 time=347 ms
64 bytes from archive.ubuntu.com (195.248.90.54): icmp_seq=3 ttl=48 time=348 ms
64 bytes from archive.ubuntu.com (195.248.90.54): icmp_seq=4 ttl=48 time=346 ms
64 bytes from archive.ubuntu.com (195.248.90.54): icmp_seq=5 ttl=48 time=345 ms

--- archive.ubuntu.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4004ms
rtt min/avg/max/mdev = 344.853/346.405/348.357/1.506 ms

```

telnet archive.ubuntu.com 80
```
Trying 1.0.0.0...
```

cat /etc/resolv.conf
```
nameserver 10.1.1.1
```

route
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.0.0.0       U     0      0        0 eth0
default         mygateway1.ar7  0.0.0.0         UG    0      0        0 eth0
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:15:C5:1A:1B:6B
          inet addr:10.1.1.4  Bcast:10.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1080 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:963700 (941.1 KiB)  TX bytes:216610 (211.5 KiB)
          Interrupt:209

eth1      Link encap:Ethernet  HWaddr 00:13:02:72:58:B2
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:220 errors:0 dropped:963 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Base address:0xe000 Memory:dfdff000-dfdfffff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)
```

cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface dsl-provider inet ppp
provider dsl-provider
```

cat /etc/hosts
```
127.0.0.1 localhost dragon
127.0.1.1 dragon

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

cat /etc/hostname
```
dragon

```

---

### Post by mssever on 2006-09-01
The fact that you can ping archive.ubuntu.com proves that you're connected properly to the Internet.

Let's try first to update from the command line. That way, any errors are visible. Type this in a terminal widow:
```
sudo apt-get update && sudo apt-get upgrade
``` Post any error messages you receive. You might want to go ahead and [enable additional repositories]("http://psychocats.net/ubuntu/sources") before updating--or afterward. If the above works, then Synaptic should work also.

BTW: the telnet line looks wrong (1.0.0.0 isn't a real IP address), but since you're able to ping, I wouldn't worry about it.

---

### Post by the bogs on 2006-09-19
I am having VERY similar problems - synaptic will not update - the connection keeps timing out. I have pinged the various locations and they work...

my sources.list is....

 # Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Canonical Repository:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


and the result is.....



~$ sudo apt-get update && sudo apt-get upgrade
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://archive.canonical.com dapper-commercial Release.gpg
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed outFailed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg](http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg)  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



Help!

---

### Post by mssever on 2006-09-19
I've heard that some people have to disable IPv6 to solve this problem. You might want to look around for help on that. I don't understand why most people (myself included) have no trouble with IPv6, but a few do.

Or, you could wait a bit and see if the problem goes away. But the fact that it's trying to use the incorrect IP address 1.0.0.0 makes me suspect IPv6.

---

### Post by the bogs on 2006-09-20
no joy - i have disabled ipv6 (eventually) but still get the below ....

Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://archive.canonical.com dapper-commercial Release.gpg
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed outFailed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg](http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg)  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by the bogs on 2006-09-20
all sorted...... found this...

[http://www.ubuntuforums.org/showthread.php?t=250149](http://www.ubuntuforums.org/showthread.php?t=250149)

---

### Post by mssever on 2006-09-20
Thanks for the followup!

---

