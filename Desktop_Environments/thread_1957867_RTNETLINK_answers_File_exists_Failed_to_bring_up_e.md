---
title: "RTNETLINK answers: File exists Failed to bring up eth1"
date: 2012-04-13
forum: Desktop Environments
---

### Post by jeetstechie on 2012-04-13
Hi,

I have three NIC at my Ubuntu machine. I have configured following interfaces on these NICs:

eth0      Link encap:Ethernet  HWaddr e4:1f:13:68:aa:24
          inet addr:10.128.0.150  Bcast:10.128.0.159  Mask:255.255.255.240
          inet6 addr: fe80::e61f:13ff:fe68:aa24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14536 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1448400 (1.4 MB)  TX bytes:1496210 (1.4 MB)
          Interrupt:28 Memory:96000000-96012800

eth1      Link encap:Ethernet  HWaddr e4:1f:13:68:aa:26
          inet addr:10.238.172.195  Bcast:10.238.172.223  Mask:255.255.255.224
          inet6 addr: fe80::e61f:13ff:fe68:aa26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:664 (664.0 B)  TX bytes:1028 (1.0 KB)
          Interrupt:40 Memory:98000000-98012800

eth2      Link encap:Ethernet  HWaddr e4:1f:13:8d:44:04
          inet addr:10.238.198.70  Bcast:10.238.198.95  Mask:255.255.255.224
          inet6 addr: fe80::e61f:13ff:fe8d:4404/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46734 errors:0 dropped:0 overruns:0 frame:0
          TX packets:594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24963482 (24.9 MB)  TX bytes:38352 (38.3 KB)
          Interrupt:29 Memory:92000000-92012800

Following are the contents of my /etc/network/interfaces file:
c/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 10.128.0.150
        netmask 255.255.255.240
        network 10.128.0.144
        broadcast 10.128.0.159
        gateway 10.128.0.145
        # dns-* options are implemented by the resolvconf package, if installed
        dns-search test

auto eth1
iface eth1 inet static
        address 10.238.172.195
        netmask 255.255.255.224
        network 10.238.172.192
        broadcast 10.238.172.223
        gateway 10.238.172.193
        dns-search test

auto eth2
iface eth2 inet static
        address 10.238.198.70
        netmask 255.255.255.224
        network 10.238.198.64
        broadcast 10.238.198.95
        gateway 10.238.198.65
        dns-search test

I am getting following error when I run the ifup eth1 command:

root@ubuntu:~# ifup eth1
RTNETLINK answers: File exists
Failed to bring up eth1.

I tried  to search the forum but couldn't get the exact solution to this problem. Early help is appreciated.

Thanks.

---

### Post by slugg007 on 2012-04-23
Hello,

I have been wrestling with this all day where I could eth1 working BUT
ifup & ifdpwn failed
I got the same RTNETLINK File exists error
and
rebooting would break with no networks at all.

Ubuntu Docs were helpful. Here are the steps I took. I hope they are useful to someone else.

I am sure I could have avoided all this work if I had added the second interface when I added the Ubuntu OS to my new machine.

% uname -r 3.0.0-17-server

1)
My starting /etc/network/interfaces file follows:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 134.174.14.142
    netmask 255.255.255.0
    network 134.174.14.0
    broadcast 134.174.14.255
    gateway 134.174.14.5
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers ?
    dns-search med.harvard.edu

3) new interfaces file

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 134.174.14.142
    netmask 255.255.255.0
    network 134.174.14.0
    broadcast 134.174.14.255
    gateway 134.174.14.5

auto eth1
iface eth1 inet static
    address 10.10.10.15
    netmask 255.255.248.0
    network 10.10.8.0
    broadcast 10.10.15.255

    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers ?
    dns-search med.harvard.edu

4)
It seems like it was critical to have the eth1 config directly follow
the eth0 config. I left the dns lines in place because they were already at the end of the file after the initial ubuntu installation. They must be good for something.

Also note that the "?" in "dns-nameservers ?" looks
like  <80>^

Good luck. It was a tough slog for me.

By the way, this is my first post to ubuntuforums ever. Quite a thrill to think I might help someone else.
---
slugg007

---

### Post by gerhardl on 2012-08-15
I was goofing around with this too for a couple of hours. Read this post and commented the DNS lines out. eth0 and eth1 came up without the error messages. 

Thanks!

---

