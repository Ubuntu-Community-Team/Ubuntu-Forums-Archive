---
title: "Ubuntu 8.10 - Dhcp3-server does not Want to Start Automatically"
date: 2009-03-12
forum: General Help
---

### Post by srangelov on 2009-03-12
Hi!

I installed Ubuntu 8.10 and over it LTSP. This also installed dhcp3-server. After restart the dhcp3-server does not want to start automatically and I have to run this command in terminal - "sudo /etc/init.d/dhcp3-server start.

I tried to update the rc.d:

```
sudo update-rc.d -f dhcp3-server start 20 2 3 4 5 . stop 80 0 1 6 .
```

But still after restart the dhcp3-server does not want to start automatically.

I would appreciate any ideas how to manage this.

Thank you in advance!

Sotir

---

### Post by srangelov on 2009-03-15
Anyone any ideas?

---

### Post by srangelov on 2009-03-15
It seems that dchp3-server is trying to start during normal boot, but it fails, here it is my syslog:

```
Mar 15 11:31:58 domlevski dhcpd: Internet Systems Consortium DHCP Server V3.1.1
Mar 15 11:31:58 domlevski dhcpd: Copyright 2004-2008 Internet Systems Consortium.
Mar 15 11:31:58 domlevski dhcpd: All rights reserved.
Mar 15 11:31:58 domlevski dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Mar 15 11:31:58 domlevski dhcpd: Wrote 1 leases to leases file.
Mar 15 11:31:58 domlevski dhcpd: 
Mar 15 11:31:58 domlevski dhcpd: Not configured to listen on any interfaces!
```

The /etc/ltsp/dhcpd.conf file is setup correctly:

```
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.20 192.168.1.50;
    option domain-name "example.com";
    option domain-name-servers 192.168.1.1;
    option broadcast-address 192.168.1.255;
    option routers 192.168.1.1;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
```

I found a thread where they advise to edit the /etc/default/dhcp3-server file and add the correct interface:

```
# Find this line

... INTERFACES=""

# Replace with the following line

INTERFACES="eth0"

```

in my case it is eth2.

I did this but then the syslog says:

```
dhcpd: Internet Systems Consortium DHCP Server V3.1.1
Mar 15 11:21:28 domlevski dhcpd: Copyright 2004-2008 Internet Systems Consortium.
Mar 15 11:21:28 domlevski dhcpd: All rights reserved.
Mar 15 11:21:28 domlevski dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Mar 15 11:21:28 domlevski dhcpd: Wrote 1 leases to leases file.
Mar 15 11:21:28 domlevski dhcpd: 
Mar 15 11:21:28 domlevski dhcpd: No subnet declaration for eth2 (0.0.0.0).
Mar 15 11:21:28 domlevski dhcpd: ** Ignoring requests on eth2.  If this is not what
Mar 15 11:21:28 domlevski dhcpd:    you want, please write a subnet declaration
Mar 15 11:21:28 domlevski dhcpd:    in your dhcpd.conf file for the network segment
Mar 15 11:21:28 domlevski dhcpd:    to which interface eth2 is attached. **
Mar 15 11:21:28 domlevski dhcpd: 
Mar 15 11:21:28 domlevski dhcpd: 
Mar 15 11:21:28 domlevski dhcpd: Not configured to listen on any interfaces!
```

What I need to do?

---

### Post by srangelov on 2009-03-17
I found what is the problem :)

DHCP requires a static IP address and is looking for it here - /etc/network/interfaces.

But Ubuntu 8.10 uses NetworkManager 0.7 which does not write static IP configuration to /etc/network/interfaces .

See [bug #256054]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/256054"):

> 2. If you rely on your network connection being constantly up during boot, you
have to disable NetworkManager for the time being:

```
  sudo update-rc.d NetworkManager remove
```

I removed NetworkManager, set manually static IP, configure default interfaces for DHCP and - it is now starting automatically after the restart.

For more info read my full article about [Setting up Standalone LTSP Server on Ubuntu 8.10]("http://my.oltrans.org/en/ubuntu-faqs/41-customizing/81-standalone-ltsp-server-on-ubuntu-810.html").

Sotir

---

### Post by Rich_B_uk on 2009-05-08
Hi Stranglov! Great work. Helped me out a great deal.

---

### Post by shel-hall on 2009-07-05
Thanks for the fix; this also seems to happen in 9.04.

Once I ditched NetworkManager and set up a static IP address, everything fell into place.

-Shel

---

### Post by bobwdn on 2009-07-12
I am experiencing the same issue with 9.04 Juanty, except when I:

> desktop2:~$ sudo /etc/init.d/dhcp3-server restart
 * Stopping DHCP server dhcpd3                                                         [fail] 
 * Starting DHCP server dhcpd3                                                                 * check syslog for diagnostics.
                                                                                       [fail]


And then "tail /var/log/syslog" says:

> desktop2:~$ tail /var/log/syslog
Jul 12 10:43:04 bob-desktop2 dhcpd: Wrote 0 leases to leases file.
Jul 12 10:43:04 bob-desktop2 dhcpd: 
Jul 12 10:43:04 bob-desktop2 dhcpd: No subnet declaration for eth1 (0.0.0.0).
Jul 12 10:43:04 bob-desktop2 dhcpd: ** Ignoring requests on eth1.  If this is not what
Jul 12 10:43:04 bob-desktop2 dhcpd:    you want, please write a subnet declaration
Jul 12 10:43:04 bob-desktop2 dhcpd:    in your dhcpd.conf file for the network segment
Jul 12 10:43:04 bob-desktop2 dhcpd:    to which interface eth1 is attached. **
Jul 12 10:43:04 bob-desktop2 dhcpd: 
Jul 12 10:43:04 bob-desktop2 dhcpd: 
Jul 12 10:43:04 bob-desktop2 dhcpd: Not configured to listen on any interfaces!

When I "ifconfig eth0" I get:

> desktop2:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:24:1d:2a:2f:4d  
          inet addr:192.168.242.120  Bcast:192.168.242.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe2a:2f4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17407860 (17.4 MB)  TX bytes:7982318 (7.9 MB)
          Interrupt:252 Base address:0xc000

And finally, when I "ifconfig eth1" I get:

> desktop2:~$ ifconfig eth1
eth1: error fetching interface information: Device not found

I have set eth0 to a static address (like the article at [http://my.oltrans.org/en/ubuntu-faqs/41-customizing/81-standalone-ltsp-server-on-ubuntu-810.html](http://my.oltrans.org/en/ubuntu-faqs/41-customizing/81-standalone-ltsp-server-on-ubuntu-810.html).)

I have tried re-installing dhcp3-server via Synaptic and still the dhcp3 will not restart.

I have searched and searched (obviously in the wrong place) for answers as to why dhcp3-server will not start and I guess it is "over my head."

Does anyone have a suggestion?

---

### Post by Rich_B_uk on 2009-07-28
Hi bob, I might be missing something but to me it just seems like DHCP is not playing ball because one of your interfaces (eth1) seems invalid. Maybe a driver problem on that card?

Either way, eth0 seems fine, but eth1 isn't configured. Because it's not configured dhcp3 seems to moan when you start it?

---

### Post by marcuswentrcek on 2009-10-06
To help others out will you output
tail -f /var/log/syslog
 
Also check to make sure your dhcp is setup correctly in /etc/ltsp/dhcpd.conf
Check the subnet and make sure it's correct for your NIC/eth and then start dhcp
 
/etc/init.d/dhcp3-server restart|start
 
Ubunutu will easily install LTSP and it will cause DHCP issues if not properly configured.
 
Bird

---

### Post by Iurie on 2009-12-04
In /etc/network/interfaces add to the interface section associated with dhcp3-server: 

**up /etc/init.d/dhcp3-server start**

Worked for me.

Example (I have a bridge):
--------------------------
auto br0
  iface br0 inet static
  address 192.168.1.254
  netmask 255.255.255.0
  network 192.168.1.0
  broadcast 192.168.1.255
  bridge_ports eth1 eth2
  up /etc/init.d/dhcp3-server start

OR

auto eth0
  iface eth0 inet static
  address 192.168.1.254
  netmask 255.255.255.0
  network 192.168.1.0
  broadcast 192.168.1.255
  up /etc/init.d/dhcp3-server start

---

