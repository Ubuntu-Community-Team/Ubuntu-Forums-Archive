---
title: "Could not build PPTP Server in Linux Ubuntu Server 8.10"
date: 2009-04-16
forum: General Help
---

### Post by Romala on 2009-04-16
Dear all,
could you help me.
There is Ubuntu Server 8.10. How to create PPTP Server:
> sudo apt-get update
sudo apt-get upgrade
1) To configure interfaces:
/etc/network/interfaces
one (eth0) - for WAN, another (eth1) - for LAN ;
eth1: ip 10.0.0.1, 10.0.0.0/8
2) To configure DHCP Server on LAN, like 
[http://taufanlubis.wordpress.com/2007/10/14/dhcp-server/]("http://taufanlubis.wordpress.com/2007/10/14/dhcp-server/")
ip 10.0.0.1, poll 10.0.0.100-200;
3) To configure PPTP Server:
ip 192.168.3.1/24, ip pool 192.168.3.100-200

> apt-get install ppp pptpd

/etc/ppp/pptpd-options 
/etc/ppp/chap-secrets

> /etc/init.d/pptpd restart

and firewall

> 
iptables -A INPUT -p gre -j ACCEPT
iptables -A INPUT -m tcp -p tcp --dport 1723 -j ACCEPT

NAT
> iptables -t nat -A POSROUTING -s 192.168.3.0/24 -j MASQUERADE

What else?
Thank you

---

### Post by Romala on 2009-04-17
DHCP works, but there's now messages in a log about PPTP

---

### Post by Romala on 2009-04-22
Is anybody could help me? 
Is any analyser for PPTP?
Or i've to go for help in another forum?
thank you

---

### Post by koenn on 2009-04-22
What exactly is your problem / your question ?

---

### Post by Romala on 2009-04-22
Thank you for your answer, koen!

The question is: 
i've tried to set PPTP Server on Ubuntu Server - my step are above-mentioned. Then i connect to server, i get an address 10.0.0.103 for my network adapter; but i could not authorize by PPTP client in Windows - it writes "error 800" (it is PPTP error setting) . 
Could you find a mistake or a gap in my steps? Or, may be there's a packet  analizer (like Wireshark) in Ubuntu to help.
Thank you

---

### Post by Romala on 2009-04-22
I also have tried to set 
> 
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
iptables --append INPUT --protocol 47 --jump ACCEPT
iptables --append INPUT --protocol tcp --match tcp --destination-port 1723 --jump ACCEPT

like here
[http://manpages.ubuntu.com/manpages/hardy/man5/pptpd.conf.5.html]("http://manpages.ubuntu.com/manpages/hardy/man5/pptpd.conf.5.html")

---

### Post by koenn on 2009-04-22
Are you doing this between two computers on your own network(s) or are you going over the internet. When using internet, how do you connect to the internet ? If you use a router with NAT on the server side, you may have a problem to get through to the pptp server.

Error 800 means "unable to establish a vpn connection". 
First check that the server is reachable from the client (ping, tracert)

---

### Post by Romala on 2009-04-22
I connect two computers with Ethernet cable. One of them is Ubuntu Server, where i try to configure PPTP Server. Another computer can see the computer with Ubuntu: they are in the same net - 10.0.0.0/8 (see above). I could not establish PPTP tunnel between these computers.
](*,)

---

### Post by koenn on 2009-04-22
you need first to be certain both computers can talk to each other. Can you ping between the (both ways) ?

also, disable the iptables (flush the rules and set all policies to ACCEPT). you don't need them in a test configuration like this, they could get in the way, and the masquerading doesn't make sense anyway if both hosts are on the same network.

if you need a firewall, add it after your vpn works. Easier to troubleshoot that way

---

### Post by Romala on 2009-04-22
Masquerading is for NAT, right? 
WAN interface (eth0) has an address (from Internet, eth0 is a DHCP client); LAN interface (eth1) has another addresses (10.0.0.0/255.0.0.0). 
I need NAT.

---

### Post by koenn on 2009-04-22
Masquerading is a form of NAT, yes.
The mere fact that you have to network interfaces doesn't automatically mean you *need* NAT. Depends on what you're trying to achieve, and according to the info you gave, you want to do pptp between 2 NIC's that are directly connected with an ethernet cable. You don't need NAT for that. Plus, you're doing NAT on your LAN interface, according to post #6.  I'd be interested in an explanation what the NAT is supposed to be doing in such case.


For the 3th (and last) time:
you need first to be certain both computers can talk to each other. Can you ping between them (both ways)?

---

### Post by Romala on 2009-04-23
> I'd be interested in an explanation what the NAT is supposed to be doing in such case.
NAT is for eth0 and eth1 interfaces of Server.
 > For the 3th (and last) time:
you need first to be certain both computers can talk to each other. Can you ping between them (both ways)?

Excuse me, koenn, but i'm not near my "network" all the time. I'll check. PC with Windows can ping Ubuntu Server, and i've seen a route in Ubuntu Sever, like 10.0.0.0 255.0.0.0 10.0.0.1 - it seems, it can ping too.

**/etc/network/interfaces**:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback



# The primary network interface
auto eth0
iface eth0 inet dhcp
 
auto eth1
iface eth1 inet static
address 10.0.0.1
netmask 255.0.0.0
broadcast 10.255.255.255

```

**/etc/default/dhcp3-server**:

```
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1"

```

**/etc/dhcp3/dhcpd.conf**:

```
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
#option domain-name "example.org";
#option domain-name-servers ns1.example.org, ns2.example.org;


default-lease-time 604800;
max-lease-time 864001;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}
subnet 10.0.0.0 netmask 255.0.0.0{
range 10.0.0.100 10.0.0.200;
option routers 10.0.0.1;
option broadcast-address 10.255.255.255;
default-lease-time 604800;
max-lease-time 864001;
}


# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}

```

**/etc/ppp/pptpd-options**: 

```
###############################################################################
# $Id: pptpd-options 4643 2006-11-06 18:42:43Z rene $
#
# Sample Poptop PPP options file /etc/ppp/pptpd-options
# Options used by PPP when a connection arrives from a client.
# This file is pointed to by /etc/pptpd.conf option keyword.
# Changes are effective on the next connection.  See "man pppd".
#
# You are expected to change this file to suit your system.  As
# packaged, it requires PPP 2.4.2 and the kernel MPPE module.
###############################################################################


# Authentication

# Name of the local system for authentication purposes 
# (must match the second field in /etc/ppp/chap-secrets entries)
name pptpd

# Optional: domain name to use for authentication
# domain mydomain.net

# Strip the domain prefix from the username before authentication.
# (applies if you use pppd with chapms-strip-domain patch)
#chapms-strip-domain


# Encryption
# Debian: on systems with a kernel built with the package
# kernel-patch-mppe >= 2.4.2 and using ppp >= 2.4.2, ...
# {{{
refuse-pap
#refuse-chap
refuse-mschap
# Require the peer to authenticate itself using MS-CHAPv2 [Microsoft
# Challenge Handshake Authentication Protocol, Version 2] authentication.
#require-mschap-v2
require-chap
# Require MPPE 128-bit encryption
# (note that MPPE requires the use of MSCHAP-V2 during authentication)
# require-mppe-128
# }}}




# Network and Routing

# If pppd is acting as a server for Microsoft Windows clients, this
# option allows pppd to supply one or two DNS (Domain Name Server)
# addresses to the clients.  The first instance of this option
# specifies the primary DNS address; the second instance (if given)
# specifies the secondary DNS address.
# Attention! This information may not be taken into account by a Windows
# client. See KB311218 in Microsoft's knowledge base for more information.
#ms-dns 10.0.0.1
#ms-dns 10.0.0.2

# If pppd is acting as a server for Microsoft Windows or "Samba"
# clients, this option allows pppd to supply one or two WINS (Windows
# Internet Name Services) server addresses to the clients.  The first
# instance of this option specifies the primary WINS address; the
# second instance (if given) specifies the secondary WINS address.
#ms-wins 10.0.0.3
#ms-wins 10.0.0.4

# Add an entry to this system's ARP [Address Resolution Protocol]
# table with the IP address of the peer and the Ethernet address of this
# system.  This will have the effect of making the peer appear to other
# systems to be on the local ethernet.
# (you do not need this if your PPTP server is responsible for routing
# packets to the clients -- James Cameron)
proxyarp

# Debian: do not replace the default route
nodefaultroute


# Logging

# Enable connection debugging facilities.
# (see your syslog configuration for where pppd sends to)
#debug

# Print out all the option values which have been set.
# (often requested by mailing list to verify options)
#dump


# Miscellaneous

# Create a UUCP-style lock file for the pseudo-tty to ensure exclusive
# access.
lock

# Disable BSD-Compress compression
nobsdcomp 

```


**/etc/ppp/chap-secrets**:

```
# Secrets for authentication using CHAP
# client	server	secret			IP addresses
user1 pptpd 1234"*" 

```

DHCP working \\:D/  , the issue is PPTP (CHAP without encryption)  [-o<

---

### Post by Romala on 2009-04-23
seems, i've lost **/etc/pptpd.conf**
:-k 
'll find them

---

### Post by koenn on 2009-04-23
assuming your network works (I still have my doubts about the masquerading, but we'll get to that), you're going to need a log to see what's happening. 
Uncomment the ' #debug ' (remove the #) line in /etc/ppp/pptpd-options and restart pptpd. Check for logs in /var/log/syslog, or other logs if nothing shows up in syslog.
If all the networking and pptp stuff turns out OK and you still can't connect, it's most likely a mismatch in encryption and authentication protocols, and the logs will tell you where the failure occurs.

On the Windows client, look for logs (via Control Panel, or run 'eventvwr') that show failed pptp connection attempts

Also, post the output of these commands (on the server, with pptpd running):
```

cat /proc/sys/net/ipv4/ip_forward
route -n
ifconfig

```

about the masquerading : NAT is a workaround for situations that can't be handled by plain routing. Since you have full control over your server and your LAN, plain routing should be sufficient. 
The man page you're referring to is incomplete : there are some titles missing and this may lead to some misunderstanding : see this one and compare : [http://pwet.fr/man/linux/formats/pptpd_conf](http://pwet.fr/man/linux/formats/pptpd_conf)

After reading this, explain why you want to do pptp with NAT. while ARP or routing should be sufficient (and a lot less complicated and error-prone), unless you have a compelling reason to think otherwise.

while we're at it, this line is not working, it has a syntax error (POSTROUTING)
```
iptables -t nat -A POSROUTING -s 192.168.3.0/24 -j MASQUERADE 
```

Also, post your pptp.conf, if only to have a closer look at the network ranges you've defined there

Lastly, explain why you're setting up a vpn between two hosts that are already on the same LAN. Some context might help to understand what it is you're trying to accomplish.

---

### Post by Romala on 2009-04-27
Thank you for your answer. There is a result.
```

pcserver@user:~$ cat /proc/sys/net/ipv4/ip_forward

0

pcserver@user:~$ route -n

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

10.0.0.0        0.0.0.0         255.0.0.0   U     0      0        0 eth1

pcserver@user:~$ ifconfig

eth0     Link encap:Ethernet  HWaddr 00:0d:61:21:54:d2  
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
         Interrupt:19 Base address:0xe000 

eth1     Link encap:Ethernet  HWaddr 00:a0:c5:30:02:07  
         inet addr:10.0.0.1  Bcast:10.255.255.255  Mask:255.0.0.0
         inet6 addr: fe80::2a0:c5ff:fe30:207/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
         RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)
         Interrupt:17 Base address:0x9800 



lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pcserver@user:~$ exit

exit

```

**/etc/sysctl.conf **:

```

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 4 4 1 7

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# This disables TCP Window Scaling (http://lkml.org/lkml/2008/2/5/167),
# and is not recommended.
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net.ipv4.icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net.ipv4.icmp_ignore_bogus_error_responses = 1
# 
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#
# The contents of /proc/<pid>/maps and smaps files are only visible to 
# readers that are allowed to ptrace() the process
# sys.kernel.maps_protect = 1

```

**/etc/pptpd.conf**:
```

###############################################################################
# $Id: pptpd.conf 4255 2004-10-03 18:44:00Z rene $
#
# Sample Poptop configuration file /etc/pptpd.conf
#
# Changes are effective when pptpd is restarted.
###############################################################################

# TAG: ppp
#	Path to the pppd program, default '/usr/sbin/pppd' on Linux
#
#ppp /usr/sbin/pppd

# TAG: option
#	Specifies the location of the PPP options file.
#	By default PPP looks in '/etc/ppp/options'
#
option /etc/ppp/pptpd-options

# TAG: debug
#	Turns on (more) debugging to syslog
#
debug

listen 0.0.0.0

# TAG: stimeout
#	Specifies timeout (in seconds) on starting ctrl connection
#
# stimeout 10

# TAG: noipparam
#       Suppress the passing of the client's IP address to PPP, which is
#       done by default otherwise.
#
#noipparam

# TAG: logwtmp
#	Use wtmp(5) to record client connections and disconnections.
#
logwtmp

# TAG: bcrelay <if>
#	Turns on broadcast relay to clients from interface <if>
#
#bcrelay eth1

# TAG: localip
# TAG: remoteip
#	Specifies the local and remote IP address ranges.
#
#       Any addresses work as long as the local machine takes care of the
#       routing.  But if you want to use MS-Windows networking, you should
#       use IP addresses out of the LAN address space and use the proxyarp
#       option in the pppd options file, or run bcrelay.
#
#	You can specify single IP addresses seperated by commas or you can
#	specify ranges, or both. For example:
#
#		192.168.0.234,192.168.0.245-249,192.168.0.254
#
#	IMPORTANT RESTRICTIONS:
#
#	1. No spaces are permitted between commas or within addresses.
#
#	2. If you give more IP addresses than MAX_CONNECTIONS, it will
#	   start at the beginning of the list and go until it gets 
#	   MAX_CONNECTIONS IPs. Others will be ignored.
#
#	3. No shortcuts in ranges! ie. 234-8 does not mean 234 to 238,
#	   you must type 234-238 if you mean this.
#
#	4. If you give a single localIP, that's ok - all local IPs will
#	   be set to the given one. You MUST still give at least one remote
#	   IP for each simultaneous client.
#
# (Recommended)
localip 192.168.3.1
remoteip 192.168.3.234-238,192.168.3.245
# or
#localip 192.168.0.234-238,192.168.0.245
#remoteip 192.168.1.234-238,192.168.1.245

```

Excuse me: i've changed a little here, thinking about my safety :-$ and self-education . And also i've unplugged Ethernet-cable from WAN-interface (eth0) during my test. 
Server can ping PC, PC can ping server. DHCP works. But PPTP no.
:)

---

### Post by koenn on 2009-04-27
OK .....

1- 
```
pcserver@user:~$ cat /proc/sys/net/ipv4/ip_forward

0
```

you don't have ip-forwarding turned on. even though you have it enabled in /etc/sysctl.conf. Did you reboot after you made that change ?
you can fix this by executing ```
echo 1 > cat /proc/sys/net/ipv4/ip_forward
```. 

2-
```
pcserver@user:~$ ifconfig
```
if pptpd is up, you'd have a tun interface (most likely tun0) here. Apparently pptpd is not running. You'll need to start it - possibly something like ```
/etc/init.d/pptp start
```
I don't have any pptpd nearby so you may have to find the correct command yourself.

3-
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

10.0.0.0        0.0.0.0         255.0.0.0   U     0      0        0 eth1

```
If pptpd is working, this should probably show that 192.168.3.0 is reachable via  192.168.3.1 and/or tun0 or so. The fact that this route isn't listed is probably due to the absence of tun0


fix the ip-forwareding, (re-)start pptpd, run these commands again, and check /var/log/syslog for errors.

also, explain why you're setting up a vpn between two hosts that are already on the same LAN. Some context might help to understand what it is you're trying to accomplish.

---

### Post by Romala on 2009-04-28
Dear koenn,
thank you for your answer
>  explain why you're setting up a vpn between two hosts that are already on the same LAN.  
- this is my test, it is not a real condition. 
I'll try your suggestions and info you.
My best respect
:)

---

### Post by Romala on 2009-04-29
Now
```
pcserver@user:~$ cat /proc/sys/net/ipv4/ip_forward

1


```
but there's no route like tun0; i've tried
```
/etc/init.d/pptpd
```

In *syslog*
 ```
Apr 29 07:36:34 user pptpd[4690]: MGR: Maximum of 100 connections reduced to 6, not enough IP addresses given
Apr 29 07:36:34 user pptpd[4690]: MGR: PPP binary /usr/sbin/pppd not executable
...
Apr 29 07:42:47 user pptpd[4439]: MGR: Maximum of 100 connections reduced to 6, not enough IP addresses given
Apr 29 07:42:47 user pptpd[4440]: MGR: Manager process started
Apr 29 07:42:47 user pptpd[4440]: MGR: Maximum of 6 connections available

```

, this is  **chap-secrets**
```
# Secrets for authentication using CHAP
# client	server	secret			IP addresses
user1 pptpd 1234"*" 
user2 pptpd 1234 "*" 
```

---

### Post by Romala on 2009-05-04
```
sudo killall pptpd
sudo /etc/init.d/pptpd restart

```
do not help too. PPTPd daemon have been restarted successfully, but there's no tun0 or tun1 in route and there's no pptp messages in logs (except above-mentioned messages in *syslog* ). :confused:

---

### Post by Romala on 2009-05-04
Does PPTP Server work on Ubuntu Server 8.10? Is there anybody who check it?
Thank you

---

### Post by koenn on 2009-05-04
> **Romala said:**
> 
In *syslog*
 ```
Apr 29 07:36:34 user pptpd[4690]: MGR: Maximum of 100 connections reduced to 6, not enough IP addresses given
Apr 29 07:36:34 user pptpd[4690]: MGR: PPP binary /usr/sbin/pppd not executable
...

```

> **Romala said:**
> Does PPTP Server work on Ubuntu Server 8.10? Is there anybody who check it?
Thank you

If pppd really isn't executable, it isn't going to work.
Apparently you're not the only one ; [https://bugs.launchpad.net/ubuntu/+source/ppp/+bug/309135](https://bugs.launchpad.net/ubuntu/+source/ppp/+bug/309135)
...

```
chmod ug+x /usr/sbin/pppd
```
should fix it

---

### Post by Romala on 2009-05-05
Koenn, thank you, 
but it has not been helped: there is the same, PPTP daemon is restarting but there is no PPTP in log and there is no tun0 in route.
Anybody have an idea? Thank you :)

---

### Post by koenn on 2009-05-05
> **Romala said:**
>  there is no tun0 in route.

how about ppp0 (or another number)?

If you post the actuak commands + their output, you have a better chance someone will notice what's going on

---

### Post by Romala on 2009-05-05
I see only Ethernet interfaces in a route: eth0, eth1.
If it is a mistake in a config - we could see it in a log. But there is no suspicious here.

---

### Post by Romala on 2009-05-06
Hope, that it could help

```
pcserver@user:~$ sudo /etc/init.d/pptpd restart

Restarting PPTP: 

Stopping PPTP: pptpd.

Starting PPTP Daemon: pptpd.

pcserver@user:~$ route

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

10.0.0.0        *               255.0.0.0   U     0      0        0 eth1
```

*messages*


```
May  5 07:29:44 user syslogd 1.5.0#2ubuntu6: restart.
May  5 07:29:44 user kernel: Inspecting /boot/System.map-2.6.27-7-server
May  5 07:29:44 user kernel: Cannot find map file.
May  5 07:29:44 user kernel: Loaded 48877 symbols from 70 modules.
May  5 07:29:44 user kernel: [    0.000000] Initializing cgroup subsys cpuset
May  5 07:29:44 user kernel: [    0.000000] Initializing cgroup subsys cpu
May  5 07:29:44 user kernel: [    0.000000] Linux version 2.6.27-7-server (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 20:18:35 UTC 2008 (Ubuntu 2.6.27-7.16-server)
May  5 07:29:44 user kernel: [    0.000000] BIOS-provided physical RAM map:
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
May  5 07:29:44 user kernel: [    0.000000] last_pfn = 0x2fff0 max_arch_pfn = 0x1000000
May  5 07:29:44 user kernel: [    0.000000] NX (Execute Disable) protection: active
May  5 07:29:44 user kernel: [    0.000000] RAMDISK: 2f832000 - 2ffdf6b8
May  5 07:29:44 user kernel: [    0.000000] DMI 2.3 present.
May  5 07:29:44 user kernel: [    0.000000] ACPI: RSDP 000F6AB0, 0014 (r0 Nvidia)
May  5 07:29:44 user kernel: [    0.000000] ACPI: RSDT 2FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  5 07:29:44 user kernel: [    0.000000] ACPI: FACP 2FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  5 07:29:44 user kernel: [    0.000000] ACPI: DSDT 2FFF30C0, 4ABF (r1 NVIDIA AWRDACPI     1000 MSFT  100000C)
May  5 07:29:44 user kernel: [    0.000000] ACPI: FACS 2FFF0000, 0040
May  5 07:29:44 user kernel: [    0.000000] ACPI: APIC 2FFF7B80, 005A (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  5 07:29:44 user kernel: [    0.000000] 0MB HIGHMEM available.
May  5 07:29:44 user kernel: [    0.000000] 767MB LOWMEM available.
May  5 07:29:44 user kernel: [    0.000000]   mapped low ram: 0 - 2fff0000
May  5 07:29:44 user kernel: [    0.000000]   low ram: 00000000 - 2fff0000
May  5 07:29:44 user kernel: [    0.000000]   bootmap 0000a000 - 00010000
May  5 07:29:44 user kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002fff0000]
May  5 07:29:44 user kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
May  5 07:29:44 user kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
May  5 07:29:44 user kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
May  5 07:29:44 user kernel: [    0.000000]   #3 [0000100000 - 00005e8220]    TEXT DATA BSS ==> [0000100000 - 00005e8220]
May  5 07:29:44 user kernel: [    0.000000]   #4 [002f832000 - 002ffdf6b8]          RAMDISK ==> [002f832000 - 002ffdf6b8]
May  5 07:29:44 user kernel: [    0.000000]   #5 [00005e9000 - 00005f1000]    INIT_PG_TABLE ==> [00005e9000 - 00005f1000]
May  5 07:29:44 user kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
May  5 07:29:44 user kernel: [    0.000000]   #7 [0000007000 - 000000a000]          PGTABLE ==> [0000007000 - 000000a000]
May  5 07:29:44 user kernel: [    0.000000]   #8 [000000a000 - 0000010000]          BOOTMAP ==> [000000a000 - 0000010000]
May  5 07:29:44 user kernel: [    0.000000] found SMP MP-table at [c00f5000] 000f5000
May  5 07:29:44 user kernel: [    0.000000] Zone PFN ranges:
May  5 07:29:44 user kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
May  5 07:29:44 user kernel: [    0.000000]   Normal   0x00001000 -> 0x0002fff0
May  5 07:29:44 user kernel: [    0.000000]   HighMem  0x0002fff0 -> 0x0002fff0
May  5 07:29:44 user kernel: [    0.000000] Movable zone start PFN for each node
May  5 07:29:44 user kernel: [    0.000000] early_node_map[2] active PFN ranges
May  5 07:29:44 user kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
May  5 07:29:44 user kernel: [    0.000000]     0: 0x00000100 -> 0x0002fff0
May  5 07:29:44 user kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
May  5 07:29:44 user kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
May  5 07:29:44 user kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
May  5 07:29:44 user kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  5 07:29:44 user kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
May  5 07:29:44 user kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  5 07:29:44 user kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
May  5 07:29:44 user kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  5 07:29:44 user kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
May  5 07:29:44 user kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  5 07:29:44 user kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  5 07:29:44 user kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  5 07:29:44 user kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
May  5 07:29:44 user kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May  5 07:29:44 user kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
May  5 07:29:44 user kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
May  5 07:29:44 user kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
May  5 07:29:44 user kernel: [    0.000000] PERCPU: Allocating 45852 bytes of per cpu data
May  5 07:29:44 user kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194767
May  5 07:29:44 user kernel: [    0.000000] Kernel command line: root=UUID=3a16f219-3073-4cf3-8fa0-646d16cda612 ro quiet splash 
May  5 07:29:44 user kernel: [    0.000000] Enabling fast FPU save and restore... done.
May  5 07:29:44 user kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May  5 07:29:44 user kernel: [    0.000000] Initializing CPU#0
May  5 07:29:44 user kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
May  5 07:29:44 user kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
May  5 07:29:44 user kernel: [    0.000000] TSC: using PIT calibration value
May  5 07:29:44 user kernel: [    0.000000] Detected 1994.824 MHz processor.
May  5 07:29:44 user kernel: [    0.010000] Console: colour VGA+ 80x25
May  5 07:29:44 user kernel: [    0.010000] console [tty0] enabled
May  5 07:29:44 user kernel: [    0.010000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  5 07:29:44 user kernel: [    0.010000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  5 07:29:44 user kernel: [    0.010000] Memory: 765068k/786368k available (2628k kernel code, 20728k reserved, 1201k data, 436k init, 0k highmem)
May  5 07:29:44 user kernel: [    0.010000] virtual kernel memory layout:
May  5 07:29:44 user kernel: [    0.010000]     fixmap  : 0xffc78000 - 0xfffff000   (3612 kB)
May  5 07:29:44 user kernel: [    0.010000]     pkmap   : 0xff800000 - 0xffa00000   (2048 kB)
May  5 07:29:44 user kernel: [    0.010000]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
May  5 07:29:44 user kernel: [    0.010000]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
May  5 07:29:44 user kernel: [    0.010000]       .init : 0xc04c3000 - 0xc0530000   ( 436 kB)
May  5 07:29:44 user kernel: [    0.010000]       .data : 0xc0391036 - 0xc04bd800   (1201 kB)
May  5 07:29:44 user kernel: [    0.010000]       .text : 0xc0100000 - 0xc0391036   (2628 kB)
May  5 07:29:44 user kernel: [    0.010000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
May  5 07:29:44 user kernel: [    0.010000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
May  5 07:29:44 user kernel: [    0.010008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.64 BogoMIPS (lpj=19948240)
May  5 07:29:44 user kernel: [    0.010026] Security Framework initialized
May  5 07:29:44 user kernel: [    0.010033] SELinux:  Disabled at boot.
May  5 07:29:44 user kernel: [    0.010053] AppArmor: AppArmor initialized
May  5 07:29:44 user kernel: [    0.010061] Mount-cache hash table entries: 512
May  5 07:29:44 user kernel: [    0.010209] Initializing cgroup subsys ns
May  5 07:29:44 user kernel: [    0.010213] Initializing cgroup subsys cpuacct
May  5 07:29:44 user kernel: [    0.010215] Initializing cgroup subsys memory
May  5 07:29:44 user kernel: [    0.010229] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May  5 07:29:44 user kernel: [    0.010231] CPU: L2 Cache: 512K (64 bytes/line)
May  5 07:29:44 user kernel: [    0.010241] Checking 'hlt' instruction... OK.
May  5 07:29:44 user kernel: [    0.050367] SMP alternatives: switching to UP code
May  5 07:29:44 user kernel: [    0.056453] Freeing SMP alternatives: 11k freed
May  5 07:29:44 user kernel: [    0.056457] ACPI: Core revision 20080609
May  5 07:29:44 user kernel: [    0.057953] ACPI: Checking initramfs for custom DSDT
May  5 07:29:44 user kernel: [    0.371036] ENABLING IO-APIC IRQs
May  5 07:29:44 user kernel: [    0.371202] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
May  5 07:29:44 user kernel: [    0.471213] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 08
May  5 07:29:44 user kernel: [    0.480000] Brought up 1 CPUs
May  5 07:29:44 user kernel: [    0.480000] Total of 1 processors activated (3989.64 BogoMIPS).
May  5 07:29:44 user kernel: [    0.480000] net_namespace: 840 bytes
May  5 07:29:44 user kernel: [    0.480000] Booting paravirtualized kernel on bare hardware
May  5 07:29:44 user kernel: [    0.480000] Time:  7:29:23  Date: 05/05/09
May  5 07:29:44 user kernel: [    0.480000] NET: Registered protocol family 16
May  5 07:29:44 user kernel: [    0.480000] EISA bus registered
May  5 07:29:44 user kernel: [    0.480000] ACPI: bus type pci registered
May  5 07:29:44 user kernel: [    0.500543] PCI: PCI BIOS revision 2.10 entry at 0xfac80, last bus=2
May  5 07:29:44 user kernel: [    0.500546] PCI: Using configuration type 1 for base access
May  5 07:29:44 user kernel: [    0.509553] ACPI: Interpreter enabled
May  5 07:29:44 user kernel: [    0.509556] ACPI: (supports S0 S3 S4 S5)
May  5 07:29:44 user kernel: [    0.509570] ACPI: Using IOAPIC for interrupt routing
May  5 07:29:44 user kernel: [    0.520234] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  5 07:29:44 user kernel: [    0.520395] pci 0000:00:01.1: PME# supported from D3hot D3cold
May  5 07:29:44 user kernel: [    0.520399] pci 0000:00:01.1: PME# disabled
May  5 07:29:44 user kernel: [    0.520437] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520441] pci 0000:00:02.0: PME# disabled
May  5 07:29:44 user kernel: [    0.520475] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520479] pci 0000:00:02.1: PME# disabled
May  5 07:29:44 user kernel: [    0.520519] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520523] pci 0000:00:02.2: PME# disabled
May  5 07:29:44 user kernel: [    0.520745] pci 0000:01:06.0: PME# supported from D0 D2 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520749] pci 0000:01:06.0: PME# disabled
May  5 07:29:44 user kernel: [    0.520798] pci 0000:01:07.0: PME# supported from D0 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520802] pci 0000:01:07.0: PME# disabled
May  5 07:29:44 user kernel: [    0.520849] pci 0000:01:08.0: PME# supported from D3hot D3cold
May  5 07:29:44 user kernel: [    0.520852] pci 0000:01:08.0: PME# disabled
May  5 07:29:44 user kernel: [    0.520905] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520909] pci 0000:01:09.0: PME# disabled
May  5 07:29:44 user kernel: [    0.520965] pci 0000:01:0b.0: PME# supported from D1 D2 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520969] pci 0000:01:0b.0: PME# disabled
May  5 07:29:44 user kernel: [    0.575512] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May  5 07:29:44 user kernel: [    0.575694] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:29:44 user kernel: [    0.575874] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  5 07:29:44 user kernel: [    0.576054] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  5 07:29:44 user kernel: [    0.576233] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May  5 07:29:44 user kernel: [    0.576413] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:29:44 user kernel: [    0.576593] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:29:44 user kernel: [    0.576771] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.576956] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.577137] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:29:44 user kernel: [    0.577315] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.577496] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  5 07:29:44 user kernel: [    0.577678] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:29:44 user kernel: [    0.577858] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.578037] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.578217] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.578404] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.578553] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
May  5 07:29:44 user kernel: [    0.578693] ACPI: PCI Interrupt Link [APC2] (IRQs *17)
May  5 07:29:44 user kernel: [    0.578832] ACPI: PCI Interrupt Link [APC3] (IRQs *18)
May  5 07:29:44 user kernel: [    0.578971] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
May  5 07:29:44 user kernel: [    0.579110] ACPI: PCI Interrupt Link [APC5] (IRQs *16)
May  5 07:29:44 user kernel: [    0.579313] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
May  5 07:29:44 user kernel: [    0.579515] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
May  5 07:29:44 user kernel: [    0.579715] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.579916] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.580140] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
May  5 07:29:44 user kernel: [    0.580340] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.580481] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
May  5 07:29:44 user kernel: [    0.580679] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
May  5 07:29:44 user kernel: [    0.580879] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.581079] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.581279] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.581486] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.581628] ACPI: Power Resource [ISAV] (on)
May  5 07:29:44 user kernel: [    0.581712] Linux Plug and Play Support v0.97 (c) Adam Belay
May  5 07:29:44 user kernel: [    0.581746] pnp: PnP ACPI init
May  5 07:29:44 user kernel: [    0.581754] ACPI: bus type pnp registered
May  5 07:29:44 user kernel: [    0.587841] pnp: PnP ACPI: found 15 devices
May  5 07:29:44 user kernel: [    0.587844] ACPI: ACPI bus type pnp unregistered
May  5 07:29:44 user kernel: [    0.587847] PnPBIOS: Disabled by ACPI PNP
May  5 07:29:44 user kernel: [    0.588175] PCI: Using ACPI for IRQ routing
May  5 07:29:44 user kernel: [    0.588293] NET: Registered protocol family 8
May  5 07:29:44 user kernel: [    0.588293] NET: Registered protocol family 20
May  5 07:29:44 user kernel: [    0.588293] NetLabel: Initializing
May  5 07:29:44 user kernel: [    0.588293] NetLabel:  domain hash size = 128
May  5 07:29:44 user kernel: [    0.588293] NetLabel:  protocols = UNLABELED CIPSOv4
May  5 07:29:44 user kernel: [    0.588293] NetLabel:  unlabeled traffic allowed by default
May  5 07:29:44 user kernel: [    0.588293] tracer: 772 pages allocated for 65536 entries of 48 bytes
May  5 07:29:44 user kernel: [    0.588293]    actual entries 65620
May  5 07:29:44 user kernel: [    0.588293] AppArmor: AppArmor Filesystem Enabled
May  5 07:29:44 user kernel: [    0.588293] ACPI: RTC can wake from S4
May  5 07:29:44 user kernel: [    0.588293] system 00:00: ioport range 0x1000-0x107f has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:00: ioport range 0x1080-0x10ff has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:00: ioport range 0x1400-0x147f has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:00: ioport range 0x1480-0x14ff has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:00: ioport range 0x1800-0x187f has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:00: ioport range 0x1880-0x18ff has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xd8800-0xdbfff has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xf0000-0xf7fff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xf8000-0xfbfff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xfc000-0xfffff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0x2fff0000-0x2fffffff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xffff0000-0xffffffff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0x0-0x9ffff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0x100000-0x2ffeffff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:03: ioport range 0x800-0x805 has been reserved
May  5 07:29:44 user kernel: [    0.624048] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:01
May  5 07:29:44 user kernel: [    0.624052] pci 0000:00:0a.0:   IO window: 0x9000-0xbfff
May  5 07:29:44 user kernel: [    0.624056] pci 0000:00:0a.0:   MEM window: 0xe2000000-0xe3ffffff
May  5 07:29:44 user kernel: [    0.624059] pci 0000:00:0a.0:   PREFETCH window: 0x00000040000000-0x000000400fffff
May  5 07:29:44 user kernel: [    0.624065] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
May  5 07:29:44 user kernel: [    0.624068] pci 0000:00:0b.0:   IO window: 0xc000-0xcfff
May  5 07:29:44 user kernel: [    0.624073] pci 0000:00:0b.0:   MEM window: 0xe0000000-0xe1ffffff
May  5 07:29:44 user kernel: [    0.624077] pci 0000:00:0b.0:   PREFETCH window: 0x000000d8000000-0x000000dfffffff
May  5 07:29:44 user kernel: [    0.624095] bus: 00 index 0 io port: [0, ffff]
May  5 07:29:44 user kernel: [    0.624098] bus: 00 index 1 mmio: [0, ffffffffffffffff]
May  5 07:29:44 user kernel: [    0.624100] bus: 01 index 0 io port: [9000, bfff]
May  5 07:29:44 user kernel: [    0.624102] bus: 01 index 1 mmio: [e2000000, e3ffffff]
May  5 07:29:44 user kernel: [    0.624105] bus: 01 index 2 mmio: [40000000, 400fffff]
May  5 07:29:44 user kernel: [    0.624107] bus: 01 index 3 mmio: [0, 0]
May  5 07:29:44 user kernel: [    0.624109] bus: 02 index 0 io port: [c000, cfff]
May  5 07:29:44 user kernel: [    0.624111] bus: 02 index 1 mmio: [e0000000, e1ffffff]
May  5 07:29:44 user kernel: [    0.624114] bus: 02 index 2 mmio: [d8000000, dfffffff]
May  5 07:29:44 user kernel: [    0.624116] bus: 02 index 3 mmio: [0, 0]
May  5 07:29:44 user kernel: [    0.624127] NET: Registered protocol family 2
May  5 07:29:44 user kernel: [    0.624251] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May  5 07:29:44 user kernel: [    0.624574] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May  5 07:29:44 user kernel: [    0.625530] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May  5 07:29:44 user kernel: [    0.626049] TCP: Hash tables configured (established 131072 bind 65536)
May  5 07:29:44 user kernel: [    0.626052] TCP reno registered
May  5 07:29:44 user kernel: [    0.626159] NET: Registered protocol family 1
May  5 07:29:44 user kernel: [    0.626278] checking if image is initramfs... it is
May  5 07:29:44 user kernel: [    1.270116] Freeing initrd memory: 7861k freed
May  5 07:29:44 user kernel: [    1.270870] audit: initializing netlink socket (disabled)
May  5 07:29:44 user kernel: [    1.270885] type=2000 audit(1241508563.270:1): initialized
May  5 07:29:44 user kernel: [    1.277057] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May  5 07:29:44 user kernel: [    1.279219] VFS: Disk quotas dquot_6.5.1
May  5 07:29:44 user kernel: [    1.279304] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  5 07:29:44 user kernel: [    1.279400] msgmni has been set to 1510
May  5 07:29:44 user kernel: [    1.279520] io scheduler noop registered
May  5 07:29:44 user kernel: [    1.279522] io scheduler anticipatory registered
May  5 07:29:44 user kernel: [    1.279525] io scheduler deadline registered (default)
May  5 07:29:44 user kernel: [    1.279536] io scheduler cfq registered
May  5 07:29:44 user kernel: [    1.320377] isapnp: Scanning for PnP cards...
May  5 07:29:44 user kernel: [    1.676732] isapnp: No Plug & Play device found
May  5 07:29:44 user kernel: [    1.712934] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
May  5 07:29:44 user kernel: [    1.713052] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  5 07:29:44 user kernel: [    1.713192] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  5 07:29:44 user kernel: [    1.713760] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  5 07:29:44 user kernel: [    1.714033] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  5 07:29:44 user kernel: [    1.714419] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
May  5 07:29:44 user kernel: [    1.714428] serial 0000:01:06.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
May  5 07:29:44 user kernel: [    1.717560] brd: module loaded
May  5 07:29:44 user kernel: [    1.717632] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May  5 07:29:44 user kernel: [    1.717750] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May  5 07:29:44 user kernel: [    1.717753] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May  5 07:29:44 user kernel: [    1.718532] serio: i8042 KBD port at 0x60,0x64 irq 1
May  5 07:29:44 user kernel: [    1.718992] mice: PS/2 mouse device common for all mice
May  5 07:29:44 user kernel: [    1.719123] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
May  5 07:29:44 user kernel: [    1.719146] rtc0: alarms up to one year, y3k
May  5 07:29:44 user kernel: [    1.719262] EISA: Probing bus 0 at eisa.0
May  5 07:29:44 user kernel: [    1.719270] Cannot allocate resource for EISA slot 1
May  5 07:29:44 user kernel: [    1.719273] Cannot allocate resource for EISA slot 2
May  5 07:29:44 user kernel: [    1.719288] EISA: Detected 0 cards.
May  5 07:29:44 user kernel: [    1.719292] cpuidle: using governor ladder
May  5 07:29:44 user kernel: [    1.719294] cpuidle: using governor menu
May  5 07:29:44 user kernel: [    1.719813] TCP cubic registered
May  5 07:29:44 user kernel: [    1.719839] Using IPI No-Shortcut mode
May  5 07:29:44 user kernel: [    1.720043] registered taskstats version 1
May  5 07:29:44 user kernel: [    1.720176]   Magic number: 9:35:470
May  5 07:29:44 user kernel: [    1.720365] rtc_cmos 00:05: setting system clock to 2009-05-05 07:29:24 UTC (1241508564)
May  5 07:29:44 user kernel: [    1.720368] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  5 07:29:44 user kernel: [    1.720371] EDD information not available.
May  5 07:29:44 user kernel: [    1.720697] Freeing unused kernel memory: 436k freed
May  5 07:29:44 user kernel: [    1.720815] Write protecting the kernel text: 2632k
May  5 07:29:44 user kernel: [    1.720863] Write protecting the kernel read-only data: 956k
May  5 07:29:44 user kernel: [    1.741491] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May  5 07:29:44 user kernel: [    1.850276] fuse init (API version 7.9)
May  5 07:29:44 user kernel: [    1.870736] ACPI: processor limited to max C-state 1
May  5 07:29:44 user kernel: [    1.870820] processor ACPI0007:00: registered as cooling_device0
May  5 07:29:44 user kernel: [    2.590594] usbcore: registered new interface driver usbfs
May  5 07:29:44 user kernel: [    2.590620] usbcore: registered new interface driver hub
May  5 07:29:44 user kernel: [    2.590658] usbcore: registered new device driver usb
May  5 07:29:44 user kernel: [    2.596560] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
May  5 07:29:44 user kernel: [    2.596569] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 22 (level, high) -> IRQ 22
May  5 07:29:44 user kernel: [    2.596586] ohci_hcd 0000:00:02.0: OHCI Host Controller
May  5 07:29:44 user kernel: [    2.596634] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
May  5 07:29:44 user kernel: [    2.596656] ohci_hcd 0000:00:02.0: irq 22, io mem 0xe4003000
May  5 07:29:44 user kernel: [    2.608392] No dock devices found.
May  5 07:29:44 user kernel: [    2.652216] usb usb1: configuration #1 chosen from 1 choice
May  5 07:29:44 user kernel: [    2.652246] hub 1-0:1.0: USB hub found
May  5 07:29:44 user kernel: [    2.652258] hub 1-0:1.0: 3 ports detected
May  5 07:29:44 user kernel: [    2.666143] SCSI subsystem initialized
May  5 07:29:44 user kernel: [    2.870818] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
May  5 07:29:44 user kernel: [    2.870829] ohci_hcd 0000:00:02.1: PCI INT B -> Link[APCG] -> GSI 21 (level, high) -> IRQ 21
May  5 07:29:44 user kernel: [    2.870849] ohci_hcd 0000:00:02.1: OHCI Host Controller
May  5 07:29:44 user kernel: [    2.870874] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
May  5 07:29:44 user kernel: [    2.870897] ohci_hcd 0000:00:02.1: irq 21, io mem 0xe4004000
May  5 07:29:44 user kernel: [    2.932226] usb usb2: configuration #1 chosen from 1 choice
May  5 07:29:44 user kernel: [    2.932256] hub 2-0:1.0: USB hub found
May  5 07:29:44 user kernel: [    2.932268] hub 2-0:1.0: 3 ports detected
May  5 07:29:44 user kernel: [    3.040883] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
May  5 07:29:44 user kernel: [    3.040893] ehci_hcd 0000:00:02.2: PCI INT C -> Link[APCL] -> GSI 20 (level, high) -> IRQ 20
May  5 07:29:44 user kernel: [    3.040913] ehci_hcd 0000:00:02.2: EHCI Host Controller
May  5 07:29:44 user kernel: [    3.040938] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
May  5 07:29:44 user kernel: [    3.040965] ehci_hcd 0000:00:02.2: debug port 1
May  5 07:29:44 user kernel: [    3.040985] ehci_hcd 0000:00:02.2: irq 20, io mem 0xe4005000
May  5 07:29:44 user kernel: [    3.050047] usb 1-1: new full speed USB device using ohci_hcd and address 2
May  5 07:29:44 user kernel: [    3.070179] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May  5 07:29:44 user kernel: [    3.070355] usb usb3: configuration #1 chosen from 1 choice
May  5 07:29:44 user kernel: [    3.070388] hub 3-0:1.0: USB hub found
May  5 07:29:44 user kernel: [    3.070399] hub 3-0:1.0: 6 ports detected
May  5 07:29:44 user kernel: [    3.290412] pata_acpi 0000:00:08.0: power state changed by ACPI to D0
May  5 07:29:44 user kernel: [    3.291297] VIA Networking Velocity Family Gigabit Ethernet Adapter Driver Ver. 1.14
May  5 07:29:44 user kernel: [    3.291301] Copyright (c) 2002, 2003 VIA Networking Technologies, Inc.
May  5 07:29:44 user kernel: [    3.291303] Copyright (c) 2004 Red Hat Inc.
May  5 07:29:44 user kernel: [    3.291496] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
May  5 07:29:44 user kernel: [    3.291504] via-velocity 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
May  5 07:29:44 user kernel: [    3.292187] eth1: VIA Networking Velocity Family Gigabit Ethernet Adapter
May  5 07:29:44 user kernel: [    3.292191] eth1: Ethernet Address: 00:A0:C5:30:02:07
May  5 07:29:44 user kernel: [    3.310155] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
May  5 07:29:44 user kernel: [    3.310370] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
May  5 07:29:44 user kernel: [    3.310379] r8169 0000:01:0b.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
May  5 07:29:44 user kernel: [    3.310722] eth0: RTL8169s at 0xf083e000, 00:0d:61:21:54:d2, XID 00800000 IRQ 19
May  5 07:29:44 user kernel: [    3.317781] sata_sil 0000:01:0d.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
May  5 07:29:44 user kernel: [    3.317800] sata_sil 0000:01:0d.0: Applying R_ERR on DMA activate FIS errata fix
May  5 07:29:44 user kernel: [    3.317856] scsi0 : sata_sil
May  5 07:29:44 user kernel: [    3.317952] scsi1 : sata_sil
May  5 07:29:44 user kernel: [    3.317987] ata1: SATA max UDMA/100 mmio m512@0xe3013000 tf 0xe3013080 irq 17
May  5 07:29:44 user kernel: [    3.317991] ata2: SATA max UDMA/100 mmio m512@0xe3013000 tf 0xe30130c0 irq 17
May  5 07:29:44 user kernel: [    3.318154] pata_amd 0000:00:08.0: power state changed by ACPI to D0
May  5 07:29:44 user kernel: [    3.318244] scsi2 : pata_amd
May  5 07:29:44 user kernel: [    3.318300] scsi3 : pata_amd
May  5 07:29:44 user kernel: [    3.319153] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
May  5 07:29:44 user kernel: [    3.319156] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
May  5 07:29:44 user kernel: [    3.550434] ata3.00: ATA-6: ST380011A, 8.01, max UDMA/100
May  5 07:29:44 user kernel: [    3.550438] ata3.00: 156301488 sectors, multi 16: LBA48 
May  5 07:29:44 user kernel: [    3.590359] ata3.00: configured for UDMA/100
May  5 07:29:44 user kernel: [    3.660026] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
May  5 07:29:44 user kernel: [    3.680397] ata1.00: ATA-6: ST3120827AS, 3.42, max UDMA/133
May  5 07:29:44 user kernel: [    3.680400] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
May  5 07:29:44 user kernel: [    3.720402] ata1.00: configured for UDMA/100
May  5 07:29:44 user kernel: [    3.780293] ata4.01: ATAPI: _NEC DVD_RW ND-1300A, 1.08, max UDMA/33
May  5 07:29:44 user kernel: [    3.820232] ata4.01: configured for UDMA/33
May  5 07:29:44 user kernel: [    3.820332] scsi 2:0:0:0: Direct-Access     ATA      ST380011A        8.01 PQ: 0 ANSI: 5
May  5 07:29:44 user kernel: [    3.823413] scsi 3:0:1:0: CD-ROM            _NEC     DVD_RW ND-1300A  1.08 PQ: 0 ANSI: 5
May  5 07:29:44 user kernel: [    4.070023] ata2: SATA link down (SStatus 0 SControl 310)
May  5 07:29:44 user kernel: [    4.070132] scsi 0:0:0:0: Direct-Access     ATA      ST3120827AS      3.42 PQ: 0 ANSI: 5
May  5 07:29:44 user kernel: [    4.079725] scsi 2:0:0:0: Attached scsi generic sg0 type 0
May  5 07:29:44 user kernel: [    4.079763] scsi 3:0:1:0: Attached scsi generic sg1 type 5
May  5 07:29:44 user kernel: [    4.079800] scsi 0:0:0:0: Attached scsi generic sg2 type 0
May  5 07:29:44 user kernel: [    4.108308] Driver 'sd' needs updating - please use bus_type methods
May  5 07:29:44 user kernel: [    4.108423] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
May  5 07:29:44 user kernel: [    4.108441] sd 2:0:0:0: [sda] Write Protect is off
May  5 07:29:44 user kernel: [    4.108470] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:29:44 user kernel: [    4.108535] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
May  5 07:29:44 user kernel: [    4.108549] sd 2:0:0:0: [sda] Write Protect is off
May  5 07:29:44 user kernel: [    4.108576] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:29:44 user kernel: [    4.108581]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
May  5 07:29:44 user kernel: [    4.126503]  sda1 < sda5 sda6 >
May  5 07:29:44 user kernel: [    4.134656] sd 2:0:0:0: [sda] Attached SCSI disk
May  5 07:29:44 user kernel: [    4.134744] sd 0:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
May  5 07:29:44 user kernel: [    4.134764] sd 0:0:0:0: [sdb] Write Protect is off
May  5 07:29:44 user kernel: [    4.134796] sd 0:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:29:44 user kernel: [    4.134858] sd 0:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
May  5 07:29:44 user kernel: [    4.134874] sd 0:0:0:0: [sdb] Write Protect is off
May  5 07:29:44 user kernel: [    4.134905] sd 0:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:29:44 user kernel: [    4.134909]  sdb:sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
May  5 07:29:44 user kernel: [    4.139192] Uniform CD-ROM driver Revision: 3.20
May  5 07:29:44 user kernel: [    4.151098]  sdb1 sdb2 < sdb5 sdb6 sdb7 >
May  5 07:29:44 user kernel: [    4.184197] sd 0:0:0:0: [sdb] Attached SCSI disk
May  5 07:29:44 user kernel: [    4.250029] usb 1-1: new full speed USB device using ohci_hcd and address 3
May  5 07:29:44 user kernel: [    4.476272] usb 1-1: configuration #1 chosen from 1 choice
May  5 07:29:44 user kernel: [    4.656792] PM: Starting manual resume from disk
May  5 07:29:44 user kernel: [    4.709126] kjournald starting.  Commit interval 5 seconds
May  5 07:29:44 user kernel: [    4.709143] EXT3-fs: mounted filesystem with ordered data mode.
May  5 07:29:44 user kernel: [    4.820026] usb 1-2: new full speed USB device using ohci_hcd and address 4
May  5 07:29:44 user kernel: [    5.043133] usb 1-2: configuration #1 chosen from 1 choice
May  5 07:29:44 user kernel: [    5.380026] usb 1-3: new low speed USB device using ohci_hcd and address 5
May  5 07:29:44 user kernel: [    5.606225] usb 1-3: configuration #1 chosen from 1 choice
May  5 07:29:44 user kernel: [    6.907183] udevd version 124 started
May  5 07:29:44 user kernel: [    7.911918] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  5 07:29:44 user kernel: [    7.952110] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  5 07:29:44 user kernel: [    8.030740] Linux agpgart interface v0.103
May  5 07:29:44 user kernel: [    8.094743] input: PC Speaker as /devices/platform/pcspkr/input/input2
May  5 07:29:44 user kernel: [    8.120911] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
May  5 07:29:44 user kernel: [    8.120946] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
May  5 07:29:44 user kernel: [    8.124787] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
May  5 07:29:44 user kernel: [    8.142953] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
May  5 07:29:44 user kernel: [    8.142973] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2000
May  5 07:29:44 user kernel: [    8.154607] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
May  5 07:29:44 user kernel: [    8.180063] ACPI: Power Button (FF) [PWRF]
May  5 07:29:44 user kernel: [    8.180162] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
May  5 07:29:44 user kernel: [    8.210085] ACPI: Power Button (CM) [PWRB]
May  5 07:29:44 user kernel: [    8.263570] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
May  5 07:29:44 user kernel: [    8.263577] Intel ICH 0000:00:06.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, high) -> IRQ 22
May  5 07:29:44 user kernel: [    8.610028] intel8x0_measure_ac97_clock: measured 59796 usecs
May  5 07:29:44 user kernel: [    8.610033] intel8x0: clocking to 48000
May  5 07:29:44 user kernel: [    8.701966] parport_pc 00:0b: reported by Plug and Play ACPI
May  5 07:29:44 user kernel: [    8.702009] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
May  5 07:29:44 user kernel: [   10.211835] ieee80211: 802.11 data/management/control stack, git-1.1.13
May  5 07:29:44 user kernel: [   10.211840] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
May  5 07:29:44 user kernel: [   10.280828] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
May  5 07:29:44 user kernel: [   10.280833] ipw2200: Copyright(c) 2003-2006 Intel Corporation
May  5 07:29:44 user kernel: [   10.280929] ipw2200 0000:01:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
May  5 07:29:44 user kernel: [   10.280981] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
May  5 07:29:44 user kernel: [   10.281034] firmware: requesting ipw2200-bss.fw
May  5 07:29:44 user kernel: [   10.626329] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
May  5 07:29:44 user kernel: [   10.632897] usbcore: registered new interface driver cdc_acm
May  5 07:29:44 user kernel: [   10.632903] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
May  5 07:29:44 user kernel: [   10.933501] usbcore: registered new interface driver snd-usb-audio
May  5 07:29:44 user kernel: [   10.933531] usbcore: registered new interface driver hiddev
May  5 07:29:44 user kernel: [   10.942276] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.3/input/input5
May  5 07:29:44 user kernel: [   11.000230] input,hidraw0: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:02.0-2
May  5 07:29:44 user kernel: [   11.006479] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.0/input/input6
May  5 07:29:44 user kernel: [   11.050386] input,hidraw1: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:02.0-3
May  5 07:29:44 user kernel: [   11.050410] usbcore: registered new interface driver usbhid
May  5 07:29:44 user kernel: [   11.050414] usbhid: v2.6:USB HID core driver
May  5 07:29:44 user kernel: [   12.615459] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
May  5 07:29:44 user kernel: [   13.508028] loop: module loaded
May  5 07:29:44 user kernel: [   13.522041] lp0: using parport0 (interrupt-driven).
May  5 07:29:44 user kernel: [   13.890054] Adding 248936k swap on /dev/sda5.  Priority:-1 extents:1 across:248936k
May  5 07:29:44 user kernel: [   14.241224] EXT3 FS on sda6, internal journal
May  5 07:29:44 user kernel: [   15.345827] ip_tables: (C) 2000-2006 Netfilter Core Team
May  5 07:29:44 user kernel: [   15.396787] r8169: eth0: link up
May  5 07:29:44 user kernel: [   16.736930] NET: Registered protocol family 17
May  5 07:29:44 user kernel: [   19.564822] Velocity is AUTO mode
May  5 07:29:44 user kernel: [   20.086147] NET: Registered protocol family 10
May  5 07:29:44 user kernel: [   20.086644] lo: Disabled Privacy Extensions
May  5 07:29:46 user kernel: [   24.094996] warning: `dhcpd3' uses 32-bit capabilities (legacy support in use)
May  5 07:29:46 user dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  5 07:29:46 user dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  5 07:29:46 user dhcpd: All rights reserved.
May  5 07:29:46 user dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  5 07:29:46 user dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  5 07:29:46 user dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  5 07:29:46 user dhcpd: All rights reserved.
May  5 07:29:46 user dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  5 07:29:46 user dhcpd: Wrote 3 leases to leases file.
May  5 07:39:58 user exiting on signal 15
May  5 07:40:59 user syslogd 1.5.0#2ubuntu6: restart.
May  5 07:40:59 user kernel: Inspecting /boot/System.map-2.6.27-7-server
May  5 07:40:59 user kernel: Cannot find map file.
May  5 07:40:59 user kernel: Loaded 48877 symbols from 70 modules.
May  5 07:40:59 user kernel: [    0.000000] Initializing cgroup subsys cpuset
May  5 07:40:59 user kernel: [    0.000000] Initializing cgroup subsys cpu
May  5 07:40:59 user kernel: [    0.000000] Linux version 2.6.27-7-server (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 20:18:35 UTC 2008 (Ubuntu 2.6.27-7.16-server)
May  5 07:40:59 user kernel: [    0.000000] BIOS-provided physical RAM map:
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
May  5 07:40:59 user kernel: [    0.000000] last_pfn = 0x2fff0 max_arch_pfn = 0x1000000
May  5 07:40:59 user kernel: [    0.000000] NX (Execute Disable) protection: active
May  5 07:40:59 user kernel: [    0.000000] RAMDISK: 2f832000 - 2ffdf6b8
May  5 07:40:59 user kernel: [    0.000000] DMI 2.3 present.
May  5 07:40:59 user kernel: [    0.000000] ACPI: RSDP 000F6AB0, 0014 (r0 Nvidia)
May  5 07:40:59 user kernel: [    0.000000] ACPI: RSDT 2FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  5 07:40:59 user kernel: [    0.000000] ACPI: FACP 2FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  5 07:40:59 user kernel: [    0.000000] ACPI: DSDT 2FFF30C0, 4ABF (r1 NVIDIA AWRDACPI     1000 MSFT  100000C)
May  5 07:40:59 user kernel: [    0.000000] ACPI: FACS 2FFF0000, 0040
May  5 07:40:59 user kernel: [    0.000000] ACPI: APIC 2FFF7B80, 005A (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  5 07:40:59 user kernel: [    0.000000] 0MB HIGHMEM available.
May  5 07:40:59 user kernel: [    0.000000] 767MB LOWMEM available.
May  5 07:40:59 user kernel: [    0.000000]   mapped low ram: 0 - 2fff0000
May  5 07:40:59 user kernel: [    0.000000]   low ram: 00000000 - 2fff0000
May  5 07:40:59 user kernel: [    0.000000]   bootmap 0000a000 - 00010000
May  5 07:40:59 user kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002fff0000]
May  5 07:40:59 user kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
May  5 07:40:59 user kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
May  5 07:40:59 user kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
May  5 07:40:59 user kernel: [    0.000000]   #3 [0000100000 - 00005e8220]    TEXT DATA BSS ==> [0000100000 - 00005e8220]
May  5 07:40:59 user kernel: [    0.000000]   #4 [002f832000 - 002ffdf6b8]          RAMDISK ==> [002f832000 - 002ffdf6b8]
May  5 07:40:59 user kernel: [    0.000000]   #5 [00005e9000 - 00005f1000]    INIT_PG_TABLE ==> [00005e9000 - 00005f1000]
May  5 07:40:59 user kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
May  5 07:40:59 user kernel: [    0.000000]   #7 [0000007000 - 000000a000]          PGTABLE ==> [0000007000 - 000000a000]
May  5 07:40:59 user kernel: [    0.000000]   #8 [000000a000 - 0000010000]          BOOTMAP ==> [000000a000 - 0000010000]
May  5 07:40:59 user kernel: [    0.000000] found SMP MP-table at [c00f5000] 000f5000
May  5 07:40:59 user kernel: [    0.000000] Zone PFN ranges:
May  5 07:40:59 user kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
May  5 07:40:59 user kernel: [    0.000000]   Normal   0x00001000 -> 0x0002fff0
May  5 07:40:59 user kernel: [    0.000000]   HighMem  0x0002fff0 -> 0x0002fff0
May  5 07:40:59 user kernel: [    0.000000] Movable zone start PFN for each node
May  5 07:40:59 user kernel: [    0.000000] early_node_map[2] active PFN ranges
May  5 07:40:59 user kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
May  5 07:40:59 user kernel: [    0.000000]     0: 0x00000100 -> 0x0002fff0
May  5 07:40:59 user kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
May  5 07:40:59 user kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
May  5 07:40:59 user kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
May  5 07:40:59 user kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  5 07:40:59 user kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
May  5 07:40:59 user kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  5 07:40:59 user kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
May  5 07:40:59 user kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  5 07:40:59 user kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
May  5 07:40:59 user kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  5 07:40:59 user kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  5 07:40:59 user kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  5 07:40:59 user kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
May  5 07:40:59 user kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May  5 07:40:59 user kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
May  5 07:40:59 user kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
May  5 07:40:59 user kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
May  5 07:40:59 user kernel: [    0.000000] PERCPU: Allocating 45852 bytes of per cpu data
May  5 07:40:59 user kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194767
May  5 07:40:59 user kernel: [    0.000000] Kernel command line: root=UUID=3a16f219-3073-4cf3-8fa0-646d16cda612 ro quiet splash 
May  5 07:40:59 user kernel: [    0.000000] Enabling fast FPU save and restore... done.
May  5 07:40:59 user kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May  5 07:40:59 user kernel: [    0.000000] Initializing CPU#0
May  5 07:40:59 user kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
May  5 07:40:59 user kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
May  5 07:40:59 user kernel: [    0.000000] TSC: using PIT calibration value
May  5 07:40:59 user kernel: [    0.000000] Detected 1994.815 MHz processor.
May  5 07:40:59 user kernel: [    0.010000] Console: colour VGA+ 80x25
May  5 07:40:59 user kernel: [    0.010000] console [tty0] enabled
May  5 07:40:59 user kernel: [    0.010000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  5 07:40:59 user kernel: [    0.010000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  5 07:40:59 user kernel: [    0.010000] Memory: 765068k/786368k available (2628k kernel code, 20728k reserved, 1201k data, 436k init, 0k highmem)
May  5 07:40:59 user kernel: [    0.010000] virtual kernel memory layout:
May  5 07:40:59 user kernel: [    0.010000]     fixmap  : 0xffc78000 - 0xfffff000   (3612 kB)
May  5 07:40:59 user kernel: [    0.010000]     pkmap   : 0xff800000 - 0xffa00000   (2048 kB)
May  5 07:40:59 user kernel: [    0.010000]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
May  5 07:40:59 user kernel: [    0.010000]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
May  5 07:40:59 user kernel: [    0.010000]       .init : 0xc04c3000 - 0xc0530000   ( 436 kB)
May  5 07:40:59 user kernel: [    0.010000]       .data : 0xc0391036 - 0xc04bd800   (1201 kB)
May  5 07:40:59 user kernel: [    0.010000]       .text : 0xc0100000 - 0xc0391036   (2628 kB)
May  5 07:40:59 user kernel: [    0.010000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
May  5 07:40:59 user kernel: [    0.010000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
May  5 07:40:59 user kernel: [    0.010008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.63 BogoMIPS (lpj=19948150)
May  5 07:40:59 user kernel: [    0.010026] Security Framework initialized
May  5 07:40:59 user kernel: [    0.010033] SELinux:  Disabled at boot.
May  5 07:40:59 user kernel: [    0.010053] AppArmor: AppArmor initialized
May  5 07:40:59 user kernel: [    0.010061] Mount-cache hash table entries: 512
May  5 07:40:59 user kernel: [    0.010209] Initializing cgroup subsys ns
May  5 07:40:59 user kernel: [    0.010213] Initializing cgroup subsys cpuacct
May  5 07:40:59 user kernel: [    0.010215] Initializing cgroup subsys memory
May  5 07:40:59 user kernel: [    0.010228] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May  5 07:40:59 user kernel: [    0.010231] CPU: L2 Cache: 512K (64 bytes/line)
May  5 07:40:59 user kernel: [    0.010241] Checking 'hlt' instruction... OK.
May  5 07:40:59 user kernel: [    0.050367] SMP alternatives: switching to UP code
May  5 07:40:59 user kernel: [    0.056452] Freeing SMP alternatives: 11k freed
May  5 07:40:59 user kernel: [    0.056457] ACPI: Core revision 20080609
May  5 07:40:59 user kernel: [    0.057952] ACPI: Checking initramfs for custom DSDT
May  5 07:40:59 user kernel: [    0.371033] ENABLING IO-APIC IRQs
May  5 07:40:59 user kernel: [    0.371200] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
May  5 07:40:59 user kernel: [    0.471211] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 08
May  5 07:40:59 user kernel: [    0.480000] Brought up 1 CPUs
May  5 07:40:59 user kernel: [    0.480000] Total of 1 processors activated (3989.63 BogoMIPS).
May  5 07:40:59 user kernel: [    0.480000] net_namespace: 840 bytes
May  5 07:40:59 user kernel: [    0.480000] Booting paravirtualized kernel on bare hardware
May  5 07:40:59 user kernel: [    0.480000] Time:  7:40:36  Date: 05/05/09
May  5 07:40:59 user kernel: [    0.480000] NET: Registered protocol family 16
May  5 07:40:59 user kernel: [    0.480000] EISA bus registered
May  5 07:40:59 user kernel: [    0.480000] ACPI: bus type pci registered
May  5 07:40:59 user kernel: [    0.500543] PCI: PCI BIOS revision 2.10 entry at 0xfac80, last bus=2
May  5 07:40:59 user kernel: [    0.500546] PCI: Using configuration type 1 for base access
May  5 07:40:59 user kernel: [    0.509554] ACPI: Interpreter enabled
May  5 07:40:59 user kernel: [    0.509557] ACPI: (supports S0 S3 S4 S5)
May  5 07:40:59 user kernel: [    0.509571] ACPI: Using IOAPIC for interrupt routing
May  5 07:40:59 user kernel: [    0.520239] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  5 07:40:59 user kernel: [    0.520400] pci 0000:00:01.1: PME# supported from D3hot D3cold
May  5 07:40:59 user kernel: [    0.520404] pci 0000:00:01.1: PME# disabled
May  5 07:40:59 user kernel: [    0.520443] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520446] pci 0000:00:02.0: PME# disabled
May  5 07:40:59 user kernel: [    0.520481] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520484] pci 0000:00:02.1: PME# disabled
May  5 07:40:59 user kernel: [    0.520525] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520528] pci 0000:00:02.2: PME# disabled
May  5 07:40:59 user kernel: [    0.520750] pci 0000:01:06.0: PME# supported from D0 D2 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520754] pci 0000:01:06.0: PME# disabled
May  5 07:40:59 user kernel: [    0.520803] pci 0000:01:07.0: PME# supported from D0 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520807] pci 0000:01:07.0: PME# disabled
May  5 07:40:59 user kernel: [    0.520854] pci 0000:01:08.0: PME# supported from D3hot D3cold
May  5 07:40:59 user kernel: [    0.520857] pci 0000:01:08.0: PME# disabled
May  5 07:40:59 user kernel: [    0.520910] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520913] pci 0000:01:09.0: PME# disabled
May  5 07:40:59 user kernel: [    0.520970] pci 0000:01:0b.0: PME# supported from D1 D2 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520974] pci 0000:01:0b.0: PME# disabled
May  5 07:40:59 user kernel: [    0.575503] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May  5 07:40:59 user kernel: [    0.575685] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:40:59 user kernel: [    0.575865] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  5 07:40:59 user kernel: [    0.576044] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  5 07:40:59 user kernel: [    0.576224] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May  5 07:40:59 user kernel: [    0.576403] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:40:59 user kernel: [    0.576583] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:40:59 user kernel: [    0.576762] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.576946] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.577127] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:40:59 user kernel: [    0.577305] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.577486] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  5 07:40:59 user kernel: [    0.577668] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:40:59 user kernel: [    0.577848] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.578027] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.578206] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.578394] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.578543] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
May  5 07:40:59 user kernel: [    0.578683] ACPI: PCI Interrupt Link [APC2] (IRQs *17)
May  5 07:40:59 user kernel: [    0.578822] ACPI: PCI Interrupt Link [APC3] (IRQs *18)
May  5 07:40:59 user kernel: [    0.578961] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
May  5 07:40:59 user kernel: [    0.579100] ACPI: PCI Interrupt Link [APC5] (IRQs *16)
May  5 07:40:59 user kernel: [    0.579303] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
May  5 07:40:59 user kernel: [    0.579505] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
May  5 07:40:59 user kernel: [    0.579705] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.579906] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.580130] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
May  5 07:40:59 user kernel: [    0.580329] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.580470] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
May  5 07:40:59 user kernel: [    0.580668] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
May  5 07:40:59 user kernel: [    0.580868] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.581068] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.581268] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.581476] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.581617] ACPI: Power Resource [ISAV] (on)
May  5 07:40:59 user kernel: [    0.581701] Linux Plug and Play Support v0.97 (c) Adam Belay
May  5 07:40:59 user kernel: [    0.581735] pnp: PnP ACPI init
May  5 07:40:59 user kernel: [    0.581743] ACPI: bus type pnp registered
May  5 07:40:59 user kernel: [    0.587831] pnp: PnP ACPI: found 15 devices
May  5 07:40:59 user kernel: [    0.587834] ACPI: ACPI bus type pnp unregistered
May  5 07:40:59 user kernel: [    0.587838] PnPBIOS: Disabled by ACPI PNP
May  5 07:40:59 user kernel: [    0.588165] PCI: Using ACPI for IRQ routing
May  5 07:40:59 user kernel: [    0.588283] NET: Registered protocol family 8
May  5 07:40:59 user kernel: [    0.588283] NET: Registered protocol family 20
May  5 07:40:59 user kernel: [    0.588283] NetLabel: Initializing
May  5 07:40:59 user kernel: [    0.588283] NetLabel:  domain hash size = 128
May  5 07:40:59 user kernel: [    0.588283] NetLabel:  protocols = UNLABELED CIPSOv4
May  5 07:40:59 user kernel: [    0.588283] NetLabel:  unlabeled traffic allowed by default
May  5 07:40:59 user kernel: [    0.588283] tracer: 772 pages allocated for 65536 entries of 48 bytes
May  5 07:40:59 user kernel: [    0.588283]    actual entries 65620
May  5 07:40:59 user kernel: [    0.588283] AppArmor: AppArmor Filesystem Enabled
May  5 07:40:59 user kernel: [    0.588283] ACPI: RTC can wake from S4
May  5 07:40:59 user kernel: [    0.588283] system 00:00: ioport range 0x1000-0x107f has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:00: ioport range 0x1080-0x10ff has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:00: ioport range 0x1400-0x147f has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:00: ioport range 0x1480-0x14ff has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:00: ioport range 0x1800-0x187f has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:00: ioport range 0x1880-0x18ff has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xd8800-0xdbfff has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xf0000-0xf7fff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xf8000-0xfbfff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xfc000-0xfffff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0x2fff0000-0x2fffffff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xffff0000-0xffffffff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0x0-0x9ffff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0x100000-0x2ffeffff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:03: ioport range 0x800-0x805 has been reserved
May  5 07:40:59 user kernel: [    0.624039] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:01
May  5 07:40:59 user kernel: [    0.624042] pci 0000:00:0a.0:   IO window: 0x9000-0xbfff
May  5 07:40:59 user kernel: [    0.624047] pci 0000:00:0a.0:   MEM window: 0xe2000000-0xe3ffffff
May  5 07:40:59 user kernel: [    0.624050] pci 0000:00:0a.0:   PREFETCH window: 0x00000040000000-0x000000400fffff
May  5 07:40:59 user kernel: [    0.624056] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
May  5 07:40:59 user kernel: [    0.624059] pci 0000:00:0b.0:   IO window: 0xc000-0xcfff
May  5 07:40:59 user kernel: [    0.624064] pci 0000:00:0b.0:   MEM window: 0xe0000000-0xe1ffffff
May  5 07:40:59 user kernel: [    0.624068] pci 0000:00:0b.0:   PREFETCH window: 0x000000d8000000-0x000000dfffffff
May  5 07:40:59 user kernel: [    0.624087] bus: 00 index 0 io port: [0, ffff]
May  5 07:40:59 user kernel: [    0.624089] bus: 00 index 1 mmio: [0, ffffffffffffffff]
May  5 07:40:59 user kernel: [    0.624091] bus: 01 index 0 io port: [9000, bfff]
May  5 07:40:59 user kernel: [    0.624094] bus: 01 index 1 mmio: [e2000000, e3ffffff]
May  5 07:40:59 user kernel: [    0.624096] bus: 01 index 2 mmio: [40000000, 400fffff]
May  5 07:40:59 user kernel: [    0.624098] bus: 01 index 3 mmio: [0, 0]
May  5 07:40:59 user kernel: [    0.624100] bus: 02 index 0 io port: [c000, cfff]
May  5 07:40:59 user kernel: [    0.624102] bus: 02 index 1 mmio: [e0000000, e1ffffff]
May  5 07:40:59 user kernel: [    0.624105] bus: 02 index 2 mmio: [d8000000, dfffffff]
May  5 07:40:59 user kernel: [    0.624107] bus: 02 index 3 mmio: [0, 0]
May  5 07:40:59 user kernel: [    0.624119] NET: Registered protocol family 2
May  5 07:40:59 user kernel: [    0.624242] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May  5 07:40:59 user kernel: [    0.624564] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May  5 07:40:59 user kernel: [    0.625521] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May  5 07:40:59 user kernel: [    0.626040] TCP: Hash tables configured (established 131072 bind 65536)
May  5 07:40:59 user kernel: [    0.626044] TCP reno registered
May  5 07:40:59 user kernel: [    0.626150] NET: Registered protocol family 1
May  5 07:40:59 user kernel: [    0.626268] checking if image is initramfs... it is
May  5 07:40:59 user kernel: [    1.270106] Freeing initrd memory: 7861k freed
May  5 07:40:59 user kernel: [    1.270859] audit: initializing netlink socket (disabled)
May  5 07:40:59 user kernel: [    1.270873] type=2000 audit(1241509236.270:1): initialized
May  5 07:40:59 user kernel: [    1.277046] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May  5 07:40:59 user kernel: [    1.279208] VFS: Disk quotas dquot_6.5.1
May  5 07:40:59 user kernel: [    1.279292] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  5 07:40:59 user kernel: [    1.279389] msgmni has been set to 1510
May  5 07:40:59 user kernel: [    1.279509] io scheduler noop registered
May  5 07:40:59 user kernel: [    1.279511] io scheduler anticipatory registered
May  5 07:40:59 user kernel: [    1.279514] io scheduler deadline registered (default)
May  5 07:40:59 user kernel: [    1.279525] io scheduler cfq registered
May  5 07:40:59 user kernel: [    1.320378] isapnp: Scanning for PnP cards...
May  5 07:40:59 user kernel: [    1.676735] isapnp: No Plug & Play device found
May  5 07:40:59 user kernel: [    1.712889] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
May  5 07:40:59 user kernel: [    1.713006] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  5 07:40:59 user kernel: [    1.713145] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  5 07:40:59 user kernel: [    1.713711] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  5 07:40:59 user kernel: [    1.713981] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  5 07:40:59 user kernel: [    1.714367] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
May  5 07:40:59 user kernel: [    1.714376] serial 0000:01:06.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
May  5 07:40:59 user kernel: [    1.717494] brd: module loaded
May  5 07:40:59 user kernel: [    1.717566] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May  5 07:40:59 user kernel: [    1.717682] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May  5 07:40:59 user kernel: [    1.717685] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May  5 07:40:59 user kernel: [    1.718259] serio: i8042 KBD port at 0x60,0x64 irq 1
May  5 07:40:59 user kernel: [    1.718714] mice: PS/2 mouse device common for all mice
May  5 07:40:59 user kernel: [    1.718846] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
May  5 07:40:59 user kernel: [    1.718869] rtc0: alarms up to one year, y3k
May  5 07:40:59 user kernel: [    1.718985] EISA: Probing bus 0 at eisa.0
May  5 07:40:59 user kernel: [    1.718993] Cannot allocate resource for EISA slot 1
May  5 07:40:59 user kernel: [    1.718996] Cannot allocate resource for EISA slot 2
May  5 07:40:59 user kernel: [    1.719011] EISA: Detected 0 cards.
May  5 07:40:59 user kernel: [    1.719015] cpuidle: using governor ladder
May  5 07:40:59 user kernel: [    1.719017] cpuidle: using governor menu
May  5 07:40:59 user kernel: [    1.719540] TCP cubic registered
May  5 07:40:59 user kernel: [    1.719566] Using IPI No-Shortcut mode
May  5 07:40:59 user kernel: [    1.719753] registered taskstats version 1
May  5 07:40:59 user kernel: [    1.719884]   Magic number: 9:241:672
May  5 07:40:59 user kernel: [    1.720092] rtc_cmos 00:05: setting system clock to 2009-05-05 07:40:37 UTC (1241509237)
May  5 07:40:59 user kernel: [    1.720096] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  5 07:40:59 user kernel: [    1.720098] EDD information not available.
May  5 07:40:59 user kernel: [    1.720424] Freeing unused kernel memory: 436k freed
May  5 07:40:59 user kernel: [    1.720543] Write protecting the kernel text: 2632k
May  5 07:40:59 user kernel: [    1.720590] Write protecting the kernel read-only data: 956k
May  5 07:40:59 user kernel: [    1.740827] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May  5 07:40:59 user kernel: [    1.850427] fuse init (API version 7.9)
May  5 07:40:59 user kernel: [    1.870946] ACPI: processor limited to max C-state 1
May  5 07:40:59 user kernel: [    1.871030] processor ACPI0007:00: registered as cooling_device0
May  5 07:40:59 user kernel: [    2.601656] usbcore: registered new interface driver usbfs
May  5 07:40:59 user kernel: [    2.601680] usbcore: registered new interface driver hub
May  5 07:40:59 user kernel: [    2.601717] usbcore: registered new device driver usb
May  5 07:40:59 user kernel: [    2.604469] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
May  5 07:40:59 user kernel: [    2.604479] ehci_hcd 0000:00:02.2: PCI INT C -> Link[APCL] -> GSI 22 (level, high) -> IRQ 22
May  5 07:40:59 user kernel: [    2.604495] ehci_hcd 0000:00:02.2: EHCI Host Controller
May  5 07:40:59 user kernel: [    2.604543] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
May  5 07:40:59 user kernel: [    2.604570] ehci_hcd 0000:00:02.2: debug port 1
May  5 07:40:59 user kernel: [    2.604588] ehci_hcd 0000:00:02.2: irq 22, io mem 0xe4005000
May  5 07:40:59 user kernel: [    2.614237] No dock devices found.
May  5 07:40:59 user kernel: [    2.627729] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May  5 07:40:59 user kernel: [    2.627912] usb usb1: configuration #1 chosen from 1 choice
May  5 07:40:59 user kernel: [    2.627940] hub 1-0:1.0: USB hub found
May  5 07:40:59 user kernel: [    2.627953] hub 1-0:1.0: 6 ports detected
May  5 07:40:59 user kernel: [    2.666619] SCSI subsystem initialized
May  5 07:40:59 user kernel: [    2.840739] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
May  5 07:40:59 user kernel: [    2.840749] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, high) -> IRQ 21
May  5 07:40:59 user kernel: [    2.840769] ohci_hcd 0000:00:02.0: OHCI Host Controller
May  5 07:40:59 user kernel: [    2.840794] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
May  5 07:40:59 user kernel: [    2.840816] ohci_hcd 0000:00:02.0: irq 21, io mem 0xe4003000
May  5 07:40:59 user kernel: [    2.902258] usb usb2: configuration #1 chosen from 1 choice
May  5 07:40:59 user kernel: [    2.902288] hub 2-0:1.0: USB hub found
May  5 07:40:59 user kernel: [    2.902300] hub 2-0:1.0: 3 ports detected
May  5 07:40:59 user kernel: [    3.120634] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
May  5 07:40:59 user kernel: [    3.120644] ohci_hcd 0000:00:02.1: PCI INT B -> Link[APCG] -> GSI 20 (level, high) -> IRQ 20
May  5 07:40:59 user kernel: [    3.120664] ohci_hcd 0000:00:02.1: OHCI Host Controller
May  5 07:40:59 user kernel: [    3.120689] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
May  5 07:40:59 user kernel: [    3.120712] ohci_hcd 0000:00:02.1: irq 20, io mem 0xe4004000
May  5 07:40:59 user kernel: [    3.182218] usb usb3: configuration #1 chosen from 1 choice
May  5 07:40:59 user kernel: [    3.182254] hub 3-0:1.0: USB hub found
May  5 07:40:59 user kernel: [    3.182266] hub 3-0:1.0: 3 ports detected
May  5 07:40:59 user kernel: [    3.290440] pata_acpi 0000:00:08.0: power state changed by ACPI to D0
May  5 07:40:59 user kernel: [    3.290965] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
May  5 07:40:59 user kernel: [    3.291145] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
May  5 07:40:59 user kernel: [    3.291154] r8169 0000:01:0b.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
May  5 07:40:59 user kernel: [    3.291452] eth1: RTL8169s at 0xf082a000, 00:0d:61:21:54:d2, XID 00800000 IRQ 19
May  5 07:40:59 user kernel: [    3.294794] VIA Networking Velocity Family Gigabit Ethernet Adapter Driver Ver. 1.14
May  5 07:40:59 user kernel: [    3.294797] Copyright (c) 2002, 2003 VIA Networking Technologies, Inc.
May  5 07:40:59 user kernel: [    3.294799] Copyright (c) 2004 Red Hat Inc.
May  5 07:40:59 user kernel: [    3.294952] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
May  5 07:40:59 user kernel: [    3.294957] via-velocity 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
May  5 07:40:59 user kernel: [    3.295625] eth0: VIA Networking Velocity Family Gigabit Ethernet Adapter
May  5 07:40:59 user kernel: [    3.295628] eth0: Ethernet Address: 00:A0:C5:30:02:07
May  5 07:40:59 user kernel: [    3.310412] sata_sil 0000:01:0d.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
May  5 07:40:59 user kernel: [    3.310432] sata_sil 0000:01:0d.0: Applying R_ERR on DMA activate FIS errata fix
May  5 07:40:59 user kernel: [    3.310512] scsi0 : sata_sil
May  5 07:40:59 user kernel: [    3.310610] scsi1 : sata_sil
May  5 07:40:59 user kernel: [    3.310644] ata1: SATA max UDMA/100 mmio m512@0xe3013000 tf 0xe3013080 irq 17
May  5 07:40:59 user kernel: [    3.310647] ata2: SATA max UDMA/100 mmio m512@0xe3013000 tf 0xe30130c0 irq 17
May  5 07:40:59 user kernel: [    3.320105] usb 2-1: new full speed USB device using ohci_hcd and address 2
May  5 07:40:59 user kernel: [    3.546248] usb 2-1: configuration #1 chosen from 1 choice
May  5 07:40:59 user kernel: [    3.660031] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
May  5 07:40:59 user kernel: [    3.680428] ata1.00: ATA-6: ST3120827AS, 3.42, max UDMA/133
May  5 07:40:59 user kernel: [    3.680431] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
May  5 07:40:59 user kernel: [    3.720397] ata1.00: configured for UDMA/100
May  5 07:40:59 user kernel: [    3.890012] usb 2-2: new full speed USB device using ohci_hcd and address 3
May  5 07:40:59 user kernel: [    4.070021] ata2: SATA link down (SStatus 0 SControl 310)
May  5 07:40:59 user kernel: [    4.070135] scsi 0:0:0:0: Direct-Access     ATA      ST3120827AS      3.42 PQ: 0 ANSI: 5
May  5 07:40:59 user kernel: [    4.073892] pata_amd 0000:00:08.0: power state changed by ACPI to D0
May  5 07:40:59 user kernel: [    4.074002] scsi2 : pata_amd
May  5 07:40:59 user kernel: [    4.074072] scsi3 : pata_amd
May  5 07:40:59 user kernel: [    4.074927] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
May  5 07:40:59 user kernel: [    4.074930] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
May  5 07:40:59 user kernel: [    4.084358] scsi 0:0:0:0: Attached scsi generic sg0 type 0
May  5 07:40:59 user kernel: [    4.096951] Driver 'sd' needs updating - please use bus_type methods
May  5 07:40:59 user kernel: [    4.097068] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
May  5 07:40:59 user kernel: [    4.097086] sd 0:0:0:0: [sda] Write Protect is off
May  5 07:40:59 user kernel: [    4.097116] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:40:59 user kernel: [    4.097180] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
May  5 07:40:59 user kernel: [    4.097195] sd 0:0:0:0: [sda] Write Protect is off
May  5 07:40:59 user kernel: [    4.097222] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:40:59 user kernel: [    4.097226]  sda: sda1 sda2 <<6>usb 2-2: configuration #1 chosen from 1 choice
May  5 07:40:59 user kernel: [    4.123339]  sda5 sda6 sda7 >
May  5 07:40:59 user kernel: [    4.145863] sd 0:0:0:0: [sda] Attached SCSI disk
May  5 07:40:59 user kernel: [    4.310433] ata3.00: ATA-6: ST380011A, 8.01, max UDMA/100
May  5 07:40:59 user kernel: [    4.310437] ata3.00: 156301488 sectors, multi 16: LBA48 
May  5 07:40:59 user kernel: [    4.350355] ata3.00: configured for UDMA/100
May  5 07:40:59 user kernel: [    4.450011] usb 2-3: new low speed USB device using ohci_hcd and address 4
May  5 07:40:59 user kernel: [    4.540297] ata4.01: ATAPI: _NEC DVD_RW ND-1300A, 1.08, max UDMA/33
May  5 07:40:59 user kernel: [    4.580238] ata4.01: configured for UDMA/33
May  5 07:40:59 user kernel: [    4.580345] scsi 2:0:0:0: Direct-Access     ATA      ST380011A        8.01 PQ: 0 ANSI: 5
May  5 07:40:59 user kernel: [    4.580527] scsi 2:0:0:0: Attached scsi generic sg1 type 0
May  5 07:40:59 user kernel: [    4.583519] scsi 3:0:1:0: CD-ROM            _NEC     DVD_RW ND-1300A  1.08 PQ: 0 ANSI: 5
May  5 07:40:59 user kernel: [    4.583615] scsi 3:0:1:0: Attached scsi generic sg2 type 5
May  5 07:40:59 user kernel: [    4.584668] sd 2:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
May  5 07:40:59 user kernel: [    4.584807] sd 2:0:0:0: [sdb] Write Protect is off
May  5 07:40:59 user kernel: [    4.584839] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:40:59 user kernel: [    4.584916] sd 2:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
May  5 07:40:59 user kernel: [    4.584930] sd 2:0:0:0: [sdb] Write Protect is off
May  5 07:40:59 user kernel: [    4.584957] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:40:59 user kernel: [    4.584962]  sdb: sdb1 < sdb5<4>Driver 'sr' needs updating - please use bus_type methods
May  5 07:40:59 user kernel: [    4.616528]  sdb6 >
May  5 07:40:59 user kernel: [    4.616678] sd 2:0:0:0: [sdb] Attached SCSI disk
May  5 07:40:59 user kernel: [    4.630705] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
May  5 07:40:59 user kernel: [    4.630711] Uniform CD-ROM driver Revision: 3.20
May  5 07:40:59 user kernel: [    4.686279] usb 2-3: configuration #1 chosen from 1 choice
May  5 07:40:59 user kernel: [    4.689778] usbcore: registered new interface driver hiddev
May  5 07:40:59 user kernel: [    4.696191] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.3/input/input2
May  5 07:40:59 user kernel: [    4.702897] input,hidraw0: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:02.0-2
May  5 07:40:59 user kernel: [    4.708407] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input3
May  5 07:40:59 user kernel: [    4.708727] input,hidraw1: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:02.0-3
May  5 07:40:59 user kernel: [    4.708748] usbcore: registered new interface driver usbhid
May  5 07:40:59 user kernel: [    4.708752] usbhid: v2.6:USB HID core driver
May  5 07:40:59 user kernel: [    5.093416] PM: Starting manual resume from disk
May  5 07:40:59 user kernel: [    5.157817] kjournald starting.  Commit interval 5 seconds
May  5 07:40:59 user kernel: [    5.157833] EXT3-fs: mounted filesystem with ordered data mode.
May  5 07:40:59 user kernel: [    8.220829] udevd version 124 started
May  5 07:40:59 user kernel: [    9.029189] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  5 07:40:59 user kernel: [    9.051929] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  5 07:40:59 user kernel: [    9.086174] Linux agpgart interface v0.103
May  5 07:40:59 user kernel: [    9.143279] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
May  5 07:40:59 user kernel: [    9.143311] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
May  5 07:40:59 user kernel: [    9.147249] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
May  5 07:40:59 user kernel: [    9.331787] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
May  5 07:40:59 user kernel: [    9.331807] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2000
May  5 07:40:59 user kernel: [    9.383350] input: PC Speaker as /devices/platform/pcspkr/input/input4
May  5 07:40:59 user kernel: [    9.477715] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input5
May  5 07:40:59 user kernel: [    9.510034] ACPI: Power Button (FF) [PWRF]
May  5 07:40:59 user kernel: [    9.510126] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
May  5 07:40:59 user kernel: [    9.535525] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
May  5 07:40:59 user kernel: [    9.535532] Intel ICH 0000:00:06.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, high) -> IRQ 22
May  5 07:40:59 user kernel: [    9.550035] ACPI: Power Button (CM) [PWRB]
May  5 07:40:59 user kernel: [    9.822266] ieee80211: 802.11 data/management/control stack, git-1.1.13
May  5 07:40:59 user kernel: [    9.822271] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
May  5 07:40:59 user kernel: [    9.880039] intel8x0_measure_ac97_clock: measured 57828 usecs
May  5 07:40:59 user kernel: [    9.880043] intel8x0: clocking to 48000
May  5 07:40:59 user kernel: [    9.897410] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
May  5 07:40:59 user kernel: [    9.897414] ipw2200: Copyright(c) 2003-2006 Intel Corporation
May  5 07:40:59 user kernel: [    9.897511] ipw2200 0000:01:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
May  5 07:40:59 user kernel: [    9.897558] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
May  5 07:40:59 user kernel: [    9.897614] firmware: requesting ipw2200-bss.fw
May  5 07:40:59 user kernel: [   10.331980] parport_pc 00:0b: reported by Plug and Play ACPI
May  5 07:40:59 user kernel: [   10.332022] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
May  5 07:40:59 user kernel: [   11.986348] cdc_acm 2-1:1.0: ttyACM0: USB ACM device
May  5 07:40:59 user kernel: [   13.916024] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
May  5 07:40:59 user kernel: [   13.917216] udev: renamed network interface eth1 to eth0
May  5 07:40:59 user kernel: [   13.967450] udev: renamed network interface eth0_rename to eth1
May  5 07:40:59 user kernel: [   17.142675] usbcore: registered new interface driver cdc_acm
May  5 07:40:59 user kernel: [   17.142681] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
May  5 07:40:59 user kernel: [   17.147471] usbcore: registered new interface driver snd-usb-audio
May  5 07:40:59 user kernel: [   17.840833] loop: module loaded
May  5 07:40:59 user kernel: [   17.854783] lp0: using parport0 (interrupt-driven).
May  5 07:40:59 user kernel: [   18.356446] Adding 248936k swap on /dev/sdb5.  Priority:-1 extents:1 across:248936k
May  5 07:40:59 user kernel: [   18.740220] EXT3 FS on sdb6, internal journal
May  5 07:40:59 user kernel: [   19.903078] ip_tables: (C) 2000-2006 Netfilter Core Team
May  5 07:40:59 user kernel: [   19.954301] r8169: eth0: link up
May  5 07:40:59 user kernel: [   21.294121] NET: Registered protocol family 17
May  5 07:40:59 user kernel: [   21.444253] Velocity is AUTO mode
May  5 07:40:59 user kernel: [   21.878328] NET: Registered protocol family 10
May  5 07:40:59 user kernel: [   21.878844] lo: Disabled Privacy Extensions
May  5 07:41:02 user kernel: [   25.940152] warning: `dhcpd3' uses 32-bit capabilities (legacy support in use)
May  5 07:41:02 user dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  5 07:41:02 user dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  5 07:41:02 user dhcpd: All rights reserved.
May  5 07:41:02 user dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  5 07:41:02 user dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  5 07:41:02 user dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  5 07:41:02 user dhcpd: All rights reserved.
May  5 07:41:02 user dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  5 07:41:02 user dhcpd: Wrote 3 leases to leases file.
May  5 07:42:58 user exiting on signal 15
May  6 07:31:18 user syslogd 1.5.0#2ubuntu6: restart.
May  6 07:31:18 user kernel: Inspecting /boot/System.map-2.6.27-7-server
May  6 07:31:18 user kernel: Cannot find map file.
May  6 07:31:18 user kernel: Loaded 48877 symbols from 70 modules.
May  6 07:31:18 user kernel: [    0.000000] Initializing cgroup subsys cpuset
May  6 07:31:18 user kernel: [    0.000000] Initializing cgroup subsys cpu
May  6 07:31:18 user kernel: [    0.000000] Linux version 2.6.27-7-server (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 20:18:35 UTC 2008 (Ubuntu 2.6.27-7.16-server)
May  6 07:31:18 user kernel: [    0.000000] BIOS-provided physical RAM map:
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
May  6 07:31:18 user kernel: [    0.000000] last_pfn = 0x2fff0 max_arch_pfn = 0x1000000
May  6 07:31:18 user kernel: [    0.000000] NX (Execute Disable) protection: active
May  6 07:31:18 user kernel: [    0.000000] RAMDISK: 2f832000 - 2ffdf6b8
May  6 07:31:18 user kernel: [    0.000000] DMI 2.3 present.
May  6 07:31:18 user kernel: [    0.000000] ACPI: RSDP 000F6AB0, 0014 (r0 Nvidia)
May  6 07:31:18 user kernel: [    0.000000] ACPI: RSDT 2FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  6 07:31:18 user kernel: [    0.000000] ACPI: FACP 2FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  6 07:31:18 user kernel: [    0.000000] ACPI: DSDT 2FFF30C0, 4ABF (r1 NVIDIA AWRDACPI     1000 MSFT  100000C)
May  6 07:31:18 user kernel: [    0.000000] ACPI: FACS 2FFF0000, 0040
May  6 07:31:18 user kernel: [    0.000000] ACPI: APIC 2FFF7B80, 005A (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  6 07:31:18 user kernel: [    0.000000] 0MB HIGHMEM available.
May  6 07:31:18 user kernel: [    0.000000] 767MB LOWMEM available.
May  6 07:31:18 user kernel: [    0.000000]   mapped low ram: 0 - 2fff0000
May  6 07:31:18 user kernel: [    0.000000]   low ram: 00000000 - 2fff0000
May  6 07:31:18 user kernel: [    0.000000]   bootmap 0000a000 - 00010000
May  6 07:31:18 user kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002fff0000]
May  6 07:31:18 user kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
May  6 07:31:18 user kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
May  6 07:31:18 user kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
May  6 07:31:18 user kernel: [    0.000000]   #3 [0000100000 - 00005e8220]    TEXT DATA BSS ==> [0000100000 - 00005e8220]
May  6 07:31:18 user kernel: [    0.000000]   #4 [002f832000 - 002ffdf6b8]          RAMDISK ==> [002f832000 - 002ffdf6b8]
May  6 07:31:18 user kernel: [    0.000000]   #5 [00005e9000 - 00005f1000]    INIT_PG_TABLE ==> [00005e9000 - 00005f1000]
May  6 07:31:18 user kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
May  6 07:31:18 user kernel: [    0.000000]   #7 [0000007000 - 000000a000]          PGTABLE ==> [0000007000 - 000000a000]
May  6 07:31:18 user kernel: [    0.000000]   #8 [000000a000 - 0000010000]          BOOTMAP ==> [000000a000 - 0000010000]
May  6 07:31:18 user kernel: [    0.000000] found SMP MP-table at [c00f5000] 000f5000
May  6 07:31:18 user kernel: [    0.000000] Zone PFN ranges:
May  6 07:31:18 user kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
May  6 07:31:18 user kernel: [    0.000000]   Normal   0x00001000 -> 0x0002fff0
May  6 07:31:18 user kernel: [    0.000000]   HighMem  0x0002fff0 -> 0x0002fff0
May  6 07:31:18 user kernel: [    0.000000] Movable zone start PFN for each node
May  6 07:31:18 user kernel: [    0.000000] early_node_map[2] active PFN ranges
May  6 07:31:18 user kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
May  6 07:31:18 user kernel: [    0.000000]     0: 0x00000100 -> 0x0002fff0
May  6 07:31:18 user kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
May  6 07:31:18 user kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
May  6 07:31:18 user kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
May  6 07:31:18 user kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  6 07:31:18 user kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
May  6 07:31:18 user kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  6 07:31:18 user kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
May  6 07:31:18 user kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  6 07:31:18 user kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
May  6 07:31:18 user kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  6 07:31:18 user kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  6 07:31:18 user kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  6 07:31:18 user kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
May  6 07:31:18 user kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May  6 07:31:18 user kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
May  6 07:31:18 user kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
May  6 07:31:18 user kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
May  6 07:31:18 user kernel: [    0.000000] PERCPU: Allocating 45852 bytes of per cpu data
May  6 07:31:18 user kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194767
May  6 07:31:18 user kernel: [    0.000000] Kernel command line: root=UUID=3a16f219-3073-4cf3-8fa0-646d16cda612 ro quiet splash 
May  6 07:31:18 user kernel: [    0.000000] Enabling fast FPU save and restore... done.
May  6 07:31:18 user kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May  6 07:31:18 user kernel: [    0.000000] Initializing CPU#0
May  6 07:31:18 user kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
May  6 07:31:18 user kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
May  6 07:31:18 user kernel: [    0.000000] TSC: using PIT calibration value
May  6 07:31:18 user kernel: [    0.000000] Detected 1994.814 MHz processor.
May  6 07:31:18 user kernel: [    0.010000] Console: colour VGA+ 80x25
May  6 07:31:18 user kernel: [    0.010000] console [tty0] enabled
May  6 07:31:18 user kernel: [    0.010000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  6 07:31:18 user kernel: [    0.010000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  6 07:31:18 user kernel: [    0.010000] Memory: 765068k/786368k available (2628k kernel code, 20728k reserved, 1201k data, 436k init, 0k highmem)
May  6 07:31:18 user kernel: [    0.010000] virtual kernel memory layout:
May  6 07:31:18 user kernel: [    0.010000]     fixmap  : 0xffc78000 - 0xfffff000   (3612 kB)
May  6 07:31:18 user kernel: [    0.010000]     pkmap   : 0xff800000 - 0xffa00000   (2048 kB)
May  6 07:31:18 user kernel: [    0.010000]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
May  6 07:31:18 user kernel: [    0.010000]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
May  6 07:31:18 user kernel: [    0.010000]       .init : 0xc04c3000 - 0xc0530000   ( 436 kB)
May  6 07:31:18 user kernel: [    0.010000]       .data : 0xc0391036 - 0xc04bd800   (1201 kB)
May  6 07:31:18 user kernel: [    0.010000]       .text : 0xc0100000 - 0xc0391036   (2628 kB)
May  6 07:31:18 user kernel: [    0.010000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
May  6 07:31:18 user kernel: [    0.010000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
May  6 07:31:18 user kernel: [    0.010008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.62 BogoMIPS (lpj=19948140)
May  6 07:31:18 user kernel: [    0.010026] Security Framework initialized
May  6 07:31:18 user kernel: [    0.010033] SELinux:  Disabled at boot.
May  6 07:31:18 user kernel: [    0.010053] AppArmor: AppArmor initialized
May  6 07:31:18 user kernel: [    0.010061] Mount-cache hash table entries: 512
May  6 07:31:18 user kernel: [    0.010209] Initializing cgroup subsys ns
May  6 07:31:18 user kernel: [    0.010213] Initializing cgroup subsys cpuacct
May  6 07:31:18 user kernel: [    0.010215] Initializing cgroup subsys memory
May  6 07:31:18 user kernel: [    0.010229] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May  6 07:31:18 user kernel: [    0.010232] CPU: L2 Cache: 512K (64 bytes/line)
May  6 07:31:18 user kernel: [    0.010241] Checking 'hlt' instruction... OK.
May  6 07:31:18 user kernel: [    0.050367] SMP alternatives: switching to UP code
May  6 07:31:18 user kernel: [    0.056453] Freeing SMP alternatives: 11k freed
May  6 07:31:18 user kernel: [    0.056457] ACPI: Core revision 20080609
May  6 07:31:18 user kernel: [    0.057953] ACPI: Checking initramfs for custom DSDT
May  6 07:31:18 user kernel: [    0.371035] ENABLING IO-APIC IRQs
May  6 07:31:18 user kernel: [    0.371201] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
May  6 07:31:18 user kernel: [    0.471212] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 08
May  6 07:31:18 user kernel: [    0.480000] Brought up 1 CPUs
May  6 07:31:18 user kernel: [    0.480000] Total of 1 processors activated (3989.62 BogoMIPS).
May  6 07:31:18 user kernel: [    0.480000] net_namespace: 840 bytes
May  6 07:31:18 user kernel: [    0.480000] Booting paravirtualized kernel on bare hardware
May  6 07:31:18 user kernel: [    0.480000] Time:  7:30:59  Date: 05/06/09
May  6 07:31:18 user kernel: [    0.480000] NET: Registered protocol family 16
May  6 07:31:18 user kernel: [    0.480000] EISA bus registered
May  6 07:31:18 user kernel: [    0.480000] ACPI: bus type pci registered
May  6 07:31:18 user kernel: [    0.500539] PCI: PCI BIOS revision 2.10 entry at 0xfac80, last bus=2
May  6 07:31:18 user kernel: [    0.500542] PCI: Using configuration type 1 for base access
May  6 07:31:18 user kernel: [    0.509549] ACPI: Interpreter enabled
May  6 07:31:18 user kernel: [    0.509553] ACPI: (supports S0 S3 S4 S5)
May  6 07:31:18 user kernel: [    0.509567] ACPI: Using IOAPIC for interrupt routing
May  6 07:31:18 user kernel: [    0.520234] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  6 07:31:18 user kernel: [    0.520395] pci 0000:00:01.1: PME# supported from D3hot D3cold
May  6 07:31:18 user kernel: [    0.520398] pci 0000:00:01.1: PME# disabled
May  6 07:31:18 user kernel: [    0.520437] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520440] pci 0000:00:02.0: PME# disabled
May  6 07:31:18 user kernel: [    0.520475] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520478] pci 0000:00:02.1: PME# disabled
May  6 07:31:18 user kernel: [    0.520519] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520522] pci 0000:00:02.2: PME# disabled
May  6 07:31:18 user kernel: [    0.520744] pci 0000:01:06.0: PME# supported from D0 D2 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520748] pci 0000:01:06.0: PME# disabled
May  6 07:31:18 user kernel: [    0.520798] pci 0000:01:07.0: PME# supported from D0 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520802] pci 0000:01:07.0: PME# disabled
May  6 07:31:18 user kernel: [    0.520849] pci 0000:01:08.0: PME# supported from D3hot D3cold
May  6 07:31:18 user kernel: [    0.520852] pci 0000:01:08.0: PME# disabled
May  6 07:31:18 user kernel: [    0.520905] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520908] pci 0000:01:09.0: PME# disabled
May  6 07:31:18 user kernel: [    0.520965] pci 0000:01:0b.0: PME# supported from D1 D2 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520968] pci 0000:01:0b.0: PME# disabled
May  6 07:31:18 user kernel: [    0.575515] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May  6 07:31:18 user kernel: [    0.575698] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  6 07:31:18 user kernel: [    0.575878] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  6 07:31:18 user kernel: [    0.576057] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  6 07:31:18 user kernel: [    0.576237] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May  6 07:31:18 user kernel: [    0.576416] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  6 07:31:18 user kernel: [    0.576596] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  6 07:31:18 user kernel: [    0.576775] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.576959] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.577140] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  6 07:31:18 user kernel: [    0.577318] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.577499] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  6 07:31:18 user kernel: [    0.577682] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  6 07:31:18 user kernel: [    0.577862] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.578041] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.578220] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.578408] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.578556] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
May  6 07:31:18 user kernel: [    0.578697] ACPI: PCI Interrupt Link [APC2] (IRQs *17)
May  6 07:31:18 user kernel: [    0.578836] ACPI: PCI Interrupt Link [APC3] (IRQs *18)
May  6 07:31:18 user kernel: [    0.578975] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
May  6 07:31:18 user kernel: [    0.579114] ACPI: PCI Interrupt Link [APC5] (IRQs *16)
May  6 07:31:18 user kernel: [    0.579317] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
May  6 07:31:18 user kernel: [    0.579519] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
May  6 07:31:18 user kernel: [    0.579719] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.579920] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.580144] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
May  6 07:31:18 user kernel: [    0.580343] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.580484] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
May  6 07:31:18 user kernel: [    0.580682] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
May  6 07:31:18 user kernel: [    0.580882] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.581082] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.581282] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.581490] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.581631] ACPI: Power Resource [ISAV] (on)
May  6 07:31:18 user kernel: [    0.581715] Linux Plug and Play Support v0.97 (c) Adam Belay
May  6 07:31:18 user kernel: [    0.581750] pnp: PnP ACPI init
May  6 07:31:18 user kernel: [    0.581757] ACPI: bus type pnp registered
May  6 07:31:18 user kernel: [    0.587845] pnp: PnP ACPI: found 15 devices
May  6 07:31:18 user kernel: [    0.587847] ACPI: ACPI bus type pnp unregistered
May  6 07:31:18 user kernel: [    0.587851] PnPBIOS: Disabled by ACPI PNP
May  6 07:31:18 user kernel: [    0.588179] PCI: Using ACPI for IRQ routing
May  6 07:31:18 user kernel: [    0.588296] NET: Registered protocol family 8
May  6 07:31:18 user kernel: [    0.588296] NET: Registered protocol family 20
May  6 07:31:18 user kernel: [    0.588296] NetLabel: Initializing
May  6 07:31:18 user kernel: [    0.588296] NetLabel:  domain hash size = 128
May  6 07:31:18 user kernel: [    0.588296] NetLabel:  protocols = UNLABELED CIPSOv4
May  6 07:31:18 user kernel: [    0.588296] NetLabel:  unlabeled traffic allowed by default
May  6 07:31:18 user kernel: [    0.588296] tracer: 772 pages allocated for 65536 entries of 48 bytes
May  6 07:31:18 user kernel: [    0.588296]    actual entries 65620
May  6 07:31:18 user kernel: [    0.588296] AppArmor: AppArmor Filesystem Enabled
May  6 07:31:18 user kernel: [    0.588296] ACPI: RTC can wake from S4
May  6 07:31:18 user kernel: [    0.588296] system 00:00: ioport range 0x1000-0x107f has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:00: ioport range 0x1080-0x10ff has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:00: ioport range 0x1400-0x147f has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:00: ioport range 0x1480-0x14ff has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:00: ioport range 0x1800-0x187f has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:00: ioport range 0x1880-0x18ff has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xd8800-0xdbfff has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xf0000-0xf7fff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xf8000-0xfbfff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xfc000-0xfffff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0x2fff0000-0x2fffffff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xffff0000-0xffffffff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0x0-0x9ffff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0x100000-0x2ffeffff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:03: ioport range 0x800-0x805 has been reserved
May  6 07:31:18 user kernel: [    0.624054] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:01
May  6 07:31:18 user kernel: [    0.624057] pci 0000:00:0a.0:   IO window: 0x9000-0xbfff
May  6 07:31:18 user kernel: [    0.624061] pci 0000:00:0a.0:   MEM window: 0xe2000000-0xe3ffffff
May  6 07:31:18 user kernel: [    0.624065] pci 0000:00:0a.0:   PREFETCH window: 0x00000040000000-0x000000400fffff
May  6 07:31:18 user kernel: [    0.624071] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
May  6 07:31:18 user kernel: [    0.624074] pci 0000:00:0b.0:   IO window: 0xc000-0xcfff
May  6 07:31:18 user kernel: [    0.624078] pci 0000:00:0b.0:   MEM window: 0xe0000000-0xe1ffffff
May  6 07:31:18 user kernel: [    0.624083] pci 0000:00:0b.0:   PREFETCH window: 0x000000d8000000-0x000000dfffffff
May  6 07:31:18 user kernel: [    0.624101] bus: 00 index 0 io port: [0, ffff]
May  6 07:31:18 user kernel: [    0.624103] bus: 00 index 1 mmio: [0, ffffffffffffffff]
May  6 07:31:18 user kernel: [    0.624105] bus: 01 index 0 io port: [9000, bfff]
May  6 07:31:18 user kernel: [    0.624108] bus: 01 index 1 mmio: [e2000000, e3ffffff]
May  6 07:31:18 user kernel: [    0.624110] bus: 01 index 2 mmio: [40000000, 400fffff]
May  6 07:31:18 user kernel: [    0.624112] bus: 01 index 3 mmio: [0, 0]
May  6 07:31:18 user kernel: [    0.624114] bus: 02 index 0 io port: [c000, cfff]
May  6 07:31:18 user kernel: [    0.624117] bus: 02 index 1 mmio: [e0000000, e1ffffff]
May  6 07:31:18 user kernel: [    0.624119] bus: 02 index 2 mmio: [d8000000, dfffffff]
May  6 07:31:18 user kernel: [    0.624121] bus: 02 index 3 mmio: [0, 0]
May  6 07:31:18 user kernel: [    0.624132] NET: Registered protocol family 2
May  6 07:31:18 user kernel: [    0.624256] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May  6 07:31:18 user kernel: [    0.624578] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May  6 07:31:18 user kernel: [    0.625534] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May  6 07:31:18 user kernel: [    0.626054] TCP: Hash tables configured (established 131072 bind 65536)
May  6 07:31:18 user kernel: [    0.626057] TCP reno registered
May  6 07:31:18 user kernel: [    0.626163] NET: Registered protocol family 1
May  6 07:31:18 user kernel: [    0.626282] checking if image is initramfs... it is
May  6 07:31:18 user kernel: [    1.270119] Freeing initrd memory: 7861k freed
May  6 07:31:18 user kernel: [    1.270873] audit: initializing netlink socket (disabled)
May  6 07:31:18 user kernel: [    1.270888] type=2000 audit(1241595059.270:1): initialized
May  6 07:31:18 user kernel: [    1.277060] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May  6 07:31:18 user kernel: [    1.279222] VFS: Disk quotas dquot_6.5.1
May  6 07:31:18 user kernel: [    1.279307] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  6 07:31:18 user kernel: [    1.279403] msgmni has been set to 1510
May  6 07:31:18 user kernel: [    1.279523] io scheduler noop registered
May  6 07:31:18 user kernel: [    1.279526] io scheduler anticipatory registered
May  6 07:31:18 user kernel: [    1.279528] io scheduler deadline registered (default)
May  6 07:31:18 user kernel: [    1.279540] io scheduler cfq registered
May  6 07:31:18 user kernel: [    1.320378] isapnp: Scanning for PnP cards...
May  6 07:31:18 user kernel: [    1.676735] isapnp: No Plug & Play device found
May  6 07:31:18 user kernel: [    1.712895] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
May  6 07:31:18 user kernel: [    1.713012] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  6 07:31:18 user kernel: [    1.713152] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  6 07:31:18 user kernel: [    1.713719] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  6 07:31:18 user kernel: [    1.713991] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  6 07:31:18 user kernel: [    1.714376] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
May  6 07:31:18 user kernel: [    1.714385] serial 0000:01:06.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
May  6 07:31:18 user kernel: [    1.717513] brd: module loaded
May  6 07:31:18 user kernel: [    1.717585] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May  6 07:31:18 user kernel: [    1.717703] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May  6 07:31:18 user kernel: [    1.717706] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May  6 07:31:18 user kernel: [    1.718280] serio: i8042 KBD port at 0x60,0x64 irq 1
May  6 07:31:18 user kernel: [    1.718737] mice: PS/2 mouse device common for all mice
May  6 07:31:18 user kernel: [    1.718869] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
May  6 07:31:18 user kernel: [    1.718891] rtc0: alarms up to one year, y3k
May  6 07:31:18 user kernel: [    1.719007] EISA: Probing bus 0 at eisa.0
May  6 07:31:18 user kernel: [    1.719015] Cannot allocate resource for EISA slot 1
May  6 07:31:18 user kernel: [    1.719018] Cannot allocate resource for EISA slot 2
May  6 07:31:18 user kernel: [    1.719033] EISA: Detected 0 cards.
May  6 07:31:18 user kernel: [    1.719037] cpuidle: using governor ladder
May  6 07:31:18 user kernel: [    1.719039] cpuidle: using governor menu
May  6 07:31:18 user kernel: [    1.719559] TCP cubic registered
May  6 07:31:18 user kernel: [    1.719585] Using IPI No-Shortcut mode
May  6 07:31:18 user kernel: [    1.719774] registered taskstats version 1
May  6 07:31:18 user kernel: [    1.719906]   Magic number: 9:660:520
May  6 07:31:18 user kernel: [    1.720111] rtc_cmos 00:05: setting system clock to 2009-05-06 07:31:00 UTC (1241595060)
May  6 07:31:18 user kernel: [    1.720115] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  6 07:31:18 user kernel: [    1.720117] EDD information not available.
May  6 07:31:18 user kernel: [    1.720443] Freeing unused kernel memory: 436k freed
May  6 07:31:18 user kernel: [    1.720562] Write protecting the kernel text: 2632k
May  6 07:31:18 user kernel: [    1.720610] Write protecting the kernel read-only data: 956k
May  6 07:31:18 user kernel: [    1.741113] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May  6 07:31:18 user kernel: [    1.850418] fuse init (API version 7.9)
May  6 07:31:18 user kernel: [    1.870845] ACPI: processor limited to max C-state 1
May  6 07:31:18 user kernel: [    1.870928] processor ACPI0007:00: registered as cooling_device0
May  6 07:31:18 user kernel: [    2.581254] usbcore: registered new interface driver usbfs
May  6 07:31:18 user kernel: [    2.581279] usbcore: registered new interface driver hub
May  6 07:31:18 user kernel: [    2.581318] usbcore: registered new device driver usb
May  6 07:31:18 user kernel: [    2.592923] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
May  6 07:31:18 user kernel: [    2.592931] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 22 (level, high) -> IRQ 22
May  6 07:31:18 user kernel: [    2.592952] ohci_hcd 0000:00:02.0: OHCI Host Controller
May  6 07:31:18 user kernel: [    2.593001] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
May  6 07:31:18 user kernel: [    2.593023] ohci_hcd 0000:00:02.0: irq 22, io mem 0xe4003000
May  6 07:31:18 user kernel: [    2.608325] No dock devices found.
May  6 07:31:18 user kernel: [    2.652216] usb usb1: configuration #1 chosen from 1 choice
May  6 07:31:18 user kernel: [    2.652247] hub 1-0:1.0: USB hub found
May  6 07:31:18 user kernel: [    2.652259] hub 1-0:1.0: 3 ports detected
May  6 07:31:18 user kernel: [    2.665817] SCSI subsystem initialized
May  6 07:31:18 user kernel: [    2.870661] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
May  6 07:31:18 user kernel: [    2.870671] ohci_hcd 0000:00:02.1: PCI INT B -> Link[APCG] -> GSI 21 (level, high) -> IRQ 21
May  6 07:31:18 user kernel: [    2.870691] ohci_hcd 0000:00:02.1: OHCI Host Controller
May  6 07:31:18 user kernel: [    2.870715] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
May  6 07:31:18 user kernel: [    2.870738] ohci_hcd 0000:00:02.1: irq 21, io mem 0xe4004000
May  6 07:31:18 user kernel: [    2.932222] usb usb2: configuration #1 chosen from 1 choice
May  6 07:31:18 user kernel: [    2.932252] hub 2-0:1.0: USB hub found
May  6 07:31:18 user kernel: [    2.932264] hub 2-0:1.0: 3 ports detected
May  6 07:31:18 user kernel: [    3.040719] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
May  6 07:31:18 user kernel: [    3.040729] ehci_hcd 0000:00:02.2: PCI INT C -> Link[APCL] -> GSI 20 (level, high) -> IRQ 20
May  6 07:31:18 user kernel: [    3.040748] ehci_hcd 0000:00:02.2: EHCI Host Controller
May  6 07:31:18 user kernel: [    3.040774] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
May  6 07:31:18 user kernel: [    3.040800] ehci_hcd 0000:00:02.2: debug port 1
May  6 07:31:18 user kernel: [    3.040819] ehci_hcd 0000:00:02.2: irq 20, io mem 0xe4005000
May  6 07:31:18 user kernel: [    3.050039] usb 1-1: new full speed USB device using ohci_hcd and address 2
May  6 07:31:18 user kernel: [    3.070031] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May  6 07:31:18 user kernel: [    3.070209] usb usb3: configuration #1 chosen from 1 choice
May  6 07:31:18 user kernel: [    3.070240] hub 3-0:1.0: USB hub found
May  6 07:31:18 user kernel: [    3.070250] hub 3-0:1.0: 6 ports detected
May  6 07:31:18 user kernel: [    3.290405] pata_acpi 0000:00:08.0: power state changed by ACPI to D0
May  6 07:31:18 user kernel: [    3.294745] VIA Networking Velocity Family Gigabit Ethernet Adapter Driver Ver. 1.14
May  6 07:31:18 user kernel: [    3.294749] Copyright (c) 2002, 2003 VIA Networking Technologies, Inc.
May  6 07:31:18 user kernel: [    3.294752] Copyright (c) 2004 Red Hat Inc.
May  6 07:31:18 user kernel: [    3.294966] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
May  6 07:31:18 user kernel: [    3.294974] via-velocity 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
May  6 07:31:18 user kernel: [    3.296023] eth1: VIA Networking Velocity Family Gigabit Ethernet Adapter
May  6 07:31:18 user kernel: [    3.296026] eth1: Ethernet Address: 00:A0:C5:30:02:07
May  6 07:31:18 user kernel: [    3.296176] pata_amd 0000:00:08.0: power state changed by ACPI to D0
May  6 07:31:18 user kernel: [    3.296279] scsi0 : pata_amd
May  6 07:31:18 user kernel: [    3.296371] scsi1 : pata_amd
May  6 07:31:18 user kernel: [    3.297216] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
May  6 07:31:18 user kernel: [    3.297220] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
May  6 07:31:18 user kernel: [    3.310126] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
May  6 07:31:18 user kernel: [    3.310339] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
May  6 07:31:18 user kernel: [    3.310348] r8169 0000:01:0b.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
May  6 07:31:18 user kernel: [    3.310668] eth0: RTL8169s at 0xf0856000, 00:0d:61:21:54:d2, XID 00800000 IRQ 19
May  6 07:31:18 user kernel: [    3.314237] sata_sil 0000:01:0d.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
May  6 07:31:18 user kernel: [    3.314251] sata_sil 0000:01:0d.0: Applying R_ERR on DMA activate FIS errata fix
May  6 07:31:18 user kernel: [    3.314327] scsi2 : sata_sil
May  6 07:31:18 user kernel: [    3.314399] scsi3 : sata_sil
May  6 07:31:18 user kernel: [    3.314436] ata3: SATA max UDMA/100 mmio m512@0xe3013000 tf 0xe3013080 irq 17
May  6 07:31:18 user kernel: [    3.314440] ata4: SATA max UDMA/100 mmio m512@0xe3013000 tf 0xe30130c0 irq 17
May  6 07:31:18 user kernel: [    3.530451] ata1.00: ATA-6: ST380011A, 8.01, max UDMA/100
May  6 07:31:18 user kernel: [    3.530456] ata1.00: 156301488 sectors, multi 16: LBA48 
May  6 07:31:18 user kernel: [    3.570379] ata1.00: configured for UDMA/100
May  6 07:31:18 user kernel: [    3.660026] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
May  6 07:31:18 user kernel: [    3.680421] ata3.00: ATA-6: ST3120827AS, 3.42, max UDMA/133
May  6 07:31:18 user kernel: [    3.680424] ata3.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
May  6 07:31:18 user kernel: [    3.720423] ata3.00: configured for UDMA/100
May  6 07:31:18 user kernel: [    3.760290] ata2.01: ATAPI: _NEC DVD_RW ND-1300A, 1.08, max UDMA/33
May  6 07:31:18 user kernel: [    3.800247] ata2.01: configured for UDMA/33
May  6 07:31:18 user kernel: [    3.800348] scsi 0:0:0:0: Direct-Access     ATA      ST380011A        8.01 PQ: 0 ANSI: 5
May  6 07:31:18 user kernel: [    3.803437] scsi 1:0:1:0: CD-ROM            _NEC     DVD_RW ND-1300A  1.08 PQ: 0 ANSI: 5
May  6 07:31:18 user kernel: [    4.070022] ata4: SATA link down (SStatus 0 SControl 310)
May  6 07:31:18 user kernel: [    4.070120] scsi 2:0:0:0: Direct-Access     ATA      ST3120827AS      3.42 PQ: 0 ANSI: 5
May  6 07:31:18 user kernel: [    4.079705] scsi 0:0:0:0: Attached scsi generic sg0 type 0
May  6 07:31:18 user kernel: [    4.079744] scsi 1:0:1:0: Attached scsi generic sg1 type 5
May  6 07:31:18 user kernel: [    4.079781] scsi 2:0:0:0: Attached scsi generic sg2 type 0
May  6 07:31:18 user kernel: [    4.108197] Driver 'sd' needs updating - please use bus_type methods
May  6 07:31:18 user kernel: [    4.108314] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
May  6 07:31:18 user kernel: [    4.108331] sd 0:0:0:0: [sda] Write Protect is off
May  6 07:31:18 user kernel: [    4.108361] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  6 07:31:18 user kernel: [    4.108426] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
May  6 07:31:18 user kernel: [    4.108441] sd 0:0:0:0: [sda] Write Protect is off
May  6 07:31:18 user kernel: [    4.108468] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  6 07:31:18 user kernel: [    4.108473]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
May  6 07:31:18 user kernel: [    4.126314]  sda1 < sda5 sda6 >
May  6 07:31:18 user kernel: [    4.134470] sd 0:0:0:0: [sda] Attached SCSI disk
May  6 07:31:18 user kernel: [    4.134559] sd 2:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
May  6 07:31:18 user kernel: [    4.134579] sd 2:0:0:0: [sdb] Write Protect is off
May  6 07:31:18 user kernel: [    4.134612] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  6 07:31:18 user kernel: [    4.134676] sd 2:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
May  6 07:31:18 user kernel: [    4.134692] sd 2:0:0:0: [sdb] Write Protect is off
May  6 07:31:18 user kernel: [    4.134722] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  6 07:31:18 user kernel: [    4.134727]  sdb:sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
May  6 07:31:18 user kernel: [    4.138985] Uniform CD-ROM driver Revision: 3.20
May  6 07:31:18 user kernel: [    4.148666]  sdb1 sdb2 < sdb5 sdb6 sdb7 >
May  6 07:31:18 user kernel: [    4.181765] sd 2:0:0:0: [sdb] Attached SCSI disk
May  6 07:31:18 user kernel: [    4.260027] usb 1-1: new full speed USB device using ohci_hcd and address 3
May  6 07:31:18 user kernel: [    4.486225] usb 1-1: configuration #1 chosen from 1 choice
May  6 07:31:18 user kernel: [    4.656171] PM: Starting manual resume from disk
May  6 07:31:18 user kernel: [    4.700618] kjournald starting.  Commit interval 5 seconds
May  6 07:31:18 user kernel: [    4.700635] EXT3-fs: mounted filesystem with ordered data mode.
May  6 07:31:18 user kernel: [    4.830025] usb 1-2: new full speed USB device using ohci_hcd and address 4
May  6 07:31:18 user kernel: [    5.053142] usb 1-2: configuration #1 chosen from 1 choice
May  6 07:31:18 user kernel: [    5.390028] usb 1-3: new low speed USB device using ohci_hcd and address 5
May  6 07:31:18 user kernel: [    5.616253] usb 1-3: configuration #1 chosen from 1 choice
May  6 07:31:18 user kernel: [    7.239717] udevd version 124 started
May  6 07:31:18 user kernel: [    8.111333] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  6 07:31:18 user kernel: [    8.157204] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  6 07:31:18 user kernel: [    8.304915] Linux agpgart interface v0.103
May  6 07:31:18 user kernel: [    8.317468] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
May  6 07:31:18 user kernel: [    8.317486] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2000
May  6 07:31:18 user kernel: [    8.327395] input: PC Speaker as /devices/platform/pcspkr/input/input2
May  6 07:31:18 user kernel: [    8.335038] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
May  6 07:31:18 user kernel: [    8.335070] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
May  6 07:31:18 user kernel: [    8.338907] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
May  6 07:31:18 user kernel: [    8.438016] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
May  6 07:31:18 user kernel: [    8.438023] Intel ICH 0000:00:06.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, high) -> IRQ 22
May  6 07:31:18 user kernel: [    8.488493] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
May  6 07:31:18 user kernel: [    8.520047] ACPI: Power Button (FF) [PWRF]
May  6 07:31:18 user kernel: [    8.520139] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
May  6 07:31:18 user kernel: [    8.560041] ACPI: Power Button (CM) [PWRB]
May  6 07:31:18 user kernel: [    8.780029] intel8x0_measure_ac97_clock: measured 59805 usecs
May  6 07:31:18 user kernel: [    8.780033] intel8x0: clocking to 48000
May  6 07:31:18 user kernel: [    8.855171] ieee80211: 802.11 data/management/control stack, git-1.1.13
May  6 07:31:18 user kernel: [    8.855176] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
May  6 07:31:18 user kernel: [    8.933048] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
May  6 07:31:18 user kernel: [    8.933052] ipw2200: Copyright(c) 2003-2006 Intel Corporation
May  6 07:31:18 user kernel: [    8.933150] ipw2200 0000:01:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
May  6 07:31:18 user kernel: [    8.933203] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
May  6 07:31:18 user kernel: [    8.933252] firmware: requesting ipw2200-bss.fw
May  6 07:31:18 user kernel: [    9.327847] parport_pc 00:0b: reported by Plug and Play ACPI
May  6 07:31:18 user kernel: [    9.327890] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
May  6 07:31:18 user kernel: [   11.000747] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
May  6 07:31:18 user kernel: [   11.007227] usbcore: registered new interface driver cdc_acm
May  6 07:31:18 user kernel: [   11.007233] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
May  6 07:31:18 user kernel: [   11.298526] usbcore: registered new interface driver snd-usb-audio
May  6 07:31:18 user kernel: [   11.298560] usbcore: registered new interface driver hiddev
May  6 07:31:18 user kernel: [   11.307296] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.3/input/input5
May  6 07:31:18 user kernel: [   11.370314] input,hidraw0: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:02.0-2
May  6 07:31:18 user kernel: [   11.376546] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.0/input/input6
May  6 07:31:18 user kernel: [   11.430213] input,hidraw1: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:02.0-3
May  6 07:31:18 user kernel: [   11.430238] usbcore: registered new interface driver usbhid
May  6 07:31:18 user kernel: [   11.430242] usbhid: v2.6:USB HID core driver
May  6 07:31:18 user kernel: [   12.797095] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
May  6 07:31:18 user kernel: [   13.857192] loop: module loaded
May  6 07:31:18 user kernel: [   13.871212] lp0: using parport0 (interrupt-driven).
May  6 07:31:18 user kernel: [   14.388910] Adding 248936k swap on /dev/sda5.  Priority:-1 extents:1 across:248936k
May  6 07:31:18 user kernel: [   14.739745] EXT3 FS on sda6, internal journal
May  6 07:31:18 user kernel: [   15.902949] ip_tables: (C) 2000-2006 Netfilter Core Team
May  6 07:31:18 user kernel: [   15.953923] r8169: eth0: link up
May  6 07:31:18 user kernel: [   17.294069] NET: Registered protocol family 17
May  6 07:31:18 user kernel: [   17.450890] Velocity is AUTO mode
May  6 07:31:18 user kernel: [   17.895533] NET: Registered protocol family 10
May  6 07:31:18 user kernel: [   17.896024] lo: Disabled Privacy Extensions
May  6 07:31:18 user kernel: [   17.896579] ADDRCONF(NETDEV_UP): eth1: link is not ready
May  6 07:31:18 user kernel: [   18.986603] eth1: Link auto-negotiation speed 100M bps full duplex
May  6 07:31:18 user kernel: [   18.988185] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
May  6 07:31:21 user kernel: [   21.857128] warning: `dhcpd3' uses 32-bit capabilities (legacy support in use)
May  6 07:31:21 user dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  6 07:31:21 user dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  6 07:31:21 user dhcpd: All rights reserved.
May  6 07:31:21 user dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  6 07:31:21 user dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  6 07:31:21 user dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  6 07:31:21 user dhcpd: All rights reserved.
May  6 07:31:21 user dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  6 07:31:21 user dhcpd: Wrote 3 leases to leases file.
May  6 07:31:46 user kernel: [   47.371589] usb 1-1: USB disconnect, address 3
May  6 07:31:50 user kernel: [   51.300012] usb 3-1: new high speed USB device using ehci_hcd and address 5
May  6 07:31:50 user kernel: [   51.452627] usb 3-1: configuration #1 chosen from 1 choice
May  6 07:31:50 user kernel: [   51.536840] usbcore: registered new interface driver libusual
May  6 07:31:50 user kernel: [   51.552255] Initializing USB Mass Storage driver...
May  6 07:31:50 user kernel: [   51.552359] scsi4 : SCSI emulation for USB Mass Storage devices
May  6 07:31:50 user kernel: [   51.552456] usbcore: registered new interface driver usb-storage
May  6 07:31:50 user kernel: [   51.552460] USB Mass Storage support registered.
May  6 07:31:55 user kernel: [   56.551354] scsi 4:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  0.00 PQ: 0 ANSI: 2
May  6 07:31:55 user kernel: [   56.556767] sd 4:0:0:0: [sdc] 31588351 512-byte hardware sectors (16173 MB)
May  6 07:31:55 user kernel: [   56.557464] sd 4:0:0:0: [sdc] Write Protect is off
May  6 07:31:55 user kernel: [   56.560343] sd 4:0:0:0: [sdc] 31588351 512-byte hardware sectors (16173 MB)
May  6 07:31:55 user kernel: [   56.561091] sd 4:0:0:0: [sdc] Write Protect is off
May  6 07:31:55 user kernel: [   56.561154]  sdc: sdc1
May  6 07:31:55 user kernel: [   56.624236] sd 4:0:0:0: [sdc] Attached SCSI removable disk
May  6 07:31:55 user kernel: [   56.624365] sd 4:0:0:0: Attached scsi generic sg3 type 0
May  6 07:39:16 user kernel: [  497.706084] eth1: failed to detect cable link
May  6 07:39:20 user kernel: [  501.233869] eth1: Link auto-negotiation speed 100M bps full duplex
May  6 07:39:51 user dhcpd: DHCPDISCOVER from 00:00:e2:50:19:15 (noobook) via eth1
May  6 07:39:52 user dhcpd: DHCPOFFER on 10.0.0.103 to 00:00:e2:50:19:15 (noobook) via eth1
May  6 07:39:52 user dhcpd: DHCPREQUEST for 10.0.0.103 (10.0.0.1) from 00:00:e2:50:19:15 (noobook) via eth1
May  6 07:39:52 user dhcpd: DHCPACK on 10.0.0.103 to 00:00:e2:50:19:15 (noobook) via eth1
```

---

### Post by Romala on 2009-05-06
*syslog*

```
May  5 07:29:44 user syslogd 1.5.0#2ubuntu6: restart.
May  5 07:29:44 user kernel: Inspecting /boot/System.map-2.6.27-7-server
May  5 07:29:44 user kernel: Cannot find map file.
May  5 07:29:44 user kernel: Loaded 48877 symbols from 70 modules.
May  5 07:29:44 user kernel: [    0.000000] Initializing cgroup subsys cpuset
May  5 07:29:44 user kernel: [    0.000000] Initializing cgroup subsys cpu
May  5 07:29:44 user kernel: [    0.000000] Linux version 2.6.27-7-server (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 20:18:35 UTC 2008 (Ubuntu 2.6.27-7.16-server)
May  5 07:29:44 user kernel: [    0.000000] BIOS-provided physical RAM map:
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
May  5 07:29:44 user kernel: [    0.000000] last_pfn = 0x2fff0 max_arch_pfn = 0x1000000
May  5 07:29:44 user kernel: [    0.000000] kernel direct mapping tables up to 2fff0000 @ 7000-d000
May  5 07:29:44 user kernel: [    0.000000] NX (Execute Disable) protection: active
May  5 07:29:44 user kernel: [    0.000000] RAMDISK: 2f832000 - 2ffdf6b8
May  5 07:29:44 user kernel: [    0.000000] DMI 2.3 present.
May  5 07:29:44 user kernel: [    0.000000] ACPI: RSDP 000F6AB0, 0014 (r0 Nvidia)
May  5 07:29:44 user kernel: [    0.000000] ACPI: RSDT 2FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  5 07:29:44 user kernel: [    0.000000] ACPI: FACP 2FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  5 07:29:44 user kernel: [    0.000000] ACPI: DSDT 2FFF30C0, 4ABF (r1 NVIDIA AWRDACPI     1000 MSFT  100000C)
May  5 07:29:44 user kernel: [    0.000000] ACPI: FACS 2FFF0000, 0040
May  5 07:29:44 user kernel: [    0.000000] ACPI: APIC 2FFF7B80, 005A (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  5 07:29:44 user kernel: [    0.000000] 0MB HIGHMEM available.
May  5 07:29:44 user kernel: [    0.000000] 767MB LOWMEM available.
May  5 07:29:44 user kernel: [    0.000000]   mapped low ram: 0 - 2fff0000
May  5 07:29:44 user kernel: [    0.000000]   low ram: 00000000 - 2fff0000
May  5 07:29:44 user kernel: [    0.000000]   bootmap 0000a000 - 00010000
May  5 07:29:44 user kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002fff0000]
May  5 07:29:44 user kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
May  5 07:29:44 user kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
May  5 07:29:44 user kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
May  5 07:29:44 user kernel: [    0.000000]   #3 [0000100000 - 00005e8220]    TEXT DATA BSS ==> [0000100000 - 00005e8220]
May  5 07:29:44 user kernel: [    0.000000]   #4 [002f832000 - 002ffdf6b8]          RAMDISK ==> [002f832000 - 002ffdf6b8]
May  5 07:29:44 user kernel: [    0.000000]   #5 [00005e9000 - 00005f1000]    INIT_PG_TABLE ==> [00005e9000 - 00005f1000]
May  5 07:29:44 user kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
May  5 07:29:44 user kernel: [    0.000000]   #7 [0000007000 - 000000a000]          PGTABLE ==> [0000007000 - 000000a000]
May  5 07:29:44 user kernel: [    0.000000]   #8 [000000a000 - 0000010000]          BOOTMAP ==> [000000a000 - 0000010000]
May  5 07:29:44 user kernel: [    0.000000] found SMP MP-table at [c00f5000] 000f5000
May  5 07:29:44 user kernel: [    0.000000] Zone PFN ranges:
May  5 07:29:44 user kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
May  5 07:29:44 user kernel: [    0.000000]   Normal   0x00001000 -> 0x0002fff0
May  5 07:29:44 user kernel: [    0.000000]   HighMem  0x0002fff0 -> 0x0002fff0
May  5 07:29:44 user kernel: [    0.000000] Movable zone start PFN for each node
May  5 07:29:44 user kernel: [    0.000000] early_node_map[2] active PFN ranges
May  5 07:29:44 user kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
May  5 07:29:44 user kernel: [    0.000000]     0: 0x00000100 -> 0x0002fff0
May  5 07:29:44 user kernel: [    0.000000] On node 0 totalpages: 196495
May  5 07:29:44 user kernel: [    0.000000] free_area_init_node: node 0, pgdat c049eb00, node_mem_map c1000000
May  5 07:29:44 user kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
May  5 07:29:44 user kernel: [    0.000000]   Normal zone: 190804 pages, LIFO batch:31
May  5 07:29:44 user kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
May  5 07:29:44 user kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
May  5 07:29:44 user kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
May  5 07:29:44 user kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  5 07:29:44 user kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  5 07:29:44 user kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
May  5 07:29:44 user kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  5 07:29:44 user kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
May  5 07:29:44 user kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  5 07:29:44 user kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
May  5 07:29:44 user kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  5 07:29:44 user kernel: [    0.000000] ACPI: IRQ9 used by override.
May  5 07:29:44 user kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  5 07:29:44 user kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  5 07:29:44 user kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
May  5 07:29:44 user kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
May  5 07:29:44 user kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
May  5 07:29:44 user kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May  5 07:29:44 user kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
May  5 07:29:44 user kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
May  5 07:29:44 user kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
May  5 07:29:44 user kernel: [    0.000000] PERCPU: Allocating 45852 bytes of per cpu data
May  5 07:29:44 user kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
May  5 07:29:44 user kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194767
May  5 07:29:44 user kernel: [    0.000000] Kernel command line: root=UUID=3a16f219-3073-4cf3-8fa0-646d16cda612 ro quiet splash 
May  5 07:29:44 user kernel: [    0.000000] Enabling fast FPU save and restore... done.
May  5 07:29:44 user kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May  5 07:29:44 user kernel: [    0.000000] Initializing CPU#0
May  5 07:29:44 user kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
May  5 07:29:44 user kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
May  5 07:29:44 user kernel: [    0.000000] TSC: using PIT calibration value
May  5 07:29:44 user kernel: [    0.000000] Detected 1994.824 MHz processor.
May  5 07:29:44 user kernel: [    0.010000] spurious 8259A interrupt: IRQ7.
May  5 07:29:44 user kernel: [    0.010000] Console: colour VGA+ 80x25
May  5 07:29:44 user kernel: [    0.010000] console [tty0] enabled
May  5 07:29:44 user kernel: [    0.010000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  5 07:29:44 user kernel: [    0.010000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  5 07:29:44 user kernel: [    0.010000] Memory: 765068k/786368k available (2628k kernel code, 20728k reserved, 1201k data, 436k init, 0k highmem)
May  5 07:29:44 user kernel: [    0.010000] virtual kernel memory layout:
May  5 07:29:44 user kernel: [    0.010000]     fixmap  : 0xffc78000 - 0xfffff000   (3612 kB)
May  5 07:29:44 user kernel: [    0.010000]     pkmap   : 0xff800000 - 0xffa00000   (2048 kB)
May  5 07:29:44 user kernel: [    0.010000]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
May  5 07:29:44 user kernel: [    0.010000]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
May  5 07:29:44 user kernel: [    0.010000]       .init : 0xc04c3000 - 0xc0530000   ( 436 kB)
May  5 07:29:44 user kernel: [    0.010000]       .data : 0xc0391036 - 0xc04bd800   (1201 kB)
May  5 07:29:44 user kernel: [    0.010000]       .text : 0xc0100000 - 0xc0391036   (2628 kB)
May  5 07:29:44 user kernel: [    0.010000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
May  5 07:29:44 user kernel: [    0.010000] CPA: page pool initialized 1 of 1 pages preallocated
May  5 07:29:44 user kernel: [    0.010000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
May  5 07:29:44 user kernel: [    0.010008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.64 BogoMIPS (lpj=19948240)
May  5 07:29:44 user kernel: [    0.010026] Security Framework initialized
May  5 07:29:44 user kernel: [    0.010033] SELinux:  Disabled at boot.
May  5 07:29:44 user kernel: [    0.010053] AppArmor: AppArmor initialized
May  5 07:29:44 user kernel: [    0.010061] Mount-cache hash table entries: 512
May  5 07:29:44 user kernel: [    0.010209] Initializing cgroup subsys ns
May  5 07:29:44 user kernel: [    0.010213] Initializing cgroup subsys cpuacct
May  5 07:29:44 user kernel: [    0.010215] Initializing cgroup subsys memory
May  5 07:29:44 user kernel: [    0.010229] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May  5 07:29:44 user kernel: [    0.010231] CPU: L2 Cache: 512K (64 bytes/line)
May  5 07:29:44 user kernel: [    0.010241] Checking 'hlt' instruction... OK.
May  5 07:29:44 user kernel: [    0.050367] SMP alternatives: switching to UP code
May  5 07:29:44 user kernel: [    0.056453] Freeing SMP alternatives: 11k freed
May  5 07:29:44 user kernel: [    0.056457] ACPI: Core revision 20080609
May  5 07:29:44 user kernel: [    0.057953] ACPI: Checking initramfs for custom DSDT
May  5 07:29:44 user kernel: [    0.371036] ENABLING IO-APIC IRQs
May  5 07:29:44 user kernel: [    0.371202] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
May  5 07:29:44 user kernel: [    0.471213] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 08
May  5 07:29:44 user kernel: [    0.480000] Brought up 1 CPUs
May  5 07:29:44 user kernel: [    0.480000] Total of 1 processors activated (3989.64 BogoMIPS).
May  5 07:29:44 user kernel: [    0.480000] CPU0 attaching sched-domain:
May  5 07:29:44 user kernel: [    0.480000]  domain 0: span 0 level CPU
May  5 07:29:44 user kernel: [    0.480000]   groups: 0
May  5 07:29:44 user kernel: [    0.480000] net_namespace: 840 bytes
May  5 07:29:44 user kernel: [    0.480000] Booting paravirtualized kernel on bare hardware
May  5 07:29:44 user kernel: [    0.480000] Time:  7:29:23  Date: 05/05/09
May  5 07:29:44 user kernel: [    0.480000] NET: Registered protocol family 16
May  5 07:29:44 user kernel: [    0.480000] EISA bus registered
May  5 07:29:44 user kernel: [    0.480000] ACPI: bus type pci registered
May  5 07:29:44 user kernel: [    0.500543] PCI: PCI BIOS revision 2.10 entry at 0xfac80, last bus=2
May  5 07:29:44 user kernel: [    0.500546] PCI: Using configuration type 1 for base access
May  5 07:29:44 user kernel: [    0.502222] ACPI: EC: Look up EC in DSDT
May  5 07:29:44 user kernel: [    0.509553] ACPI: Interpreter enabled
May  5 07:29:44 user kernel: [    0.509556] ACPI: (supports S0 S3 S4 S5)
May  5 07:29:44 user kernel: [    0.509570] ACPI: Using IOAPIC for interrupt routing
May  5 07:29:44 user kernel: [    0.520234] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  5 07:29:44 user kernel: [    0.520312] PCI: 0000:00:00.0 reg 10 32bit mmio: [d0000000, d7ffffff]
May  5 07:29:44 user kernel: [    0.520381] PCI: 0000:00:01.1 reg 20 io port: [1c00, 1c3f]
May  5 07:29:44 user kernel: [    0.520385] PCI: 0000:00:01.1 reg 24 io port: [2000, 203f]
May  5 07:29:44 user kernel: [    0.520395] pci 0000:00:01.1: PME# supported from D3hot D3cold
May  5 07:29:44 user kernel: [    0.520399] pci 0000:00:01.1: PME# disabled
May  5 07:29:44 user kernel: [    0.520416] PCI: 0000:00:02.0 reg 10 32bit mmio: [e4003000, e4003fff]
May  5 07:29:44 user kernel: [    0.520434] pci 0000:00:02.0: supports D1
May  5 07:29:44 user kernel: [    0.520435] pci 0000:00:02.0: supports D2
May  5 07:29:44 user kernel: [    0.520437] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520441] pci 0000:00:02.0: PME# disabled
May  5 07:29:44 user kernel: [    0.520455] PCI: 0000:00:02.1 reg 10 32bit mmio: [e4004000, e4004fff]
May  5 07:29:44 user kernel: [    0.520472] pci 0000:00:02.1: supports D1
May  5 07:29:44 user kernel: [    0.520473] pci 0000:00:02.1: supports D2
May  5 07:29:44 user kernel: [    0.520475] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520479] pci 0000:00:02.1: PME# disabled
May  5 07:29:44 user kernel: [    0.520496] PCI: 0000:00:02.2 reg 10 32bit mmio: [e4005000, e40050ff]
May  5 07:29:44 user kernel: [    0.520515] pci 0000:00:02.2: supports D1
May  5 07:29:44 user kernel: [    0.520517] pci 0000:00:02.2: supports D2
May  5 07:29:44 user kernel: [    0.520519] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520523] pci 0000:00:02.2: PME# disabled
May  5 07:29:44 user kernel: [    0.520543] PCI: 0000:00:06.0 reg 10 io port: [d400, d4ff]
May  5 07:29:44 user kernel: [    0.520547] PCI: 0000:00:06.0 reg 14 io port: [d800, d87f]
May  5 07:29:44 user kernel: [    0.520552] PCI: 0000:00:06.0 reg 18 32bit mmio: [e4001000, e4001fff]
May  5 07:29:44 user kernel: [    0.520565] pci 0000:00:06.0: supports D1
May  5 07:29:44 user kernel: [    0.520567] pci 0000:00:06.0: supports D2
May  5 07:29:44 user kernel: [    0.520587] PCI: 0000:00:08.0 reg 20 io port: [f000, f00f]
May  5 07:29:44 user kernel: [    0.520714] PCI: 0000:01:06.0 reg 10 io port: [9000, 903f]
May  5 07:29:44 user kernel: [    0.520743] pci 0000:01:06.0: supports D2
May  5 07:29:44 user kernel: [    0.520745] pci 0000:01:06.0: PME# supported from D0 D2 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520749] pci 0000:01:06.0: PME# disabled
May  5 07:29:44 user kernel: [    0.520769] PCI: 0000:01:07.0 reg 10 32bit mmio: [e3012000, e3012fff]
May  5 07:29:44 user kernel: [    0.520798] pci 0000:01:07.0: PME# supported from D0 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520802] pci 0000:01:07.0: PME# disabled
May  5 07:29:44 user kernel: [    0.520821] PCI: 0000:01:08.0 reg 10 32bit mmio: [e3000000, e300ffff]
May  5 07:29:44 user kernel: [    0.520826] PCI: 0000:01:08.0 reg 14 io port: [9400, 9407]
May  5 07:29:44 user kernel: [    0.520849] pci 0000:01:08.0: PME# supported from D3hot D3cold
May  5 07:29:44 user kernel: [    0.520852] pci 0000:01:08.0: PME# disabled
May  5 07:29:44 user kernel: [    0.520872] PCI: 0000:01:09.0 reg 10 io port: [9800, 98ff]
May  5 07:29:44 user kernel: [    0.520877] PCI: 0000:01:09.0 reg 14 32bit mmio: [e3010000, e30100ff]
May  5 07:29:44 user kernel: [    0.520901] pci 0000:01:09.0: supports D1
May  5 07:29:44 user kernel: [    0.520903] pci 0000:01:09.0: supports D2
May  5 07:29:44 user kernel: [    0.520905] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520909] pci 0000:01:09.0: PME# disabled
May  5 07:29:44 user kernel: [    0.520929] PCI: 0000:01:0b.0 reg 10 io port: [9c00, 9cff]
May  5 07:29:44 user kernel: [    0.520934] PCI: 0000:01:0b.0 reg 14 32bit mmio: [e3011000, e30110ff]
May  5 07:29:44 user kernel: [    0.520951] PCI: 0000:01:0b.0 reg 30 32bit mmio: [0, ffff]
May  5 07:29:44 user kernel: [    0.520961] pci 0000:01:0b.0: supports D1
May  5 07:29:44 user kernel: [    0.520963] pci 0000:01:0b.0: supports D2
May  5 07:29:44 user kernel: [    0.520965] pci 0000:01:0b.0: PME# supported from D1 D2 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520969] pci 0000:01:0b.0: PME# disabled
May  5 07:29:44 user kernel: [    0.520989] PCI: 0000:01:0d.0 reg 10 io port: [a000, a007]
May  5 07:29:44 user kernel: [    0.520994] PCI: 0000:01:0d.0 reg 14 io port: [a400, a403]
May  5 07:29:44 user kernel: [    0.520999] PCI: 0000:01:0d.0 reg 18 io port: [a800, a807]
May  5 07:29:44 user kernel: [    0.521004] PCI: 0000:01:0d.0 reg 1c io port: [ac00, ac03]
May  5 07:29:44 user kernel: [    0.521010] PCI: 0000:01:0d.0 reg 20 io port: [b000, b00f]
May  5 07:29:44 user kernel: [    0.521015] PCI: 0000:01:0d.0 reg 24 32bit mmio: [e3013000, e30131ff]
May  5 07:29:44 user kernel: [    0.521020] PCI: 0000:01:0d.0 reg 30 32bit mmio: [0, 7ffff]
May  5 07:29:44 user kernel: [    0.521030] pci 0000:01:0d.0: supports D1
May  5 07:29:44 user kernel: [    0.521032] pci 0000:01:0d.0: supports D2
May  5 07:29:44 user kernel: [    0.521049] PCI: bridge 0000:00:0a.0 io port: [9000, bfff]
May  5 07:29:44 user kernel: [    0.521052] PCI: bridge 0000:00:0a.0 32bit mmio: [e2000000, e3ffffff]
May  5 07:29:44 user kernel: [    0.521086] PCI: 0000:02:00.0 reg 10 32bit mmio: [d8000000, dbffffff]
May  5 07:29:44 user kernel: [    0.521092] PCI: 0000:02:00.0 reg 14 io port: [c000, c0ff]
May  5 07:29:44 user kernel: [    0.521098] PCI: 0000:02:00.0 reg 18 32bit mmio: [e1000000, e100ffff]
May  5 07:29:44 user kernel: [    0.521115] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, 1ffff]
May  5 07:29:44 user kernel: [    0.521130] pci 0000:02:00.0: supports D1
May  5 07:29:44 user kernel: [    0.521132] pci 0000:02:00.0: supports D2
May  5 07:29:44 user kernel: [    0.521154] PCI: 0000:02:00.1 reg 10 32bit mmio: [dc000000, dfffffff]
May  5 07:29:44 user kernel: [    0.521160] PCI: 0000:02:00.1 reg 14 32bit mmio: [e1010000, e101ffff]
May  5 07:29:44 user kernel: [    0.521190] pci 0000:02:00.1: supports D1
May  5 07:29:44 user kernel: [    0.521191] pci 0000:02:00.1: supports D2
May  5 07:29:44 user kernel: [    0.521229] PCI: bridge 0000:00:0b.0 io port: [c000, cfff]
May  5 07:29:44 user kernel: [    0.521233] PCI: bridge 0000:00:0b.0 32bit mmio: [e0000000, e1ffffff]
May  5 07:29:44 user kernel: [    0.521237] PCI: bridge 0000:00:0b.0 32bit mmio pref: [d8000000, dfffffff]
May  5 07:29:44 user kernel: [    0.521245] bus 00 -> node 0
May  5 07:29:44 user kernel: [    0.521252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May  5 07:29:44 user kernel: [    0.521449] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
May  5 07:29:44 user kernel: [    0.521867] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
May  5 07:29:44 user kernel: [    0.575512] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May  5 07:29:44 user kernel: [    0.575694] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:29:44 user kernel: [    0.575874] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  5 07:29:44 user kernel: [    0.576054] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  5 07:29:44 user kernel: [    0.576233] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May  5 07:29:44 user kernel: [    0.576413] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:29:44 user kernel: [    0.576593] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:29:44 user kernel: [    0.576771] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.576956] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.577137] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:29:44 user kernel: [    0.577315] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.577496] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  5 07:29:44 user kernel: [    0.577678] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:29:44 user kernel: [    0.577858] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.578037] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.578217] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.578404] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.578553] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
May  5 07:29:44 user kernel: [    0.578693] ACPI: PCI Interrupt Link [APC2] (IRQs *17)
May  5 07:29:44 user kernel: [    0.578832] ACPI: PCI Interrupt Link [APC3] (IRQs *18)
May  5 07:29:44 user kernel: [    0.578971] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
May  5 07:29:44 user kernel: [    0.579110] ACPI: PCI Interrupt Link [APC5] (IRQs *16)
May  5 07:29:44 user kernel: [    0.579313] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
May  5 07:29:44 user kernel: [    0.579515] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
May  5 07:29:44 user kernel: [    0.579715] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.579916] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.580140] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
May  5 07:29:44 user kernel: [    0.580340] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.580481] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
May  5 07:29:44 user kernel: [    0.580679] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
May  5 07:29:44 user kernel: [    0.580879] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.581079] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.581279] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.581486] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.581628] ACPI: Power Resource [ISAV] (on)
May  5 07:29:44 user kernel: [    0.581712] Linux Plug and Play Support v0.97 (c) Adam Belay
May  5 07:29:44 user kernel: [    0.581746] pnp: PnP ACPI init
May  5 07:29:44 user kernel: [    0.581754] ACPI: bus type pnp registered
May  5 07:29:44 user kernel: [    0.587841] pnp: PnP ACPI: found 15 devices
May  5 07:29:44 user kernel: [    0.587844] ACPI: ACPI bus type pnp unregistered
May  5 07:29:44 user kernel: [    0.587847] PnPBIOS: Disabled by ACPI PNP
May  5 07:29:44 user kernel: [    0.588175] PCI: Using ACPI for IRQ routing
May  5 07:29:44 user kernel: [    0.588293] NET: Registered protocol family 8
May  5 07:29:44 user kernel: [    0.588293] NET: Registered protocol family 20
May  5 07:29:44 user kernel: [    0.588293] NetLabel: Initializing
May  5 07:29:44 user kernel: [    0.588293] NetLabel:  domain hash size = 128
May  5 07:29:44 user kernel: [    0.588293] NetLabel:  protocols = UNLABELED CIPSOv4
May  5 07:29:44 user kernel: [    0.588293] NetLabel:  unlabeled traffic allowed by default
May  5 07:29:44 user kernel: [    0.588293] tracer: 772 pages allocated for 65536 entries of 48 bytes
May  5 07:29:44 user kernel: [    0.588293]    actual entries 65620
May  5 07:29:44 user kernel: [    0.588293] AppArmor: AppArmor Filesystem Enabled
May  5 07:29:44 user kernel: [    0.588293] ACPI: RTC can wake from S4
May  5 07:29:44 user kernel: [    0.588293] system 00:00: ioport range 0x1000-0x107f has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:00: ioport range 0x1080-0x10ff has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:00: ioport range 0x1400-0x147f has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:00: ioport range 0x1480-0x14ff has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:00: ioport range 0x1800-0x187f has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:00: ioport range 0x1880-0x18ff has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xd8800-0xdbfff has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xf0000-0xf7fff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xf8000-0xfbfff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xfc000-0xfffff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0x2fff0000-0x2fffffff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xffff0000-0xffffffff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0x0-0x9ffff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0x100000-0x2ffeffff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:03: ioport range 0x800-0x805 has been reserved
May  5 07:29:44 user kernel: [    0.624048] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:01
May  5 07:29:44 user kernel: [    0.624052] pci 0000:00:0a.0:   IO window: 0x9000-0xbfff
May  5 07:29:44 user kernel: [    0.624056] pci 0000:00:0a.0:   MEM window: 0xe2000000-0xe3ffffff
May  5 07:29:44 user kernel: [    0.624059] pci 0000:00:0a.0:   PREFETCH window: 0x00000040000000-0x000000400fffff
May  5 07:29:44 user kernel: [    0.624065] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
May  5 07:29:44 user kernel: [    0.624068] pci 0000:00:0b.0:   IO window: 0xc000-0xcfff
May  5 07:29:44 user kernel: [    0.624073] pci 0000:00:0b.0:   MEM window: 0xe0000000-0xe1ffffff
May  5 07:29:44 user kernel: [    0.624077] pci 0000:00:0b.0:   PREFETCH window: 0x000000d8000000-0x000000dfffffff
May  5 07:29:44 user kernel: [    0.624089] pci 0000:00:0a.0: setting latency timer to 64
May  5 07:29:44 user kernel: [    0.624095] bus: 00 index 0 io port: [0, ffff]
May  5 07:29:44 user kernel: [    0.624098] bus: 00 index 1 mmio: [0, ffffffffffffffff]
May  5 07:29:44 user kernel: [    0.624100] bus: 01 index 0 io port: [9000, bfff]
May  5 07:29:44 user kernel: [    0.624102] bus: 01 index 1 mmio: [e2000000, e3ffffff]
May  5 07:29:44 user kernel: [    0.624105] bus: 01 index 2 mmio: [40000000, 400fffff]
May  5 07:29:44 user kernel: [    0.624107] bus: 01 index 3 mmio: [0, 0]
May  5 07:29:44 user kernel: [    0.624109] bus: 02 index 0 io port: [c000, cfff]
May  5 07:29:44 user kernel: [    0.624111] bus: 02 index 1 mmio: [e0000000, e1ffffff]
May  5 07:29:44 user kernel: [    0.624114] bus: 02 index 2 mmio: [d8000000, dfffffff]
May  5 07:29:44 user kernel: [    0.624116] bus: 02 index 3 mmio: [0, 0]
May  5 07:29:44 user kernel: [    0.624127] NET: Registered protocol family 2
May  5 07:29:44 user kernel: [    0.624251] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May  5 07:29:44 user kernel: [    0.624574] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May  5 07:29:44 user kernel: [    0.625530] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May  5 07:29:44 user kernel: [    0.626049] TCP: Hash tables configured (established 131072 bind 65536)
May  5 07:29:44 user kernel: [    0.626052] TCP reno registered
May  5 07:29:44 user kernel: [    0.626159] NET: Registered protocol family 1
May  5 07:29:44 user kernel: [    0.626278] checking if image is initramfs... it is
May  5 07:29:44 user kernel: [    1.130027] Switched to high resolution mode on CPU 0
May  5 07:29:44 user kernel: [    1.270116] Freeing initrd memory: 7861k freed
May  5 07:29:44 user kernel: [    1.270870] audit: initializing netlink socket (disabled)
May  5 07:29:44 user kernel: [    1.270885] type=2000 audit(1241508563.270:1): initialized
May  5 07:29:44 user kernel: [    1.277057] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May  5 07:29:44 user kernel: [    1.279219] VFS: Disk quotas dquot_6.5.1
May  5 07:29:44 user kernel: [    1.279304] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  5 07:29:44 user kernel: [    1.279400] msgmni has been set to 1510
May  5 07:29:44 user kernel: [    1.279520] io scheduler noop registered
May  5 07:29:44 user kernel: [    1.279522] io scheduler anticipatory registered
May  5 07:29:44 user kernel: [    1.279525] io scheduler deadline registered (default)
May  5 07:29:44 user kernel: [    1.279536] io scheduler cfq registered
May  5 07:29:44 user kernel: [    1.320057] pci 0000:02:00.0: Boot video device
May  5 07:29:44 user kernel: [    1.320377] isapnp: Scanning for PnP cards...
May  5 07:29:44 user kernel: [    1.676732] isapnp: No Plug & Play device found
May  5 07:29:44 user kernel: [    1.712934] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
May  5 07:29:44 user kernel: [    1.713052] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  5 07:29:44 user kernel: [    1.713192] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  5 07:29:44 user kernel: [    1.713760] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  5 07:29:44 user kernel: [    1.714033] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  5 07:29:44 user kernel: [    1.714419] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
May  5 07:29:44 user kernel: [    1.714428] serial 0000:01:06.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
May  5 07:29:44 user kernel: [    1.717560] brd: module loaded
May  5 07:29:44 user kernel: [    1.717632] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May  5 07:29:44 user kernel: [    1.717750] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May  5 07:29:44 user kernel: [    1.717753] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May  5 07:29:44 user kernel: [    1.718532] serio: i8042 KBD port at 0x60,0x64 irq 1
May  5 07:29:44 user kernel: [    1.718992] mice: PS/2 mouse device common for all mice
May  5 07:29:44 user kernel: [    1.719123] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
May  5 07:29:44 user kernel: [    1.719146] rtc0: alarms up to one year, y3k
May  5 07:29:44 user kernel: [    1.719262] EISA: Probing bus 0 at eisa.0
May  5 07:29:44 user kernel: [    1.719270] Cannot allocate resource for EISA slot 1
May  5 07:29:44 user kernel: [    1.719273] Cannot allocate resource for EISA slot 2
May  5 07:29:44 user kernel: [    1.719288] EISA: Detected 0 cards.
May  5 07:29:44 user kernel: [    1.719292] cpuidle: using governor ladder
May  5 07:29:44 user kernel: [    1.719294] cpuidle: using governor menu
May  5 07:29:44 user kernel: [    1.719813] TCP cubic registered
May  5 07:29:44 user kernel: [    1.719839] Using IPI No-Shortcut mode
May  5 07:29:44 user kernel: [    1.720043] registered taskstats version 1
May  5 07:29:44 user kernel: [    1.720176]   Magic number: 9:35:470
May  5 07:29:44 user kernel: [    1.720365] rtc_cmos 00:05: setting system clock to 2009-05-05 07:29:24 UTC (1241508564)
May  5 07:29:44 user kernel: [    1.720368] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  5 07:29:44 user kernel: [    1.720371] EDD information not available.
May  5 07:29:44 user kernel: [    1.720697] Freeing unused kernel memory: 436k freed
May  5 07:29:44 user kernel: [    1.720815] Write protecting the kernel text: 2632k
May  5 07:29:44 user kernel: [    1.720863] Write protecting the kernel read-only data: 956k
May  5 07:29:44 user kernel: [    1.741491] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May  5 07:29:44 user kernel: [    1.850276] fuse init (API version 7.9)
May  5 07:29:44 user kernel: [    1.870736] ACPI: processor limited to max C-state 1
May  5 07:29:44 user kernel: [    1.870820] processor ACPI0007:00: registered as cooling_device0
May  5 07:29:44 user kernel: [    2.590594] usbcore: registered new interface driver usbfs
May  5 07:29:44 user kernel: [    2.590620] usbcore: registered new interface driver hub
May  5 07:29:44 user kernel: [    2.590658] usbcore: registered new device driver usb
May  5 07:29:44 user kernel: [    2.596194] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
May  5 07:29:44 user kernel: [    2.596560] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
May  5 07:29:44 user kernel: [    2.596569] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 22 (level, high) -> IRQ 22
May  5 07:29:44 user kernel: [    2.596583] ohci_hcd 0000:00:02.0: setting latency timer to 64
May  5 07:29:44 user kernel: [    2.596586] ohci_hcd 0000:00:02.0: OHCI Host Controller
May  5 07:29:44 user kernel: [    2.596634] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
May  5 07:29:44 user kernel: [    2.596656] ohci_hcd 0000:00:02.0: irq 22, io mem 0xe4003000
May  5 07:29:44 user kernel: [    2.608392] No dock devices found.
May  5 07:29:44 user kernel: [    2.652216] usb usb1: configuration #1 chosen from 1 choice
May  5 07:29:44 user kernel: [    2.652246] hub 1-0:1.0: USB hub found
May  5 07:29:44 user kernel: [    2.652258] hub 1-0:1.0: 3 ports detected
May  5 07:29:44 user kernel: [    2.666143] SCSI subsystem initialized
May  5 07:29:44 user kernel: [    2.712969] libata version 3.00 loaded.
May  5 07:29:44 user kernel: [    2.870818] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
May  5 07:29:44 user kernel: [    2.870829] ohci_hcd 0000:00:02.1: PCI INT B -> Link[APCG] -> GSI 21 (level, high) -> IRQ 21
May  5 07:29:44 user kernel: [    2.870846] ohci_hcd 0000:00:02.1: setting latency timer to 64
May  5 07:29:44 user kernel: [    2.870849] ohci_hcd 0000:00:02.1: OHCI Host Controller
May  5 07:29:44 user kernel: [    2.870874] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
May  5 07:29:44 user kernel: [    2.870897] ohci_hcd 0000:00:02.1: irq 21, io mem 0xe4004000
May  5 07:29:44 user kernel: [    2.932226] usb usb2: configuration #1 chosen from 1 choice
May  5 07:29:44 user kernel: [    2.932256] hub 2-0:1.0: USB hub found
May  5 07:29:44 user kernel: [    2.932268] hub 2-0:1.0: 3 ports detected
May  5 07:29:44 user kernel: [    3.040883] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
May  5 07:29:44 user kernel: [    3.040893] ehci_hcd 0000:00:02.2: PCI INT C -> Link[APCL] -> GSI 20 (level, high) -> IRQ 20
May  5 07:29:44 user kernel: [    3.040910] ehci_hcd 0000:00:02.2: setting latency timer to 64
May  5 07:29:44 user kernel: [    3.040913] ehci_hcd 0000:00:02.2: EHCI Host Controller
May  5 07:29:44 user kernel: [    3.040938] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
May  5 07:29:44 user kernel: [    3.040965] ehci_hcd 0000:00:02.2: debug port 1
May  5 07:29:44 user kernel: [    3.040969] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
May  5 07:29:44 user kernel: [    3.040985] ehci_hcd 0000:00:02.2: irq 20, io mem 0xe4005000
May  5 07:29:44 user kernel: [    3.050047] usb 1-1: new full speed USB device using ohci_hcd and address 2
May  5 07:29:44 user kernel: [    3.070179] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May  5 07:29:44 user kernel: [    3.070355] usb usb3: configuration #1 chosen from 1 choice
May  5 07:29:44 user kernel: [    3.070388] hub 3-0:1.0: USB hub found
May  5 07:29:44 user kernel: [    3.070399] hub 3-0:1.0: 6 ports detected
May  5 07:29:44 user kernel: [    3.130205] hub 1-0:1.0: unable to enumerate USB device on port 1
May  5 07:29:44 user kernel: [    3.290412] pata_acpi 0000:00:08.0: power state changed by ACPI to D0
May  5 07:29:44 user kernel: [    3.290461] pata_acpi 0000:00:08.0: setting latency timer to 64
May  5 07:29:44 user kernel: [    3.291297] VIA Networking Velocity Family Gigabit Ethernet Adapter Driver Ver. 1.14
May  5 07:29:44 user kernel: [    3.291301] Copyright (c) 2002, 2003 VIA Networking Technologies, Inc.
May  5 07:29:44 user kernel: [    3.291303] Copyright (c) 2004 Red Hat Inc.
May  5 07:29:44 user kernel: [    3.291496] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
May  5 07:29:44 user kernel: [    3.291504] via-velocity 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
May  5 07:29:44 user kernel: [    3.292187] eth1: VIA Networking Velocity Family Gigabit Ethernet Adapter
May  5 07:29:44 user kernel: [    3.292191] eth1: Ethernet Address: 00:A0:C5:30:02:07
May  5 07:29:44 user kernel: [    3.310155] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
May  5 07:29:44 user kernel: [    3.310370] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
May  5 07:29:44 user kernel: [    3.310379] r8169 0000:01:0b.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
May  5 07:29:44 user kernel: [    3.310722] eth0: RTL8169s at 0xf083e000, 00:0d:61:21:54:d2, XID 00800000 IRQ 19
May  5 07:29:44 user kernel: [    3.317737] sata_sil 0000:01:0d.0: version 2.3
May  5 07:29:44 user kernel: [    3.317781] sata_sil 0000:01:0d.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
May  5 07:29:44 user kernel: [    3.317800] sata_sil 0000:01:0d.0: Applying R_ERR on DMA activate FIS errata fix
May  5 07:29:44 user kernel: [    3.317856] scsi0 : sata_sil
May  5 07:29:44 user kernel: [    3.317952] scsi1 : sata_sil
May  5 07:29:44 user kernel: [    3.317987] ata1: SATA max UDMA/100 mmio m512@0xe3013000 tf 0xe3013080 irq 17
May  5 07:29:44 user kernel: [    3.317991] ata2: SATA max UDMA/100 mmio m512@0xe3013000 tf 0xe30130c0 irq 17
May  5 07:29:44 user kernel: [    3.318072] pata_amd 0000:00:08.0: version 0.3.10
May  5 07:29:44 user kernel: [    3.318154] pata_amd 0000:00:08.0: power state changed by ACPI to D0
May  5 07:29:44 user kernel: [    3.318193] pata_amd 0000:00:08.0: setting latency timer to 64
May  5 07:29:44 user kernel: [    3.318244] scsi2 : pata_amd
May  5 07:29:44 user kernel: [    3.318300] scsi3 : pata_amd
May  5 07:29:44 user kernel: [    3.319153] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
May  5 07:29:44 user kernel: [    3.319156] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
May  5 07:29:44 user kernel: [    3.550434] ata3.00: ATA-6: ST380011A, 8.01, max UDMA/100
May  5 07:29:44 user kernel: [    3.550438] ata3.00: 156301488 sectors, multi 16: LBA48 
May  5 07:29:44 user kernel: [    3.550453] ata3: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc60000c0) ACPI=0x3f01f (20:600:0x13)
May  5 07:29:44 user kernel: [    3.590359] ata3.00: configured for UDMA/100
May  5 07:29:44 user kernel: [    3.660026] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
May  5 07:29:44 user kernel: [    3.680397] ata1.00: ATA-6: ST3120827AS, 3.42, max UDMA/133
May  5 07:29:44 user kernel: [    3.680400] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
May  5 07:29:44 user kernel: [    3.720402] ata1.00: configured for UDMA/100
May  5 07:29:44 user kernel: [    3.780293] ata4.01: ATAPI: _NEC DVD_RW ND-1300A, 1.08, max UDMA/33
May  5 07:29:44 user kernel: [    3.780306] ata4: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc60000c0) ACPI=0x701f (600:60:0x1c)
May  5 07:29:44 user kernel: [    3.820232] ata4.01: configured for UDMA/33
May  5 07:29:44 user kernel: [    3.820332] scsi 2:0:0:0: Direct-Access     ATA      ST380011A        8.01 PQ: 0 ANSI: 5
May  5 07:29:44 user kernel: [    3.823413] scsi 3:0:1:0: CD-ROM            _NEC     DVD_RW ND-1300A  1.08 PQ: 0 ANSI: 5
May  5 07:29:44 user kernel: [    4.070023] ata2: SATA link down (SStatus 0 SControl 310)
May  5 07:29:44 user kernel: [    4.070132] scsi 0:0:0:0: Direct-Access     ATA      ST3120827AS      3.42 PQ: 0 ANSI: 5
May  5 07:29:44 user kernel: [    4.079725] scsi 2:0:0:0: Attached scsi generic sg0 type 0
May  5 07:29:44 user kernel: [    4.079763] scsi 3:0:1:0: Attached scsi generic sg1 type 5
May  5 07:29:44 user kernel: [    4.079800] scsi 0:0:0:0: Attached scsi generic sg2 type 0
May  5 07:29:44 user kernel: [    4.108308] Driver 'sd' needs updating - please use bus_type methods
May  5 07:29:44 user kernel: [    4.108423] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
May  5 07:29:44 user kernel: [    4.108441] sd 2:0:0:0: [sda] Write Protect is off
May  5 07:29:44 user kernel: [    4.108444] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  5 07:29:44 user kernel: [    4.108470] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:29:44 user kernel: [    4.108535] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
May  5 07:29:44 user kernel: [    4.108549] sd 2:0:0:0: [sda] Write Protect is off
May  5 07:29:44 user kernel: [    4.108551] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  5 07:29:44 user kernel: [    4.108576] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:29:44 user kernel: [    4.108581]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
May  5 07:29:44 user kernel: [    4.126503]  sda1 < sda5 sda6 >
May  5 07:29:44 user kernel: [    4.134656] sd 2:0:0:0: [sda] Attached SCSI disk
May  5 07:29:44 user kernel: [    4.134744] sd 0:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
May  5 07:29:44 user kernel: [    4.134764] sd 0:0:0:0: [sdb] Write Protect is off
May  5 07:29:44 user kernel: [    4.134766] sd 0:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May  5 07:29:44 user kernel: [    4.134796] sd 0:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:29:44 user kernel: [    4.134858] sd 0:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
May  5 07:29:44 user kernel: [    4.134874] sd 0:0:0:0: [sdb] Write Protect is off
May  5 07:29:44 user kernel: [    4.134877] sd 0:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May  5 07:29:44 user kernel: [    4.134905] sd 0:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:29:44 user kernel: [    4.134909]  sdb:sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
May  5 07:29:44 user kernel: [    4.139192] Uniform CD-ROM driver Revision: 3.20
May  5 07:29:44 user kernel: [    4.139290] sr 3:0:1:0: Attached scsi CD-ROM sr0
May  5 07:29:44 user kernel: [    4.151098]  sdb1 sdb2 < sdb5 sdb6 sdb7 >
May  5 07:29:44 user kernel: [    4.184197] sd 0:0:0:0: [sdb] Attached SCSI disk
May  5 07:29:44 user kernel: [    4.250029] usb 1-1: new full speed USB device using ohci_hcd and address 3
May  5 07:29:44 user kernel: [    4.476272] usb 1-1: configuration #1 chosen from 1 choice
May  5 07:29:44 user kernel: [    4.656792] PM: Starting manual resume from disk
May  5 07:29:44 user kernel: [    4.656797] PM: Resume from partition 8:5
May  5 07:29:44 user kernel: [    4.656799] PM: Checking hibernation image.
May  5 07:29:44 user kernel: [    4.656959] PM: Resume from disk failed.
May  5 07:29:44 user kernel: [    4.709126] kjournald starting.  Commit interval 5 seconds
May  5 07:29:44 user kernel: [    4.709143] EXT3-fs: mounted filesystem with ordered data mode.
May  5 07:29:44 user kernel: [    4.820026] usb 1-2: new full speed USB device using ohci_hcd and address 4
May  5 07:29:44 user kernel: [    5.043133] usb 1-2: configuration #1 chosen from 1 choice
May  5 07:29:44 user kernel: [    5.380026] usb 1-3: new low speed USB device using ohci_hcd and address 5
May  5 07:29:44 user kernel: [    5.606225] usb 1-3: configuration #1 chosen from 1 choice
May  5 07:29:44 user kernel: [    6.907183] udevd version 124 started
May  5 07:29:44 user kernel: [    7.911918] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  5 07:29:44 user kernel: [    7.952110] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  5 07:29:44 user kernel: [    8.030740] Linux agpgart interface v0.103
May  5 07:29:44 user kernel: [    8.094743] input: PC Speaker as /devices/platform/pcspkr/input/input2
May  5 07:29:44 user kernel: [    8.120911] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
May  5 07:29:44 user kernel: [    8.120946] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
May  5 07:29:44 user kernel: [    8.124787] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
May  5 07:29:44 user kernel: [    8.142953] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
May  5 07:29:44 user kernel: [    8.142973] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2000
May  5 07:29:44 user kernel: [    8.154607] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
May  5 07:29:44 user kernel: [    8.180063] ACPI: Power Button (FF) [PWRF]
May  5 07:29:44 user kernel: [    8.180162] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
May  5 07:29:44 user kernel: [    8.210085] ACPI: Power Button (CM) [PWRB]
May  5 07:29:44 user kernel: [    8.263570] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
May  5 07:29:44 user kernel: [    8.263577] Intel ICH 0000:00:06.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, high) -> IRQ 22
May  5 07:29:44 user kernel: [    8.263600] Intel ICH 0000:00:06.0: setting latency timer to 64
May  5 07:29:44 user kernel: [    8.610028] intel8x0_measure_ac97_clock: measured 59796 usecs
May  5 07:29:44 user kernel: [    8.610033] intel8x0: clocking to 48000
May  5 07:29:44 user kernel: [    8.701966] parport_pc 00:0b: reported by Plug and Play ACPI
May  5 07:29:44 user kernel: [    8.702009] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
May  5 07:29:44 user kernel: [   10.207818] ieee80211_crypt: registered algorithm 'NULL'
May  5 07:29:44 user kernel: [   10.211835] ieee80211: 802.11 data/management/control stack, git-1.1.13
May  5 07:29:44 user kernel: [   10.211840] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
May  5 07:29:44 user kernel: [   10.280828] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
May  5 07:29:44 user kernel: [   10.280833] ipw2200: Copyright(c) 2003-2006 Intel Corporation
May  5 07:29:44 user kernel: [   10.280929] ipw2200 0000:01:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
May  5 07:29:44 user kernel: [   10.280981] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
May  5 07:29:44 user kernel: [   10.281034] firmware: requesting ipw2200-bss.fw
May  5 07:29:44 user kernel: [   10.626329] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
May  5 07:29:44 user kernel: [   10.632897] usbcore: registered new interface driver cdc_acm
May  5 07:29:44 user kernel: [   10.632903] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
May  5 07:29:44 user kernel: [   10.933501] usbcore: registered new interface driver snd-usb-audio
May  5 07:29:44 user kernel: [   10.933531] usbcore: registered new interface driver hiddev
May  5 07:29:44 user kernel: [   10.942276] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.3/input/input5
May  5 07:29:44 user kernel: [   11.000230] input,hidraw0: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:02.0-2
May  5 07:29:44 user kernel: [   11.006479] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.0/input/input6
May  5 07:29:44 user kernel: [   11.050386] input,hidraw1: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:02.0-3
May  5 07:29:44 user kernel: [   11.050410] usbcore: registered new interface driver usbhid
May  5 07:29:44 user kernel: [   11.050414] usbhid: v2.6:USB HID core driver
May  5 07:29:44 user kernel: [   12.615459] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
May  5 07:29:44 user kernel: [   13.508028] loop: module loaded
May  5 07:29:44 user kernel: [   13.522041] lp0: using parport0 (interrupt-driven).
May  5 07:29:44 user kernel: [   13.890054] Adding 248936k swap on /dev/sda5.  Priority:-1 extents:1 across:248936k
May  5 07:29:44 user kernel: [   14.241224] EXT3 FS on sda6, internal journal
May  5 07:29:44 user kernel: [   15.345827] ip_tables: (C) 2000-2006 Netfilter Core Team
May  5 07:29:44 user kernel: [   15.396787] r8169: eth0: link up
May  5 07:29:44 user kernel: [   16.736930] NET: Registered protocol family 17
May  5 07:29:44 user kernel: [   19.564822] Velocity is AUTO mode
May  5 07:29:44 user kernel: [   20.086147] NET: Registered protocol family 10
May  5 07:29:44 user kernel: [   20.086644] lo: Disabled Privacy Extensions
May  5 07:29:44 user pptpd[4372]: MGR: connections limit (100) reached, extra IP addresses ignored
May  5 07:29:45 user pptpd[4373]: MGR: Manager process started
May  5 07:29:45 user pptpd[4373]: MGR: Maximum of 100 connections available
May  5 07:29:46 user kernel: [   24.094996] warning: `dhcpd3' uses 32-bit capabilities (legacy support in use)
May  5 07:29:46 user dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  5 07:29:46 user dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  5 07:29:46 user dhcpd: All rights reserved.
May  5 07:29:46 user dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  5 07:29:46 user dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  5 07:29:46 user dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  5 07:29:46 user dhcpd: All rights reserved.
May  5 07:29:46 user dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  5 07:29:46 user dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  5 07:29:46 user dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  5 07:29:46 user dhcpd: All rights reserved.
May  5 07:29:46 user dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  5 07:29:46 user dhcpd: Wrote 3 leases to leases file.
May  5 07:29:46 user ntpdate[3993]: no server suitable for synchronization found
May  5 07:29:49 user /usr/sbin/cron[4578]: (CRON) INFO (pidfile fd = 3)
May  5 07:29:49 user /usr/sbin/cron[4579]: (CRON) STARTUP (fork ok)
May  5 07:29:49 user /usr/sbin/cron[4579]: (CRON) INFO (Running @reboot jobs)
May  5 07:29:51 user ntpdate[4540]: no server suitable for synchronization found
May  5 07:29:52 user kernel: [   30.290010] eth1: no IPv6 routers present
May  5 07:29:53 user kernel: [   30.540005] eth0: no IPv6 routers present
May  5 07:30:01 user /USR/SBIN/CRON[4682]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May  5 07:33:19 user pptpd[4823]: MGR: connections limit (100) reached, extra IP addresses ignored
May  5 07:33:19 user pptpd[4824]: MGR: Manager process started
May  5 07:33:19 user pptpd[4824]: MGR: Maximum of 100 connections available
May  5 07:39:56 user init: tty4 main process (4276) killed by TERM signal
May  5 07:39:56 user init: tty5 main process (4277) killed by TERM signal
May  5 07:39:56 user init: tty2 main process (4285) killed by TERM signal
May  5 07:39:56 user init: tty3 main process (4287) killed by TERM signal
May  5 07:39:56 user init: tty6 main process (4288) killed by TERM signal
May  5 07:39:56 user init: tty1 main process (4589) killed by TERM signal
May  5 07:39:56 user console-kit-daemon[4392]: WARNING: Unable to activate console: No such device or address 
May  5 07:39:58 user exiting on signal 15
May  5 07:40:59 user syslogd 1.5.0#2ubuntu6: restart.
May  5 07:40:59 user kernel: Inspecting /boot/System.map-2.6.27-7-server
May  5 07:40:59 user kernel: Cannot find map file.
May  5 07:40:59 user kernel: Loaded 48877 symbols from 70 modules.
May  5 07:40:59 user kernel: [    0.000000] Initializing cgroup subsys cpuset
May  5 07:40:59 user kernel: [    0.000000] Initializing cgroup subsys cpu
May  5 07:40:59 user kernel: [    0.000000] Linux version 2.6.27-7-server (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 20:18:35 UTC 2008 (Ubuntu 2.6.27-7.16-server)
May  5 07:40:59 user kernel: [    0.000000] BIOS-provided physical RAM map:
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
May  5 07:40:59 user kernel: [    0.000000] last_pfn = 0x2fff0 max_arch_pfn = 0x1000000
May  5 07:40:59 user kernel: [    0.000000] kernel direct mapping tables up to 2fff0000 @ 7000-d000
May  5 07:40:59 user kernel: [    0.000000] NX (Execute Disable) protection: active
May  5 07:40:59 user kernel: [    0.000000] RAMDISK: 2f832000 - 2ffdf6b8
May  5 07:40:59 user kernel: [    0.000000] DMI 2.3 present.
May  5 07:40:59 user kernel: [    0.000000] ACPI: RSDP 000F6AB0, 0014 (r0 Nvidia)
May  5 07:40:59 user kernel: [    0.000000] ACPI: RSDT 2FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  5 07:40:59 user kernel: [    0.000000] ACPI: FACP 2FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  5 07:40:59 user kernel: [    0.000000] ACPI: DSDT 2FFF30C0, 4ABF (r1 NVIDIA AWRDACPI     1000 MSFT  100000C)
May  5 07:40:59 user kernel: [    0.000000] ACPI: FACS 2FFF0000, 0040
May  5 07:40:59 user kernel: [    0.000000] ACPI: APIC 2FFF7B80, 005A (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  5 07:40:59 user kernel: [    0.000000] 0MB HIGHMEM available.
May  5 07:40:59 user kernel: [    0.000000] 767MB LOWMEM available.
May  5 07:40:59 user kernel: [    0.000000]   mapped low ram: 0 - 2fff0000
May  5 07:40:59 user kernel: [    0.000000]   low ram: 00000000 - 2fff0000
May  5 07:40:59 user kernel: [    0.000000]   bootmap 0000a000 - 00010000
May  5 07:40:59 user kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002fff0000]
May  5 07:40:59 user kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
May  5 07:40:59 user kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
May  5 07:40:59 user kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
May  5 07:40:59 user kernel: [    0.000000]   #3 [0000100000 - 00005e8220]    TEXT DATA BSS ==> [0000100000 - 00005e8220]
May  5 07:40:59 user kernel: [    0.000000]   #4 [002f832000 - 002ffdf6b8]          RAMDISK ==> [002f832000 - 002ffdf6b8]
May  5 07:40:59 user kernel: [    0.000000]   #5 [00005e9000 - 00005f1000]    INIT_PG_TABLE ==> [00005e9000 - 00005f1000]
May  5 07:40:59 user kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
May  5 07:40:59 user kernel: [    0.000000]   #7 [0000007000 - 000000a000]          PGTABLE ==> [0000007000 - 000000a000]
May  5 07:40:59 user kernel: [    0.000000]   #8 [000000a000 - 0000010000]          BOOTMAP ==> [000000a000 - 0000010000]
May  5 07:40:59 user kernel: [    0.000000] found SMP MP-table at [c00f5000] 000f5000
May  5 07:40:59 user kernel: [    0.000000] Zone PFN ranges:
May  5 07:40:59 user kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
May  5 07:40:59 user kernel: [    0.000000]   Normal   0x00001000 -> 0x0002fff0
May  5 07:40:59 user kernel: [    0.000000]   HighMem  0x0002fff0 -> 0x0002fff0
May  5 07:40:59 user kernel: [    0.000000] Movable zone start PFN for each node
May  5 07:40:59 user kernel: [    0.000000] early_node_map[2] active PFN ranges
May  5 07:40:59 user kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
May  5 07:40:59 user kernel: [    0.000000]     0: 0x00000100 -> 0x0002fff0
May  5 07:40:59 user kernel: [    0.000000] On node 0 totalpages: 196495
May  5 07:40:59 user kernel: [    0.000000] free_area_init_node: node 0, pgdat c049eb00, node_mem_map c1000000
May  5 07:40:59 user kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
May  5 07:40:59 user kernel: [    0.000000]   Normal zone: 190804 pages, LIFO batch:31
May  5 07:40:59 user kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
May  5 07:40:59 user kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
May  5 07:40:59 user kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
May  5 07:40:59 user kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  5 07:40:59 user kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  5 07:40:59 user kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
May  5 07:40:59 user kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  5 07:40:59 user kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
May  5 07:40:59 user kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  5 07:40:59 user kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
May  5 07:40:59 user kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  5 07:40:59 user kernel: [    0.000000] ACPI: IRQ9 used by override.
May  5 07:40:59 user kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  5 07:40:59 user kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  5 07:40:59 user kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
May  5 07:40:59 user kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
May  5 07:40:59 user kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
May  5 07:40:59 user kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May  5 07:40:59 user kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
May  5 07:40:59 user kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
May  5 07:40:59 user kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
May  5 07:40:59 user kernel: [    0.000000] PERCPU: Allocating 45852 bytes of per cpu data
May  5 07:40:59 user kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
May  5 07:40:59 user kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194767
May  5 07:40:59 user kernel: [    0.000000] Kernel command line: root=UUID=3a16f219-3073-4cf3-8fa0-646d16cda612 ro quiet splash 
May  5 07:40:59 user kernel: [    0.000000] Enabling fast FPU save and restore... done.
May  5 07:40:59 user kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May  5 07:40:59 user kernel: [    0.000000] Initializing CPU#0
May  5 07:40:59 user kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
May  5 07:40:59 user kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
May  5 07:40:59 user kernel: [    0.000000] TSC: using PIT calibration value
May  5 07:40:59 user kernel: [    0.000000] Detected 1994.815 MHz processor.
May  5 07:40:59 user kernel: [    0.010000] spurious 8259A interrupt: IRQ7.
May  5 07:40:59 user kernel: [    0.010000] Console: colour VGA+ 80x25
May  5 07:40:59 user kernel: [    0.010000] console [tty0] enabled
May  5 07:40:59 user kernel: [    0.010000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  5 07:40:59 user kernel: [    0.010000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  5 07:40:59 user kernel: [    0.010000] Memory: 765068k/786368k available (2628k kernel code, 20728k reserved, 1201k data, 436k init, 0k highmem)
May  5 07:40:59 user kernel: [    0.010000] virtual kernel memory layout:
May  5 07:40:59 user kernel: [    0.010000]     fixmap  : 0xffc78000 - 0xfffff000   (3612 kB)
May  5 07:40:59 user kernel: [    0.010000]     pkmap   : 0xff800000 - 0xffa00000   (2048 kB)
May  5 07:40:59 user kernel: [    0.010000]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
May  5 07:40:59 user kernel: [    0.010000]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
May  5 07:40:59 user kernel: [    0.010000]       .init : 0xc04c3000 - 0xc0530000   ( 436 kB)
May  5 07:40:59 user kernel: [    0.010000]       .data : 0xc0391036 - 0xc04bd800   (1201 kB)
May  5 07:40:59 user kernel: [    0.010000]       .text : 0xc0100000 - 0xc0391036   (2628 kB)
May  5 07:40:59 user kernel: [    0.010000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
May  5 07:40:59 user kernel: [    0.010000] CPA: page pool initialized 1 of 1 pages preallocated
May  5 07:40:59 user kernel: [    0.010000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
May  5 07:40:59 user kernel: [    0.010008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.63 BogoMIPS (lpj=19948150)
May  5 07:40:59 user kernel: [    0.010026] Security Framework initialized
May  5 07:40:59 user kernel: [    0.010033] SELinux:  Disabled at boot.
May  5 07:40:59 user kernel: [    0.010053] AppArmor: AppArmor initialized
May  5 07:40:59 user kernel: [    0.010061] Mount-cache hash table entries: 512
May  5 07:40:59 user kernel: [    0.010209] Initializing cgroup subsys ns
May  5 07:40:59 user kernel: [    0.010213] Initializing cgroup subsys cpuacct
May  5 07:40:59 user kernel: [    0.010215] Initializing cgroup subsys memory
May  5 07:40:59 user kernel: [    0.010228] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May  5 07:40:59 user kernel: [    0.010231] CPU: L2 Cache: 512K (64 bytes/line)
May  5 07:40:59 user kernel: [    0.010241] Checking 'hlt' instruction... OK.
May  5 07:40:59 user kernel: [    0.050367] SMP alternatives: switching to UP code
May  5 07:40:59 user kernel: [    0.056452] Freeing SMP alternatives: 11k freed
May  5 07:40:59 user kernel: [    0.056457] ACPI: Core revision 20080609
May  5 07:40:59 user kernel: [    0.057952] ACPI: Checking initramfs for custom DSDT
May  5 07:40:59 user kernel: [    0.371033] ENABLING IO-APIC IRQs
May  5 07:40:59 user kernel: [    0.371200] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
May  5 07:40:59 user kernel: [    0.471211] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 08
May  5 07:40:59 user kernel: [    0.480000] Brought up 1 CPUs
May  5 07:40:59 user kernel: [    0.480000] Total of 1 processors activated (3989.63 BogoMIPS).
May  5 07:40:59 user kernel: [    0.480000] CPU0 attaching sched-domain:
May  5 07:40:59 user kernel: [    0.480000]  domain 0: span 0 level CPU
May  5 07:40:59 user kernel: [    0.480000]   groups: 0
May  5 07:40:59 user kernel: [    0.480000] net_namespace: 840 bytes
May  5 07:40:59 user kernel: [    0.480000] Booting paravirtualized kernel on bare hardware
May  5 07:40:59 user kernel: [    0.480000] Time:  7:40:36  Date: 05/05/09
May  5 07:40:59 user kernel: [    0.480000] NET: Registered protocol family 16
May  5 07:40:59 user kernel: [    0.480000] EISA bus registered
May  5 07:40:59 user kernel: [    0.480000] ACPI: bus type pci registered
May  5 07:40:59 user kernel: [    0.500543] PCI: PCI BIOS revision 2.10 entry at 0xfac80, last bus=2
May  5 07:40:59 user kernel: [    0.500546] PCI: Using configuration type 1 for base access
May  5 07:40:59 user kernel: [    0.502223] ACPI: EC: Look up EC in DSDT
May  5 07:40:59 user kernel: [    0.509554] ACPI: Interpreter enabled
May  5 07:40:59 user kernel: [    0.509557] ACPI: (supports S0 S3 S4 S5)
May  5 07:40:59 user kernel: [    0.509571] ACPI: Using IOAPIC for interrupt routing
May  5 07:40:59 user kernel: [    0.520239] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  5 07:40:59 user kernel: [    0.520317] PCI: 0000:00:00.0 reg 10 32bit mmio: [d0000000, d7ffffff]
May  5 07:40:59 user kernel: [    0.520386] PCI: 0000:00:01.1 reg 20 io port: [1c00, 1c3f]
May  5 07:40:59 user kernel: [    0.520391] PCI: 0000:00:01.1 reg 24 io port: [2000, 203f]
May  5 07:40:59 user kernel: [    0.520400] pci 0000:00:01.1: PME# supported from D3hot D3cold
May  5 07:40:59 user kernel: [    0.520404] pci 0000:00:01.1: PME# disabled
May  5 07:40:59 user kernel: [    0.520422] PCI: 0000:00:02.0 reg 10 32bit mmio: [e4003000, e4003fff]
May  5 07:40:59 user kernel: [    0.520439] pci 0000:00:02.0: supports D1
May  5 07:40:59 user kernel: [    0.520441] pci 0000:00:02.0: supports D2
May  5 07:40:59 user kernel: [    0.520443] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520446] pci 0000:00:02.0: PME# disabled
May  5 07:40:59 user kernel: [    0.520460] PCI: 0000:00:02.1 reg 10 32bit mmio: [e4004000, e4004fff]
May  5 07:40:59 user kernel: [    0.520477] pci 0000:00:02.1: supports D1
May  5 07:40:59 user kernel: [    0.520479] pci 0000:00:02.1: supports D2
May  5 07:40:59 user kernel: [    0.520481] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520484] pci 0000:00:02.1: PME# disabled
May  5 07:40:59 user kernel: [    0.520501] PCI: 0000:00:02.2 reg 10 32bit mmio: [e4005000, e40050ff]
May  5 07:40:59 user kernel: [    0.520521] pci 0000:00:02.2: supports D1
May  5 07:40:59 user kernel: [    0.520522] pci 0000:00:02.2: supports D2
May  5 07:40:59 user kernel: [    0.520525] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520528] pci 0000:00:02.2: PME# disabled
May  5 07:40:59 user kernel: [    0.520549] PCI: 0000:00:06.0 reg 10 io port: [d400, d4ff]
May  5 07:40:59 user kernel: [    0.520553] PCI: 0000:00:06.0 reg 14 io port: [d800, d87f]
May  5 07:40:59 user kernel: [    0.520557] PCI: 0000:00:06.0 reg 18 32bit mmio: [e4001000, e4001fff]
May  5 07:40:59 user kernel: [    0.520571] pci 0000:00:06.0: supports D1
May  5 07:40:59 user kernel: [    0.520572] pci 0000:00:06.0: supports D2
May  5 07:40:59 user kernel: [    0.520592] PCI: 0000:00:08.0 reg 20 io port: [f000, f00f]
May  5 07:40:59 user kernel: [    0.520719] PCI: 0000:01:06.0 reg 10 io port: [9000, 903f]
May  5 07:40:59 user kernel: [    0.520748] pci 0000:01:06.0: supports D2
May  5 07:40:59 user kernel: [    0.520750] pci 0000:01:06.0: PME# supported from D0 D2 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520754] pci 0000:01:06.0: PME# disabled
May  5 07:40:59 user kernel: [    0.520774] PCI: 0000:01:07.0 reg 10 32bit mmio: [e3012000, e3012fff]
May  5 07:40:59 user kernel: [    0.520803] pci 0000:01:07.0: PME# supported from D0 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520807] pci 0000:01:07.0: PME# disabled
May  5 07:40:59 user kernel: [    0.520826] PCI: 0000:01:08.0 reg 10 32bit mmio: [e3000000, e300ffff]
May  5 07:40:59 user kernel: [    0.520831] PCI: 0000:01:08.0 reg 14 io port: [9400, 9407]
May  5 07:40:59 user kernel: [    0.520854] pci 0000:01:08.0: PME# supported from D3hot D3cold
May  5 07:40:59 user kernel: [    0.520857] pci 0000:01:08.0: PME# disabled
May  5 07:40:59 user kernel: [    0.520876] PCI: 0000:01:09.0 reg 10 io port: [9800, 98ff]
May  5 07:40:59 user kernel: [    0.520882] PCI: 0000:01:09.0 reg 14 32bit mmio: [e3010000, e30100ff]
May  5 07:40:59 user kernel: [    0.520906] pci 0000:01:09.0: supports D1
May  5 07:40:59 user kernel: [    0.520908] pci 0000:01:09.0: supports D2
May  5 07:40:59 user kernel: [    0.520910] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520913] pci 0000:01:09.0: PME# disabled
May  5 07:40:59 user kernel: [    0.520934] PCI: 0000:01:0b.0 reg 10 io port: [9c00, 9cff]
May  5 07:40:59 user kernel: [    0.520939] PCI: 0000:01:0b.0 reg 14 32bit mmio: [e3011000, e30110ff]
May  5 07:40:59 user kernel: [    0.520956] PCI: 0000:01:0b.0 reg 30 32bit mmio: [0, ffff]
May  5 07:40:59 user kernel: [    0.520966] pci 0000:01:0b.0: supports D1
May  5 07:40:59 user kernel: [    0.520968] pci 0000:01:0b.0: supports D2
May  5 07:40:59 user kernel: [    0.520970] pci 0000:01:0b.0: PME# supported from D1 D2 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520974] pci 0000:01:0b.0: PME# disabled
May  5 07:40:59 user kernel: [    0.520994] PCI: 0000:01:0d.0 reg 10 io port: [a000, a007]
May  5 07:40:59 user kernel: [    0.520999] PCI: 0000:01:0d.0 reg 14 io port: [a400, a403]
May  5 07:40:59 user kernel: [    0.521004] PCI: 0000:01:0d.0 reg 18 io port: [a800, a807]
May  5 07:40:59 user kernel: [    0.521009] PCI: 0000:01:0d.0 reg 1c io port: [ac00, ac03]
May  5 07:40:59 user kernel: [    0.521014] PCI: 0000:01:0d.0 reg 20 io port: [b000, b00f]
May  5 07:40:59 user kernel: [    0.521020] PCI: 0000:01:0d.0 reg 24 32bit mmio: [e3013000, e30131ff]
May  5 07:40:59 user kernel: [    0.521025] PCI: 0000:01:0d.0 reg 30 32bit mmio: [0, 7ffff]
May  5 07:40:59 user kernel: [    0.521035] pci 0000:01:0d.0: supports D1
May  5 07:40:59 user kernel: [    0.521037] pci 0000:01:0d.0: supports D2
May  5 07:40:59 user kernel: [    0.521054] PCI: bridge 0000:00:0a.0 io port: [9000, bfff]
May  5 07:40:59 user kernel: [    0.521057] PCI: bridge 0000:00:0a.0 32bit mmio: [e2000000, e3ffffff]
May  5 07:40:59 user kernel: [    0.521091] PCI: 0000:02:00.0 reg 10 32bit mmio: [d8000000, dbffffff]
May  5 07:40:59 user kernel: [    0.521097] PCI: 0000:02:00.0 reg 14 io port: [c000, c0ff]
May  5 07:40:59 user kernel: [    0.521103] PCI: 0000:02:00.0 reg 18 32bit mmio: [e1000000, e100ffff]
May  5 07:40:59 user kernel: [    0.521120] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, 1ffff]
May  5 07:40:59 user kernel: [    0.521135] pci 0000:02:00.0: supports D1
May  5 07:40:59 user kernel: [    0.521137] pci 0000:02:00.0: supports D2
May  5 07:40:59 user kernel: [    0.521159] PCI: 0000:02:00.1 reg 10 32bit mmio: [dc000000, dfffffff]
May  5 07:40:59 user kernel: [    0.521165] PCI: 0000:02:00.1 reg 14 32bit mmio: [e1010000, e101ffff]
May  5 07:40:59 user kernel: [    0.521195] pci 0000:02:00.1: supports D1
May  5 07:40:59 user kernel: [    0.521197] pci 0000:02:00.1: supports D2
May  5 07:40:59 user kernel: [    0.521234] PCI: bridge 0000:00:0b.0 io port: [c000, cfff]
May  5 07:40:59 user kernel: [    0.521238] PCI: bridge 0000:00:0b.0 32bit mmio: [e0000000, e1ffffff]
May  5 07:40:59 user kernel: [    0.521242] PCI: bridge 0000:00:0b.0 32bit mmio pref: [d8000000, dfffffff]
May  5 07:40:59 user kernel: [    0.521251] bus 00 -> node 0
May  5 07:40:59 user kernel: [    0.521257] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May  5 07:40:59 user kernel: [    0.521454] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
May  5 07:40:59 user kernel: [    0.521872] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
May  5 07:40:59 user kernel: [    0.575503] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May  5 07:40:59 user kernel: [    0.575685] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:40:59 user kernel: [    0.575865] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  5 07:40:59 user kernel: [    0.576044] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  5 07:40:59 user kernel: [    0.576224] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May  5 07:40:59 user kernel: [    0.576403] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:40:59 user kernel: [    0.576583] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:40:59 user kernel: [    0.576762] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.576946] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.577127] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:40:59 user kernel: [    0.577305] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.577486] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  5 07:40:59 user kernel: [    0.577668] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:40:59 user kernel: [    0.577848] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.578027] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.578206] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.578394] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.578543] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
May  5 07:40:59 user kernel: [    0.578683] ACPI: PCI Interrupt Link [APC2] (IRQs *17)
May  5 07:40:59 user kernel: [    0.578822] ACPI: PCI Interrupt Link [APC3] (IRQs *18)
May  5 07:40:59 user kernel: [    0.578961] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
May  5 07:40:59 user kernel: [    0.579100] ACPI: PCI Interrupt Link [APC5] (IRQs *16)
May  5 07:40:59 user kernel: [    0.579303] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
May  5 07:40:59 user kernel: [    0.579505] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
May  5 07:40:59 user kernel: [    0.579705] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.579906] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.580130] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
May  5 07:40:59 user kernel: [    0.580329] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.580470] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
May  5 07:40:59 user kernel: [    0.580668] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
May  5 07:40:59 user kernel: [    0.580868] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.581068] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.581268] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.581476] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.581617] ACPI: Power Resource [ISAV] (on)
May  5 07:40:59 user kernel: [    0.581701] Linux Plug and Play Support v0.97 (c) Adam Belay
May  5 07:40:59 user kernel: [    0.581735] pnp: PnP ACPI init
May  5 07:40:59 user kernel: [    0.581743] ACPI: bus type pnp registered
May  5 07:40:59 user kernel: [    0.587831] pnp: PnP ACPI: found 15 devices
May  5 07:40:59 user kernel: [    0.587834] ACPI: ACPI bus type pnp unregistered
May  5 07:40:59 user kernel: [    0.587838] PnPBIOS: Disabled by ACPI PNP
May  5 07:40:59 user kernel: [    0.588165] PCI: Using ACPI for IRQ routing
May  5 07:40:59 user kernel: [    0.588283] NET: Registered protocol family 8
May  5 07:40:59 user kernel: [    0.588283] NET: Registered protocol family 20
May  5 07:40:59 user kernel: [    0.588283] NetLabel: Initializing
May  5 07:40:59 user kernel: [    0.588283] NetLabel:  domain hash size = 128
May  5 07:40:59 user kernel: [    0.588283] NetLabel:  protocols = UNLABELED CIPSOv4
May  5 07:40:59 user kernel: [    0.588283] NetLabel:  unlabeled traffic allowed by default
May  5 07:40:59 user kernel: [    0.588283] tracer: 772 pages allocated for 65536 entries of 48 bytes
May  5 07:40:59 user kernel: [    0.588283]    actual entries 65620
May  5 07:40:59 user kernel: [    0.588283] AppArmor: AppArmor Filesystem Enabled
May  5 07:40:59 user kernel: [    0.588283] ACPI: RTC can wake from S4
May  5 07:40:59 user kernel: [    0.588283] system 00:00: ioport range 0x1000-0x107f has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:00: ioport range 0x1080-0x10ff has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:00: ioport range 0x1400-0x147f has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:00: ioport range 0x1480-0x14ff has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:00: ioport range 0x1800-0x187f has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:00: ioport range 0x1880-0x18ff has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xd8800-0xdbfff has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xf0000-0xf7fff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xf8000-0xfbfff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xfc000-0xfffff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0x2fff0000-0x2fffffff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xffff0000-0xffffffff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0x0-0x9ffff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0x100000-0x2ffeffff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:03: ioport range 0x800-0x805 has been reserved
May  5 07:40:59 user kernel: [    0.624039] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:01
May  5 07:40:59 user kernel: [    0.624042] pci 0000:00:0a.0:   IO window: 0x9000-0xbfff
May  5 07:40:59 user kernel: [    0.624047] pci 0000:00:0a.0:   MEM window: 0xe2000000-0xe3ffffff
May  5 07:40:59 user kernel: [    0.624050] pci 0000:00:0a.0:   PREFETCH window: 0x00000040000000-0x000000400fffff
May  5 07:40:59 user kernel: [    0.624056] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
May  5 07:40:59 user kernel: [    0.624059] pci 0000:00:0b.0:   IO window: 0xc000-0xcfff
May  5 07:40:59 user kernel: [    0.624064] pci 0000:00:0b.0:   MEM window: 0xe0000000-0xe1ffffff
May  5 07:40:59 user kernel: [    0.624068] pci 0000:00:0b.0:   PREFETCH window: 0x000000d8000000-0x000000dfffffff
May  5 07:40:59 user kernel: [    0.624080] pci 0000:00:0a.0: setting latency timer to 64
May  5 07:40:59 user kernel: [    0.624087] bus: 00 index 0 io port: [0, ffff]
May  5 07:40:59 user kernel: [    0.624089] bus: 00 index 1 mmio: [0, ffffffffffffffff]
May  5 07:40:59 user kernel: [    0.624091] bus: 01 index 0 io port: [9000, bfff]
May  5 07:40:59 user kernel: [    0.624094] bus: 01 index 1 mmio: [e2000000, e3ffffff]
May  5 07:40:59 user kernel: [    0.624096] bus: 01 index 2 mmio: [40000000, 400fffff]
May  5 07:40:59 user kernel: [    0.624098] bus: 01 index 3 mmio: [0, 0]
May  5 07:40:59 user kernel: [    0.624100] bus: 02 index 0 io port: [c000, cfff]
May  5 07:40:59 user kernel: [    0.624102] bus: 02 index 1 mmio: [e0000000, e1ffffff]
May  5 07:40:59 user kernel: [    0.624105] bus: 02 index 2 mmio: [d8000000, dfffffff]
May  5 07:40:59 user kernel: [    0.624107] bus: 02 index 3 mmio: [0, 0]
May  5 07:40:59 user kernel: [    0.624119] NET: Registered protocol family 2
May  5 07:40:59 user kernel: [    0.624242] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May  5 07:40:59 user kernel: [    0.624564] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May  5 07:40:59 user kernel: [    0.625521] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May  5 07:40:59 user kernel: [    0.626040] TCP: Hash tables configured (established 131072 bind 65536)
May  5 07:40:59 user kernel: [    0.626044] TCP reno registered
May  5 07:40:59 user kernel: [    0.626150] NET: Registered protocol family 1
May  5 07:40:59 user kernel: [    0.626268] checking if image is initramfs... it is
May  5 07:40:59 user kernel: [    1.130030] Switched to high resolution mode on CPU 0
May  5 07:40:59 user kernel: [    1.270106] Freeing initrd memory: 7861k freed
May  5 07:40:59 user kernel: [    1.270859] audit: initializing netlink socket (disabled)
May  5 07:40:59 user kernel: [    1.270873] type=2000 audit(1241509236.270:1): initialized
May  5 07:40:59 user kernel: [    1.277046] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May  5 07:40:59 user kernel: [    1.279208] VFS: Disk quotas dquot_6.5.1
May  5 07:40:59 user kernel: [    1.279292] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  5 07:40:59 user kernel: [    1.279389] msgmni has been set to 1510
May  5 07:40:59 user kernel: [    1.279509] io scheduler noop registered
May  5 07:40:59 user kernel: [    1.279511] io scheduler anticipatory registered
May  5 07:40:59 user kernel: [    1.279514] io scheduler deadline registered (default)
May  5 07:40:59 user kernel: [    1.279525] io scheduler cfq registered
May  5 07:40:59 user kernel: [    1.320057] pci 0000:02:00.0: Boot video device
May  5 07:40:59 user kernel: [    1.320378] isapnp: Scanning for PnP cards...
May  5 07:40:59 user kernel: [    1.676735] isapnp: No Plug & Play device found
May  5 07:40:59 user kernel: [    1.712889] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
May  5 07:40:59 user kernel: [    1.713006] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  5 07:40:59 user kernel: [    1.713145] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  5 07:40:59 user kernel: [    1.713711] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  5 07:40:59 user kernel: [    1.713981] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  5 07:40:59 user kernel: [    1.714367] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
May  5 07:40:59 user kernel: [    1.714376] serial 0000:01:06.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
May  5 07:40:59 user kernel: [    1.717494] brd: module loaded
May  5 07:40:59 user kernel: [    1.717566] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May  5 07:40:59 user kernel: [    1.717682] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May  5 07:40:59 user kernel: [    1.717685] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May  5 07:40:59 user kernel: [    1.718259] serio: i8042 KBD port at 0x60,0x64 irq 1
May  5 07:40:59 user kernel: [    1.718714] mice: PS/2 mouse device common for all mice
May  5 07:40:59 user kernel: [    1.718846] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
May  5 07:40:59 user kernel: [    1.718869] rtc0: alarms up to one year, y3k
May  5 07:40:59 user kernel: [    1.718985] EISA: Probing bus 0 at eisa.0
May  5 07:40:59 user kernel: [    1.718993] Cannot allocate resource for EISA slot 1
May  5 07:40:59 user kernel: [    1.718996] Cannot allocate resource for EISA slot 2
May  5 07:40:59 user kernel: [    1.719011] EISA: Detected 0 cards.
May  5 07:40:59 user kernel: [    1.719015] cpuidle: using governor ladder
May  5 07:40:59 user kernel: [    1.719017] cpuidle: using governor menu
May  5 07:40:59 user kernel: [    1.719540] TCP cubic registered
May  5 07:40:59 user kernel: [    1.719566] Using IPI No-Shortcut mode
May  5 07:40:59 user kernel: [    1.719753] registered taskstats version 1
May  5 07:40:59 user kernel: [    1.719884]   Magic number: 9:241:672
May  5 07:40:59 user kernel: [    1.720092] rtc_cmos 00:05: setting system clock to 2009-05-05 07:40:37 UTC (1241509237)
May  5 07:40:59 user kernel: [    1.720096] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  5 07:40:59 user kernel: [    1.720098] EDD information not available.
May  5 07:40:59 user kernel: [    1.720424] Freeing unused kernel memory: 436k freed
May  5 07:40:59 user kernel: [    1.720543] Write protecting the kernel text: 2632k
May  5 07:40:59 user kernel: [    1.720590] Write protecting the kernel read-only data: 956k
May  5 07:40:59 user kernel: [    1.740827] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May  5 07:40:59 user kernel: [    1.850427] fuse init (API version 7.9)
May  5 07:40:59 user kernel: [    1.870946] ACPI: processor limited to max C-state 1
May  5 07:40:59 user kernel: [    1.871030] processor ACPI0007:00: registered as cooling_device0
May  5 07:40:59 user kernel: [    2.601656] usbcore: registered new interface driver usbfs
May  5 07:40:59 user kernel: [    2.601680] usbcore: registered new interface driver hub
May  5 07:40:59 user kernel: [    2.601717] usbcore: registered new device driver usb
May  5 07:40:59 user kernel: [    2.604469] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
May  5 07:40:59 user kernel: [    2.604479] ehci_hcd 0000:00:02.2: PCI INT C -> Link[APCL] -> GSI 22 (level, high) -> IRQ 22
May  5 07:40:59 user kernel: [    2.604492] ehci_hcd 0000:00:02.2: setting latency timer to 64
May  5 07:40:59 user kernel: [    2.604495] ehci_hcd 0000:00:02.2: EHCI Host Controller
May  5 07:40:59 user kernel: [    2.604543] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
May  5 07:40:59 user kernel: [    2.604570] ehci_hcd 0000:00:02.2: debug port 1
May  5 07:40:59 user kernel: [    2.604574] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
May  5 07:40:59 user kernel: [    2.604588] ehci_hcd 0000:00:02.2: irq 22, io mem 0xe4005000
May  5 07:40:59 user kernel: [    2.608456] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
May  5 07:40:59 user kernel: [    2.614237] No dock devices found.
May  5 07:40:59 user kernel: [    2.627729] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May  5 07:40:59 user kernel: [    2.627912] usb usb1: configuration #1 chosen from 1 choice
May  5 07:40:59 user kernel: [    2.627940] hub 1-0:1.0: USB hub found
May  5 07:40:59 user kernel: [    2.627953] hub 1-0:1.0: 6 ports detected
May  5 07:40:59 user kernel: [    2.666619] SCSI subsystem initialized
May  5 07:40:59 user kernel: [    2.717185] libata version 3.00 loaded.
May  5 07:40:59 user kernel: [    2.840739] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
May  5 07:40:59 user kernel: [    2.840749] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, high) -> IRQ 21
May  5 07:40:59 user kernel: [    2.840766] ohci_hcd 0000:00:02.0: setting latency timer to 64
May  5 07:40:59 user kernel: [    2.840769] ohci_hcd 0000:00:02.0: OHCI Host Controller
May  5 07:40:59 user kernel: [    2.840794] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
May  5 07:40:59 user kernel: [    2.840816] ohci_hcd 0000:00:02.0: irq 21, io mem 0xe4003000
May  5 07:40:59 user kernel: [    2.902258] usb usb2: configuration #1 chosen from 1 choice
May  5 07:40:59 user kernel: [    2.902288] hub 2-0:1.0: USB hub found
May  5 07:40:59 user kernel: [    2.902300] hub 2-0:1.0: 3 ports detected
May  5 07:40:59 user kernel: [    3.120634] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
May  5 07:40:59 user kernel: [    3.120644] ohci_hcd 0000:00:02.1: PCI INT B -> Link[APCG] -> GSI 20 (level, high) -> IRQ 20
May  5 07:40:59 user kernel: [    3.120661] ohci_hcd 0000:00:02.1: setting latency timer to 64
May  5 07:40:59 user kernel: [    3.120664] ohci_hcd 0000:00:02.1: OHCI Host Controller
May  5 07:40:59 user kernel: [    3.120689] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
May  5 07:40:59 user kernel: [    3.120712] ohci_hcd 0000:00:02.1: irq 20, io mem 0xe4004000
May  5 07:40:59 user kernel: [    3.182218] usb usb3: configuration #1 chosen from 1 choice
May  5 07:40:59 user kernel: [    3.182254] hub 3-0:1.0: USB hub found
May  5 07:40:59 user kernel: [    3.182266] hub 3-0:1.0: 3 ports detected
May  5 07:40:59 user kernel: [    3.290440] pata_acpi 0000:00:08.0: power state changed by ACPI to D0
May  5 07:40:59 user kernel: [    3.290491] pata_acpi 0000:00:08.0: setting latency timer to 64
May  5 07:40:59 user kernel: [    3.290965] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
May  5 07:40:59 user kernel: [    3.291145] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
May  5 07:40:59 user kernel: [    3.291154] r8169 0000:01:0b.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
May  5 07:40:59 user kernel: [    3.291452] eth1: RTL8169s at 0xf082a000, 00:0d:61:21:54:d2, XID 00800000 IRQ 19
May  5 07:40:59 user kernel: [    3.294794] VIA Networking Velocity Family Gigabit Ethernet Adapter Driver Ver. 1.14
May  5 07:40:59 user kernel: [    3.294797] Copyright (c) 2002, 2003 VIA Networking Technologies, Inc.
May  5 07:40:59 user kernel: [    3.294799] Copyright (c) 2004 Red Hat Inc.
May  5 07:40:59 user kernel: [    3.294952] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
May  5 07:40:59 user kernel: [    3.294957] via-velocity 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
May  5 07:40:59 user kernel: [    3.295625] eth0: VIA Networking Velocity Family Gigabit Ethernet Adapter
May  5 07:40:59 user kernel: [    3.295628] eth0: Ethernet Address: 00:A0:C5:30:02:07
May  5 07:40:59 user kernel: [    3.310368] sata_sil 0000:01:0d.0: version 2.3
May  5 07:40:59 user kernel: [    3.310412] sata_sil 0000:01:0d.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
May  5 07:40:59 user kernel: [    3.310432] sata_sil 0000:01:0d.0: Applying R_ERR on DMA activate FIS errata fix
May  5 07:40:59 user kernel: [    3.310512] scsi0 : sata_sil
May  5 07:40:59 user kernel: [    3.310610] scsi1 : sata_sil
May  5 07:40:59 user kernel: [    3.310644] ata1: SATA max UDMA/100 mmio m512@0xe3013000 tf 0xe3013080 irq 17
May  5 07:40:59 user kernel: [    3.310647] ata2: SATA max UDMA/100 mmio m512@0xe3013000 tf 0xe30130c0 irq 17
May  5 07:40:59 user kernel: [    3.320105] usb 2-1: new full speed USB device using ohci_hcd and address 2
May  5 07:40:59 user kernel: [    3.546248] usb 2-1: configuration #1 chosen from 1 choice
May  5 07:40:59 user kernel: [    3.660031] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
May  5 07:40:59 user kernel: [    3.680428] ata1.00: ATA-6: ST3120827AS, 3.42, max UDMA/133
May  5 07:40:59 user kernel: [    3.680431] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
May  5 07:40:59 user kernel: [    3.720397] ata1.00: configured for UDMA/100
May  5 07:40:59 user kernel: [    3.890012] usb 2-2: new full speed USB device using ohci_hcd and address 3
May  5 07:40:59 user kernel: [    4.070021] ata2: SATA link down (SStatus 0 SControl 310)
May  5 07:40:59 user kernel: [    4.070135] scsi 0:0:0:0: Direct-Access     ATA      ST3120827AS      3.42 PQ: 0 ANSI: 5
May  5 07:40:59 user kernel: [    4.073806] pata_amd 0000:00:08.0: version 0.3.10
May  5 07:40:59 user kernel: [    4.073892] pata_amd 0000:00:08.0: power state changed by ACPI to D0
May  5 07:40:59 user kernel: [    4.073938] pata_amd 0000:00:08.0: setting latency timer to 64
May  5 07:40:59 user kernel: [    4.074002] scsi2 : pata_amd
May  5 07:40:59 user kernel: [    4.074072] scsi3 : pata_amd
May  5 07:40:59 user kernel: [    4.074927] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
May  5 07:40:59 user kernel: [    4.074930] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
May  5 07:40:59 user kernel: [    4.084358] scsi 0:0:0:0: Attached scsi generic sg0 type 0
May  5 07:40:59 user kernel: [    4.096951] Driver 'sd' needs updating - please use bus_type methods
May  5 07:40:59 user kernel: [    4.097068] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
May  5 07:40:59 user kernel: [    4.097086] sd 0:0:0:0: [sda] Write Protect is off
May  5 07:40:59 user kernel: [    4.097089] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  5 07:40:59 user kernel: [    4.097116] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:40:59 user kernel: [    4.097180] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
May  5 07:40:59 user kernel: [    4.097195] sd 0:0:0:0: [sda] Write Protect is off
May  5 07:40:59 user kernel: [    4.097197] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  5 07:40:59 user kernel: [    4.097222] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:40:59 user kernel: [    4.097226]  sda: sda1 sda2 <<6>usb 2-2: configuration #1 chosen from 1 choice
May  5 07:40:59 user kernel: [    4.123339]  sda5 sda6 sda7 >
May  5 07:40:59 user kernel: [    4.145863] sd 0:0:0:0: [sda] Attached SCSI disk
May  5 07:40:59 user kernel: [    4.310433] ata3.00: ATA-6: ST380011A, 8.01, max UDMA/100
May  5 07:40:59 user kernel: [    4.310437] ata3.00: 156301488 sectors, multi 16: LBA48 
May  5 07:40:59 user kernel: [    4.310452] ata3: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc60000c0) ACPI=0x3f01f (20:600:0x13)
May  5 07:40:59 user kernel: [    4.350355] ata3.00: configured for UDMA/100
May  5 07:40:59 user kernel: [    4.450011] usb 2-3: new low speed USB device using ohci_hcd and address 4
May  5 07:40:59 user kernel: [    4.540297] ata4.01: ATAPI: _NEC DVD_RW ND-1300A, 1.08, max UDMA/33
May  5 07:40:59 user kernel: [    4.540310] ata4: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc60000c0) ACPI=0x701f (600:60:0x1c)
May  5 07:40:59 user kernel: [    4.580238] ata4.01: configured for UDMA/33
May  5 07:40:59 user kernel: [    4.580345] scsi 2:0:0:0: Direct-Access     ATA      ST380011A        8.01 PQ: 0 ANSI: 5
May  5 07:40:59 user kernel: [    4.580527] scsi 2:0:0:0: Attached scsi generic sg1 type 0
May  5 07:40:59 user kernel: [    4.583519] scsi 3:0:1:0: CD-ROM            _NEC     DVD_RW ND-1300A  1.08 PQ: 0 ANSI: 5
May  5 07:40:59 user kernel: [    4.583615] scsi 3:0:1:0: Attached scsi generic sg2 type 5
May  5 07:40:59 user kernel: [    4.584668] sd 2:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
May  5 07:40:59 user kernel: [    4.584807] sd 2:0:0:0: [sdb] Write Protect is off
May  5 07:40:59 user kernel: [    4.584810] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May  5 07:40:59 user kernel: [    4.584839] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:40:59 user kernel: [    4.584916] sd 2:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
May  5 07:40:59 user kernel: [    4.584930] sd 2:0:0:0: [sdb] Write Protect is off
May  5 07:40:59 user kernel: [    4.584933] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May  5 07:40:59 user kernel: [    4.584957] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:40:59 user kernel: [    4.584962]  sdb: sdb1 < sdb5<4>Driver 'sr' needs updating - please use bus_type methods
May  5 07:40:59 user kernel: [    4.616528]  sdb6 >
May  5 07:40:59 user kernel: [    4.616678] sd 2:0:0:0: [sdb] Attached SCSI disk
May  5 07:40:59 user kernel: [    4.630705] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
May  5 07:40:59 user kernel: [    4.630711] Uniform CD-ROM driver Revision: 3.20
May  5 07:40:59 user kernel: [    4.630818] sr 3:0:1:0: Attached scsi CD-ROM sr0
May  5 07:40:59 user kernel: [    4.686279] usb 2-3: configuration #1 chosen from 1 choice
May  5 07:40:59 user kernel: [    4.689778] usbcore: registered new interface driver hiddev
May  5 07:40:59 user kernel: [    4.696191] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.3/input/input2
May  5 07:40:59 user kernel: [    4.702897] input,hidraw0: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:02.0-2
May  5 07:40:59 user kernel: [    4.708407] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input3
May  5 07:40:59 user kernel: [    4.708727] input,hidraw1: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:02.0-3
May  5 07:40:59 user kernel: [    4.708748] usbcore: registered new interface driver usbhid
May  5 07:40:59 user kernel: [    4.708752] usbhid: v2.6:USB HID core driver
May  5 07:40:59 user kernel: [    5.093416] PM: Starting manual resume from disk
May  5 07:40:59 user kernel: [    5.093421] PM: Resume from partition 8:5
May  5 07:40:59 user kernel: [    5.093423] PM: Checking hibernation image.
May  5 07:40:59 user kernel: [    5.093587] PM: Resume from disk failed.
May  5 07:40:59 user kernel: [    5.157817] kjournald starting.  Commit interval 5 seconds
May  5 07:40:59 user kernel: [    5.157833] EXT3-fs: mounted filesystem with ordered data mode.
May  5 07:40:59 user kernel: [    8.220829] udevd version 124 started
May  5 07:40:59 user kernel: [    9.029189] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  5 07:40:59 user kernel: [    9.051929] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  5 07:40:59 user kernel: [    9.086174] Linux agpgart interface v0.103
May  5 07:40:59 user kernel: [    9.143279] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
May  5 07:40:59 user kernel: [    9.143311] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
May  5 07:40:59 user kernel: [    9.147249] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
May  5 07:40:59 user kernel: [    9.331787] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
May  5 07:40:59 user kernel: [    9.331807] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2000
May  5 07:40:59 user kernel: [    9.383350] input: PC Speaker as /devices/platform/pcspkr/input/input4
May  5 07:40:59 user kernel: [    9.477715] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input5
May  5 07:40:59 user kernel: [    9.510034] ACPI: Power Button (FF) [PWRF]
May  5 07:40:59 user kernel: [    9.510126] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
May  5 07:40:59 user kernel: [    9.535525] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
May  5 07:40:59 user kernel: [    9.535532] Intel ICH 0000:00:06.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, high) -> IRQ 22
May  5 07:40:59 user kernel: [    9.535555] Intel ICH 0000:00:06.0: setting latency timer to 64
May  5 07:40:59 user kernel: [    9.550035] ACPI: Power Button (CM) [PWRB]
May  5 07:40:59 user kernel: [    9.807796] ieee80211_crypt: registered algorithm 'NULL'
May  5 07:40:59 user kernel: [    9.822266] ieee80211: 802.11 data/management/control stack, git-1.1.13
May  5 07:40:59 user kernel: [    9.822271] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
May  5 07:40:59 user kernel: [    9.880039] intel8x0_measure_ac97_clock: measured 57828 usecs
May  5 07:40:59 user kernel: [    9.880043] intel8x0: clocking to 48000
May  5 07:40:59 user kernel: [    9.897410] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
May  5 07:40:59 user kernel: [    9.897414] ipw2200: Copyright(c) 2003-2006 Intel Corporation
May  5 07:40:59 user kernel: [    9.897511] ipw2200 0000:01:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
May  5 07:40:59 user kernel: [    9.897558] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
May  5 07:40:59 user kernel: [    9.897614] firmware: requesting ipw2200-bss.fw
May  5 07:40:59 user kernel: [   10.331980] parport_pc 00:0b: reported by Plug and Play ACPI
May  5 07:40:59 user kernel: [   10.332022] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
May  5 07:40:59 user kernel: [   11.986348] cdc_acm 2-1:1.0: ttyACM0: USB ACM device
May  5 07:40:59 user kernel: [   13.916024] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
May  5 07:40:59 user kernel: [   13.917216] udev: renamed network interface eth1 to eth0
May  5 07:40:59 user kernel: [   13.967450] udev: renamed network interface eth0_rename to eth1
May  5 07:40:59 user kernel: [   17.142675] usbcore: registered new interface driver cdc_acm
May  5 07:40:59 user kernel: [   17.142681] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
May  5 07:40:59 user kernel: [   17.147471] usbcore: registered new interface driver snd-usb-audio
May  5 07:40:59 user kernel: [   17.840833] loop: module loaded
May  5 07:40:59 user kernel: [   17.854783] lp0: using parport0 (interrupt-driven).
May  5 07:40:59 user kernel: [   18.356446] Adding 248936k swap on /dev/sdb5.  Priority:-1 extents:1 across:248936k
May  5 07:40:59 user kernel: [   18.740220] EXT3 FS on sdb6, internal journal
May  5 07:40:59 user kernel: [   19.903078] ip_tables: (C) 2000-2006 Netfilter Core Team
May  5 07:40:59 user kernel: [   19.954301] r8169: eth0: link up
May  5 07:40:59 user kernel: [   21.294121] NET: Registered protocol family 17
May  5 07:40:59 user kernel: [   21.444253] Velocity is AUTO mode
May  5 07:40:59 user kernel: [   21.878328] NET: Registered protocol family 10
May  5 07:40:59 user kernel: [   21.878844] lo: Disabled Privacy Extensions
May  5 07:41:00 user pptpd[4405]: MGR: connections limit (100) reached, extra IP addresses ignored
May  5 07:41:00 user pptpd[4406]: MGR: Manager process started
May  5 07:41:00 user pptpd[4406]: MGR: Maximum of 100 connections available
May  5 07:41:02 user kernel: [   25.940152] warning: `dhcpd3' uses 32-bit capabilities (legacy support in use)
May  5 07:41:02 user dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  5 07:41:02 user dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  5 07:41:02 user dhcpd: All rights reserved.
May  5 07:41:02 user dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  5 07:41:02 user dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  5 07:41:02 user dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  5 07:41:02 user dhcpd: All rights reserved.
May  5 07:41:02 user dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  5 07:41:02 user dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  5 07:41:02 user dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  5 07:41:02 user dhcpd: All rights reserved.
May  5 07:41:02 user dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  5 07:41:02 user dhcpd: Wrote 3 leases to leases file.
May  5 07:41:02 user ntpdate[4010]: no server suitable for synchronization found
May  5 07:41:04 user /usr/sbin/cron[4611]: (CRON) INFO (pidfile fd = 3)
May  5 07:41:04 user /usr/sbin/cron[4612]: (CRON) STARTUP (fork ok)
May  5 07:41:04 user /usr/sbin/cron[4612]: (CRON) INFO (Running @reboot jobs)
May  5 07:41:06 user ntpdate[4573]: no server suitable for synchronization found
May  5 07:41:08 user kernel: [   32.160006] eth1: no IPv6 routers present
May  5 07:41:08 user kernel: [   32.730007] eth0: no IPv6 routers present
May  5 07:42:16 user pptpd[4704]: MGR: connections limit (100) reached, extra IP addresses ignored
May  5 07:42:16 user pptpd[4705]: MGR: Manager process started
May  5 07:42:16 user pptpd[4705]: MGR: Maximum of 100 connections available
May  5 07:42:56 user init: tty4 main process (4309) killed by TERM signal
May  5 07:42:56 user init: tty5 main process (4310) killed by TERM signal
May  5 07:42:56 user init: tty2 main process (4319) killed by TERM signal
May  5 07:42:56 user init: tty3 main process (4321) killed by TERM signal
May  5 07:42:56 user init: tty6 main process (4323) killed by TERM signal
May  5 07:42:56 user init: tty1 main process (4622) killed by TERM signal
May  5 07:42:56 user console-kit-daemon[4425]: WARNING: Unable to activate console: No such device or address 
May  5 07:42:58 user exiting on signal 15
May  6 07:31:18 user syslogd 1.5.0#2ubuntu6: restart.
May  6 07:31:18 user kernel: Inspecting /boot/System.map-2.6.27-7-server
May  6 07:31:18 user kernel: Cannot find map file.
May  6 07:31:18 user kernel: Loaded 48877 symbols from 70 modules.
May  6 07:31:18 user kernel: [    0.000000] Initializing cgroup subsys cpuset
May  6 07:31:18 user kernel: [    0.000000] Initializing cgroup subsys cpu
May  6 07:31:18 user kernel: [    0.000000] Linux version 2.6.27-7-server (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 20:18:35 UTC 2008 (Ubuntu 2.6.27-7.16-server)
May  6 07:31:18 user kernel: [    0.000000] BIOS-provided physical RAM map:
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
May  6 07:31:18 user kernel: [    0.000000] last_pfn = 0x2fff0 max_arch_pfn = 0x1000000
May  6 07:31:18 user kernel: [    0.000000] kernel direct mapping tables up to 2fff0000 @ 7000-d000
May  6 07:31:18 user kernel: [    0.000000] NX (Execute Disable) protection: active
May  6 07:31:18 user kernel: [    0.000000] RAMDISK: 2f832000 - 2ffdf6b8
May  6 07:31:18 user kernel: [    0.000000] DMI 2.3 present.
May  6 07:31:18 user kernel: [    0.000000] ACPI: RSDP 000F6AB0, 0014 (r0 Nvidia)
May  6 07:31:18 user kernel: [    0.000000] ACPI: RSDT 2FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  6 07:31:18 user kernel: [    0.000000] ACPI: FACP 2FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  6 07:31:18 user kernel: [    0.000000] ACPI: DSDT 2FFF30C0, 4ABF (r1 NVIDIA AWRDACPI     1000 MSFT  100000C)
May  6 07:31:18 user kernel: [    0.000000] ACPI: FACS 2FFF0000, 0040
May  6 07:31:18 user kernel: [    0.000000] ACPI: APIC 2FFF7B80, 005A (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  6 07:31:18 user kernel: [    0.000000] 0MB HIGHMEM available.
May  6 07:31:18 user kernel: [    0.000000] 767MB LOWMEM available.
May  6 07:31:18 user kernel: [    0.000000]   mapped low ram: 0 - 2fff0000
May  6 07:31:18 user kernel: [    0.000000]   low ram: 00000000 - 2fff0000
May  6 07:31:18 user kernel: [    0.000000]   bootmap 0000a000 - 00010000
May  6 07:31:18 user kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002fff0000]
May  6 07:31:18 user kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
May  6 07:31:18 user kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
May  6 07:31:18 user kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
May  6 07:31:18 user kernel: [    0.000000]   #3 [0000100000 - 00005e8220]    TEXT DATA BSS ==> [0000100000 - 00005e8220]
May  6 07:31:18 user kernel: [    0.000000]   #4 [002f832000 - 002ffdf6b8]          RAMDISK ==> [002f832000 - 002ffdf6b8]
May  6 07:31:18 user kernel: [    0.000000]   #5 [00005e9000 - 00005f1000]    INIT_PG_TABLE ==> [00005e9000 - 00005f1000]
May  6 07:31:18 user kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
May  6 07:31:18 user kernel: [    0.000000]   #7 [0000007000 - 000000a000]          PGTABLE ==> [0000007000 - 000000a000]
May  6 07:31:18 user kernel: [    0.000000]   #8 [000000a000 - 0000010000]          BOOTMAP ==> [000000a000 - 0000010000]
May  6 07:31:18 user kernel: [    0.000000] found SMP MP-table at [c00f5000] 000f5000
May  6 07:31:18 user kernel: [    0.000000] Zone PFN ranges:
May  6 07:31:18 user kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
May  6 07:31:18 user kernel: [    0.000000]   Normal   0x00001000 -> 0x0002fff0
May  6 07:31:18 user kernel: [    0.000000]   HighMem  0x0002fff0 -> 0x0002fff0
May  6 07:31:18 user kernel: [    0.000000] Movable zone start PFN for each node
May  6 07:31:18 user kernel: [    0.000000] early_node_map[2] active PFN ranges
May  6 07:31:18 user kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
May  6 07:31:18 user kernel: [    0.000000]     0: 0x00000100 -> 0x0002fff0
May  6 07:31:18 user kernel: [    0.000000] On node 0 totalpages: 196495
May  6 07:31:18 user kernel: [    0.000000] free_area_init_node: node 0, pgdat c049eb00, node_mem_map c1000000
May  6 07:31:18 user kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
May  6 07:31:18 user kernel: [    0.000000]   Normal zone: 190804 pages, LIFO batch:31
May  6 07:31:18 user kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
May  6 07:31:18 user kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
May  6 07:31:18 user kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
May  6 07:31:18 user kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  6 07:31:18 user kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  6 07:31:18 user kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
May  6 07:31:18 user kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  6 07:31:18 user kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
May  6 07:31:18 user kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  6 07:31:18 user kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
May  6 07:31:18 user kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  6 07:31:18 user kernel: [    0.000000] ACPI: IRQ9 used by override.
May  6 07:31:18 user kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  6 07:31:18 user kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  6 07:31:18 user kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
May  6 07:31:18 user kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
May  6 07:31:18 user kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
May  6 07:31:18 user kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May  6 07:31:18 user kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
May  6 07:31:18 user kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
May  6 07:31:18 user kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
May  6 07:31:18 user kernel: [    0.000000] PERCPU: Allocating 45852 bytes of per cpu data
May  6 07:31:18 user kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
May  6 07:31:18 user kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194767
May  6 07:31:18 user kernel: [    0.000000] Kernel command line: root=UUID=3a16f219-3073-4cf3-8fa0-646d16cda612 ro quiet splash 
May  6 07:31:18 user kernel: [    0.000000] Enabling fast FPU save and restore... done.
May  6 07:31:18 user kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May  6 07:31:18 user kernel: [    0.000000] Initializing CPU#0
May  6 07:31:18 user kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
May  6 07:31:18 user kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
May  6 07:31:18 user kernel: [    0.000000] TSC: using PIT calibration value
May  6 07:31:18 user kernel: [    0.000000] Detected 1994.814 MHz processor.
May  6 07:31:18 user kernel: [    0.010000] spurious 8259A interrupt: IRQ7.
May  6 07:31:18 user kernel: [    0.010000] Console: colour VGA+ 80x25
May  6 07:31:18 user kernel: [    0.010000] console [tty0] enabled
May  6 07:31:18 user kernel: [    0.010000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  6 07:31:18 user kernel: [    0.010000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  6 07:31:18 user kernel: [    0.010000] Memory: 765068k/786368k available (2628k kernel code, 20728k reserved, 1201k data, 436k init, 0k highmem)
May  6 07:31:18 user kernel: [    0.010000] virtual kernel memory layout:
May  6 07:31:18 user kernel: [    0.010000]     fixmap  : 0xffc78000 - 0xfffff000   (3612 kB)
May  6 07:31:18 user kernel: [    0.010000]     pkmap   : 0xff800000 - 0xffa00000   (2048 kB)
May  6 07:31:18 user kernel: [    0.010000]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
May  6 07:31:18 user kernel: [    0.010000]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
May  6 07:31:18 user kernel: [    0.010000]       .init : 0xc04c3000 - 0xc0530000   ( 436 kB)
May  6 07:31:18 user kernel: [    0.010000]       .data : 0xc0391036 - 0xc04bd800   (1201 kB)
May  6 07:31:18 user kernel: [    0.010000]       .text : 0xc0100000 - 0xc0391036   (2628 kB)
May  6 07:31:18 user kernel: [    0.010000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
May  6 07:31:18 user kernel: [    0.010000] CPA: page pool initialized 1 of 1 pages preallocated
May  6 07:31:18 user kernel: [    0.010000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
May  6 07:31:18 user kernel: [    0.010008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.62 BogoMIPS (lpj=19948140)
May  6 07:31:18 user kernel: [    0.010026] Security Framework initialized
May  6 07:31:18 user kernel: [    0.010033] SELinux:  Disabled at boot.
May  6 07:31:18 user kernel: [    0.010053] AppArmor: AppArmor initialized
May  6 07:31:18 user kernel: [    0.010061] Mount-cache hash table entries: 512
May  6 07:31:18 user kernel: [    0.010209] Initializing cgroup subsys ns
May  6 07:31:18 user kernel: [    0.010213] Initializing cgroup subsys cpuacct
May  6 07:31:18 user kernel: [    0.010215] Initializing cgroup subsys memory
May  6 07:31:18 user kernel: [    0.010229] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May  6 07:31:18 user kernel: [    0.010232] CPU: L2 Cache: 512K (64 bytes/line)
May  6 07:31:18 user kernel: [    0.010241] Checking 'hlt' instruction... OK.
May  6 07:31:18 user kernel: [    0.050367] SMP alternatives: switching to UP code
May  6 07:31:18 user kernel: [    0.056453] Freeing SMP alternatives: 11k freed
May  6 07:31:18 user kernel: [    0.056457] ACPI: Core revision 20080609
May  6 07:31:18 user kernel: [    0.057953] ACPI: Checking initramfs for custom DSDT
May  6 07:31:18 user kernel: [    0.371035] ENABLING IO-APIC IRQs
May  6 07:31:18 user kernel: [    0.371201] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
May  6 07:31:18 user kernel: [    0.471212] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 08
May  6 07:31:18 user kernel: [    0.480000] Brought up 1 CPUs
May  6 07:31:18 user kernel: [    0.480000] Total of 1 processors activated (3989.62 BogoMIPS).
May  6 07:31:18 user kernel: [    0.480000] CPU0 attaching sched-domain:
May  6 07:31:18 user kernel: [    0.480000]  domain 0: span 0 level CPU
May  6 07:31:18 user kernel: [    0.480000]   groups: 0
May  6 07:31:18 user kernel: [    0.480000] net_namespace: 840 bytes
May  6 07:31:18 user kernel: [    0.480000] Booting paravirtualized kernel on bare hardware
May  6 07:31:18 user kernel: [    0.480000] Time:  7:30:59  Date: 05/06/09
May  6 07:31:18 user kernel: [    0.480000] NET: Registered protocol family 16
May  6 07:31:18 user kernel: [    0.480000] EISA bus registered
May  6 07:31:18 user kernel: [    0.480000] ACPI: bus type pci registered
May  6 07:31:18 user kernel: [    0.500539] PCI: PCI BIOS revision 2.10 entry at 0xfac80, last bus=2
May  6 07:31:18 user kernel: [    0.500542] PCI: Using configuration type 1 for base access
May  6 07:31:18 user kernel: [    0.502219] ACPI: EC: Look up EC in DSDT
May  6 07:31:18 user kernel: [    0.509549] ACPI: Interpreter enabled
May  6 07:31:18 user kernel: [    0.509553] ACPI: (supports S0 S3 S4 S5)
May  6 07:31:18 user kernel: [    0.509567] ACPI: Using IOAPIC for interrupt routing
May  6 07:31:18 user kernel: [    0.520234] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  6 07:31:18 user kernel: [    0.520311] PCI: 0000:00:00.0 reg 10 32bit mmio: [d0000000, d7ffffff]
May  6 07:31:18 user kernel: [    0.520381] PCI: 0000:00:01.1 reg 20 io port: [1c00, 1c3f]
May  6 07:31:18 user kernel: [    0.520385] PCI: 0000:00:01.1 reg 24 io port: [2000, 203f]
May  6 07:31:18 user kernel: [    0.520395] pci 0000:00:01.1: PME# supported from D3hot D3cold
May  6 07:31:18 user kernel: [    0.520398] pci 0000:00:01.1: PME# disabled
May  6 07:31:18 user kernel: [    0.520416] PCI: 0000:00:02.0 reg 10 32bit mmio: [e4003000, e4003fff]
May  6 07:31:18 user kernel: [    0.520433] pci 0000:00:02.0: supports D1
May  6 07:31:18 user kernel: [    0.520435] pci 0000:00:02.0: supports D2
May  6 07:31:18 user kernel: [    0.520437] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520440] pci 0000:00:02.0: PME# disabled
May  6 07:31:18 user kernel: [    0.520454] PCI: 0000:00:02.1 reg 10 32bit mmio: [e4004000, e4004fff]
May  6 07:31:18 user kernel: [    0.520471] pci 0000:00:02.1: supports D1
May  6 07:31:18 user kernel: [    0.520473] pci 0000:00:02.1: supports D2
May  6 07:31:18 user kernel: [    0.520475] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520478] pci 0000:00:02.1: PME# disabled
May  6 07:31:18 user kernel: [    0.520496] PCI: 0000:00:02.2 reg 10 32bit mmio: [e4005000, e40050ff]
May  6 07:31:18 user kernel: [    0.520515] pci 0000:00:02.2: supports D1
May  6 07:31:18 user kernel: [    0.520517] pci 0000:00:02.2: supports D2
May  6 07:31:18 user kernel: [    0.520519] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520522] pci 0000:00:02.2: PME# disabled
May  6 07:31:18 user kernel: [    0.520543] PCI: 0000:00:06.0 reg 10 io port: [d400, d4ff]
May  6 07:31:18 user kernel: [    0.520547] PCI: 0000:00:06.0 reg 14 io port: [d800, d87f]
May  6 07:31:18 user kernel: [    0.520551] PCI: 0000:00:06.0 reg 18 32bit mmio: [e4001000, e4001fff]
May  6 07:31:18 user kernel: [    0.520565] pci 0000:00:06.0: supports D1
May  6 07:31:18 user kernel: [    0.520567] pci 0000:00:06.0: supports D2
May  6 07:31:18 user kernel: [    0.520586] PCI: 0000:00:08.0 reg 20 io port: [f000, f00f]
May  6 07:31:18 user kernel: [    0.520714] PCI: 0000:01:06.0 reg 10 io port: [9000, 903f]
May  6 07:31:18 user kernel: [    0.520742] pci 0000:01:06.0: supports D2
May  6 07:31:18 user kernel: [    0.520744] pci 0000:01:06.0: PME# supported from D0 D2 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520748] pci 0000:01:06.0: PME# disabled
May  6 07:31:18 user kernel: [    0.520769] PCI: 0000:01:07.0 reg 10 32bit mmio: [e3012000, e3012fff]
May  6 07:31:18 user kernel: [    0.520798] pci 0000:01:07.0: PME# supported from D0 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520802] pci 0000:01:07.0: PME# disabled
May  6 07:31:18 user kernel: [    0.520820] PCI: 0000:01:08.0 reg 10 32bit mmio: [e3000000, e300ffff]
May  6 07:31:18 user kernel: [    0.520826] PCI: 0000:01:08.0 reg 14 io port: [9400, 9407]
May  6 07:31:18 user kernel: [    0.520849] pci 0000:01:08.0: PME# supported from D3hot D3cold
May  6 07:31:18 user kernel: [    0.520852] pci 0000:01:08.0: PME# disabled
May  6 07:31:18 user kernel: [    0.520871] PCI: 0000:01:09.0 reg 10 io port: [9800, 98ff]
May  6 07:31:18 user kernel: [    0.520877] PCI: 0000:01:09.0 reg 14 32bit mmio: [e3010000, e30100ff]
May  6 07:31:18 user kernel: [    0.520901] pci 0000:01:09.0: supports D1
May  6 07:31:18 user kernel: [    0.520903] pci 0000:01:09.0: supports D2
May  6 07:31:18 user kernel: [    0.520905] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520908] pci 0000:01:09.0: PME# disabled
May  6 07:31:18 user kernel: [    0.520929] PCI: 0000:01:0b.0 reg 10 io port: [9c00, 9cff]
May  6 07:31:18 user kernel: [    0.520934] PCI: 0000:01:0b.0 reg 14 32bit mmio: [e3011000, e30110ff]
May  6 07:31:18 user kernel: [    0.520951] PCI: 0000:01:0b.0 reg 30 32bit mmio: [0, ffff]
May  6 07:31:18 user kernel: [    0.520961] pci 0000:01:0b.0: supports D1
May  6 07:31:18 user kernel: [    0.520963] pci 0000:01:0b.0: supports D2
May  6 07:31:18 user kernel: [    0.520965] pci 0000:01:0b.0: PME# supported from D1 D2 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520968] pci 0000:01:0b.0: PME# disabled
May  6 07:31:18 user kernel: [    0.520989] PCI: 0000:01:0d.0 reg 10 io port: [a000, a007]
May  6 07:31:18 user kernel: [    0.520994] PCI: 0000:01:0d.0 reg 14 io port: [a400, a403]
May  6 07:31:18 user kernel: [    0.520999] PCI: 0000:01:0d.0 reg 18 io port: [a800, a807]
May  6 07:31:18 user kernel: [    0.521004] PCI: 0000:01:0d.0 reg 1c io port: [ac00, ac03]
May  6 07:31:18 user kernel: [    0.521009] PCI: 0000:01:0d.0 reg 20 io port: [b000, b00f]
May  6 07:31:18 user kernel: [    0.521015] PCI: 0000:01:0d.0 reg 24 32bit mmio: [e3013000, e30131ff]
May  6 07:31:18 user kernel: [    0.521020] PCI: 0000:01:0d.0 reg 30 32bit mmio: [0, 7ffff]
May  6 07:31:18 user kernel: [    0.521030] pci 0000:01:0d.0: supports D1
May  6 07:31:18 user kernel: [    0.521032] pci 0000:01:0d.0: supports D2
May  6 07:31:18 user kernel: [    0.521049] PCI: bridge 0000:00:0a.0 io port: [9000, bfff]
May  6 07:31:18 user kernel: [    0.521052] PCI: bridge 0000:00:0a.0 32bit mmio: [e2000000, e3ffffff]
May  6 07:31:18 user kernel: [    0.521086] PCI: 0000:02:00.0 reg 10 32bit mmio: [d8000000, dbffffff]
May  6 07:31:18 user kernel: [    0.521092] PCI: 0000:02:00.0 reg 14 io port: [c000, c0ff]
May  6 07:31:18 user kernel: [    0.521098] PCI: 0000:02:00.0 reg 18 32bit mmio: [e1000000, e100ffff]
May  6 07:31:18 user kernel: [    0.521115] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, 1ffff]
May  6 07:31:18 user kernel: [    0.521130] pci 0000:02:00.0: supports D1
May  6 07:31:18 user kernel: [    0.521132] pci 0000:02:00.0: supports D2
May  6 07:31:18 user kernel: [    0.521154] PCI: 0000:02:00.1 reg 10 32bit mmio: [dc000000, dfffffff]
May  6 07:31:18 user kernel: [    0.521160] PCI: 0000:02:00.1 reg 14 32bit mmio: [e1010000, e101ffff]
May  6 07:31:18 user kernel: [    0.521190] pci 0000:02:00.1: supports D1
May  6 07:31:18 user kernel: [    0.521192] pci 0000:02:00.1: supports D2
May  6 07:31:18 user kernel: [    0.521229] PCI: bridge 0000:00:0b.0 io port: [c000, cfff]
May  6 07:31:18 user kernel: [    0.521233] PCI: bridge 0000:00:0b.0 32bit mmio: [e0000000, e1ffffff]
May  6 07:31:18 user kernel: [    0.521237] PCI: bridge 0000:00:0b.0 32bit mmio pref: [d8000000, dfffffff]
May  6 07:31:18 user kernel: [    0.521245] bus 00 -> node 0
May  6 07:31:18 user kernel: [    0.521252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May  6 07:31:18 user kernel: [    0.521449] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
May  6 07:31:18 user kernel: [    0.521868] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
May  6 07:31:18 user kernel: [    0.575515] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May  6 07:31:18 user kernel: [    0.575698] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  6 07:31:18 user kernel: [    0.575878] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  6 07:31:18 user kernel: [    0.576057] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  6 07:31:18 user kernel: [    0.576237] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May  6 07:31:18 user kernel: [    0.576416] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  6 07:31:18 user kernel: [    0.576596] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  6 07:31:18 user kernel: [    0.576775] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.576959] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.577140] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  6 07:31:18 user kernel: [    0.577318] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.577499] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  6 07:31:18 user kernel: [    0.577682] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  6 07:31:18 user kernel: [    0.577862] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.578041] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.578220] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.578408] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.578556] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
May  6 07:31:18 user kernel: [    0.578697] ACPI: PCI Interrupt Link [APC2] (IRQs *17)
May  6 07:31:18 user kernel: [    0.578836] ACPI: PCI Interrupt Link [APC3] (IRQs *18)
May  6 07:31:18 user kernel: [    0.578975] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
May  6 07:31:18 user kernel: [    0.579114] ACPI: PCI Interrupt Link [APC5] (IRQs *16)
May  6 07:31:18 user kernel: [    0.579317] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
May  6 07:31:18 user kernel: [    0.579519] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
May  6 07:31:18 user kernel: [    0.579719] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.579920] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.580144] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
May  6 07:31:18 user kernel: [    0.580343] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.580484] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
May  6 07:31:18 user kernel: [    0.580682] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
May  6 07:31:18 user kernel: [    0.580882] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.581082] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.581282] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.581490] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.581631] ACPI: Power Resource [ISAV] (on)
May  6 07:31:18 user kernel: [    0.581715] Linux Plug and Play Support v0.97 (c) Adam Belay
May  6 07:31:18 user kernel: [    0.581750] pnp: PnP ACPI init
May  6 07:31:18 user kernel: [    0.581757] ACPI: bus type pnp registered
May  6 07:31:18 user kernel: [    0.587845] pnp: PnP ACPI: found 15 devices
May  6 07:31:18 user kernel: [    0.587847] ACPI: ACPI bus type pnp unregistered
May  6 07:31:18 user kernel: [    0.587851] PnPBIOS: Disabled by ACPI PNP
May  6 07:31:18 user kernel: [    0.588179] PCI: Using ACPI for IRQ routing
May  6 07:31:18 user kernel: [    0.588296] NET: Registered protocol family 8
May  6 07:31:18 user kernel: [    0.588296] NET: Registered protocol family 20
May  6 07:31:18 user kernel: [    0.588296] NetLabel: Initializing
May  6 07:31:18 user kernel: [    0.588296] NetLabel:  domain hash size = 128
May  6 07:31:18 user kernel: [    0.588296] NetLabel:  protocols = UNLABELED CIPSOv4
May  6 07:31:18 user kernel: [    0.588296] NetLabel:  unlabeled traffic allowed by default
May  6 07:31:18 user kernel: [    0.588296] tracer: 772 pages allocated for 65536 entries of 48 bytes
May  6 07:31:18 user kernel: [    0.588296]    actual entries 65620
May  6 07:31:18 user kernel: [    0.588296] AppArmor: AppArmor Filesystem Enabled
May  6 07:31:18 user kernel: [    0.588296] ACPI: RTC can wake from S4
May  6 07:31:18 user kernel: [    0.588296] system 00:00: ioport range 0x1000-0x107f has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:00: ioport range 0x1080-0x10ff has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:00: ioport range 0x1400-0x147f has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:00: ioport range 0x1480-0x14ff has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:00: ioport range 0x1800-0x187f has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:00: ioport range 0x1880-0x18ff has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xd8800-0xdbfff has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xf0000-0xf7fff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xf8000-0xfbfff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xfc000-0xfffff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0x2fff0000-0x2fffffff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xffff0000-0xffffffff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0x0-0x9ffff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0x100000-0x2ffeffff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:03: ioport range 0x800-0x805 has been reserved
May  6 07:31:18 user kernel: [    0.624054] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:01
May  6 07:31:18 user kernel: [    0.624057] pci 0000:00:0a.0:   IO window: 0x9000-0xbfff
May  6 07:31:18 user kernel: [    0.624061] pci 0000:00:0a.0:   MEM window: 0xe2000000-0xe3ffffff
May  6 07:31:18 user kernel: [    0.624065] pci 0000:00:0a.0:   PREFETCH window: 0x00000040000000-0x000000400fffff
May  6 07:31:18 user kernel: [    0.624071] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
May  6 07:31:18 user kernel: [    0.624074] pci 0000:00:0b.0:   IO window: 0xc000-0xcfff
May  6 07:31:18 user kernel: [    0.624078] pci 0000:00:0b.0:   MEM window: 0xe0000000-0xe1ffffff
May  6 07:31:18 user kernel: [    0.624083] pci 0000:00:0b.0:   PREFETCH window: 0x000000d8000000-0x000000dfffffff
May  6 07:31:18 user kernel: [    0.624094] pci 0000:00:0a.0: setting latency timer to 64
May  6 07:31:18 user kernel: [    0.624101] bus: 00 index 0 io port: [0, ffff]
May  6 07:31:18 user kernel: [    0.624103] bus: 00 index 1 mmio: [0, ffffffffffffffff]
May  6 07:31:18 user kernel: [    0.624105] bus: 01 index 0 io port: [9000, bfff]
May  6 07:31:18 user kernel: [    0.624108] bus: 01 index 1 mmio: [e2000000, e3ffffff]
May  6 07:31:18 user kernel: [    0.624110] bus: 01 index 2 mmio: [40000000, 400fffff]
May  6 07:31:18 user kernel: [    0.624112] bus: 01 index 3 mmio: [0, 0]
May  6 07:31:18 user kernel: [    0.624114] bus: 02 index 0 io port: [c000, cfff]
May  6 07:31:18 user kernel: [    0.624117] bus: 02 index 1 mmio: [e0000000, e1ffffff]
May  6 07:31:18 user kernel: [    0.624119] bus: 02 index 2 mmio: [d8000000, dfffffff]
May  6 07:31:18 user kernel: [    0.624121] bus: 02 index 3 mmio: [0, 0]
May  6 07:31:18 user kernel: [    0.624132] NET: Registered protocol family 2
May  6 07:31:18 user kernel: [    0.624256] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May  6 07:31:18 user kernel: [    0.624578] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May  6 07:31:18 user kernel: [    0.625534] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May  6 07:31:18 user kernel: [    0.626054] TCP: Hash tables configured (established 131072 bind 65536)
May  6 07:31:18 user kernel: [    0.626057] TCP reno registered
May  6 07:31:18 user kernel: [    0.626163] NET: Registered protocol family 1
May  6 07:31:18 user kernel: [    0.626282] checking if image is initramfs... it is
May  6 07:31:18 user kernel: [    1.130030] Switched to high resolution mode on CPU 0
May  6 07:31:18 user kernel: [    1.270119] Freeing initrd memory: 7861k freed
May  6 07:31:18 user kernel: [    1.270873] audit: initializing netlink socket (disabled)
May  6 07:31:18 user kernel: [    1.270888] type=2000 audit(1241595059.270:1): initialized
May  6 07:31:18 user kernel: [    1.277060] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May  6 07:31:18 user kernel: [    1.279222] VFS: Disk quotas dquot_6.5.1
May  6 07:31:18 user kernel: [    1.279307] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  6 07:31:18 user kernel: [    1.279403] msgmni has been set to 1510
May  6 07:31:18 user kernel: [    1.279523] io scheduler noop registered
May  6 07:31:18 user kernel: [    1.279526] io scheduler anticipatory registered
May  6 07:31:18 user kernel: [    1.279528] io scheduler deadline registered (default)
May  6 07:31:18 user kernel: [    1.279540] io scheduler cfq registered
May  6 07:31:18 user kernel: [    1.320057] pci 0000:02:00.0: Boot video device
May  6 07:31:18 user kernel: [    1.320378] isapnp: Scanning for PnP cards...
May  6 07:31:18 user kernel: [    1.676735] isapnp: No Plug & Play device found
May  6 07:31:18 user kernel: [    1.712895] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
May  6 07:31:18 user kernel: [    1.713012] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  6 07:31:18 user kernel: [    1.713152] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  6 07:31:18 user kernel: [    1.713719] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  6 07:31:18 user kernel: [    1.713991] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  6 07:31:18 user kernel: [    1.714376] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
May  6 07:31:18 user kernel: [    1.714385] serial 0000:01:06.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
May  6 07:31:18 user kernel: [    1.717513] brd: module loaded
May  6 07:31:18 user kernel: [    1.717585] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May  6 07:31:18 user kernel: [    1.717703] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May  6 07:31:18 user kernel: [    1.717706] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May  6 07:31:18 user kernel: [    1.718280] serio: i8042 KBD port at 0x60,0x64 irq 1
May  6 07:31:18 user kernel: [    1.718737] mice: PS/2 mouse device common for all mice
May  6 07:31:18 user kernel: [    1.718869] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
May  6 07:31:18 user kernel: [    1.718891] rtc0: alarms up to one year, y3k
May  6 07:31:18 user kernel: [    1.719007] EISA: Probing bus 0 at eisa.0
May  6 07:31:18 user kernel: [    1.719015] Cannot allocate resource for EISA slot 1
May  6 07:31:18 user kernel: [    1.719018] Cannot allocate resource for EISA slot 2
May  6 07:31:18 user kernel: [    1.719033] EISA: Detected 0 cards.
May  6 07:31:18 user kernel: [    1.719037] cpuidle: using governor ladder
May  6 07:31:18 user kernel: [    1.719039] cpuidle: using governor menu
May  6 07:31:18 user kernel: [    1.719559] TCP cubic registered
May  6 07:31:18 user kernel: [    1.719585] Using IPI No-Shortcut mode
May  6 07:31:18 user kernel: [    1.719774] registered taskstats version 1
May  6 07:31:18 user kernel: [    1.719906]   Magic number: 9:660:520
May  6 07:31:18 user kernel: [    1.720111] rtc_cmos 00:05: setting system clock to 2009-05-06 07:31:00 UTC (1241595060)
May  6 07:31:18 user kernel: [    1.720115] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  6 07:31:18 user kernel: [    1.720117] EDD information not available.
May  6 07:31:18 user kernel: [    1.720443] Freeing unused kernel memory: 436k freed
May  6 07:31:18 user kernel: [    1.720562] Write protecting the kernel text: 2632k
May  6 07:31:18 user kernel: [    1.720610] Write protecting the kernel read-only data: 956k
May  6 07:31:18 user kernel: [    1.741113] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May  6 07:31:18 user kernel: [    1.850418] fuse init (API version 7.9)
May  6 07:31:18 user kernel: [    1.870845] ACPI: processor limited to max C-state 1
May  6 07:31:18 user kernel: [    1.870928] processor ACPI0007:00: registered as cooling_device0
May  6 07:31:18 user kernel: [    2.581254] usbcore: registered new interface driver usbfs
May  6 07:31:18 user kernel: [    2.581279] usbcore: registered new interface driver hub
May  6 07:31:18 user kernel: [    2.581318] usbcore: registered new device driver usb
May  6 07:31:18 user kernel: [    2.592554] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
May  6 07:31:18 user kernel: [    2.592923] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
May  6 07:31:18 user kernel: [    2.592931] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 22 (level, high) -> IRQ 22
May  6 07:31:18 user kernel: [    2.592949] ohci_hcd 0000:00:02.0: setting latency timer to 64
May  6 07:31:18 user kernel: [    2.592952] ohci_hcd 0000:00:02.0: OHCI Host Controller
May  6 07:31:18 user kernel: [    2.593001] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
May  6 07:31:18 user kernel: [    2.593023] ohci_hcd 0000:00:02.0: irq 22, io mem 0xe4003000
May  6 07:31:18 user kernel: [    2.608325] No dock devices found.
May  6 07:31:18 user kernel: [    2.652216] usb usb1: configuration #1 chosen from 1 choice
May  6 07:31:18 user kernel: [    2.652247] hub 1-0:1.0: USB hub found
May  6 07:31:18 user kernel: [    2.652259] hub 1-0:1.0: 3 ports detected
May  6 07:31:18 user kernel: [    2.665817] SCSI subsystem initialized
May  6 07:31:18 user kernel: [    2.711621] libata version 3.00 loaded.
May  6 07:31:18 user kernel: [    2.870661] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
May  6 07:31:18 user kernel: [    2.870671] ohci_hcd 0000:00:02.1: PCI INT B -> Link[APCG] -> GSI 21 (level, high) -> IRQ 21
May  6 07:31:18 user kernel: [    2.870688] ohci_hcd 0000:00:02.1: setting latency timer to 64
May  6 07:31:18 user kernel: [    2.870691] ohci_hcd 0000:00:02.1: OHCI Host Controller
May  6 07:31:18 user kernel: [    2.870715] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
May  6 07:31:18 user kernel: [    2.870738] ohci_hcd 0000:00:02.1: irq 21, io mem 0xe4004000
May  6 07:31:18 user kernel: [    2.932222] usb usb2: configuration #1 chosen from 1 choice
May  6 07:31:18 user kernel: [    2.932252] hub 2-0:1.0: USB hub found
May  6 07:31:18 user kernel: [    2.932264] hub 2-0:1.0: 3 ports detected
May  6 07:31:18 user kernel: [    3.040719] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
May  6 07:31:18 user kernel: [    3.040729] ehci_hcd 0000:00:02.2: PCI INT C -> Link[APCL] -> GSI 20 (level, high) -> IRQ 20
May  6 07:31:18 user kernel: [    3.040745] ehci_hcd 0000:00:02.2: setting latency timer to 64
May  6 07:31:18 user kernel: [    3.040748] ehci_hcd 0000:00:02.2: EHCI Host Controller
May  6 07:31:18 user kernel: [    3.040774] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
May  6 07:31:18 user kernel: [    3.040800] ehci_hcd 0000:00:02.2: debug port 1
May  6 07:31:18 user kernel: [    3.040804] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
May  6 07:31:18 user kernel: [    3.040819] ehci_hcd 0000:00:02.2: irq 20, io mem 0xe4005000
May  6 07:31:18 user kernel: [    3.050039] usb 1-1: new full speed USB device using ohci_hcd and address 2
May  6 07:31:18 user kernel: [    3.070031] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May  6 07:31:18 user kernel: [    3.070209] usb usb3: configuration #1 chosen from 1 choice
May  6 07:31:18 user kernel: [    3.070240] hub 3-0:1.0: USB hub found
May  6 07:31:18 user kernel: [    3.070250] hub 3-0:1.0: 6 ports detected
May  6 07:31:18 user kernel: [    3.130048] hub 1-0:1.0: unable to enumerate USB device on port 1
May  6 07:31:18 user kernel: [    3.290405] pata_acpi 0000:00:08.0: power state changed by ACPI to D0
May  6 07:31:18 user kernel: [    3.290454] pata_acpi 0000:00:08.0: setting latency timer to 64
May  6 07:31:18 user kernel: [    3.294745] VIA Networking Velocity Family Gigabit Ethernet Adapter Driver Ver. 1.14
May  6 07:31:18 user kernel: [    3.294749] Copyright (c) 2002, 2003 VIA Networking Technologies, Inc.
May  6 07:31:18 user kernel: [    3.294752] Copyright (c) 2004 Red Hat Inc.
May  6 07:31:18 user kernel: [    3.294966] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
May  6 07:31:18 user kernel: [    3.294974] via-velocity 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
May  6 07:31:18 user kernel: [    3.296023] eth1: VIA Networking Velocity Family Gigabit Ethernet Adapter
May  6 07:31:18 user kernel: [    3.296026] eth1: Ethernet Address: 00:A0:C5:30:02:07
May  6 07:31:18 user kernel: [    3.296124] pata_amd 0000:00:08.0: version 0.3.10
May  6 07:31:18 user kernel: [    3.296176] pata_amd 0000:00:08.0: power state changed by ACPI to D0
May  6 07:31:18 user kernel: [    3.296217] pata_amd 0000:00:08.0: setting latency timer to 64
May  6 07:31:18 user kernel: [    3.296279] scsi0 : pata_amd
May  6 07:31:18 user kernel: [    3.296371] scsi1 : pata_amd
May  6 07:31:18 user kernel: [    3.297216] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
May  6 07:31:18 user kernel: [    3.297220] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
May  6 07:31:18 user kernel: [    3.310126] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
May  6 07:31:18 user kernel: [    3.310339] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
May  6 07:31:18 user kernel: [    3.310348] r8169 0000:01:0b.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
May  6 07:31:18 user kernel: [    3.310668] eth0: RTL8169s at 0xf0856000, 00:0d:61:21:54:d2, XID 00800000 IRQ 19
May  6 07:31:18 user kernel: [    3.314200] sata_sil 0000:01:0d.0: version 2.3
May  6 07:31:18 user kernel: [    3.314237] sata_sil 0000:01:0d.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
May  6 07:31:18 user kernel: [    3.314251] sata_sil 0000:01:0d.0: Applying R_ERR on DMA activate FIS errata fix
May  6 07:31:18 user kernel: [    3.314327] scsi2 : sata_sil
May  6 07:31:18 user kernel: [    3.314399] scsi3 : sata_sil
May  6 07:31:18 user kernel: [    3.314436] ata3: SATA max UDMA/100 mmio m512@0xe3013000 tf 0xe3013080 irq 17
May  6 07:31:18 user kernel: [    3.314440] ata4: SATA max UDMA/100 mmio m512@0xe3013000 tf 0xe30130c0 irq 17
May  6 07:31:18 user kernel: [    3.530451] ata1.00: ATA-6: ST380011A, 8.01, max UDMA/100
May  6 07:31:18 user kernel: [    3.530456] ata1.00: 156301488 sectors, multi 16: LBA48 
May  6 07:31:18 user kernel: [    3.530470] ata1: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc60000c0) ACPI=0x3f01f (20:600:0x13)
May  6 07:31:18 user kernel: [    3.570379] ata1.00: configured for UDMA/100
May  6 07:31:18 user kernel: [    3.660026] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
May  6 07:31:18 user kernel: [    3.680421] ata3.00: ATA-6: ST3120827AS, 3.42, max UDMA/133
May  6 07:31:18 user kernel: [    3.680424] ata3.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
May  6 07:31:18 user kernel: [    3.720423] ata3.00: configured for UDMA/100
May  6 07:31:18 user kernel: [    3.760290] ata2.01: ATAPI: _NEC DVD_RW ND-1300A, 1.08, max UDMA/33
May  6 07:31:18 user kernel: [    3.760303] ata2: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc60000c0) ACPI=0x701f (600:60:0x1c)
May  6 07:31:18 user kernel: [    3.800247] ata2.01: configured for UDMA/33
May  6 07:31:18 user kernel: [    3.800348] scsi 0:0:0:0: Direct-Access     ATA      ST380011A        8.01 PQ: 0 ANSI: 5
May  6 07:31:18 user kernel: [    3.803437] scsi 1:0:1:0: CD-ROM            _NEC     DVD_RW ND-1300A  1.08 PQ: 0 ANSI: 5
May  6 07:31:18 user kernel: [    4.070022] ata4: SATA link down (SStatus 0 SControl 310)
May  6 07:31:18 user kernel: [    4.070120] scsi 2:0:0:0: Direct-Access     ATA      ST3120827AS      3.42 PQ: 0 ANSI: 5
May  6 07:31:18 user kernel: [    4.079705] scsi 0:0:0:0: Attached scsi generic sg0 type 0
May  6 07:31:18 user kernel: [    4.079744] scsi 1:0:1:0: Attached scsi generic sg1 type 5
May  6 07:31:18 user kernel: [    4.079781] scsi 2:0:0:0: Attached scsi generic sg2 type 0
May  6 07:31:18 user kernel: [    4.108197] Driver 'sd' needs updating - please use bus_type methods
May  6 07:31:18 user kernel: [    4.108314] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
May  6 07:31:18 user kernel: [    4.108331] sd 0:0:0:0: [sda] Write Protect is off
May  6 07:31:18 user kernel: [    4.108334] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  6 07:31:18 user kernel: [    4.108361] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  6 07:31:18 user kernel: [    4.108426] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
May  6 07:31:18 user kernel: [    4.108441] sd 0:0:0:0: [sda] Write Protect is off
May  6 07:31:18 user kernel: [    4.108443] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  6 07:31:18 user kernel: [    4.108468] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  6 07:31:18 user kernel: [    4.108473]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
May  6 07:31:18 user kernel: [    4.126314]  sda1 < sda5 sda6 >
May  6 07:31:18 user kernel: [    4.134470] sd 0:0:0:0: [sda] Attached SCSI disk
May  6 07:31:18 user kernel: [    4.134559] sd 2:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
May  6 07:31:18 user kernel: [    4.134579] sd 2:0:0:0: [sdb] Write Protect is off
May  6 07:31:18 user kernel: [    4.134582] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May  6 07:31:18 user kernel: [    4.134612] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  6 07:31:18 user kernel: [    4.134676] sd 2:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
May  6 07:31:18 user kernel: [    4.134692] sd 2:0:0:0: [sdb] Write Protect is off
May  6 07:31:18 user kernel: [    4.134694] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May  6 07:31:18 user kernel: [    4.134722] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  6 07:31:18 user kernel: [    4.134727]  sdb:sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
May  6 07:31:18 user kernel: [    4.138985] Uniform CD-ROM driver Revision: 3.20
May  6 07:31:18 user kernel: [    4.139080] sr 1:0:1:0: Attached scsi CD-ROM sr0
May  6 07:31:18 user kernel: [    4.148666]  sdb1 sdb2 < sdb5 sdb6 sdb7 >
May  6 07:31:18 user kernel: [    4.181765] sd 2:0:0:0: [sdb] Attached SCSI disk
May  6 07:31:18 user kernel: [    4.260027] usb 1-1: new full speed USB device using ohci_hcd and address 3
May  6 07:31:18 user kernel: [    4.486225] usb 1-1: configuration #1 chosen from 1 choice
May  6 07:31:18 user kernel: [    4.656171] PM: Starting manual resume from disk
May  6 07:31:18 user kernel: [    4.656175] PM: Resume from partition 8:5
May  6 07:31:18 user kernel: [    4.656177] PM: Checking hibernation image.
May  6 07:31:18 user kernel: [    4.656357] PM: Resume from disk failed.
May  6 07:31:18 user kernel: [    4.700618] kjournald starting.  Commit interval 5 seconds
May  6 07:31:18 user kernel: [    4.700635] EXT3-fs: mounted filesystem with ordered data mode.
May  6 07:31:18 user kernel: [    4.830025] usb 1-2: new full speed USB device using ohci_hcd and address 4
May  6 07:31:18 user kernel: [    5.053142] usb 1-2: configuration #1 chosen from 1 choice
May  6 07:31:18 user kernel: [    5.390028] usb 1-3: new low speed USB device using ohci_hcd and address 5
May  6 07:31:18 user kernel: [    5.616253] usb 1-3: configuration #1 chosen from 1 choice
May  6 07:31:18 user kernel: [    7.239717] udevd version 124 started
May  6 07:31:18 user kernel: [    8.111333] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  6 07:31:18 user kernel: [    8.157204] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  6 07:31:18 user kernel: [    8.304915] Linux agpgart interface v0.103
May  6 07:31:18 user kernel: [    8.317468] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
May  6 07:31:18 user kernel: [    8.317486] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2000
May  6 07:31:18 user kernel: [    8.327395] input: PC Speaker as /devices/platform/pcspkr/input/input2
May  6 07:31:18 user kernel: [    8.335038] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
May  6 07:31:18 user kernel: [    8.335070] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
May  6 07:31:18 user kernel: [    8.338907] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
May  6 07:31:18 user kernel: [    8.438016] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
May  6 07:31:18 user kernel: [    8.438023] Intel ICH 0000:00:06.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, high) -> IRQ 22
May  6 07:31:18 user kernel: [    8.438045] Intel ICH 0000:00:06.0: setting latency timer to 64
May  6 07:31:18 user kernel: [    8.488493] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
May  6 07:31:18 user kernel: [    8.520047] ACPI: Power Button (FF) [PWRF]
May  6 07:31:18 user kernel: [    8.520139] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
May  6 07:31:18 user kernel: [    8.560041] ACPI: Power Button (CM) [PWRB]
May  6 07:31:18 user kernel: [    8.780029] intel8x0_measure_ac97_clock: measured 59805 usecs
May  6 07:31:18 user kernel: [    8.780033] intel8x0: clocking to 48000
May  6 07:31:18 user kernel: [    8.844067] ieee80211_crypt: registered algorithm 'NULL'
May  6 07:31:18 user kernel: [    8.855171] ieee80211: 802.11 data/management/control stack, git-1.1.13
May  6 07:31:18 user kernel: [    8.855176] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
May  6 07:31:18 user kernel: [    8.933048] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
May  6 07:31:18 user kernel: [    8.933052] ipw2200: Copyright(c) 2003-2006 Intel Corporation
May  6 07:31:18 user kernel: [    8.933150] ipw2200 0000:01:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
May  6 07:31:18 user kernel: [    8.933203] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
May  6 07:31:18 user kernel: [    8.933252] firmware: requesting ipw2200-bss.fw
May  6 07:31:18 user kernel: [    9.327847] parport_pc 00:0b: reported by Plug and Play ACPI
May  6 07:31:18 user kernel: [    9.327890] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
May  6 07:31:18 user kernel: [   11.000747] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
May  6 07:31:18 user kernel: [   11.007227] usbcore: registered new interface driver cdc_acm
May  6 07:31:18 user kernel: [   11.007233] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
May  6 07:31:18 user kernel: [   11.298526] usbcore: registered new interface driver snd-usb-audio
May  6 07:31:18 user kernel: [   11.298560] usbcore: registered new interface driver hiddev
May  6 07:31:18 user kernel: [   11.307296] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.3/input/input5
May  6 07:31:18 user kernel: [   11.370314] input,hidraw0: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:02.0-2
May  6 07:31:18 user kernel: [   11.376546] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.0/input/input6
May  6 07:31:18 user kernel: [   11.430213] input,hidraw1: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:02.0-3
May  6 07:31:18 user kernel: [   11.430238] usbcore: registered new interface driver usbhid
May  6 07:31:18 user kernel: [   11.430242] usbhid: v2.6:USB HID core driver
May  6 07:31:18 user kernel: [   12.797095] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
May  6 07:31:18 user kernel: [   13.857192] loop: module loaded
May  6 07:31:18 user kernel: [   13.871212] lp0: using parport0 (interrupt-driven).
May  6 07:31:18 user kernel: [   14.388910] Adding 248936k swap on /dev/sda5.  Priority:-1 extents:1 across:248936k
May  6 07:31:18 user kernel: [   14.739745] EXT3 FS on sda6, internal journal
May  6 07:31:18 user kernel: [   15.902949] ip_tables: (C) 2000-2006 Netfilter Core Team
May  6 07:31:18 user kernel: [   15.953923] r8169: eth0: link up
May  6 07:31:18 user kernel: [   17.294069] NET: Registered protocol family 17
May  6 07:31:18 user kernel: [   17.450890] Velocity is AUTO mode
May  6 07:31:18 user kernel: [   17.895533] NET: Registered protocol family 10
May  6 07:31:18 user kernel: [   17.896024] lo: Disabled Privacy Extensions
May  6 07:31:18 user kernel: [   17.896579] ADDRCONF(NETDEV_UP): eth1: link is not ready
May  6 07:31:18 user kernel: [   18.986603] eth1: Link auto-negotiation speed 100M bps full duplex
May  6 07:31:18 user kernel: [   18.988185] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
May  6 07:31:19 user pptpd[4372]: MGR: connections limit (100) reached, extra IP addresses ignored
May  6 07:31:19 user pptpd[4373]: MGR: Manager process started
May  6 07:31:19 user pptpd[4373]: MGR: Maximum of 100 connections available
May  6 07:31:21 user kernel: [   21.857128] warning: `dhcpd3' uses 32-bit capabilities (legacy support in use)
May  6 07:31:21 user dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  6 07:31:21 user dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  6 07:31:21 user dhcpd: All rights reserved.
May  6 07:31:21 user dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  6 07:31:21 user dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  6 07:31:21 user dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  6 07:31:21 user dhcpd: All rights reserved.
May  6 07:31:21 user dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  6 07:31:21 user dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  6 07:31:21 user dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  6 07:31:21 user dhcpd: All rights reserved.
May  6 07:31:21 user dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  6 07:31:21 user dhcpd: Wrote 3 leases to leases file.
May  6 07:31:21 user ntpdate[3974]: no server suitable for synchronization found
May  6 07:31:23 user /usr/sbin/cron[4578]: (CRON) INFO (pidfile fd = 3)
May  6 07:31:23 user /usr/sbin/cron[4579]: (CRON) STARTUP (fork ok)
May  6 07:31:23 user /usr/sbin/cron[4579]: (CRON) INFO (Running @reboot jobs)
May  6 07:31:25 user ntpdate[4540]: no server suitable for synchronization found
May  6 07:31:27 user kernel: [   28.700006] eth0: no IPv6 routers present
May  6 07:31:29 user kernel: [   29.760012] eth1: no IPv6 routers present
May  6 07:31:46 user kernel: [   47.371589] usb 1-1: USB disconnect, address 3
May  6 07:31:50 user kernel: [   51.300012] usb 3-1: new high speed USB device using ehci_hcd and address 5
May  6 07:31:50 user kernel: [   51.452627] usb 3-1: configuration #1 chosen from 1 choice
May  6 07:31:50 user kernel: [   51.536840] usbcore: registered new interface driver libusual
May  6 07:31:50 user kernel: [   51.552255] Initializing USB Mass Storage driver...
May  6 07:31:50 user kernel: [   51.552359] scsi4 : SCSI emulation for USB Mass Storage devices
May  6 07:31:50 user kernel: [   51.552456] usbcore: registered new interface driver usb-storage
May  6 07:31:50 user kernel: [   51.552460] USB Mass Storage support registered.
May  6 07:31:50 user kernel: [   51.555777] usb-storage: device found at 5
May  6 07:31:50 user kernel: [   51.555782] usb-storage: waiting for device to settle before scanning
May  6 07:31:55 user kernel: [   56.550124] usb-storage: device scan complete
May  6 07:31:55 user kernel: [   56.551354] scsi 4:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  0.00 PQ: 0 ANSI: 2
May  6 07:31:55 user kernel: [   56.556767] sd 4:0:0:0: [sdc] 31588351 512-byte hardware sectors (16173 MB)
May  6 07:31:55 user kernel: [   56.557464] sd 4:0:0:0: [sdc] Write Protect is off
May  6 07:31:55 user kernel: [   56.557469] sd 4:0:0:0: [sdc] Mode Sense: 00 00 00 00
May  6 07:31:55 user kernel: [   56.557472] sd 4:0:0:0: [sdc] Assuming drive cache: write through
May  6 07:31:55 user kernel: [   56.560343] sd 4:0:0:0: [sdc] 31588351 512-byte hardware sectors (16173 MB)
May  6 07:31:55 user kernel: [   56.561091] sd 4:0:0:0: [sdc] Write Protect is off
May  6 07:31:55 user kernel: [   56.561096] sd 4:0:0:0: [sdc] Mode Sense: 00 00 00 00
May  6 07:31:55 user kernel: [   56.561098] sd 4:0:0:0: [sdc] Assuming drive cache: write through
May  6 07:31:55 user kernel: [   56.561154]  sdc: sdc1
May  6 07:31:55 user kernel: [   56.624236] sd 4:0:0:0: [sdc] Attached SCSI removable disk
May  6 07:31:55 user kernel: [   56.624365] sd 4:0:0:0: Attached scsi generic sg3 type 0
May  6 07:39:16 user kernel: [  497.706084] eth1: failed to detect cable link
May  6 07:39:20 user kernel: [  501.233869] eth1: Link auto-negotiation speed 100M bps full duplex
May  6 07:39:51 user dhcpd: DHCPDISCOVER from 00:00:e2:50:19:15 (noobook) via eth1
May  6 07:39:52 user dhcpd: DHCPOFFER on 10.0.0.103 to 00:00:e2:50:19:15 (noobook) via eth1
May  6 07:39:52 user dhcpd: DHCPREQUEST for 10.0.0.103 (10.0.0.1) from 00:00:e2:50:19:15 (noobook) via eth1
May  6 07:39:52 user dhcpd: DHCPACK on 10.0.0.103 to 00:00:e2:50:19:15 (noobook) via eth1
May  6 07:40:01 user /USR/SBIN/CRON[4793]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
```

---

### Post by Romala on 2009-05-06
*kern.log*

```
May  5 07:29:44 user kernel: Inspecting /boot/System.map-2.6.27-7-server
May  5 07:29:44 user kernel: Cannot find map file.
May  5 07:29:44 user kernel: Loaded 48877 symbols from 70 modules.
May  5 07:29:44 user kernel: [    0.000000] Initializing cgroup subsys cpuset
May  5 07:29:44 user kernel: [    0.000000] Initializing cgroup subsys cpu
May  5 07:29:44 user kernel: [    0.000000] Linux version 2.6.27-7-server (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 20:18:35 UTC 2008 (Ubuntu 2.6.27-7.16-server)
May  5 07:29:44 user kernel: [    0.000000] BIOS-provided physical RAM map:
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May  5 07:29:44 user kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
May  5 07:29:44 user kernel: [    0.000000] last_pfn = 0x2fff0 max_arch_pfn = 0x1000000
May  5 07:29:44 user kernel: [    0.000000] kernel direct mapping tables up to 2fff0000 @ 7000-d000
May  5 07:29:44 user kernel: [    0.000000] NX (Execute Disable) protection: active
May  5 07:29:44 user kernel: [    0.000000] RAMDISK: 2f832000 - 2ffdf6b8
May  5 07:29:44 user kernel: [    0.000000] DMI 2.3 present.
May  5 07:29:44 user kernel: [    0.000000] ACPI: RSDP 000F6AB0, 0014 (r0 Nvidia)
May  5 07:29:44 user kernel: [    0.000000] ACPI: RSDT 2FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  5 07:29:44 user kernel: [    0.000000] ACPI: FACP 2FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  5 07:29:44 user kernel: [    0.000000] ACPI: DSDT 2FFF30C0, 4ABF (r1 NVIDIA AWRDACPI     1000 MSFT  100000C)
May  5 07:29:44 user kernel: [    0.000000] ACPI: FACS 2FFF0000, 0040
May  5 07:29:44 user kernel: [    0.000000] ACPI: APIC 2FFF7B80, 005A (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  5 07:29:44 user kernel: [    0.000000] 0MB HIGHMEM available.
May  5 07:29:44 user kernel: [    0.000000] 767MB LOWMEM available.
May  5 07:29:44 user kernel: [    0.000000]   mapped low ram: 0 - 2fff0000
May  5 07:29:44 user kernel: [    0.000000]   low ram: 00000000 - 2fff0000
May  5 07:29:44 user kernel: [    0.000000]   bootmap 0000a000 - 00010000
May  5 07:29:44 user kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002fff0000]
May  5 07:29:44 user kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
May  5 07:29:44 user kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
May  5 07:29:44 user kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
May  5 07:29:44 user kernel: [    0.000000]   #3 [0000100000 - 00005e8220]    TEXT DATA BSS ==> [0000100000 - 00005e8220]
May  5 07:29:44 user kernel: [    0.000000]   #4 [002f832000 - 002ffdf6b8]          RAMDISK ==> [002f832000 - 002ffdf6b8]
May  5 07:29:44 user kernel: [    0.000000]   #5 [00005e9000 - 00005f1000]    INIT_PG_TABLE ==> [00005e9000 - 00005f1000]
May  5 07:29:44 user kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
May  5 07:29:44 user kernel: [    0.000000]   #7 [0000007000 - 000000a000]          PGTABLE ==> [0000007000 - 000000a000]
May  5 07:29:44 user kernel: [    0.000000]   #8 [000000a000 - 0000010000]          BOOTMAP ==> [000000a000 - 0000010000]
May  5 07:29:44 user kernel: [    0.000000] found SMP MP-table at [c00f5000] 000f5000
May  5 07:29:44 user kernel: [    0.000000] Zone PFN ranges:
May  5 07:29:44 user kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
May  5 07:29:44 user kernel: [    0.000000]   Normal   0x00001000 -> 0x0002fff0
May  5 07:29:44 user kernel: [    0.000000]   HighMem  0x0002fff0 -> 0x0002fff0
May  5 07:29:44 user kernel: [    0.000000] Movable zone start PFN for each node
May  5 07:29:44 user kernel: [    0.000000] early_node_map[2] active PFN ranges
May  5 07:29:44 user kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
May  5 07:29:44 user kernel: [    0.000000]     0: 0x00000100 -> 0x0002fff0
May  5 07:29:44 user kernel: [    0.000000] On node 0 totalpages: 196495
May  5 07:29:44 user kernel: [    0.000000] free_area_init_node: node 0, pgdat c049eb00, node_mem_map c1000000
May  5 07:29:44 user kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
May  5 07:29:44 user kernel: [    0.000000]   Normal zone: 190804 pages, LIFO batch:31
May  5 07:29:44 user kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
May  5 07:29:44 user kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
May  5 07:29:44 user kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
May  5 07:29:44 user kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  5 07:29:44 user kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  5 07:29:44 user kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
May  5 07:29:44 user kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  5 07:29:44 user kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
May  5 07:29:44 user kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  5 07:29:44 user kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
May  5 07:29:44 user kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  5 07:29:44 user kernel: [    0.000000] ACPI: IRQ9 used by override.
May  5 07:29:44 user kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  5 07:29:44 user kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  5 07:29:44 user kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
May  5 07:29:44 user kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
May  5 07:29:44 user kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
May  5 07:29:44 user kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May  5 07:29:44 user kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
May  5 07:29:44 user kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
May  5 07:29:44 user kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
May  5 07:29:44 user kernel: [    0.000000] PERCPU: Allocating 45852 bytes of per cpu data
May  5 07:29:44 user kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
May  5 07:29:44 user kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194767
May  5 07:29:44 user kernel: [    0.000000] Kernel command line: root=UUID=3a16f219-3073-4cf3-8fa0-646d16cda612 ro quiet splash 
May  5 07:29:44 user kernel: [    0.000000] Enabling fast FPU save and restore... done.
May  5 07:29:44 user kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May  5 07:29:44 user kernel: [    0.000000] Initializing CPU#0
May  5 07:29:44 user kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
May  5 07:29:44 user kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
May  5 07:29:44 user kernel: [    0.000000] TSC: using PIT calibration value
May  5 07:29:44 user kernel: [    0.000000] Detected 1994.824 MHz processor.
May  5 07:29:44 user kernel: [    0.010000] spurious 8259A interrupt: IRQ7.
May  5 07:29:44 user kernel: [    0.010000] Console: colour VGA+ 80x25
May  5 07:29:44 user kernel: [    0.010000] console [tty0] enabled
May  5 07:29:44 user kernel: [    0.010000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  5 07:29:44 user kernel: [    0.010000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  5 07:29:44 user kernel: [    0.010000] Memory: 765068k/786368k available (2628k kernel code, 20728k reserved, 1201k data, 436k init, 0k highmem)
May  5 07:29:44 user kernel: [    0.010000] virtual kernel memory layout:
May  5 07:29:44 user kernel: [    0.010000]     fixmap  : 0xffc78000 - 0xfffff000   (3612 kB)
May  5 07:29:44 user kernel: [    0.010000]     pkmap   : 0xff800000 - 0xffa00000   (2048 kB)
May  5 07:29:44 user kernel: [    0.010000]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
May  5 07:29:44 user kernel: [    0.010000]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
May  5 07:29:44 user kernel: [    0.010000]       .init : 0xc04c3000 - 0xc0530000   ( 436 kB)
May  5 07:29:44 user kernel: [    0.010000]       .data : 0xc0391036 - 0xc04bd800   (1201 kB)
May  5 07:29:44 user kernel: [    0.010000]       .text : 0xc0100000 - 0xc0391036   (2628 kB)
May  5 07:29:44 user kernel: [    0.010000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
May  5 07:29:44 user kernel: [    0.010000] CPA: page pool initialized 1 of 1 pages preallocated
May  5 07:29:44 user kernel: [    0.010000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
May  5 07:29:44 user kernel: [    0.010008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.64 BogoMIPS (lpj=19948240)
May  5 07:29:44 user kernel: [    0.010026] Security Framework initialized
May  5 07:29:44 user kernel: [    0.010033] SELinux:  Disabled at boot.
May  5 07:29:44 user kernel: [    0.010053] AppArmor: AppArmor initialized
May  5 07:29:44 user kernel: [    0.010061] Mount-cache hash table entries: 512
May  5 07:29:44 user kernel: [    0.010209] Initializing cgroup subsys ns
May  5 07:29:44 user kernel: [    0.010213] Initializing cgroup subsys cpuacct
May  5 07:29:44 user kernel: [    0.010215] Initializing cgroup subsys memory
May  5 07:29:44 user kernel: [    0.010229] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May  5 07:29:44 user kernel: [    0.010231] CPU: L2 Cache: 512K (64 bytes/line)
May  5 07:29:44 user kernel: [    0.010241] Checking 'hlt' instruction... OK.
May  5 07:29:44 user kernel: [    0.050367] SMP alternatives: switching to UP code
May  5 07:29:44 user kernel: [    0.056453] Freeing SMP alternatives: 11k freed
May  5 07:29:44 user kernel: [    0.056457] ACPI: Core revision 20080609
May  5 07:29:44 user kernel: [    0.057953] ACPI: Checking initramfs for custom DSDT
May  5 07:29:44 user kernel: [    0.371036] ENABLING IO-APIC IRQs
May  5 07:29:44 user kernel: [    0.371202] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
May  5 07:29:44 user kernel: [    0.471213] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 08
May  5 07:29:44 user kernel: [    0.480000] Brought up 1 CPUs
May  5 07:29:44 user kernel: [    0.480000] Total of 1 processors activated (3989.64 BogoMIPS).
May  5 07:29:44 user kernel: [    0.480000] CPU0 attaching sched-domain:
May  5 07:29:44 user kernel: [    0.480000]  domain 0: span 0 level CPU
May  5 07:29:44 user kernel: [    0.480000]   groups: 0
May  5 07:29:44 user kernel: [    0.480000] net_namespace: 840 bytes
May  5 07:29:44 user kernel: [    0.480000] Booting paravirtualized kernel on bare hardware
May  5 07:29:44 user kernel: [    0.480000] Time:  7:29:23  Date: 05/05/09
May  5 07:29:44 user kernel: [    0.480000] NET: Registered protocol family 16
May  5 07:29:44 user kernel: [    0.480000] EISA bus registered
May  5 07:29:44 user kernel: [    0.480000] ACPI: bus type pci registered
May  5 07:29:44 user kernel: [    0.500543] PCI: PCI BIOS revision 2.10 entry at 0xfac80, last bus=2
May  5 07:29:44 user kernel: [    0.500546] PCI: Using configuration type 1 for base access
May  5 07:29:44 user kernel: [    0.502222] ACPI: EC: Look up EC in DSDT
May  5 07:29:44 user kernel: [    0.509553] ACPI: Interpreter enabled
May  5 07:29:44 user kernel: [    0.509556] ACPI: (supports S0 S3 S4 S5)
May  5 07:29:44 user kernel: [    0.509570] ACPI: Using IOAPIC for interrupt routing
May  5 07:29:44 user kernel: [    0.520234] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  5 07:29:44 user kernel: [    0.520312] PCI: 0000:00:00.0 reg 10 32bit mmio: [d0000000, d7ffffff]
May  5 07:29:44 user kernel: [    0.520381] PCI: 0000:00:01.1 reg 20 io port: [1c00, 1c3f]
May  5 07:29:44 user kernel: [    0.520385] PCI: 0000:00:01.1 reg 24 io port: [2000, 203f]
May  5 07:29:44 user kernel: [    0.520395] pci 0000:00:01.1: PME# supported from D3hot D3cold
May  5 07:29:44 user kernel: [    0.520399] pci 0000:00:01.1: PME# disabled
May  5 07:29:44 user kernel: [    0.520416] PCI: 0000:00:02.0 reg 10 32bit mmio: [e4003000, e4003fff]
May  5 07:29:44 user kernel: [    0.520434] pci 0000:00:02.0: supports D1
May  5 07:29:44 user kernel: [    0.520435] pci 0000:00:02.0: supports D2
May  5 07:29:44 user kernel: [    0.520437] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520441] pci 0000:00:02.0: PME# disabled
May  5 07:29:44 user kernel: [    0.520455] PCI: 0000:00:02.1 reg 10 32bit mmio: [e4004000, e4004fff]
May  5 07:29:44 user kernel: [    0.520472] pci 0000:00:02.1: supports D1
May  5 07:29:44 user kernel: [    0.520473] pci 0000:00:02.1: supports D2
May  5 07:29:44 user kernel: [    0.520475] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520479] pci 0000:00:02.1: PME# disabled
May  5 07:29:44 user kernel: [    0.520496] PCI: 0000:00:02.2 reg 10 32bit mmio: [e4005000, e40050ff]
May  5 07:29:44 user kernel: [    0.520515] pci 0000:00:02.2: supports D1
May  5 07:29:44 user kernel: [    0.520517] pci 0000:00:02.2: supports D2
May  5 07:29:44 user kernel: [    0.520519] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520523] pci 0000:00:02.2: PME# disabled
May  5 07:29:44 user kernel: [    0.520543] PCI: 0000:00:06.0 reg 10 io port: [d400, d4ff]
May  5 07:29:44 user kernel: [    0.520547] PCI: 0000:00:06.0 reg 14 io port: [d800, d87f]
May  5 07:29:44 user kernel: [    0.520552] PCI: 0000:00:06.0 reg 18 32bit mmio: [e4001000, e4001fff]
May  5 07:29:44 user kernel: [    0.520565] pci 0000:00:06.0: supports D1
May  5 07:29:44 user kernel: [    0.520567] pci 0000:00:06.0: supports D2
May  5 07:29:44 user kernel: [    0.520587] PCI: 0000:00:08.0 reg 20 io port: [f000, f00f]
May  5 07:29:44 user kernel: [    0.520714] PCI: 0000:01:06.0 reg 10 io port: [9000, 903f]
May  5 07:29:44 user kernel: [    0.520743] pci 0000:01:06.0: supports D2
May  5 07:29:44 user kernel: [    0.520745] pci 0000:01:06.0: PME# supported from D0 D2 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520749] pci 0000:01:06.0: PME# disabled
May  5 07:29:44 user kernel: [    0.520769] PCI: 0000:01:07.0 reg 10 32bit mmio: [e3012000, e3012fff]
May  5 07:29:44 user kernel: [    0.520798] pci 0000:01:07.0: PME# supported from D0 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520802] pci 0000:01:07.0: PME# disabled
May  5 07:29:44 user kernel: [    0.520821] PCI: 0000:01:08.0 reg 10 32bit mmio: [e3000000, e300ffff]
May  5 07:29:44 user kernel: [    0.520826] PCI: 0000:01:08.0 reg 14 io port: [9400, 9407]
May  5 07:29:44 user kernel: [    0.520849] pci 0000:01:08.0: PME# supported from D3hot D3cold
May  5 07:29:44 user kernel: [    0.520852] pci 0000:01:08.0: PME# disabled
May  5 07:29:44 user kernel: [    0.520872] PCI: 0000:01:09.0 reg 10 io port: [9800, 98ff]
May  5 07:29:44 user kernel: [    0.520877] PCI: 0000:01:09.0 reg 14 32bit mmio: [e3010000, e30100ff]
May  5 07:29:44 user kernel: [    0.520901] pci 0000:01:09.0: supports D1
May  5 07:29:44 user kernel: [    0.520903] pci 0000:01:09.0: supports D2
May  5 07:29:44 user kernel: [    0.520905] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520909] pci 0000:01:09.0: PME# disabled
May  5 07:29:44 user kernel: [    0.520929] PCI: 0000:01:0b.0 reg 10 io port: [9c00, 9cff]
May  5 07:29:44 user kernel: [    0.520934] PCI: 0000:01:0b.0 reg 14 32bit mmio: [e3011000, e30110ff]
May  5 07:29:44 user kernel: [    0.520951] PCI: 0000:01:0b.0 reg 30 32bit mmio: [0, ffff]
May  5 07:29:44 user kernel: [    0.520961] pci 0000:01:0b.0: supports D1
May  5 07:29:44 user kernel: [    0.520963] pci 0000:01:0b.0: supports D2
May  5 07:29:44 user kernel: [    0.520965] pci 0000:01:0b.0: PME# supported from D1 D2 D3hot D3cold
May  5 07:29:44 user kernel: [    0.520969] pci 0000:01:0b.0: PME# disabled
May  5 07:29:44 user kernel: [    0.520989] PCI: 0000:01:0d.0 reg 10 io port: [a000, a007]
May  5 07:29:44 user kernel: [    0.520994] PCI: 0000:01:0d.0 reg 14 io port: [a400, a403]
May  5 07:29:44 user kernel: [    0.520999] PCI: 0000:01:0d.0 reg 18 io port: [a800, a807]
May  5 07:29:44 user kernel: [    0.521004] PCI: 0000:01:0d.0 reg 1c io port: [ac00, ac03]
May  5 07:29:44 user kernel: [    0.521010] PCI: 0000:01:0d.0 reg 20 io port: [b000, b00f]
May  5 07:29:44 user kernel: [    0.521015] PCI: 0000:01:0d.0 reg 24 32bit mmio: [e3013000, e30131ff]
May  5 07:29:44 user kernel: [    0.521020] PCI: 0000:01:0d.0 reg 30 32bit mmio: [0, 7ffff]
May  5 07:29:44 user kernel: [    0.521030] pci 0000:01:0d.0: supports D1
May  5 07:29:44 user kernel: [    0.521032] pci 0000:01:0d.0: supports D2
May  5 07:29:44 user kernel: [    0.521049] PCI: bridge 0000:00:0a.0 io port: [9000, bfff]
May  5 07:29:44 user kernel: [    0.521052] PCI: bridge 0000:00:0a.0 32bit mmio: [e2000000, e3ffffff]
May  5 07:29:44 user kernel: [    0.521086] PCI: 0000:02:00.0 reg 10 32bit mmio: [d8000000, dbffffff]
May  5 07:29:44 user kernel: [    0.521092] PCI: 0000:02:00.0 reg 14 io port: [c000, c0ff]
May  5 07:29:44 user kernel: [    0.521098] PCI: 0000:02:00.0 reg 18 32bit mmio: [e1000000, e100ffff]
May  5 07:29:44 user kernel: [    0.521115] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, 1ffff]
May  5 07:29:44 user kernel: [    0.521130] pci 0000:02:00.0: supports D1
May  5 07:29:44 user kernel: [    0.521132] pci 0000:02:00.0: supports D2
May  5 07:29:44 user kernel: [    0.521154] PCI: 0000:02:00.1 reg 10 32bit mmio: [dc000000, dfffffff]
May  5 07:29:44 user kernel: [    0.521160] PCI: 0000:02:00.1 reg 14 32bit mmio: [e1010000, e101ffff]
May  5 07:29:44 user kernel: [    0.521190] pci 0000:02:00.1: supports D1
May  5 07:29:44 user kernel: [    0.521191] pci 0000:02:00.1: supports D2
May  5 07:29:44 user kernel: [    0.521229] PCI: bridge 0000:00:0b.0 io port: [c000, cfff]
May  5 07:29:44 user kernel: [    0.521233] PCI: bridge 0000:00:0b.0 32bit mmio: [e0000000, e1ffffff]
May  5 07:29:44 user kernel: [    0.521237] PCI: bridge 0000:00:0b.0 32bit mmio pref: [d8000000, dfffffff]
May  5 07:29:44 user kernel: [    0.521245] bus 00 -> node 0
May  5 07:29:44 user kernel: [    0.521252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May  5 07:29:44 user kernel: [    0.521449] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
May  5 07:29:44 user kernel: [    0.521867] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
May  5 07:29:44 user kernel: [    0.575512] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May  5 07:29:44 user kernel: [    0.575694] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:29:44 user kernel: [    0.575874] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  5 07:29:44 user kernel: [    0.576054] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  5 07:29:44 user kernel: [    0.576233] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May  5 07:29:44 user kernel: [    0.576413] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:29:44 user kernel: [    0.576593] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:29:44 user kernel: [    0.576771] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.576956] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.577137] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:29:44 user kernel: [    0.577315] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.577496] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  5 07:29:44 user kernel: [    0.577678] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:29:44 user kernel: [    0.577858] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.578037] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.578217] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.578404] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:29:44 user kernel: [    0.578553] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
May  5 07:29:44 user kernel: [    0.578693] ACPI: PCI Interrupt Link [APC2] (IRQs *17)
May  5 07:29:44 user kernel: [    0.578832] ACPI: PCI Interrupt Link [APC3] (IRQs *18)
May  5 07:29:44 user kernel: [    0.578971] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
May  5 07:29:44 user kernel: [    0.579110] ACPI: PCI Interrupt Link [APC5] (IRQs *16)
May  5 07:29:44 user kernel: [    0.579313] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
May  5 07:29:44 user kernel: [    0.579515] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
May  5 07:29:44 user kernel: [    0.579715] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.579916] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.580140] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
May  5 07:29:44 user kernel: [    0.580340] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.580481] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
May  5 07:29:44 user kernel: [    0.580679] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
May  5 07:29:44 user kernel: [    0.580879] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.581079] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.581279] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.581486] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22) *0, disabled.
May  5 07:29:44 user kernel: [    0.581628] ACPI: Power Resource [ISAV] (on)
May  5 07:29:44 user kernel: [    0.581712] Linux Plug and Play Support v0.97 (c) Adam Belay
May  5 07:29:44 user kernel: [    0.581746] pnp: PnP ACPI init
May  5 07:29:44 user kernel: [    0.581754] ACPI: bus type pnp registered
May  5 07:29:44 user kernel: [    0.587841] pnp: PnP ACPI: found 15 devices
May  5 07:29:44 user kernel: [    0.587844] ACPI: ACPI bus type pnp unregistered
May  5 07:29:44 user kernel: [    0.587847] PnPBIOS: Disabled by ACPI PNP
May  5 07:29:44 user kernel: [    0.588175] PCI: Using ACPI for IRQ routing
May  5 07:29:44 user kernel: [    0.588293] NET: Registered protocol family 8
May  5 07:29:44 user kernel: [    0.588293] NET: Registered protocol family 20
May  5 07:29:44 user kernel: [    0.588293] NetLabel: Initializing
May  5 07:29:44 user kernel: [    0.588293] NetLabel:  domain hash size = 128
May  5 07:29:44 user kernel: [    0.588293] NetLabel:  protocols = UNLABELED CIPSOv4
May  5 07:29:44 user kernel: [    0.588293] NetLabel:  unlabeled traffic allowed by default
May  5 07:29:44 user kernel: [    0.588293] tracer: 772 pages allocated for 65536 entries of 48 bytes
May  5 07:29:44 user kernel: [    0.588293]    actual entries 65620
May  5 07:29:44 user kernel: [    0.588293] AppArmor: AppArmor Filesystem Enabled
May  5 07:29:44 user kernel: [    0.588293] ACPI: RTC can wake from S4
May  5 07:29:44 user kernel: [    0.588293] system 00:00: ioport range 0x1000-0x107f has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:00: ioport range 0x1080-0x10ff has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:00: ioport range 0x1400-0x147f has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:00: ioport range 0x1480-0x14ff has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:00: ioport range 0x1800-0x187f has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:00: ioport range 0x1880-0x18ff has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xd8800-0xdbfff has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xf0000-0xf7fff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xf8000-0xfbfff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xfc000-0xfffff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0x2fff0000-0x2fffffff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xffff0000-0xffffffff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0x0-0x9ffff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0x100000-0x2ffeffff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
May  5 07:29:44 user kernel: [    0.588293] system 00:03: ioport range 0x800-0x805 has been reserved
May  5 07:29:44 user kernel: [    0.624048] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:01
May  5 07:29:44 user kernel: [    0.624052] pci 0000:00:0a.0:   IO window: 0x9000-0xbfff
May  5 07:29:44 user kernel: [    0.624056] pci 0000:00:0a.0:   MEM window: 0xe2000000-0xe3ffffff
May  5 07:29:44 user kernel: [    0.624059] pci 0000:00:0a.0:   PREFETCH window: 0x00000040000000-0x000000400fffff
May  5 07:29:44 user kernel: [    0.624065] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
May  5 07:29:44 user kernel: [    0.624068] pci 0000:00:0b.0:   IO window: 0xc000-0xcfff
May  5 07:29:44 user kernel: [    0.624073] pci 0000:00:0b.0:   MEM window: 0xe0000000-0xe1ffffff
May  5 07:29:44 user kernel: [    0.624077] pci 0000:00:0b.0:   PREFETCH window: 0x000000d8000000-0x000000dfffffff
May  5 07:29:44 user kernel: [    0.624089] pci 0000:00:0a.0: setting latency timer to 64
May  5 07:29:44 user kernel: [    0.624095] bus: 00 index 0 io port: [0, ffff]
May  5 07:29:44 user kernel: [    0.624098] bus: 00 index 1 mmio: [0, ffffffffffffffff]
May  5 07:29:44 user kernel: [    0.624100] bus: 01 index 0 io port: [9000, bfff]
May  5 07:29:44 user kernel: [    0.624102] bus: 01 index 1 mmio: [e2000000, e3ffffff]
May  5 07:29:44 user kernel: [    0.624105] bus: 01 index 2 mmio: [40000000, 400fffff]
May  5 07:29:44 user kernel: [    0.624107] bus: 01 index 3 mmio: [0, 0]
May  5 07:29:44 user kernel: [    0.624109] bus: 02 index 0 io port: [c000, cfff]
May  5 07:29:44 user kernel: [    0.624111] bus: 02 index 1 mmio: [e0000000, e1ffffff]
May  5 07:29:44 user kernel: [    0.624114] bus: 02 index 2 mmio: [d8000000, dfffffff]
May  5 07:29:44 user kernel: [    0.624116] bus: 02 index 3 mmio: [0, 0]
May  5 07:29:44 user kernel: [    0.624127] NET: Registered protocol family 2
May  5 07:29:44 user kernel: [    0.624251] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May  5 07:29:44 user kernel: [    0.624574] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May  5 07:29:44 user kernel: [    0.625530] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May  5 07:29:44 user kernel: [    0.626049] TCP: Hash tables configured (established 131072 bind 65536)
May  5 07:29:44 user kernel: [    0.626052] TCP reno registered
May  5 07:29:44 user kernel: [    0.626159] NET: Registered protocol family 1
May  5 07:29:44 user kernel: [    0.626278] checking if image is initramfs... it is
May  5 07:29:44 user kernel: [    1.130027] Switched to high resolution mode on CPU 0
May  5 07:29:44 user kernel: [    1.270116] Freeing initrd memory: 7861k freed
May  5 07:29:44 user kernel: [    1.270870] audit: initializing netlink socket (disabled)
May  5 07:29:44 user kernel: [    1.270885] type=2000 audit(1241508563.270:1): initialized
May  5 07:29:44 user kernel: [    1.277057] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May  5 07:29:44 user kernel: [    1.279219] VFS: Disk quotas dquot_6.5.1
May  5 07:29:44 user kernel: [    1.279304] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  5 07:29:44 user kernel: [    1.279400] msgmni has been set to 1510
May  5 07:29:44 user kernel: [    1.279520] io scheduler noop registered
May  5 07:29:44 user kernel: [    1.279522] io scheduler anticipatory registered
May  5 07:29:44 user kernel: [    1.279525] io scheduler deadline registered (default)
May  5 07:29:44 user kernel: [    1.279536] io scheduler cfq registered
May  5 07:29:44 user kernel: [    1.320057] pci 0000:02:00.0: Boot video device
May  5 07:29:44 user kernel: [    1.320377] isapnp: Scanning for PnP cards...
May  5 07:29:44 user kernel: [    1.676732] isapnp: No Plug & Play device found
May  5 07:29:44 user kernel: [    1.712934] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
May  5 07:29:44 user kernel: [    1.713052] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  5 07:29:44 user kernel: [    1.713192] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  5 07:29:44 user kernel: [    1.713760] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  5 07:29:44 user kernel: [    1.714033] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  5 07:29:44 user kernel: [    1.714419] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
May  5 07:29:44 user kernel: [    1.714428] serial 0000:01:06.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
May  5 07:29:44 user kernel: [    1.717560] brd: module loaded
May  5 07:29:44 user kernel: [    1.717632] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May  5 07:29:44 user kernel: [    1.717750] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May  5 07:29:44 user kernel: [    1.717753] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May  5 07:29:44 user kernel: [    1.718532] serio: i8042 KBD port at 0x60,0x64 irq 1
May  5 07:29:44 user kernel: [    1.718992] mice: PS/2 mouse device common for all mice
May  5 07:29:44 user kernel: [    1.719123] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
May  5 07:29:44 user kernel: [    1.719146] rtc0: alarms up to one year, y3k
May  5 07:29:44 user kernel: [    1.719262] EISA: Probing bus 0 at eisa.0
May  5 07:29:44 user kernel: [    1.719270] Cannot allocate resource for EISA slot 1
May  5 07:29:44 user kernel: [    1.719273] Cannot allocate resource for EISA slot 2
May  5 07:29:44 user kernel: [    1.719288] EISA: Detected 0 cards.
May  5 07:29:44 user kernel: [    1.719292] cpuidle: using governor ladder
May  5 07:29:44 user kernel: [    1.719294] cpuidle: using governor menu
May  5 07:29:44 user kernel: [    1.719813] TCP cubic registered
May  5 07:29:44 user kernel: [    1.719839] Using IPI No-Shortcut mode
May  5 07:29:44 user kernel: [    1.720043] registered taskstats version 1
May  5 07:29:44 user kernel: [    1.720176]   Magic number: 9:35:470
May  5 07:29:44 user kernel: [    1.720365] rtc_cmos 00:05: setting system clock to 2009-05-05 07:29:24 UTC (1241508564)
May  5 07:29:44 user kernel: [    1.720368] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  5 07:29:44 user kernel: [    1.720371] EDD information not available.
May  5 07:29:44 user kernel: [    1.720697] Freeing unused kernel memory: 436k freed
May  5 07:29:44 user kernel: [    1.720815] Write protecting the kernel text: 2632k
May  5 07:29:44 user kernel: [    1.720863] Write protecting the kernel read-only data: 956k
May  5 07:29:44 user kernel: [    1.741491] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May  5 07:29:44 user kernel: [    1.850276] fuse init (API version 7.9)
May  5 07:29:44 user kernel: [    1.870736] ACPI: processor limited to max C-state 1
May  5 07:29:44 user kernel: [    1.870820] processor ACPI0007:00: registered as cooling_device0
May  5 07:29:44 user kernel: [    2.590594] usbcore: registered new interface driver usbfs
May  5 07:29:44 user kernel: [    2.590620] usbcore: registered new interface driver hub
May  5 07:29:44 user kernel: [    2.590658] usbcore: registered new device driver usb
May  5 07:29:44 user kernel: [    2.596194] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
May  5 07:29:44 user kernel: [    2.596560] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
May  5 07:29:44 user kernel: [    2.596569] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 22 (level, high) -> IRQ 22
May  5 07:29:44 user kernel: [    2.596583] ohci_hcd 0000:00:02.0: setting latency timer to 64
May  5 07:29:44 user kernel: [    2.596586] ohci_hcd 0000:00:02.0: OHCI Host Controller
May  5 07:29:44 user kernel: [    2.596634] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
May  5 07:29:44 user kernel: [    2.596656] ohci_hcd 0000:00:02.0: irq 22, io mem 0xe4003000
May  5 07:29:44 user kernel: [    2.608392] No dock devices found.
May  5 07:29:44 user kernel: [    2.652216] usb usb1: configuration #1 chosen from 1 choice
May  5 07:29:44 user kernel: [    2.652246] hub 1-0:1.0: USB hub found
May  5 07:29:44 user kernel: [    2.652258] hub 1-0:1.0: 3 ports detected
May  5 07:29:44 user kernel: [    2.666143] SCSI subsystem initialized
May  5 07:29:44 user kernel: [    2.712969] libata version 3.00 loaded.
May  5 07:29:44 user kernel: [    2.870818] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
May  5 07:29:44 user kernel: [    2.870829] ohci_hcd 0000:00:02.1: PCI INT B -> Link[APCG] -> GSI 21 (level, high) -> IRQ 21
May  5 07:29:44 user kernel: [    2.870846] ohci_hcd 0000:00:02.1: setting latency timer to 64
May  5 07:29:44 user kernel: [    2.870849] ohci_hcd 0000:00:02.1: OHCI Host Controller
May  5 07:29:44 user kernel: [    2.870874] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
May  5 07:29:44 user kernel: [    2.870897] ohci_hcd 0000:00:02.1: irq 21, io mem 0xe4004000
May  5 07:29:44 user kernel: [    2.932226] usb usb2: configuration #1 chosen from 1 choice
May  5 07:29:44 user kernel: [    2.932256] hub 2-0:1.0: USB hub found
May  5 07:29:44 user kernel: [    2.932268] hub 2-0:1.0: 3 ports detected
May  5 07:29:44 user kernel: [    3.040883] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
May  5 07:29:44 user kernel: [    3.040893] ehci_hcd 0000:00:02.2: PCI INT C -> Link[APCL] -> GSI 20 (level, high) -> IRQ 20
May  5 07:29:44 user kernel: [    3.040910] ehci_hcd 0000:00:02.2: setting latency timer to 64
May  5 07:29:44 user kernel: [    3.040913] ehci_hcd 0000:00:02.2: EHCI Host Controller
May  5 07:29:44 user kernel: [    3.040938] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
May  5 07:29:44 user kernel: [    3.040965] ehci_hcd 0000:00:02.2: debug port 1
May  5 07:29:44 user kernel: [    3.040969] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
May  5 07:29:44 user kernel: [    3.040985] ehci_hcd 0000:00:02.2: irq 20, io mem 0xe4005000
May  5 07:29:44 user kernel: [    3.050047] usb 1-1: new full speed USB device using ohci_hcd and address 2
May  5 07:29:44 user kernel: [    3.070179] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May  5 07:29:44 user kernel: [    3.070355] usb usb3: configuration #1 chosen from 1 choice
May  5 07:29:44 user kernel: [    3.070388] hub 3-0:1.0: USB hub found
May  5 07:29:44 user kernel: [    3.070399] hub 3-0:1.0: 6 ports detected
May  5 07:29:44 user kernel: [    3.130205] hub 1-0:1.0: unable to enumerate USB device on port 1
May  5 07:29:44 user kernel: [    3.290412] pata_acpi 0000:00:08.0: power state changed by ACPI to D0
May  5 07:29:44 user kernel: [    3.290461] pata_acpi 0000:00:08.0: setting latency timer to 64
May  5 07:29:44 user kernel: [    3.291297] VIA Networking Velocity Family Gigabit Ethernet Adapter Driver Ver. 1.14
May  5 07:29:44 user kernel: [    3.291301] Copyright (c) 2002, 2003 VIA Networking Technologies, Inc.
May  5 07:29:44 user kernel: [    3.291303] Copyright (c) 2004 Red Hat Inc.
May  5 07:29:44 user kernel: [    3.291496] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
May  5 07:29:44 user kernel: [    3.291504] via-velocity 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
May  5 07:29:44 user kernel: [    3.292187] eth1: VIA Networking Velocity Family Gigabit Ethernet Adapter
May  5 07:29:44 user kernel: [    3.292191] eth1: Ethernet Address: 00:A0:C5:30:02:07
May  5 07:29:44 user kernel: [    3.310155] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
May  5 07:29:44 user kernel: [    3.310370] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
May  5 07:29:44 user kernel: [    3.310379] r8169 0000:01:0b.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
May  5 07:29:44 user kernel: [    3.310722] eth0: RTL8169s at 0xf083e000, 00:0d:61:21:54:d2, XID 00800000 IRQ 19
May  5 07:29:44 user kernel: [    3.317737] sata_sil 0000:01:0d.0: version 2.3
May  5 07:29:44 user kernel: [    3.317781] sata_sil 0000:01:0d.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
May  5 07:29:44 user kernel: [    3.317800] sata_sil 0000:01:0d.0: Applying R_ERR on DMA activate FIS errata fix
May  5 07:29:44 user kernel: [    3.317856] scsi0 : sata_sil
May  5 07:29:44 user kernel: [    3.317952] scsi1 : sata_sil
May  5 07:29:44 user kernel: [    3.317987] ata1: SATA max UDMA/100 mmio m512@0xe3013000 tf 0xe3013080 irq 17
May  5 07:29:44 user kernel: [    3.317991] ata2: SATA max UDMA/100 mmio m512@0xe3013000 tf 0xe30130c0 irq 17
May  5 07:29:44 user kernel: [    3.318072] pata_amd 0000:00:08.0: version 0.3.10
May  5 07:29:44 user kernel: [    3.318154] pata_amd 0000:00:08.0: power state changed by ACPI to D0
May  5 07:29:44 user kernel: [    3.318193] pata_amd 0000:00:08.0: setting latency timer to 64
May  5 07:29:44 user kernel: [    3.318244] scsi2 : pata_amd
May  5 07:29:44 user kernel: [    3.318300] scsi3 : pata_amd
May  5 07:29:44 user kernel: [    3.319153] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
May  5 07:29:44 user kernel: [    3.319156] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
May  5 07:29:44 user kernel: [    3.550434] ata3.00: ATA-6: ST380011A, 8.01, max UDMA/100
May  5 07:29:44 user kernel: [    3.550438] ata3.00: 156301488 sectors, multi 16: LBA48 
May  5 07:29:44 user kernel: [    3.550453] ata3: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc60000c0) ACPI=0x3f01f (20:600:0x13)
May  5 07:29:44 user kernel: [    3.590359] ata3.00: configured for UDMA/100
May  5 07:29:44 user kernel: [    3.660026] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
May  5 07:29:44 user kernel: [    3.680397] ata1.00: ATA-6: ST3120827AS, 3.42, max UDMA/133
May  5 07:29:44 user kernel: [    3.680400] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
May  5 07:29:44 user kernel: [    3.720402] ata1.00: configured for UDMA/100
May  5 07:29:44 user kernel: [    3.780293] ata4.01: ATAPI: _NEC DVD_RW ND-1300A, 1.08, max UDMA/33
May  5 07:29:44 user kernel: [    3.780306] ata4: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc60000c0) ACPI=0x701f (600:60:0x1c)
May  5 07:29:44 user kernel: [    3.820232] ata4.01: configured for UDMA/33
May  5 07:29:44 user kernel: [    3.820332] scsi 2:0:0:0: Direct-Access     ATA      ST380011A        8.01 PQ: 0 ANSI: 5
May  5 07:29:44 user kernel: [    3.823413] scsi 3:0:1:0: CD-ROM            _NEC     DVD_RW ND-1300A  1.08 PQ: 0 ANSI: 5
May  5 07:29:44 user kernel: [    4.070023] ata2: SATA link down (SStatus 0 SControl 310)
May  5 07:29:44 user kernel: [    4.070132] scsi 0:0:0:0: Direct-Access     ATA      ST3120827AS      3.42 PQ: 0 ANSI: 5
May  5 07:29:44 user kernel: [    4.079725] scsi 2:0:0:0: Attached scsi generic sg0 type 0
May  5 07:29:44 user kernel: [    4.079763] scsi 3:0:1:0: Attached scsi generic sg1 type 5
May  5 07:29:44 user kernel: [    4.079800] scsi 0:0:0:0: Attached scsi generic sg2 type 0
May  5 07:29:44 user kernel: [    4.108308] Driver 'sd' needs updating - please use bus_type methods
May  5 07:29:44 user kernel: [    4.108423] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
May  5 07:29:44 user kernel: [    4.108441] sd 2:0:0:0: [sda] Write Protect is off
May  5 07:29:44 user kernel: [    4.108444] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  5 07:29:44 user kernel: [    4.108470] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:29:44 user kernel: [    4.108535] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
May  5 07:29:44 user kernel: [    4.108549] sd 2:0:0:0: [sda] Write Protect is off
May  5 07:29:44 user kernel: [    4.108551] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  5 07:29:44 user kernel: [    4.108576] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:29:44 user kernel: [    4.108581]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
May  5 07:29:44 user kernel: [    4.126503]  sda1 < sda5 sda6 >
May  5 07:29:44 user kernel: [    4.134656] sd 2:0:0:0: [sda] Attached SCSI disk
May  5 07:29:44 user kernel: [    4.134744] sd 0:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
May  5 07:29:44 user kernel: [    4.134764] sd 0:0:0:0: [sdb] Write Protect is off
May  5 07:29:44 user kernel: [    4.134766] sd 0:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May  5 07:29:44 user kernel: [    4.134796] sd 0:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:29:44 user kernel: [    4.134858] sd 0:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
May  5 07:29:44 user kernel: [    4.134874] sd 0:0:0:0: [sdb] Write Protect is off
May  5 07:29:44 user kernel: [    4.134877] sd 0:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May  5 07:29:44 user kernel: [    4.134905] sd 0:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:29:44 user kernel: [    4.134909]  sdb:sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
May  5 07:29:44 user kernel: [    4.139192] Uniform CD-ROM driver Revision: 3.20
May  5 07:29:44 user kernel: [    4.139290] sr 3:0:1:0: Attached scsi CD-ROM sr0
May  5 07:29:44 user kernel: [    4.151098]  sdb1 sdb2 < sdb5 sdb6 sdb7 >
May  5 07:29:44 user kernel: [    4.184197] sd 0:0:0:0: [sdb] Attached SCSI disk
May  5 07:29:44 user kernel: [    4.250029] usb 1-1: new full speed USB device using ohci_hcd and address 3
May  5 07:29:44 user kernel: [    4.476272] usb 1-1: configuration #1 chosen from 1 choice
May  5 07:29:44 user kernel: [    4.656792] PM: Starting manual resume from disk
May  5 07:29:44 user kernel: [    4.656797] PM: Resume from partition 8:5
May  5 07:29:44 user kernel: [    4.656799] PM: Checking hibernation image.
May  5 07:29:44 user kernel: [    4.656959] PM: Resume from disk failed.
May  5 07:29:44 user kernel: [    4.709126] kjournald starting.  Commit interval 5 seconds
May  5 07:29:44 user kernel: [    4.709143] EXT3-fs: mounted filesystem with ordered data mode.
May  5 07:29:44 user kernel: [    4.820026] usb 1-2: new full speed USB device using ohci_hcd and address 4
May  5 07:29:44 user kernel: [    5.043133] usb 1-2: configuration #1 chosen from 1 choice
May  5 07:29:44 user kernel: [    5.380026] usb 1-3: new low speed USB device using ohci_hcd and address 5
May  5 07:29:44 user kernel: [    5.606225] usb 1-3: configuration #1 chosen from 1 choice
May  5 07:29:44 user kernel: [    6.907183] udevd version 124 started
May  5 07:29:44 user kernel: [    7.911918] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  5 07:29:44 user kernel: [    7.952110] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  5 07:29:44 user kernel: [    8.030740] Linux agpgart interface v0.103
May  5 07:29:44 user kernel: [    8.094743] input: PC Speaker as /devices/platform/pcspkr/input/input2
May  5 07:29:44 user kernel: [    8.120911] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
May  5 07:29:44 user kernel: [    8.120946] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
May  5 07:29:44 user kernel: [    8.124787] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
May  5 07:29:44 user kernel: [    8.142953] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
May  5 07:29:44 user kernel: [    8.142973] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2000
May  5 07:29:44 user kernel: [    8.154607] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
May  5 07:29:44 user kernel: [    8.180063] ACPI: Power Button (FF) [PWRF]
May  5 07:29:44 user kernel: [    8.180162] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
May  5 07:29:44 user kernel: [    8.210085] ACPI: Power Button (CM) [PWRB]
May  5 07:29:44 user kernel: [    8.263570] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
May  5 07:29:44 user kernel: [    8.263577] Intel ICH 0000:00:06.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, high) -> IRQ 22
May  5 07:29:44 user kernel: [    8.263600] Intel ICH 0000:00:06.0: setting latency timer to 64
May  5 07:29:44 user kernel: [    8.610028] intel8x0_measure_ac97_clock: measured 59796 usecs
May  5 07:29:44 user kernel: [    8.610033] intel8x0: clocking to 48000
May  5 07:29:44 user kernel: [    8.701966] parport_pc 00:0b: reported by Plug and Play ACPI
May  5 07:29:44 user kernel: [    8.702009] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
May  5 07:29:44 user kernel: [   10.207818] ieee80211_crypt: registered algorithm 'NULL'
May  5 07:29:44 user kernel: [   10.211835] ieee80211: 802.11 data/management/control stack, git-1.1.13
May  5 07:29:44 user kernel: [   10.211840] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
May  5 07:29:44 user kernel: [   10.280828] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
May  5 07:29:44 user kernel: [   10.280833] ipw2200: Copyright(c) 2003-2006 Intel Corporation
May  5 07:29:44 user kernel: [   10.280929] ipw2200 0000:01:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
May  5 07:29:44 user kernel: [   10.280981] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
May  5 07:29:44 user kernel: [   10.281034] firmware: requesting ipw2200-bss.fw
May  5 07:29:44 user kernel: [   10.626329] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
May  5 07:29:44 user kernel: [   10.632897] usbcore: registered new interface driver cdc_acm
May  5 07:29:44 user kernel: [   10.632903] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
May  5 07:29:44 user kernel: [   10.933501] usbcore: registered new interface driver snd-usb-audio
May  5 07:29:44 user kernel: [   10.933531] usbcore: registered new interface driver hiddev
May  5 07:29:44 user kernel: [   10.942276] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.3/input/input5
May  5 07:29:44 user kernel: [   11.000230] input,hidraw0: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:02.0-2
May  5 07:29:44 user kernel: [   11.006479] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.0/input/input6
May  5 07:29:44 user kernel: [   11.050386] input,hidraw1: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:02.0-3
May  5 07:29:44 user kernel: [   11.050410] usbcore: registered new interface driver usbhid
May  5 07:29:44 user kernel: [   11.050414] usbhid: v2.6:USB HID core driver
May  5 07:29:44 user kernel: [   12.615459] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
May  5 07:29:44 user kernel: [   13.508028] loop: module loaded
May  5 07:29:44 user kernel: [   13.522041] lp0: using parport0 (interrupt-driven).
May  5 07:29:44 user kernel: [   13.890054] Adding 248936k swap on /dev/sda5.  Priority:-1 extents:1 across:248936k
May  5 07:29:44 user kernel: [   14.241224] EXT3 FS on sda6, internal journal
May  5 07:29:44 user kernel: [   15.345827] ip_tables: (C) 2000-2006 Netfilter Core Team
May  5 07:29:44 user kernel: [   15.396787] r8169: eth0: link up
May  5 07:29:44 user kernel: [   16.736930] NET: Registered protocol family 17
May  5 07:29:44 user kernel: [   19.564822] Velocity is AUTO mode
May  5 07:29:44 user kernel: [   20.086147] NET: Registered protocol family 10
May  5 07:29:44 user kernel: [   20.086644] lo: Disabled Privacy Extensions
May  5 07:29:46 user kernel: [   24.094996] warning: `dhcpd3' uses 32-bit capabilities (legacy support in use)
May  5 07:29:52 user kernel: [   30.290010] eth1: no IPv6 routers present
May  5 07:29:53 user kernel: [   30.540005] eth0: no IPv6 routers present
May  5 07:40:59 user kernel: Inspecting /boot/System.map-2.6.27-7-server
May  5 07:40:59 user kernel: Cannot find map file.
May  5 07:40:59 user kernel: Loaded 48877 symbols from 70 modules.
May  5 07:40:59 user kernel: [    0.000000] Initializing cgroup subsys cpuset
May  5 07:40:59 user kernel: [    0.000000] Initializing cgroup subsys cpu
May  5 07:40:59 user kernel: [    0.000000] Linux version 2.6.27-7-server (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 20:18:35 UTC 2008 (Ubuntu 2.6.27-7.16-server)
May  5 07:40:59 user kernel: [    0.000000] BIOS-provided physical RAM map:
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May  5 07:40:59 user kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
May  5 07:40:59 user kernel: [    0.000000] last_pfn = 0x2fff0 max_arch_pfn = 0x1000000
May  5 07:40:59 user kernel: [    0.000000] kernel direct mapping tables up to 2fff0000 @ 7000-d000
May  5 07:40:59 user kernel: [    0.000000] NX (Execute Disable) protection: active
May  5 07:40:59 user kernel: [    0.000000] RAMDISK: 2f832000 - 2ffdf6b8
May  5 07:40:59 user kernel: [    0.000000] DMI 2.3 present.
May  5 07:40:59 user kernel: [    0.000000] ACPI: RSDP 000F6AB0, 0014 (r0 Nvidia)
May  5 07:40:59 user kernel: [    0.000000] ACPI: RSDT 2FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  5 07:40:59 user kernel: [    0.000000] ACPI: FACP 2FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  5 07:40:59 user kernel: [    0.000000] ACPI: DSDT 2FFF30C0, 4ABF (r1 NVIDIA AWRDACPI     1000 MSFT  100000C)
May  5 07:40:59 user kernel: [    0.000000] ACPI: FACS 2FFF0000, 0040
May  5 07:40:59 user kernel: [    0.000000] ACPI: APIC 2FFF7B80, 005A (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  5 07:40:59 user kernel: [    0.000000] 0MB HIGHMEM available.
May  5 07:40:59 user kernel: [    0.000000] 767MB LOWMEM available.
May  5 07:40:59 user kernel: [    0.000000]   mapped low ram: 0 - 2fff0000
May  5 07:40:59 user kernel: [    0.000000]   low ram: 00000000 - 2fff0000
May  5 07:40:59 user kernel: [    0.000000]   bootmap 0000a000 - 00010000
May  5 07:40:59 user kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002fff0000]
May  5 07:40:59 user kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
May  5 07:40:59 user kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
May  5 07:40:59 user kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
May  5 07:40:59 user kernel: [    0.000000]   #3 [0000100000 - 00005e8220]    TEXT DATA BSS ==> [0000100000 - 00005e8220]
May  5 07:40:59 user kernel: [    0.000000]   #4 [002f832000 - 002ffdf6b8]          RAMDISK ==> [002f832000 - 002ffdf6b8]
May  5 07:40:59 user kernel: [    0.000000]   #5 [00005e9000 - 00005f1000]    INIT_PG_TABLE ==> [00005e9000 - 00005f1000]
May  5 07:40:59 user kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
May  5 07:40:59 user kernel: [    0.000000]   #7 [0000007000 - 000000a000]          PGTABLE ==> [0000007000 - 000000a000]
May  5 07:40:59 user kernel: [    0.000000]   #8 [000000a000 - 0000010000]          BOOTMAP ==> [000000a000 - 0000010000]
May  5 07:40:59 user kernel: [    0.000000] found SMP MP-table at [c00f5000] 000f5000
May  5 07:40:59 user kernel: [    0.000000] Zone PFN ranges:
May  5 07:40:59 user kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
May  5 07:40:59 user kernel: [    0.000000]   Normal   0x00001000 -> 0x0002fff0
May  5 07:40:59 user kernel: [    0.000000]   HighMem  0x0002fff0 -> 0x0002fff0
May  5 07:40:59 user kernel: [    0.000000] Movable zone start PFN for each node
May  5 07:40:59 user kernel: [    0.000000] early_node_map[2] active PFN ranges
May  5 07:40:59 user kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
May  5 07:40:59 user kernel: [    0.000000]     0: 0x00000100 -> 0x0002fff0
May  5 07:40:59 user kernel: [    0.000000] On node 0 totalpages: 196495
May  5 07:40:59 user kernel: [    0.000000] free_area_init_node: node 0, pgdat c049eb00, node_mem_map c1000000
May  5 07:40:59 user kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
May  5 07:40:59 user kernel: [    0.000000]   Normal zone: 190804 pages, LIFO batch:31
May  5 07:40:59 user kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
May  5 07:40:59 user kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
May  5 07:40:59 user kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
May  5 07:40:59 user kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  5 07:40:59 user kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  5 07:40:59 user kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
May  5 07:40:59 user kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  5 07:40:59 user kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
May  5 07:40:59 user kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  5 07:40:59 user kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
May  5 07:40:59 user kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  5 07:40:59 user kernel: [    0.000000] ACPI: IRQ9 used by override.
May  5 07:40:59 user kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  5 07:40:59 user kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  5 07:40:59 user kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
May  5 07:40:59 user kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
May  5 07:40:59 user kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
May  5 07:40:59 user kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May  5 07:40:59 user kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
May  5 07:40:59 user kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
May  5 07:40:59 user kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
May  5 07:40:59 user kernel: [    0.000000] PERCPU: Allocating 45852 bytes of per cpu data
May  5 07:40:59 user kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
May  5 07:40:59 user kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194767
May  5 07:40:59 user kernel: [    0.000000] Kernel command line: root=UUID=3a16f219-3073-4cf3-8fa0-646d16cda612 ro quiet splash 
May  5 07:40:59 user kernel: [    0.000000] Enabling fast FPU save and restore... done.
May  5 07:40:59 user kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May  5 07:40:59 user kernel: [    0.000000] Initializing CPU#0
May  5 07:40:59 user kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
May  5 07:40:59 user kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
May  5 07:40:59 user kernel: [    0.000000] TSC: using PIT calibration value
May  5 07:40:59 user kernel: [    0.000000] Detected 1994.815 MHz processor.
May  5 07:40:59 user kernel: [    0.010000] spurious 8259A interrupt: IRQ7.
May  5 07:40:59 user kernel: [    0.010000] Console: colour VGA+ 80x25
May  5 07:40:59 user kernel: [    0.010000] console [tty0] enabled
May  5 07:40:59 user kernel: [    0.010000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  5 07:40:59 user kernel: [    0.010000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  5 07:40:59 user kernel: [    0.010000] Memory: 765068k/786368k available (2628k kernel code, 20728k reserved, 1201k data, 436k init, 0k highmem)
May  5 07:40:59 user kernel: [    0.010000] virtual kernel memory layout:
May  5 07:40:59 user kernel: [    0.010000]     fixmap  : 0xffc78000 - 0xfffff000   (3612 kB)
May  5 07:40:59 user kernel: [    0.010000]     pkmap   : 0xff800000 - 0xffa00000   (2048 kB)
May  5 07:40:59 user kernel: [    0.010000]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
May  5 07:40:59 user kernel: [    0.010000]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
May  5 07:40:59 user kernel: [    0.010000]       .init : 0xc04c3000 - 0xc0530000   ( 436 kB)
May  5 07:40:59 user kernel: [    0.010000]       .data : 0xc0391036 - 0xc04bd800   (1201 kB)
May  5 07:40:59 user kernel: [    0.010000]       .text : 0xc0100000 - 0xc0391036   (2628 kB)
May  5 07:40:59 user kernel: [    0.010000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
May  5 07:40:59 user kernel: [    0.010000] CPA: page pool initialized 1 of 1 pages preallocated
May  5 07:40:59 user kernel: [    0.010000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
May  5 07:40:59 user kernel: [    0.010008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.63 BogoMIPS (lpj=19948150)
May  5 07:40:59 user kernel: [    0.010026] Security Framework initialized
May  5 07:40:59 user kernel: [    0.010033] SELinux:  Disabled at boot.
May  5 07:40:59 user kernel: [    0.010053] AppArmor: AppArmor initialized
May  5 07:40:59 user kernel: [    0.010061] Mount-cache hash table entries: 512
May  5 07:40:59 user kernel: [    0.010209] Initializing cgroup subsys ns
May  5 07:40:59 user kernel: [    0.010213] Initializing cgroup subsys cpuacct
May  5 07:40:59 user kernel: [    0.010215] Initializing cgroup subsys memory
May  5 07:40:59 user kernel: [    0.010228] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May  5 07:40:59 user kernel: [    0.010231] CPU: L2 Cache: 512K (64 bytes/line)
May  5 07:40:59 user kernel: [    0.010241] Checking 'hlt' instruction... OK.
May  5 07:40:59 user kernel: [    0.050367] SMP alternatives: switching to UP code
May  5 07:40:59 user kernel: [    0.056452] Freeing SMP alternatives: 11k freed
May  5 07:40:59 user kernel: [    0.056457] ACPI: Core revision 20080609
May  5 07:40:59 user kernel: [    0.057952] ACPI: Checking initramfs for custom DSDT
May  5 07:40:59 user kernel: [    0.371033] ENABLING IO-APIC IRQs
May  5 07:40:59 user kernel: [    0.371200] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
May  5 07:40:59 user kernel: [    0.471211] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 08
May  5 07:40:59 user kernel: [    0.480000] Brought up 1 CPUs
May  5 07:40:59 user kernel: [    0.480000] Total of 1 processors activated (3989.63 BogoMIPS).
May  5 07:40:59 user kernel: [    0.480000] CPU0 attaching sched-domain:
May  5 07:40:59 user kernel: [    0.480000]  domain 0: span 0 level CPU
May  5 07:40:59 user kernel: [    0.480000]   groups: 0
May  5 07:40:59 user kernel: [    0.480000] net_namespace: 840 bytes
May  5 07:40:59 user kernel: [    0.480000] Booting paravirtualized kernel on bare hardware
May  5 07:40:59 user kernel: [    0.480000] Time:  7:40:36  Date: 05/05/09
May  5 07:40:59 user kernel: [    0.480000] NET: Registered protocol family 16
May  5 07:40:59 user kernel: [    0.480000] EISA bus registered
May  5 07:40:59 user kernel: [    0.480000] ACPI: bus type pci registered
May  5 07:40:59 user kernel: [    0.500543] PCI: PCI BIOS revision 2.10 entry at 0xfac80, last bus=2
May  5 07:40:59 user kernel: [    0.500546] PCI: Using configuration type 1 for base access
May  5 07:40:59 user kernel: [    0.502223] ACPI: EC: Look up EC in DSDT
May  5 07:40:59 user kernel: [    0.509554] ACPI: Interpreter enabled
May  5 07:40:59 user kernel: [    0.509557] ACPI: (supports S0 S3 S4 S5)
May  5 07:40:59 user kernel: [    0.509571] ACPI: Using IOAPIC for interrupt routing
May  5 07:40:59 user kernel: [    0.520239] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  5 07:40:59 user kernel: [    0.520317] PCI: 0000:00:00.0 reg 10 32bit mmio: [d0000000, d7ffffff]
May  5 07:40:59 user kernel: [    0.520386] PCI: 0000:00:01.1 reg 20 io port: [1c00, 1c3f]
May  5 07:40:59 user kernel: [    0.520391] PCI: 0000:00:01.1 reg 24 io port: [2000, 203f]
May  5 07:40:59 user kernel: [    0.520400] pci 0000:00:01.1: PME# supported from D3hot D3cold
May  5 07:40:59 user kernel: [    0.520404] pci 0000:00:01.1: PME# disabled
May  5 07:40:59 user kernel: [    0.520422] PCI: 0000:00:02.0 reg 10 32bit mmio: [e4003000, e4003fff]
May  5 07:40:59 user kernel: [    0.520439] pci 0000:00:02.0: supports D1
May  5 07:40:59 user kernel: [    0.520441] pci 0000:00:02.0: supports D2
May  5 07:40:59 user kernel: [    0.520443] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520446] pci 0000:00:02.0: PME# disabled
May  5 07:40:59 user kernel: [    0.520460] PCI: 0000:00:02.1 reg 10 32bit mmio: [e4004000, e4004fff]
May  5 07:40:59 user kernel: [    0.520477] pci 0000:00:02.1: supports D1
May  5 07:40:59 user kernel: [    0.520479] pci 0000:00:02.1: supports D2
May  5 07:40:59 user kernel: [    0.520481] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520484] pci 0000:00:02.1: PME# disabled
May  5 07:40:59 user kernel: [    0.520501] PCI: 0000:00:02.2 reg 10 32bit mmio: [e4005000, e40050ff]
May  5 07:40:59 user kernel: [    0.520521] pci 0000:00:02.2: supports D1
May  5 07:40:59 user kernel: [    0.520522] pci 0000:00:02.2: supports D2
May  5 07:40:59 user kernel: [    0.520525] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520528] pci 0000:00:02.2: PME# disabled
May  5 07:40:59 user kernel: [    0.520549] PCI: 0000:00:06.0 reg 10 io port: [d400, d4ff]
May  5 07:40:59 user kernel: [    0.520553] PCI: 0000:00:06.0 reg 14 io port: [d800, d87f]
May  5 07:40:59 user kernel: [    0.520557] PCI: 0000:00:06.0 reg 18 32bit mmio: [e4001000, e4001fff]
May  5 07:40:59 user kernel: [    0.520571] pci 0000:00:06.0: supports D1
May  5 07:40:59 user kernel: [    0.520572] pci 0000:00:06.0: supports D2
May  5 07:40:59 user kernel: [    0.520592] PCI: 0000:00:08.0 reg 20 io port: [f000, f00f]
May  5 07:40:59 user kernel: [    0.520719] PCI: 0000:01:06.0 reg 10 io port: [9000, 903f]
May  5 07:40:59 user kernel: [    0.520748] pci 0000:01:06.0: supports D2
May  5 07:40:59 user kernel: [    0.520750] pci 0000:01:06.0: PME# supported from D0 D2 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520754] pci 0000:01:06.0: PME# disabled
May  5 07:40:59 user kernel: [    0.520774] PCI: 0000:01:07.0 reg 10 32bit mmio: [e3012000, e3012fff]
May  5 07:40:59 user kernel: [    0.520803] pci 0000:01:07.0: PME# supported from D0 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520807] pci 0000:01:07.0: PME# disabled
May  5 07:40:59 user kernel: [    0.520826] PCI: 0000:01:08.0 reg 10 32bit mmio: [e3000000, e300ffff]
May  5 07:40:59 user kernel: [    0.520831] PCI: 0000:01:08.0 reg 14 io port: [9400, 9407]
May  5 07:40:59 user kernel: [    0.520854] pci 0000:01:08.0: PME# supported from D3hot D3cold
May  5 07:40:59 user kernel: [    0.520857] pci 0000:01:08.0: PME# disabled
May  5 07:40:59 user kernel: [    0.520876] PCI: 0000:01:09.0 reg 10 io port: [9800, 98ff]
May  5 07:40:59 user kernel: [    0.520882] PCI: 0000:01:09.0 reg 14 32bit mmio: [e3010000, e30100ff]
May  5 07:40:59 user kernel: [    0.520906] pci 0000:01:09.0: supports D1
May  5 07:40:59 user kernel: [    0.520908] pci 0000:01:09.0: supports D2
May  5 07:40:59 user kernel: [    0.520910] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520913] pci 0000:01:09.0: PME# disabled
May  5 07:40:59 user kernel: [    0.520934] PCI: 0000:01:0b.0 reg 10 io port: [9c00, 9cff]
May  5 07:40:59 user kernel: [    0.520939] PCI: 0000:01:0b.0 reg 14 32bit mmio: [e3011000, e30110ff]
May  5 07:40:59 user kernel: [    0.520956] PCI: 0000:01:0b.0 reg 30 32bit mmio: [0, ffff]
May  5 07:40:59 user kernel: [    0.520966] pci 0000:01:0b.0: supports D1
May  5 07:40:59 user kernel: [    0.520968] pci 0000:01:0b.0: supports D2
May  5 07:40:59 user kernel: [    0.520970] pci 0000:01:0b.0: PME# supported from D1 D2 D3hot D3cold
May  5 07:40:59 user kernel: [    0.520974] pci 0000:01:0b.0: PME# disabled
May  5 07:40:59 user kernel: [    0.520994] PCI: 0000:01:0d.0 reg 10 io port: [a000, a007]
May  5 07:40:59 user kernel: [    0.520999] PCI: 0000:01:0d.0 reg 14 io port: [a400, a403]
May  5 07:40:59 user kernel: [    0.521004] PCI: 0000:01:0d.0 reg 18 io port: [a800, a807]
May  5 07:40:59 user kernel: [    0.521009] PCI: 0000:01:0d.0 reg 1c io port: [ac00, ac03]
May  5 07:40:59 user kernel: [    0.521014] PCI: 0000:01:0d.0 reg 20 io port: [b000, b00f]
May  5 07:40:59 user kernel: [    0.521020] PCI: 0000:01:0d.0 reg 24 32bit mmio: [e3013000, e30131ff]
May  5 07:40:59 user kernel: [    0.521025] PCI: 0000:01:0d.0 reg 30 32bit mmio: [0, 7ffff]
May  5 07:40:59 user kernel: [    0.521035] pci 0000:01:0d.0: supports D1
May  5 07:40:59 user kernel: [    0.521037] pci 0000:01:0d.0: supports D2
May  5 07:40:59 user kernel: [    0.521054] PCI: bridge 0000:00:0a.0 io port: [9000, bfff]
May  5 07:40:59 user kernel: [    0.521057] PCI: bridge 0000:00:0a.0 32bit mmio: [e2000000, e3ffffff]
May  5 07:40:59 user kernel: [    0.521091] PCI: 0000:02:00.0 reg 10 32bit mmio: [d8000000, dbffffff]
May  5 07:40:59 user kernel: [    0.521097] PCI: 0000:02:00.0 reg 14 io port: [c000, c0ff]
May  5 07:40:59 user kernel: [    0.521103] PCI: 0000:02:00.0 reg 18 32bit mmio: [e1000000, e100ffff]
May  5 07:40:59 user kernel: [    0.521120] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, 1ffff]
May  5 07:40:59 user kernel: [    0.521135] pci 0000:02:00.0: supports D1
May  5 07:40:59 user kernel: [    0.521137] pci 0000:02:00.0: supports D2
May  5 07:40:59 user kernel: [    0.521159] PCI: 0000:02:00.1 reg 10 32bit mmio: [dc000000, dfffffff]
May  5 07:40:59 user kernel: [    0.521165] PCI: 0000:02:00.1 reg 14 32bit mmio: [e1010000, e101ffff]
May  5 07:40:59 user kernel: [    0.521195] pci 0000:02:00.1: supports D1
May  5 07:40:59 user kernel: [    0.521197] pci 0000:02:00.1: supports D2
May  5 07:40:59 user kernel: [    0.521234] PCI: bridge 0000:00:0b.0 io port: [c000, cfff]
May  5 07:40:59 user kernel: [    0.521238] PCI: bridge 0000:00:0b.0 32bit mmio: [e0000000, e1ffffff]
May  5 07:40:59 user kernel: [    0.521242] PCI: bridge 0000:00:0b.0 32bit mmio pref: [d8000000, dfffffff]
May  5 07:40:59 user kernel: [    0.521251] bus 00 -> node 0
May  5 07:40:59 user kernel: [    0.521257] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May  5 07:40:59 user kernel: [    0.521454] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
May  5 07:40:59 user kernel: [    0.521872] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
May  5 07:40:59 user kernel: [    0.575503] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May  5 07:40:59 user kernel: [    0.575685] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:40:59 user kernel: [    0.575865] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  5 07:40:59 user kernel: [    0.576044] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  5 07:40:59 user kernel: [    0.576224] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May  5 07:40:59 user kernel: [    0.576403] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:40:59 user kernel: [    0.576583] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:40:59 user kernel: [    0.576762] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.576946] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.577127] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:40:59 user kernel: [    0.577305] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.577486] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  5 07:40:59 user kernel: [    0.577668] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  5 07:40:59 user kernel: [    0.577848] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.578027] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.578206] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.578394] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  5 07:40:59 user kernel: [    0.578543] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
May  5 07:40:59 user kernel: [    0.578683] ACPI: PCI Interrupt Link [APC2] (IRQs *17)
May  5 07:40:59 user kernel: [    0.578822] ACPI: PCI Interrupt Link [APC3] (IRQs *18)
May  5 07:40:59 user kernel: [    0.578961] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
May  5 07:40:59 user kernel: [    0.579100] ACPI: PCI Interrupt Link [APC5] (IRQs *16)
May  5 07:40:59 user kernel: [    0.579303] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
May  5 07:40:59 user kernel: [    0.579505] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
May  5 07:40:59 user kernel: [    0.579705] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.579906] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.580130] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
May  5 07:40:59 user kernel: [    0.580329] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.580470] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
May  5 07:40:59 user kernel: [    0.580668] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
May  5 07:40:59 user kernel: [    0.580868] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.581068] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.581268] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.581476] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22) *0, disabled.
May  5 07:40:59 user kernel: [    0.581617] ACPI: Power Resource [ISAV] (on)
May  5 07:40:59 user kernel: [    0.581701] Linux Plug and Play Support v0.97 (c) Adam Belay
May  5 07:40:59 user kernel: [    0.581735] pnp: PnP ACPI init
May  5 07:40:59 user kernel: [    0.581743] ACPI: bus type pnp registered
May  5 07:40:59 user kernel: [    0.587831] pnp: PnP ACPI: found 15 devices
May  5 07:40:59 user kernel: [    0.587834] ACPI: ACPI bus type pnp unregistered
May  5 07:40:59 user kernel: [    0.587838] PnPBIOS: Disabled by ACPI PNP
May  5 07:40:59 user kernel: [    0.588165] PCI: Using ACPI for IRQ routing
May  5 07:40:59 user kernel: [    0.588283] NET: Registered protocol family 8
May  5 07:40:59 user kernel: [    0.588283] NET: Registered protocol family 20
May  5 07:40:59 user kernel: [    0.588283] NetLabel: Initializing
May  5 07:40:59 user kernel: [    0.588283] NetLabel:  domain hash size = 128
May  5 07:40:59 user kernel: [    0.588283] NetLabel:  protocols = UNLABELED CIPSOv4
May  5 07:40:59 user kernel: [    0.588283] NetLabel:  unlabeled traffic allowed by default
May  5 07:40:59 user kernel: [    0.588283] tracer: 772 pages allocated for 65536 entries of 48 bytes
May  5 07:40:59 user kernel: [    0.588283]    actual entries 65620
May  5 07:40:59 user kernel: [    0.588283] AppArmor: AppArmor Filesystem Enabled
May  5 07:40:59 user kernel: [    0.588283] ACPI: RTC can wake from S4
May  5 07:40:59 user kernel: [    0.588283] system 00:00: ioport range 0x1000-0x107f has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:00: ioport range 0x1080-0x10ff has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:00: ioport range 0x1400-0x147f has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:00: ioport range 0x1480-0x14ff has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:00: ioport range 0x1800-0x187f has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:00: ioport range 0x1880-0x18ff has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xd8800-0xdbfff has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xf0000-0xf7fff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xf8000-0xfbfff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xfc000-0xfffff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0x2fff0000-0x2fffffff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xffff0000-0xffffffff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0x0-0x9ffff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0x100000-0x2ffeffff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
May  5 07:40:59 user kernel: [    0.588283] system 00:03: ioport range 0x800-0x805 has been reserved
May  5 07:40:59 user kernel: [    0.624039] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:01
May  5 07:40:59 user kernel: [    0.624042] pci 0000:00:0a.0:   IO window: 0x9000-0xbfff
May  5 07:40:59 user kernel: [    0.624047] pci 0000:00:0a.0:   MEM window: 0xe2000000-0xe3ffffff
May  5 07:40:59 user kernel: [    0.624050] pci 0000:00:0a.0:   PREFETCH window: 0x00000040000000-0x000000400fffff
May  5 07:40:59 user kernel: [    0.624056] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
May  5 07:40:59 user kernel: [    0.624059] pci 0000:00:0b.0:   IO window: 0xc000-0xcfff
May  5 07:40:59 user kernel: [    0.624064] pci 0000:00:0b.0:   MEM window: 0xe0000000-0xe1ffffff
May  5 07:40:59 user kernel: [    0.624068] pci 0000:00:0b.0:   PREFETCH window: 0x000000d8000000-0x000000dfffffff
May  5 07:40:59 user kernel: [    0.624080] pci 0000:00:0a.0: setting latency timer to 64
May  5 07:40:59 user kernel: [    0.624087] bus: 00 index 0 io port: [0, ffff]
May  5 07:40:59 user kernel: [    0.624089] bus: 00 index 1 mmio: [0, ffffffffffffffff]
May  5 07:40:59 user kernel: [    0.624091] bus: 01 index 0 io port: [9000, bfff]
May  5 07:40:59 user kernel: [    0.624094] bus: 01 index 1 mmio: [e2000000, e3ffffff]
May  5 07:40:59 user kernel: [    0.624096] bus: 01 index 2 mmio: [40000000, 400fffff]
May  5 07:40:59 user kernel: [    0.624098] bus: 01 index 3 mmio: [0, 0]
May  5 07:40:59 user kernel: [    0.624100] bus: 02 index 0 io port: [c000, cfff]
May  5 07:40:59 user kernel: [    0.624102] bus: 02 index 1 mmio: [e0000000, e1ffffff]
May  5 07:40:59 user kernel: [    0.624105] bus: 02 index 2 mmio: [d8000000, dfffffff]
May  5 07:40:59 user kernel: [    0.624107] bus: 02 index 3 mmio: [0, 0]
May  5 07:40:59 user kernel: [    0.624119] NET: Registered protocol family 2
May  5 07:40:59 user kernel: [    0.624242] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May  5 07:40:59 user kernel: [    0.624564] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May  5 07:40:59 user kernel: [    0.625521] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May  5 07:40:59 user kernel: [    0.626040] TCP: Hash tables configured (established 131072 bind 65536)
May  5 07:40:59 user kernel: [    0.626044] TCP reno registered
May  5 07:40:59 user kernel: [    0.626150] NET: Registered protocol family 1
May  5 07:40:59 user kernel: [    0.626268] checking if image is initramfs... it is
May  5 07:40:59 user kernel: [    1.130030] Switched to high resolution mode on CPU 0
May  5 07:40:59 user kernel: [    1.270106] Freeing initrd memory: 7861k freed
May  5 07:40:59 user kernel: [    1.270859] audit: initializing netlink socket (disabled)
May  5 07:40:59 user kernel: [    1.270873] type=2000 audit(1241509236.270:1): initialized
May  5 07:40:59 user kernel: [    1.277046] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May  5 07:40:59 user kernel: [    1.279208] VFS: Disk quotas dquot_6.5.1
May  5 07:40:59 user kernel: [    1.279292] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  5 07:40:59 user kernel: [    1.279389] msgmni has been set to 1510
May  5 07:40:59 user kernel: [    1.279509] io scheduler noop registered
May  5 07:40:59 user kernel: [    1.279511] io scheduler anticipatory registered
May  5 07:40:59 user kernel: [    1.279514] io scheduler deadline registered (default)
May  5 07:40:59 user kernel: [    1.279525] io scheduler cfq registered
May  5 07:40:59 user kernel: [    1.320057] pci 0000:02:00.0: Boot video device
May  5 07:40:59 user kernel: [    1.320378] isapnp: Scanning for PnP cards...
May  5 07:40:59 user kernel: [    1.676735] isapnp: No Plug & Play device found
May  5 07:40:59 user kernel: [    1.712889] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
May  5 07:40:59 user kernel: [    1.713006] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  5 07:40:59 user kernel: [    1.713145] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  5 07:40:59 user kernel: [    1.713711] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  5 07:40:59 user kernel: [    1.713981] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  5 07:40:59 user kernel: [    1.714367] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
May  5 07:40:59 user kernel: [    1.714376] serial 0000:01:06.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
May  5 07:40:59 user kernel: [    1.717494] brd: module loaded
May  5 07:40:59 user kernel: [    1.717566] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May  5 07:40:59 user kernel: [    1.717682] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May  5 07:40:59 user kernel: [    1.717685] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May  5 07:40:59 user kernel: [    1.718259] serio: i8042 KBD port at 0x60,0x64 irq 1
May  5 07:40:59 user kernel: [    1.718714] mice: PS/2 mouse device common for all mice
May  5 07:40:59 user kernel: [    1.718846] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
May  5 07:40:59 user kernel: [    1.718869] rtc0: alarms up to one year, y3k
May  5 07:40:59 user kernel: [    1.718985] EISA: Probing bus 0 at eisa.0
May  5 07:40:59 user kernel: [    1.718993] Cannot allocate resource for EISA slot 1
May  5 07:40:59 user kernel: [    1.718996] Cannot allocate resource for EISA slot 2
May  5 07:40:59 user kernel: [    1.719011] EISA: Detected 0 cards.
May  5 07:40:59 user kernel: [    1.719015] cpuidle: using governor ladder
May  5 07:40:59 user kernel: [    1.719017] cpuidle: using governor menu
May  5 07:40:59 user kernel: [    1.719540] TCP cubic registered
May  5 07:40:59 user kernel: [    1.719566] Using IPI No-Shortcut mode
May  5 07:40:59 user kernel: [    1.719753] registered taskstats version 1
May  5 07:40:59 user kernel: [    1.719884]   Magic number: 9:241:672
May  5 07:40:59 user kernel: [    1.720092] rtc_cmos 00:05: setting system clock to 2009-05-05 07:40:37 UTC (1241509237)
May  5 07:40:59 user kernel: [    1.720096] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  5 07:40:59 user kernel: [    1.720098] EDD information not available.
May  5 07:40:59 user kernel: [    1.720424] Freeing unused kernel memory: 436k freed
May  5 07:40:59 user kernel: [    1.720543] Write protecting the kernel text: 2632k
May  5 07:40:59 user kernel: [    1.720590] Write protecting the kernel read-only data: 956k
May  5 07:40:59 user kernel: [    1.740827] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May  5 07:40:59 user kernel: [    1.850427] fuse init (API version 7.9)
May  5 07:40:59 user kernel: [    1.870946] ACPI: processor limited to max C-state 1
May  5 07:40:59 user kernel: [    1.871030] processor ACPI0007:00: registered as cooling_device0
May  5 07:40:59 user kernel: [    2.601656] usbcore: registered new interface driver usbfs
May  5 07:40:59 user kernel: [    2.601680] usbcore: registered new interface driver hub
May  5 07:40:59 user kernel: [    2.601717] usbcore: registered new device driver usb
May  5 07:40:59 user kernel: [    2.604469] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
May  5 07:40:59 user kernel: [    2.604479] ehci_hcd 0000:00:02.2: PCI INT C -> Link[APCL] -> GSI 22 (level, high) -> IRQ 22
May  5 07:40:59 user kernel: [    2.604492] ehci_hcd 0000:00:02.2: setting latency timer to 64
May  5 07:40:59 user kernel: [    2.604495] ehci_hcd 0000:00:02.2: EHCI Host Controller
May  5 07:40:59 user kernel: [    2.604543] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
May  5 07:40:59 user kernel: [    2.604570] ehci_hcd 0000:00:02.2: debug port 1
May  5 07:40:59 user kernel: [    2.604574] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
May  5 07:40:59 user kernel: [    2.604588] ehci_hcd 0000:00:02.2: irq 22, io mem 0xe4005000
May  5 07:40:59 user kernel: [    2.608456] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
May  5 07:40:59 user kernel: [    2.614237] No dock devices found.
May  5 07:40:59 user kernel: [    2.627729] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May  5 07:40:59 user kernel: [    2.627912] usb usb1: configuration #1 chosen from 1 choice
May  5 07:40:59 user kernel: [    2.627940] hub 1-0:1.0: USB hub found
May  5 07:40:59 user kernel: [    2.627953] hub 1-0:1.0: 6 ports detected
May  5 07:40:59 user kernel: [    2.666619] SCSI subsystem initialized
May  5 07:40:59 user kernel: [    2.717185] libata version 3.00 loaded.
May  5 07:40:59 user kernel: [    2.840739] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
May  5 07:40:59 user kernel: [    2.840749] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, high) -> IRQ 21
May  5 07:40:59 user kernel: [    2.840766] ohci_hcd 0000:00:02.0: setting latency timer to 64
May  5 07:40:59 user kernel: [    2.840769] ohci_hcd 0000:00:02.0: OHCI Host Controller
May  5 07:40:59 user kernel: [    2.840794] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
May  5 07:40:59 user kernel: [    2.840816] ohci_hcd 0000:00:02.0: irq 21, io mem 0xe4003000
May  5 07:40:59 user kernel: [    2.902258] usb usb2: configuration #1 chosen from 1 choice
May  5 07:40:59 user kernel: [    2.902288] hub 2-0:1.0: USB hub found
May  5 07:40:59 user kernel: [    2.902300] hub 2-0:1.0: 3 ports detected
May  5 07:40:59 user kernel: [    3.120634] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
May  5 07:40:59 user kernel: [    3.120644] ohci_hcd 0000:00:02.1: PCI INT B -> Link[APCG] -> GSI 20 (level, high) -> IRQ 20
May  5 07:40:59 user kernel: [    3.120661] ohci_hcd 0000:00:02.1: setting latency timer to 64
May  5 07:40:59 user kernel: [    3.120664] ohci_hcd 0000:00:02.1: OHCI Host Controller
May  5 07:40:59 user kernel: [    3.120689] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
May  5 07:40:59 user kernel: [    3.120712] ohci_hcd 0000:00:02.1: irq 20, io mem 0xe4004000
May  5 07:40:59 user kernel: [    3.182218] usb usb3: configuration #1 chosen from 1 choice
May  5 07:40:59 user kernel: [    3.182254] hub 3-0:1.0: USB hub found
May  5 07:40:59 user kernel: [    3.182266] hub 3-0:1.0: 3 ports detected
May  5 07:40:59 user kernel: [    3.290440] pata_acpi 0000:00:08.0: power state changed by ACPI to D0
May  5 07:40:59 user kernel: [    3.290491] pata_acpi 0000:00:08.0: setting latency timer to 64
May  5 07:40:59 user kernel: [    3.290965] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
May  5 07:40:59 user kernel: [    3.291145] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
May  5 07:40:59 user kernel: [    3.291154] r8169 0000:01:0b.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
May  5 07:40:59 user kernel: [    3.291452] eth1: RTL8169s at 0xf082a000, 00:0d:61:21:54:d2, XID 00800000 IRQ 19
May  5 07:40:59 user kernel: [    3.294794] VIA Networking Velocity Family Gigabit Ethernet Adapter Driver Ver. 1.14
May  5 07:40:59 user kernel: [    3.294797] Copyright (c) 2002, 2003 VIA Networking Technologies, Inc.
May  5 07:40:59 user kernel: [    3.294799] Copyright (c) 2004 Red Hat Inc.
May  5 07:40:59 user kernel: [    3.294952] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
May  5 07:40:59 user kernel: [    3.294957] via-velocity 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
May  5 07:40:59 user kernel: [    3.295625] eth0: VIA Networking Velocity Family Gigabit Ethernet Adapter
May  5 07:40:59 user kernel: [    3.295628] eth0: Ethernet Address: 00:A0:C5:30:02:07
May  5 07:40:59 user kernel: [    3.310368] sata_sil 0000:01:0d.0: version 2.3
May  5 07:40:59 user kernel: [    3.310412] sata_sil 0000:01:0d.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
May  5 07:40:59 user kernel: [    3.310432] sata_sil 0000:01:0d.0: Applying R_ERR on DMA activate FIS errata fix
May  5 07:40:59 user kernel: [    3.310512] scsi0 : sata_sil
May  5 07:40:59 user kernel: [    3.310610] scsi1 : sata_sil
May  5 07:40:59 user kernel: [    3.310644] ata1: SATA max UDMA/100 mmio m512@0xe3013000 tf 0xe3013080 irq 17
May  5 07:40:59 user kernel: [    3.310647] ata2: SATA max UDMA/100 mmio m512@0xe3013000 tf 0xe30130c0 irq 17
May  5 07:40:59 user kernel: [    3.320105] usb 2-1: new full speed USB device using ohci_hcd and address 2
May  5 07:40:59 user kernel: [    3.546248] usb 2-1: configuration #1 chosen from 1 choice
May  5 07:40:59 user kernel: [    3.660031] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
May  5 07:40:59 user kernel: [    3.680428] ata1.00: ATA-6: ST3120827AS, 3.42, max UDMA/133
May  5 07:40:59 user kernel: [    3.680431] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
May  5 07:40:59 user kernel: [    3.720397] ata1.00: configured for UDMA/100
May  5 07:40:59 user kernel: [    3.890012] usb 2-2: new full speed USB device using ohci_hcd and address 3
May  5 07:40:59 user kernel: [    4.070021] ata2: SATA link down (SStatus 0 SControl 310)
May  5 07:40:59 user kernel: [    4.070135] scsi 0:0:0:0: Direct-Access     ATA      ST3120827AS      3.42 PQ: 0 ANSI: 5
May  5 07:40:59 user kernel: [    4.073806] pata_amd 0000:00:08.0: version 0.3.10
May  5 07:40:59 user kernel: [    4.073892] pata_amd 0000:00:08.0: power state changed by ACPI to D0
May  5 07:40:59 user kernel: [    4.073938] pata_amd 0000:00:08.0: setting latency timer to 64
May  5 07:40:59 user kernel: [    4.074002] scsi2 : pata_amd
May  5 07:40:59 user kernel: [    4.074072] scsi3 : pata_amd
May  5 07:40:59 user kernel: [    4.074927] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
May  5 07:40:59 user kernel: [    4.074930] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
May  5 07:40:59 user kernel: [    4.084358] scsi 0:0:0:0: Attached scsi generic sg0 type 0
May  5 07:40:59 user kernel: [    4.096951] Driver 'sd' needs updating - please use bus_type methods
May  5 07:40:59 user kernel: [    4.097068] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
May  5 07:40:59 user kernel: [    4.097086] sd 0:0:0:0: [sda] Write Protect is off
May  5 07:40:59 user kernel: [    4.097089] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  5 07:40:59 user kernel: [    4.097116] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:40:59 user kernel: [    4.097180] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
May  5 07:40:59 user kernel: [    4.097195] sd 0:0:0:0: [sda] Write Protect is off
May  5 07:40:59 user kernel: [    4.097197] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  5 07:40:59 user kernel: [    4.097222] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:40:59 user kernel: [    4.097226]  sda: sda1 sda2 <<6>usb 2-2: configuration #1 chosen from 1 choice
May  5 07:40:59 user kernel: [    4.123339]  sda5 sda6 sda7 >
May  5 07:40:59 user kernel: [    4.145863] sd 0:0:0:0: [sda] Attached SCSI disk
May  5 07:40:59 user kernel: [    4.310433] ata3.00: ATA-6: ST380011A, 8.01, max UDMA/100
May  5 07:40:59 user kernel: [    4.310437] ata3.00: 156301488 sectors, multi 16: LBA48 
May  5 07:40:59 user kernel: [    4.310452] ata3: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc60000c0) ACPI=0x3f01f (20:600:0x13)
May  5 07:40:59 user kernel: [    4.350355] ata3.00: configured for UDMA/100
May  5 07:40:59 user kernel: [    4.450011] usb 2-3: new low speed USB device using ohci_hcd and address 4
May  5 07:40:59 user kernel: [    4.540297] ata4.01: ATAPI: _NEC DVD_RW ND-1300A, 1.08, max UDMA/33
May  5 07:40:59 user kernel: [    4.540310] ata4: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc60000c0) ACPI=0x701f (600:60:0x1c)
May  5 07:40:59 user kernel: [    4.580238] ata4.01: configured for UDMA/33
May  5 07:40:59 user kernel: [    4.580345] scsi 2:0:0:0: Direct-Access     ATA      ST380011A        8.01 PQ: 0 ANSI: 5
May  5 07:40:59 user kernel: [    4.580527] scsi 2:0:0:0: Attached scsi generic sg1 type 0
May  5 07:40:59 user kernel: [    4.583519] scsi 3:0:1:0: CD-ROM            _NEC     DVD_RW ND-1300A  1.08 PQ: 0 ANSI: 5
May  5 07:40:59 user kernel: [    4.583615] scsi 3:0:1:0: Attached scsi generic sg2 type 5
May  5 07:40:59 user kernel: [    4.584668] sd 2:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
May  5 07:40:59 user kernel: [    4.584807] sd 2:0:0:0: [sdb] Write Protect is off
May  5 07:40:59 user kernel: [    4.584810] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May  5 07:40:59 user kernel: [    4.584839] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:40:59 user kernel: [    4.584916] sd 2:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
May  5 07:40:59 user kernel: [    4.584930] sd 2:0:0:0: [sdb] Write Protect is off
May  5 07:40:59 user kernel: [    4.584933] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May  5 07:40:59 user kernel: [    4.584957] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 07:40:59 user kernel: [    4.584962]  sdb: sdb1 < sdb5<4>Driver 'sr' needs updating - please use bus_type methods
May  5 07:40:59 user kernel: [    4.616528]  sdb6 >
May  5 07:40:59 user kernel: [    4.616678] sd 2:0:0:0: [sdb] Attached SCSI disk
May  5 07:40:59 user kernel: [    4.630705] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
May  5 07:40:59 user kernel: [    4.630711] Uniform CD-ROM driver Revision: 3.20
May  5 07:40:59 user kernel: [    4.630818] sr 3:0:1:0: Attached scsi CD-ROM sr0
May  5 07:40:59 user kernel: [    4.686279] usb 2-3: configuration #1 chosen from 1 choice
May  5 07:40:59 user kernel: [    4.689778] usbcore: registered new interface driver hiddev
May  5 07:40:59 user kernel: [    4.696191] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.3/input/input2
May  5 07:40:59 user kernel: [    4.702897] input,hidraw0: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:02.0-2
May  5 07:40:59 user kernel: [    4.708407] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input3
May  5 07:40:59 user kernel: [    4.708727] input,hidraw1: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:02.0-3
May  5 07:40:59 user kernel: [    4.708748] usbcore: registered new interface driver usbhid
May  5 07:40:59 user kernel: [    4.708752] usbhid: v2.6:USB HID core driver
May  5 07:40:59 user kernel: [    5.093416] PM: Starting manual resume from disk
May  5 07:40:59 user kernel: [    5.093421] PM: Resume from partition 8:5
May  5 07:40:59 user kernel: [    5.093423] PM: Checking hibernation image.
May  5 07:40:59 user kernel: [    5.093587] PM: Resume from disk failed.
May  5 07:40:59 user kernel: [    5.157817] kjournald starting.  Commit interval 5 seconds
May  5 07:40:59 user kernel: [    5.157833] EXT3-fs: mounted filesystem with ordered data mode.
May  5 07:40:59 user kernel: [    8.220829] udevd version 124 started
May  5 07:40:59 user kernel: [    9.029189] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  5 07:40:59 user kernel: [    9.051929] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  5 07:40:59 user kernel: [    9.086174] Linux agpgart interface v0.103
May  5 07:40:59 user kernel: [    9.143279] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
May  5 07:40:59 user kernel: [    9.143311] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
May  5 07:40:59 user kernel: [    9.147249] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
May  5 07:40:59 user kernel: [    9.331787] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
May  5 07:40:59 user kernel: [    9.331807] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2000
May  5 07:40:59 user kernel: [    9.383350] input: PC Speaker as /devices/platform/pcspkr/input/input4
May  5 07:40:59 user kernel: [    9.477715] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input5
May  5 07:40:59 user kernel: [    9.510034] ACPI: Power Button (FF) [PWRF]
May  5 07:40:59 user kernel: [    9.510126] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
May  5 07:40:59 user kernel: [    9.535525] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
May  5 07:40:59 user kernel: [    9.535532] Intel ICH 0000:00:06.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, high) -> IRQ 22
May  5 07:40:59 user kernel: [    9.535555] Intel ICH 0000:00:06.0: setting latency timer to 64
May  5 07:40:59 user kernel: [    9.550035] ACPI: Power Button (CM) [PWRB]
May  5 07:40:59 user kernel: [    9.807796] ieee80211_crypt: registered algorithm 'NULL'
May  5 07:40:59 user kernel: [    9.822266] ieee80211: 802.11 data/management/control stack, git-1.1.13
May  5 07:40:59 user kernel: [    9.822271] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
May  5 07:40:59 user kernel: [    9.880039] intel8x0_measure_ac97_clock: measured 57828 usecs
May  5 07:40:59 user kernel: [    9.880043] intel8x0: clocking to 48000
May  5 07:40:59 user kernel: [    9.897410] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
May  5 07:40:59 user kernel: [    9.897414] ipw2200: Copyright(c) 2003-2006 Intel Corporation
May  5 07:40:59 user kernel: [    9.897511] ipw2200 0000:01:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
May  5 07:40:59 user kernel: [    9.897558] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
May  5 07:40:59 user kernel: [    9.897614] firmware: requesting ipw2200-bss.fw
May  5 07:40:59 user kernel: [   10.331980] parport_pc 00:0b: reported by Plug and Play ACPI
May  5 07:40:59 user kernel: [   10.332022] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
May  5 07:40:59 user kernel: [   11.986348] cdc_acm 2-1:1.0: ttyACM0: USB ACM device
May  5 07:40:59 user kernel: [   13.916024] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
May  5 07:40:59 user kernel: [   13.917216] udev: renamed network interface eth1 to eth0
May  5 07:40:59 user kernel: [   13.967450] udev: renamed network interface eth0_rename to eth1
May  5 07:40:59 user kernel: [   17.142675] usbcore: registered new interface driver cdc_acm
May  5 07:40:59 user kernel: [   17.142681] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
May  5 07:40:59 user kernel: [   17.147471] usbcore: registered new interface driver snd-usb-audio
May  5 07:40:59 user kernel: [   17.840833] loop: module loaded
May  5 07:40:59 user kernel: [   17.854783] lp0: using parport0 (interrupt-driven).
May  5 07:40:59 user kernel: [   18.356446] Adding 248936k swap on /dev/sdb5.  Priority:-1 extents:1 across:248936k
May  5 07:40:59 user kernel: [   18.740220] EXT3 FS on sdb6, internal journal
May  5 07:40:59 user kernel: [   19.903078] ip_tables: (C) 2000-2006 Netfilter Core Team
May  5 07:40:59 user kernel: [   19.954301] r8169: eth0: link up
May  5 07:40:59 user kernel: [   21.294121] NET: Registered protocol family 17
May  5 07:40:59 user kernel: [   21.444253] Velocity is AUTO mode
May  5 07:40:59 user kernel: [   21.878328] NET: Registered protocol family 10
May  5 07:40:59 user kernel: [   21.878844] lo: Disabled Privacy Extensions
May  5 07:41:02 user kernel: [   25.940152] warning: `dhcpd3' uses 32-bit capabilities (legacy support in use)
May  5 07:41:08 user kernel: [   32.160006] eth1: no IPv6 routers present
May  5 07:41:08 user kernel: [   32.730007] eth0: no IPv6 routers present
May  6 07:31:18 user kernel: Inspecting /boot/System.map-2.6.27-7-server
May  6 07:31:18 user kernel: Cannot find map file.
May  6 07:31:18 user kernel: Loaded 48877 symbols from 70 modules.
May  6 07:31:18 user kernel: [    0.000000] Initializing cgroup subsys cpuset
May  6 07:31:18 user kernel: [    0.000000] Initializing cgroup subsys cpu
May  6 07:31:18 user kernel: [    0.000000] Linux version 2.6.27-7-server (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 20:18:35 UTC 2008 (Ubuntu 2.6.27-7.16-server)
May  6 07:31:18 user kernel: [    0.000000] BIOS-provided physical RAM map:
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May  6 07:31:18 user kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
May  6 07:31:18 user kernel: [    0.000000] last_pfn = 0x2fff0 max_arch_pfn = 0x1000000
May  6 07:31:18 user kernel: [    0.000000] kernel direct mapping tables up to 2fff0000 @ 7000-d000
May  6 07:31:18 user kernel: [    0.000000] NX (Execute Disable) protection: active
May  6 07:31:18 user kernel: [    0.000000] RAMDISK: 2f832000 - 2ffdf6b8
May  6 07:31:18 user kernel: [    0.000000] DMI 2.3 present.
May  6 07:31:18 user kernel: [    0.000000] ACPI: RSDP 000F6AB0, 0014 (r0 Nvidia)
May  6 07:31:18 user kernel: [    0.000000] ACPI: RSDT 2FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  6 07:31:18 user kernel: [    0.000000] ACPI: FACP 2FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  6 07:31:18 user kernel: [    0.000000] ACPI: DSDT 2FFF30C0, 4ABF (r1 NVIDIA AWRDACPI     1000 MSFT  100000C)
May  6 07:31:18 user kernel: [    0.000000] ACPI: FACS 2FFF0000, 0040
May  6 07:31:18 user kernel: [    0.000000] ACPI: APIC 2FFF7B80, 005A (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
May  6 07:31:18 user kernel: [    0.000000] 0MB HIGHMEM available.
May  6 07:31:18 user kernel: [    0.000000] 767MB LOWMEM available.
May  6 07:31:18 user kernel: [    0.000000]   mapped low ram: 0 - 2fff0000
May  6 07:31:18 user kernel: [    0.000000]   low ram: 00000000 - 2fff0000
May  6 07:31:18 user kernel: [    0.000000]   bootmap 0000a000 - 00010000
May  6 07:31:18 user kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002fff0000]
May  6 07:31:18 user kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
May  6 07:31:18 user kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
May  6 07:31:18 user kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
May  6 07:31:18 user kernel: [    0.000000]   #3 [0000100000 - 00005e8220]    TEXT DATA BSS ==> [0000100000 - 00005e8220]
May  6 07:31:18 user kernel: [    0.000000]   #4 [002f832000 - 002ffdf6b8]          RAMDISK ==> [002f832000 - 002ffdf6b8]
May  6 07:31:18 user kernel: [    0.000000]   #5 [00005e9000 - 00005f1000]    INIT_PG_TABLE ==> [00005e9000 - 00005f1000]
May  6 07:31:18 user kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
May  6 07:31:18 user kernel: [    0.000000]   #7 [0000007000 - 000000a000]          PGTABLE ==> [0000007000 - 000000a000]
May  6 07:31:18 user kernel: [    0.000000]   #8 [000000a000 - 0000010000]          BOOTMAP ==> [000000a000 - 0000010000]
May  6 07:31:18 user kernel: [    0.000000] found SMP MP-table at [c00f5000] 000f5000
May  6 07:31:18 user kernel: [    0.000000] Zone PFN ranges:
May  6 07:31:18 user kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
May  6 07:31:18 user kernel: [    0.000000]   Normal   0x00001000 -> 0x0002fff0
May  6 07:31:18 user kernel: [    0.000000]   HighMem  0x0002fff0 -> 0x0002fff0
May  6 07:31:18 user kernel: [    0.000000] Movable zone start PFN for each node
May  6 07:31:18 user kernel: [    0.000000] early_node_map[2] active PFN ranges
May  6 07:31:18 user kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
May  6 07:31:18 user kernel: [    0.000000]     0: 0x00000100 -> 0x0002fff0
May  6 07:31:18 user kernel: [    0.000000] On node 0 totalpages: 196495
May  6 07:31:18 user kernel: [    0.000000] free_area_init_node: node 0, pgdat c049eb00, node_mem_map c1000000
May  6 07:31:18 user kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
May  6 07:31:18 user kernel: [    0.000000]   Normal zone: 190804 pages, LIFO batch:31
May  6 07:31:18 user kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
May  6 07:31:18 user kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
May  6 07:31:18 user kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
May  6 07:31:18 user kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  6 07:31:18 user kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  6 07:31:18 user kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
May  6 07:31:18 user kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  6 07:31:18 user kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
May  6 07:31:18 user kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  6 07:31:18 user kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
May  6 07:31:18 user kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  6 07:31:18 user kernel: [    0.000000] ACPI: IRQ9 used by override.
May  6 07:31:18 user kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  6 07:31:18 user kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  6 07:31:18 user kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
May  6 07:31:18 user kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
May  6 07:31:18 user kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
May  6 07:31:18 user kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May  6 07:31:18 user kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
May  6 07:31:18 user kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
May  6 07:31:18 user kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
May  6 07:31:18 user kernel: [    0.000000] PERCPU: Allocating 45852 bytes of per cpu data
May  6 07:31:18 user kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
May  6 07:31:18 user kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194767
May  6 07:31:18 user kernel: [    0.000000] Kernel command line: root=UUID=3a16f219-3073-4cf3-8fa0-646d16cda612 ro quiet splash 
May  6 07:31:18 user kernel: [    0.000000] Enabling fast FPU save and restore... done.
May  6 07:31:18 user kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May  6 07:31:18 user kernel: [    0.000000] Initializing CPU#0
May  6 07:31:18 user kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
May  6 07:31:18 user kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
May  6 07:31:18 user kernel: [    0.000000] TSC: using PIT calibration value
May  6 07:31:18 user kernel: [    0.000000] Detected 1994.814 MHz processor.
May  6 07:31:18 user kernel: [    0.010000] spurious 8259A interrupt: IRQ7.
May  6 07:31:18 user kernel: [    0.010000] Console: colour VGA+ 80x25
May  6 07:31:18 user kernel: [    0.010000] console [tty0] enabled
May  6 07:31:18 user kernel: [    0.010000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  6 07:31:18 user kernel: [    0.010000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  6 07:31:18 user kernel: [    0.010000] Memory: 765068k/786368k available (2628k kernel code, 20728k reserved, 1201k data, 436k init, 0k highmem)
May  6 07:31:18 user kernel: [    0.010000] virtual kernel memory layout:
May  6 07:31:18 user kernel: [    0.010000]     fixmap  : 0xffc78000 - 0xfffff000   (3612 kB)
May  6 07:31:18 user kernel: [    0.010000]     pkmap   : 0xff800000 - 0xffa00000   (2048 kB)
May  6 07:31:18 user kernel: [    0.010000]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
May  6 07:31:18 user kernel: [    0.010000]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
May  6 07:31:18 user kernel: [    0.010000]       .init : 0xc04c3000 - 0xc0530000   ( 436 kB)
May  6 07:31:18 user kernel: [    0.010000]       .data : 0xc0391036 - 0xc04bd800   (1201 kB)
May  6 07:31:18 user kernel: [    0.010000]       .text : 0xc0100000 - 0xc0391036   (2628 kB)
May  6 07:31:18 user kernel: [    0.010000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
May  6 07:31:18 user kernel: [    0.010000] CPA: page pool initialized 1 of 1 pages preallocated
May  6 07:31:18 user kernel: [    0.010000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
May  6 07:31:18 user kernel: [    0.010008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.62 BogoMIPS (lpj=19948140)
May  6 07:31:18 user kernel: [    0.010026] Security Framework initialized
May  6 07:31:18 user kernel: [    0.010033] SELinux:  Disabled at boot.
May  6 07:31:18 user kernel: [    0.010053] AppArmor: AppArmor initialized
May  6 07:31:18 user kernel: [    0.010061] Mount-cache hash table entries: 512
May  6 07:31:18 user kernel: [    0.010209] Initializing cgroup subsys ns
May  6 07:31:18 user kernel: [    0.010213] Initializing cgroup subsys cpuacct
May  6 07:31:18 user kernel: [    0.010215] Initializing cgroup subsys memory
May  6 07:31:18 user kernel: [    0.010229] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May  6 07:31:18 user kernel: [    0.010232] CPU: L2 Cache: 512K (64 bytes/line)
May  6 07:31:18 user kernel: [    0.010241] Checking 'hlt' instruction... OK.
May  6 07:31:18 user kernel: [    0.050367] SMP alternatives: switching to UP code
May  6 07:31:18 user kernel: [    0.056453] Freeing SMP alternatives: 11k freed
May  6 07:31:18 user kernel: [    0.056457] ACPI: Core revision 20080609
May  6 07:31:18 user kernel: [    0.057953] ACPI: Checking initramfs for custom DSDT
May  6 07:31:18 user kernel: [    0.371035] ENABLING IO-APIC IRQs
May  6 07:31:18 user kernel: [    0.371201] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
May  6 07:31:18 user kernel: [    0.471212] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 08
May  6 07:31:18 user kernel: [    0.480000] Brought up 1 CPUs
May  6 07:31:18 user kernel: [    0.480000] Total of 1 processors activated (3989.62 BogoMIPS).
May  6 07:31:18 user kernel: [    0.480000] CPU0 attaching sched-domain:
May  6 07:31:18 user kernel: [    0.480000]  domain 0: span 0 level CPU
May  6 07:31:18 user kernel: [    0.480000]   groups: 0
May  6 07:31:18 user kernel: [    0.480000] net_namespace: 840 bytes
May  6 07:31:18 user kernel: [    0.480000] Booting paravirtualized kernel on bare hardware
May  6 07:31:18 user kernel: [    0.480000] Time:  7:30:59  Date: 05/06/09
May  6 07:31:18 user kernel: [    0.480000] NET: Registered protocol family 16
May  6 07:31:18 user kernel: [    0.480000] EISA bus registered
May  6 07:31:18 user kernel: [    0.480000] ACPI: bus type pci registered
May  6 07:31:18 user kernel: [    0.500539] PCI: PCI BIOS revision 2.10 entry at 0xfac80, last bus=2
May  6 07:31:18 user kernel: [    0.500542] PCI: Using configuration type 1 for base access
May  6 07:31:18 user kernel: [    0.502219] ACPI: EC: Look up EC in DSDT
May  6 07:31:18 user kernel: [    0.509549] ACPI: Interpreter enabled
May  6 07:31:18 user kernel: [    0.509553] ACPI: (supports S0 S3 S4 S5)
May  6 07:31:18 user kernel: [    0.509567] ACPI: Using IOAPIC for interrupt routing
May  6 07:31:18 user kernel: [    0.520234] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  6 07:31:18 user kernel: [    0.520311] PCI: 0000:00:00.0 reg 10 32bit mmio: [d0000000, d7ffffff]
May  6 07:31:18 user kernel: [    0.520381] PCI: 0000:00:01.1 reg 20 io port: [1c00, 1c3f]
May  6 07:31:18 user kernel: [    0.520385] PCI: 0000:00:01.1 reg 24 io port: [2000, 203f]
May  6 07:31:18 user kernel: [    0.520395] pci 0000:00:01.1: PME# supported from D3hot D3cold
May  6 07:31:18 user kernel: [    0.520398] pci 0000:00:01.1: PME# disabled
May  6 07:31:18 user kernel: [    0.520416] PCI: 0000:00:02.0 reg 10 32bit mmio: [e4003000, e4003fff]
May  6 07:31:18 user kernel: [    0.520433] pci 0000:00:02.0: supports D1
May  6 07:31:18 user kernel: [    0.520435] pci 0000:00:02.0: supports D2
May  6 07:31:18 user kernel: [    0.520437] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520440] pci 0000:00:02.0: PME# disabled
May  6 07:31:18 user kernel: [    0.520454] PCI: 0000:00:02.1 reg 10 32bit mmio: [e4004000, e4004fff]
May  6 07:31:18 user kernel: [    0.520471] pci 0000:00:02.1: supports D1
May  6 07:31:18 user kernel: [    0.520473] pci 0000:00:02.1: supports D2
May  6 07:31:18 user kernel: [    0.520475] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520478] pci 0000:00:02.1: PME# disabled
May  6 07:31:18 user kernel: [    0.520496] PCI: 0000:00:02.2 reg 10 32bit mmio: [e4005000, e40050ff]
May  6 07:31:18 user kernel: [    0.520515] pci 0000:00:02.2: supports D1
May  6 07:31:18 user kernel: [    0.520517] pci 0000:00:02.2: supports D2
May  6 07:31:18 user kernel: [    0.520519] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520522] pci 0000:00:02.2: PME# disabled
May  6 07:31:18 user kernel: [    0.520543] PCI: 0000:00:06.0 reg 10 io port: [d400, d4ff]
May  6 07:31:18 user kernel: [    0.520547] PCI: 0000:00:06.0 reg 14 io port: [d800, d87f]
May  6 07:31:18 user kernel: [    0.520551] PCI: 0000:00:06.0 reg 18 32bit mmio: [e4001000, e4001fff]
May  6 07:31:18 user kernel: [    0.520565] pci 0000:00:06.0: supports D1
May  6 07:31:18 user kernel: [    0.520567] pci 0000:00:06.0: supports D2
May  6 07:31:18 user kernel: [    0.520586] PCI: 0000:00:08.0 reg 20 io port: [f000, f00f]
May  6 07:31:18 user kernel: [    0.520714] PCI: 0000:01:06.0 reg 10 io port: [9000, 903f]
May  6 07:31:18 user kernel: [    0.520742] pci 0000:01:06.0: supports D2
May  6 07:31:18 user kernel: [    0.520744] pci 0000:01:06.0: PME# supported from D0 D2 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520748] pci 0000:01:06.0: PME# disabled
May  6 07:31:18 user kernel: [    0.520769] PCI: 0000:01:07.0 reg 10 32bit mmio: [e3012000, e3012fff]
May  6 07:31:18 user kernel: [    0.520798] pci 0000:01:07.0: PME# supported from D0 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520802] pci 0000:01:07.0: PME# disabled
May  6 07:31:18 user kernel: [    0.520820] PCI: 0000:01:08.0 reg 10 32bit mmio: [e3000000, e300ffff]
May  6 07:31:18 user kernel: [    0.520826] PCI: 0000:01:08.0 reg 14 io port: [9400, 9407]
May  6 07:31:18 user kernel: [    0.520849] pci 0000:01:08.0: PME# supported from D3hot D3cold
May  6 07:31:18 user kernel: [    0.520852] pci 0000:01:08.0: PME# disabled
May  6 07:31:18 user kernel: [    0.520871] PCI: 0000:01:09.0 reg 10 io port: [9800, 98ff]
May  6 07:31:18 user kernel: [    0.520877] PCI: 0000:01:09.0 reg 14 32bit mmio: [e3010000, e30100ff]
May  6 07:31:18 user kernel: [    0.520901] pci 0000:01:09.0: supports D1
May  6 07:31:18 user kernel: [    0.520903] pci 0000:01:09.0: supports D2
May  6 07:31:18 user kernel: [    0.520905] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520908] pci 0000:01:09.0: PME# disabled
May  6 07:31:18 user kernel: [    0.520929] PCI: 0000:01:0b.0 reg 10 io port: [9c00, 9cff]
May  6 07:31:18 user kernel: [    0.520934] PCI: 0000:01:0b.0 reg 14 32bit mmio: [e3011000, e30110ff]
May  6 07:31:18 user kernel: [    0.520951] PCI: 0000:01:0b.0 reg 30 32bit mmio: [0, ffff]
May  6 07:31:18 user kernel: [    0.520961] pci 0000:01:0b.0: supports D1
May  6 07:31:18 user kernel: [    0.520963] pci 0000:01:0b.0: supports D2
May  6 07:31:18 user kernel: [    0.520965] pci 0000:01:0b.0: PME# supported from D1 D2 D3hot D3cold
May  6 07:31:18 user kernel: [    0.520968] pci 0000:01:0b.0: PME# disabled
May  6 07:31:18 user kernel: [    0.520989] PCI: 0000:01:0d.0 reg 10 io port: [a000, a007]
May  6 07:31:18 user kernel: [    0.520994] PCI: 0000:01:0d.0 reg 14 io port: [a400, a403]
May  6 07:31:18 user kernel: [    0.520999] PCI: 0000:01:0d.0 reg 18 io port: [a800, a807]
May  6 07:31:18 user kernel: [    0.521004] PCI: 0000:01:0d.0 reg 1c io port: [ac00, ac03]
May  6 07:31:18 user kernel: [    0.521009] PCI: 0000:01:0d.0 reg 20 io port: [b000, b00f]
May  6 07:31:18 user kernel: [    0.521015] PCI: 0000:01:0d.0 reg 24 32bit mmio: [e3013000, e30131ff]
May  6 07:31:18 user kernel: [    0.521020] PCI: 0000:01:0d.0 reg 30 32bit mmio: [0, 7ffff]
May  6 07:31:18 user kernel: [    0.521030] pci 0000:01:0d.0: supports D1
May  6 07:31:18 user kernel: [    0.521032] pci 0000:01:0d.0: supports D2
May  6 07:31:18 user kernel: [    0.521049] PCI: bridge 0000:00:0a.0 io port: [9000, bfff]
May  6 07:31:18 user kernel: [    0.521052] PCI: bridge 0000:00:0a.0 32bit mmio: [e2000000, e3ffffff]
May  6 07:31:18 user kernel: [    0.521086] PCI: 0000:02:00.0 reg 10 32bit mmio: [d8000000, dbffffff]
May  6 07:31:18 user kernel: [    0.521092] PCI: 0000:02:00.0 reg 14 io port: [c000, c0ff]
May  6 07:31:18 user kernel: [    0.521098] PCI: 0000:02:00.0 reg 18 32bit mmio: [e1000000, e100ffff]
May  6 07:31:18 user kernel: [    0.521115] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, 1ffff]
May  6 07:31:18 user kernel: [    0.521130] pci 0000:02:00.0: supports D1
May  6 07:31:18 user kernel: [    0.521132] pci 0000:02:00.0: supports D2
May  6 07:31:18 user kernel: [    0.521154] PCI: 0000:02:00.1 reg 10 32bit mmio: [dc000000, dfffffff]
May  6 07:31:18 user kernel: [    0.521160] PCI: 0000:02:00.1 reg 14 32bit mmio: [e1010000, e101ffff]
May  6 07:31:18 user kernel: [    0.521190] pci 0000:02:00.1: supports D1
May  6 07:31:18 user kernel: [    0.521192] pci 0000:02:00.1: supports D2
May  6 07:31:18 user kernel: [    0.521229] PCI: bridge 0000:00:0b.0 io port: [c000, cfff]
May  6 07:31:18 user kernel: [    0.521233] PCI: bridge 0000:00:0b.0 32bit mmio: [e0000000, e1ffffff]
May  6 07:31:18 user kernel: [    0.521237] PCI: bridge 0000:00:0b.0 32bit mmio pref: [d8000000, dfffffff]
May  6 07:31:18 user kernel: [    0.521245] bus 00 -> node 0
May  6 07:31:18 user kernel: [    0.521252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May  6 07:31:18 user kernel: [    0.521449] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
May  6 07:31:18 user kernel: [    0.521868] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
May  6 07:31:18 user kernel: [    0.575515] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May  6 07:31:18 user kernel: [    0.575698] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  6 07:31:18 user kernel: [    0.575878] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  6 07:31:18 user kernel: [    0.576057] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  6 07:31:18 user kernel: [    0.576237] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May  6 07:31:18 user kernel: [    0.576416] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  6 07:31:18 user kernel: [    0.576596] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  6 07:31:18 user kernel: [    0.576775] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.576959] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.577140] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  6 07:31:18 user kernel: [    0.577318] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.577499] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May  6 07:31:18 user kernel: [    0.577682] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May  6 07:31:18 user kernel: [    0.577862] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.578041] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.578220] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.578408] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May  6 07:31:18 user kernel: [    0.578556] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
May  6 07:31:18 user kernel: [    0.578697] ACPI: PCI Interrupt Link [APC2] (IRQs *17)
May  6 07:31:18 user kernel: [    0.578836] ACPI: PCI Interrupt Link [APC3] (IRQs *18)
May  6 07:31:18 user kernel: [    0.578975] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
May  6 07:31:18 user kernel: [    0.579114] ACPI: PCI Interrupt Link [APC5] (IRQs *16)
May  6 07:31:18 user kernel: [    0.579317] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
May  6 07:31:18 user kernel: [    0.579519] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
May  6 07:31:18 user kernel: [    0.579719] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.579920] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.580144] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
May  6 07:31:18 user kernel: [    0.580343] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.580484] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
May  6 07:31:18 user kernel: [    0.580682] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
May  6 07:31:18 user kernel: [    0.580882] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.581082] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.581282] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.581490] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22) *0, disabled.
May  6 07:31:18 user kernel: [    0.581631] ACPI: Power Resource [ISAV] (on)
May  6 07:31:18 user kernel: [    0.581715] Linux Plug and Play Support v0.97 (c) Adam Belay
May  6 07:31:18 user kernel: [    0.581750] pnp: PnP ACPI init
May  6 07:31:18 user kernel: [    0.581757] ACPI: bus type pnp registered
May  6 07:31:18 user kernel: [    0.587845] pnp: PnP ACPI: found 15 devices
May  6 07:31:18 user kernel: [    0.587847] ACPI: ACPI bus type pnp unregistered
May  6 07:31:18 user kernel: [    0.587851] PnPBIOS: Disabled by ACPI PNP
May  6 07:31:18 user kernel: [    0.588179] PCI: Using ACPI for IRQ routing
May  6 07:31:18 user kernel: [    0.588296] NET: Registered protocol family 8
May  6 07:31:18 user kernel: [    0.588296] NET: Registered protocol family 20
May  6 07:31:18 user kernel: [    0.588296] NetLabel: Initializing
May  6 07:31:18 user kernel: [    0.588296] NetLabel:  domain hash size = 128
May  6 07:31:18 user kernel: [    0.588296] NetLabel:  protocols = UNLABELED CIPSOv4
May  6 07:31:18 user kernel: [    0.588296] NetLabel:  unlabeled traffic allowed by default
May  6 07:31:18 user kernel: [    0.588296] tracer: 772 pages allocated for 65536 entries of 48 bytes
May  6 07:31:18 user kernel: [    0.588296]    actual entries 65620
May  6 07:31:18 user kernel: [    0.588296] AppArmor: AppArmor Filesystem Enabled
May  6 07:31:18 user kernel: [    0.588296] ACPI: RTC can wake from S4
May  6 07:31:18 user kernel: [    0.588296] system 00:00: ioport range 0x1000-0x107f has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:00: ioport range 0x1080-0x10ff has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:00: ioport range 0x1400-0x147f has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:00: ioport range 0x1480-0x14ff has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:00: ioport range 0x1800-0x187f has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:00: ioport range 0x1880-0x18ff has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xd8800-0xdbfff has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xf0000-0xf7fff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xf8000-0xfbfff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xfc000-0xfffff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0x2fff0000-0x2fffffff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xffff0000-0xffffffff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0x0-0x9ffff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0x100000-0x2ffeffff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
May  6 07:31:18 user kernel: [    0.588296] system 00:03: ioport range 0x800-0x805 has been reserved
May  6 07:31:18 user kernel: [    0.624054] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:01
May  6 07:31:18 user kernel: [    0.624057] pci 0000:00:0a.0:   IO window: 0x9000-0xbfff
May  6 07:31:18 user kernel: [    0.624061] pci 0000:00:0a.0:   MEM window: 0xe2000000-0xe3ffffff
May  6 07:31:18 user kernel: [    0.624065] pci 0000:00:0a.0:   PREFETCH window: 0x00000040000000-0x000000400fffff
May  6 07:31:18 user kernel: [    0.624071] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
May  6 07:31:18 user kernel: [    0.624074] pci 0000:00:0b.0:   IO window: 0xc000-0xcfff
May  6 07:31:18 user kernel: [    0.624078] pci 0000:00:0b.0:   MEM window: 0xe0000000-0xe1ffffff
May  6 07:31:18 user kernel: [    0.624083] pci 0000:00:0b.0:   PREFETCH window: 0x000000d8000000-0x000000dfffffff
May  6 07:31:18 user kernel: [    0.624094] pci 0000:00:0a.0: setting latency timer to 64
May  6 07:31:18 user kernel: [    0.624101] bus: 00 index 0 io port: [0, ffff]
May  6 07:31:18 user kernel: [    0.624103] bus: 00 index 1 mmio: [0, ffffffffffffffff]
May  6 07:31:18 user kernel: [    0.624105] bus: 01 index 0 io port: [9000, bfff]
May  6 07:31:18 user kernel: [    0.624108] bus: 01 index 1 mmio: [e2000000, e3ffffff]
May  6 07:31:18 user kernel: [    0.624110] bus: 01 index 2 mmio: [40000000, 400fffff]
May  6 07:31:18 user kernel: [    0.624112] bus: 01 index 3 mmio: [0, 0]
May  6 07:31:18 user kernel: [    0.624114] bus: 02 index 0 io port: [c000, cfff]
May  6 07:31:18 user kernel: [    0.624117] bus: 02 index 1 mmio: [e0000000, e1ffffff]
May  6 07:31:18 user kernel: [    0.624119] bus: 02 index 2 mmio: [d8000000, dfffffff]
May  6 07:31:18 user kernel: [    0.624121] bus: 02 index 3 mmio: [0, 0]
May  6 07:31:18 user kernel: [    0.624132] NET: Registered protocol family 2
May  6 07:31:18 user kernel: [    0.624256] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May  6 07:31:18 user kernel: [    0.624578] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May  6 07:31:18 user kernel: [    0.625534] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May  6 07:31:18 user kernel: [    0.626054] TCP: Hash tables configured (established 131072 bind 65536)
May  6 07:31:18 user kernel: [    0.626057] TCP reno registered
May  6 07:31:18 user kernel: [    0.626163] NET: Registered protocol family 1
May  6 07:31:18 user kernel: [    0.626282] checking if image is initramfs... it is
May  6 07:31:18 user kernel: [    1.130030] Switched to high resolution mode on CPU 0
May  6 07:31:18 user kernel: [    1.270119] Freeing initrd memory: 7861k freed
May  6 07:31:18 user kernel: [    1.270873] audit: initializing netlink socket (disabled)
May  6 07:31:18 user kernel: [    1.270888] type=2000 audit(1241595059.270:1): initialized
May  6 07:31:18 user kernel: [    1.277060] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May  6 07:31:18 user kernel: [    1.279222] VFS: Disk quotas dquot_6.5.1
May  6 07:31:18 user kernel: [    1.279307] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  6 07:31:18 user kernel: [    1.279403] msgmni has been set to 1510
May  6 07:31:18 user kernel: [    1.279523] io scheduler noop registered
May  6 07:31:18 user kernel: [    1.279526] io scheduler anticipatory registered
May  6 07:31:18 user kernel: [    1.279528] io scheduler deadline registered (default)
May  6 07:31:18 user kernel: [    1.279540] io scheduler cfq registered
May  6 07:31:18 user kernel: [    1.320057] pci 0000:02:00.0: Boot video device
May  6 07:31:18 user kernel: [    1.320378] isapnp: Scanning for PnP cards...
May  6 07:31:18 user kernel: [    1.676735] isapnp: No Plug & Play device found
May  6 07:31:18 user kernel: [    1.712895] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
May  6 07:31:18 user kernel: [    1.713012] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  6 07:31:18 user kernel: [    1.713152] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  6 07:31:18 user kernel: [    1.713719] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  6 07:31:18 user kernel: [    1.713991] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  6 07:31:18 user kernel: [    1.714376] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
May  6 07:31:18 user kernel: [    1.714385] serial 0000:01:06.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
May  6 07:31:18 user kernel: [    1.717513] brd: module loaded
May  6 07:31:18 user kernel: [    1.717585] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May  6 07:31:18 user kernel: [    1.717703] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May  6 07:31:18 user kernel: [    1.717706] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May  6 07:31:18 user kernel: [    1.718280] serio: i8042 KBD port at 0x60,0x64 irq 1
May  6 07:31:18 user kernel: [    1.718737] mice: PS/2 mouse device common for all mice
May  6 07:31:18 user kernel: [    1.718869] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
May  6 07:31:18 user kernel: [    1.718891] rtc0: alarms up to one year, y3k
May  6 07:31:18 user kernel: [    1.719007] EISA: Probing bus 0 at eisa.0
May  6 07:31:18 user kernel: [    1.719015] Cannot allocate resource for EISA slot 1
May  6 07:31:18 user kernel: [    1.719018] Cannot allocate resource for EISA slot 2
May  6 07:31:18 user kernel: [    1.719033] EISA: Detected 0 cards.
May  6 07:31:18 user kernel: [    1.719037] cpuidle: using governor ladder
May  6 07:31:18 user kernel: [    1.719039] cpuidle: using governor menu
May  6 07:31:18 user kernel: [    1.719559] TCP cubic registered
May  6 07:31:18 user kernel: [    1.719585] Using IPI No-Shortcut mode
May  6 07:31:18 user kernel: [    1.719774] registered taskstats version 1
May  6 07:31:18 user kernel: [    1.719906]   Magic number: 9:660:520
May  6 07:31:18 user kernel: [    1.720111] rtc_cmos 00:05: setting system clock to 2009-05-06 07:31:00 UTC (1241595060)
May  6 07:31:18 user kernel: [    1.720115] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  6 07:31:18 user kernel: [    1.720117] EDD information not available.
May  6 07:31:18 user kernel: [    1.720443] Freeing unused kernel memory: 436k freed
May  6 07:31:18 user kernel: [    1.720562] Write protecting the kernel text: 2632k
May  6 07:31:18 user kernel: [    1.720610] Write protecting the kernel read-only data: 956k
May  6 07:31:18 user kernel: [    1.741113] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May  6 07:31:18 user kernel: [    1.850418] fuse init (API version 7.9)
May  6 07:31:18 user kernel: [    1.870845] ACPI: processor limited to max C-state 1
May  6 07:31:18 user kernel: [    1.870928] processor ACPI0007:00: registered as cooling_device0
May  6 07:31:18 user kernel: [    2.581254] usbcore: registered new interface driver usbfs
May  6 07:31:18 user kernel: [    2.581279] usbcore: registered new interface driver hub
May  6 07:31:18 user kernel: [    2.581318] usbcore: registered new device driver usb
May  6 07:31:18 user kernel: [    2.592554] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
May  6 07:31:18 user kernel: [    2.592923] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
May  6 07:31:18 user kernel: [    2.592931] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 22 (level, high) -> IRQ 22
May  6 07:31:18 user kernel: [    2.592949] ohci_hcd 0000:00:02.0: setting latency timer to 64
May  6 07:31:18 user kernel: [    2.592952] ohci_hcd 0000:00:02.0: OHCI Host Controller
May  6 07:31:18 user kernel: [    2.593001] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
May  6 07:31:18 user kernel: [    2.593023] ohci_hcd 0000:00:02.0: irq 22, io mem 0xe4003000
May  6 07:31:18 user kernel: [    2.608325] No dock devices found.
May  6 07:31:18 user kernel: [    2.652216] usb usb1: configuration #1 chosen from 1 choice
May  6 07:31:18 user kernel: [    2.652247] hub 1-0:1.0: USB hub found
May  6 07:31:18 user kernel: [    2.652259] hub 1-0:1.0: 3 ports detected
May  6 07:31:18 user kernel: [    2.665817] SCSI subsystem initialized
May  6 07:31:18 user kernel: [    2.711621] libata version 3.00 loaded.
May  6 07:31:18 user kernel: [    2.870661] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
May  6 07:31:18 user kernel: [    2.870671] ohci_hcd 0000:00:02.1: PCI INT B -> Link[APCG] -> GSI 21 (level, high) -> IRQ 21
May  6 07:31:18 user kernel: [    2.870688] ohci_hcd 0000:00:02.1: setting latency timer to 64
May  6 07:31:18 user kernel: [    2.870691] ohci_hcd 0000:00:02.1: OHCI Host Controller
May  6 07:31:18 user kernel: [    2.870715] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
May  6 07:31:18 user kernel: [    2.870738] ohci_hcd 0000:00:02.1: irq 21, io mem 0xe4004000
May  6 07:31:18 user kernel: [    2.932222] usb usb2: configuration #1 chosen from 1 choice
May  6 07:31:18 user kernel: [    2.932252] hub 2-0:1.0: USB hub found
May  6 07:31:18 user kernel: [    2.932264] hub 2-0:1.0: 3 ports detected
May  6 07:31:18 user kernel: [    3.040719] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
May  6 07:31:18 user kernel: [    3.040729] ehci_hcd 0000:00:02.2: PCI INT C -> Link[APCL] -> GSI 20 (level, high) -> IRQ 20
May  6 07:31:18 user kernel: [    3.040745] ehci_hcd 0000:00:02.2: setting latency timer to 64
May  6 07:31:18 user kernel: [    3.040748] ehci_hcd 0000:00:02.2: EHCI Host Controller
May  6 07:31:18 user kernel: [    3.040774] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
May  6 07:31:18 user kernel: [    3.040800] ehci_hcd 0000:00:02.2: debug port 1
May  6 07:31:18 user kernel: [    3.040804] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
May  6 07:31:18 user kernel: [    3.040819] ehci_hcd 0000:00:02.2: irq 20, io mem 0xe4005000
May  6 07:31:18 user kernel: [    3.050039] usb 1-1: new full speed USB device using ohci_hcd and address 2
May  6 07:31:18 user kernel: [    3.070031] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May  6 07:31:18 user kernel: [    3.070209] usb usb3: configuration #1 chosen from 1 choice
May  6 07:31:18 user kernel: [    3.070240] hub 3-0:1.0: USB hub found
May  6 07:31:18 user kernel: [    3.070250] hub 3-0:1.0: 6 ports detected
May  6 07:31:18 user kernel: [    3.130048] hub 1-0:1.0: unable to enumerate USB device on port 1
May  6 07:31:18 user kernel: [    3.290405] pata_acpi 0000:00:08.0: power state changed by ACPI to D0
May  6 07:31:18 user kernel: [    3.290454] pata_acpi 0000:00:08.0: setting latency timer to 64
May  6 07:31:18 user kernel: [    3.294745] VIA Networking Velocity Family Gigabit Ethernet Adapter Driver Ver. 1.14
May  6 07:31:18 user kernel: [    3.294749] Copyright (c) 2002, 2003 VIA Networking Technologies, Inc.
May  6 07:31:18 user kernel: [    3.294752] Copyright (c) 2004 Red Hat Inc.
May  6 07:31:18 user kernel: [    3.294966] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
May  6 07:31:18 user kernel: [    3.294974] via-velocity 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
May  6 07:31:18 user kernel: [    3.296023] eth1: VIA Networking Velocity Family Gigabit Ethernet Adapter
May  6 07:31:18 user kernel: [    3.296026] eth1: Ethernet Address: 00:A0:C5:30:02:07
May  6 07:31:18 user kernel: [    3.296124] pata_amd 0000:00:08.0: version 0.3.10
May  6 07:31:18 user kernel: [    3.296176] pata_amd 0000:00:08.0: power state changed by ACPI to D0
May  6 07:31:18 user kernel: [    3.296217] pata_amd 0000:00:08.0: setting latency timer to 64
May  6 07:31:18 user kernel: [    3.296279] scsi0 : pata_amd
May  6 07:31:18 user kernel: [    3.296371] scsi1 : pata_amd
May  6 07:31:18 user kernel: [    3.297216] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
May  6 07:31:18 user kernel: [    3.297220] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
May  6 07:31:18 user kernel: [    3.310126] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
May  6 07:31:18 user kernel: [    3.310339] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
May  6 07:31:18 user kernel: [    3.310348] r8169 0000:01:0b.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
May  6 07:31:18 user kernel: [    3.310668] eth0: RTL8169s at 0xf0856000, 00:0d:61:21:54:d2, XID 00800000 IRQ 19
May  6 07:31:18 user kernel: [    3.314200] sata_sil 0000:01:0d.0: version 2.3
May  6 07:31:18 user kernel: [    3.314237] sata_sil 0000:01:0d.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
May  6 07:31:18 user kernel: [    3.314251] sata_sil 0000:01:0d.0: Applying R_ERR on DMA activate FIS errata fix
May  6 07:31:18 user kernel: [    3.314327] scsi2 : sata_sil
May  6 07:31:18 user kernel: [    3.314399] scsi3 : sata_sil
May  6 07:31:18 user kernel: [    3.314436] ata3: SATA max UDMA/100 mmio m512@0xe3013000 tf 0xe3013080 irq 17
May  6 07:31:18 user kernel: [    3.314440] ata4: SATA max UDMA/100 mmio m512@0xe3013000 tf 0xe30130c0 irq 17
May  6 07:31:18 user kernel: [    3.530451] ata1.00: ATA-6: ST380011A, 8.01, max UDMA/100
May  6 07:31:18 user kernel: [    3.530456] ata1.00: 156301488 sectors, multi 16: LBA48 
May  6 07:31:18 user kernel: [    3.530470] ata1: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc60000c0) ACPI=0x3f01f (20:600:0x13)
May  6 07:31:18 user kernel: [    3.570379] ata1.00: configured for UDMA/100
May  6 07:31:18 user kernel: [    3.660026] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
May  6 07:31:18 user kernel: [    3.680421] ata3.00: ATA-6: ST3120827AS, 3.42, max UDMA/133
May  6 07:31:18 user kernel: [    3.680424] ata3.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
May  6 07:31:18 user kernel: [    3.720423] ata3.00: configured for UDMA/100
May  6 07:31:18 user kernel: [    3.760290] ata2.01: ATAPI: _NEC DVD_RW ND-1300A, 1.08, max UDMA/33
May  6 07:31:18 user kernel: [    3.760303] ata2: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc60000c0) ACPI=0x701f (600:60:0x1c)
May  6 07:31:18 user kernel: [    3.800247] ata2.01: configured for UDMA/33
May  6 07:31:18 user kernel: [    3.800348] scsi 0:0:0:0: Direct-Access     ATA      ST380011A        8.01 PQ: 0 ANSI: 5
May  6 07:31:18 user kernel: [    3.803437] scsi 1:0:1:0: CD-ROM            _NEC     DVD_RW ND-1300A  1.08 PQ: 0 ANSI: 5
May  6 07:31:18 user kernel: [    4.070022] ata4: SATA link down (SStatus 0 SControl 310)
May  6 07:31:18 user kernel: [    4.070120] scsi 2:0:0:0: Direct-Access     ATA      ST3120827AS      3.42 PQ: 0 ANSI: 5
May  6 07:31:18 user kernel: [    4.079705] scsi 0:0:0:0: Attached scsi generic sg0 type 0
May  6 07:31:18 user kernel: [    4.079744] scsi 1:0:1:0: Attached scsi generic sg1 type 5
May  6 07:31:18 user kernel: [    4.079781] scsi 2:0:0:0: Attached scsi generic sg2 type 0
May  6 07:31:18 user kernel: [    4.108197] Driver 'sd' needs updating - please use bus_type methods
May  6 07:31:18 user kernel: [    4.108314] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
May  6 07:31:18 user kernel: [    4.108331] sd 0:0:0:0: [sda] Write Protect is off
May  6 07:31:18 user kernel: [    4.108334] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  6 07:31:18 user kernel: [    4.108361] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  6 07:31:18 user kernel: [    4.108426] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
May  6 07:31:18 user kernel: [    4.108441] sd 0:0:0:0: [sda] Write Protect is off
May  6 07:31:18 user kernel: [    4.108443] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  6 07:31:18 user kernel: [    4.108468] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  6 07:31:18 user kernel: [    4.108473]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
May  6 07:31:18 user kernel: [    4.126314]  sda1 < sda5 sda6 >
May  6 07:31:18 user kernel: [    4.134470] sd 0:0:0:0: [sda] Attached SCSI disk
May  6 07:31:18 user kernel: [    4.134559] sd 2:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
May  6 07:31:18 user kernel: [    4.134579] sd 2:0:0:0: [sdb] Write Protect is off
May  6 07:31:18 user kernel: [    4.134582] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May  6 07:31:18 user kernel: [    4.134612] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  6 07:31:18 user kernel: [    4.134676] sd 2:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
May  6 07:31:18 user kernel: [    4.134692] sd 2:0:0:0: [sdb] Write Protect is off
May  6 07:31:18 user kernel: [    4.134694] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May  6 07:31:18 user kernel: [    4.134722] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  6 07:31:18 user kernel: [    4.134727]  sdb:sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
May  6 07:31:18 user kernel: [    4.138985] Uniform CD-ROM driver Revision: 3.20
May  6 07:31:18 user kernel: [    4.139080] sr 1:0:1:0: Attached scsi CD-ROM sr0
May  6 07:31:18 user kernel: [    4.148666]  sdb1 sdb2 < sdb5 sdb6 sdb7 >
May  6 07:31:18 user kernel: [    4.181765] sd 2:0:0:0: [sdb] Attached SCSI disk
May  6 07:31:18 user kernel: [    4.260027] usb 1-1: new full speed USB device using ohci_hcd and address 3
May  6 07:31:18 user kernel: [    4.486225] usb 1-1: configuration #1 chosen from 1 choice
May  6 07:31:18 user kernel: [    4.656171] PM: Starting manual resume from disk
May  6 07:31:18 user kernel: [    4.656175] PM: Resume from partition 8:5
May  6 07:31:18 user kernel: [    4.656177] PM: Checking hibernation image.
May  6 07:31:18 user kernel: [    4.656357] PM: Resume from disk failed.
May  6 07:31:18 user kernel: [    4.700618] kjournald starting.  Commit interval 5 seconds
May  6 07:31:18 user kernel: [    4.700635] EXT3-fs: mounted filesystem with ordered data mode.
May  6 07:31:18 user kernel: [    4.830025] usb 1-2: new full speed USB device using ohci_hcd and address 4
May  6 07:31:18 user kernel: [    5.053142] usb 1-2: configuration #1 chosen from 1 choice
May  6 07:31:18 user kernel: [    5.390028] usb 1-3: new low speed USB device using ohci_hcd and address 5
May  6 07:31:18 user kernel: [    5.616253] usb 1-3: configuration #1 chosen from 1 choice
May  6 07:31:18 user kernel: [    7.239717] udevd version 124 started
May  6 07:31:18 user kernel: [    8.111333] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  6 07:31:18 user kernel: [    8.157204] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  6 07:31:18 user kernel: [    8.304915] Linux agpgart interface v0.103
May  6 07:31:18 user kernel: [    8.317468] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
May  6 07:31:18 user kernel: [    8.317486] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2000
May  6 07:31:18 user kernel: [    8.327395] input: PC Speaker as /devices/platform/pcspkr/input/input2
May  6 07:31:18 user kernel: [    8.335038] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
May  6 07:31:18 user kernel: [    8.335070] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
May  6 07:31:18 user kernel: [    8.338907] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
May  6 07:31:18 user kernel: [    8.438016] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
May  6 07:31:18 user kernel: [    8.438023] Intel ICH 0000:00:06.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, high) -> IRQ 22
May  6 07:31:18 user kernel: [    8.438045] Intel ICH 0000:00:06.0: setting latency timer to 64
May  6 07:31:18 user kernel: [    8.488493] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
May  6 07:31:18 user kernel: [    8.520047] ACPI: Power Button (FF) [PWRF]
May  6 07:31:18 user kernel: [    8.520139] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
May  6 07:31:18 user kernel: [    8.560041] ACPI: Power Button (CM) [PWRB]
May  6 07:31:18 user kernel: [    8.780029] intel8x0_measure_ac97_clock: measured 59805 usecs
May  6 07:31:18 user kernel: [    8.780033] intel8x0: clocking to 48000
May  6 07:31:18 user kernel: [    8.844067] ieee80211_crypt: registered algorithm 'NULL'
May  6 07:31:18 user kernel: [    8.855171] ieee80211: 802.11 data/management/control stack, git-1.1.13
May  6 07:31:18 user kernel: [    8.855176] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
May  6 07:31:18 user kernel: [    8.933048] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
May  6 07:31:18 user kernel: [    8.933052] ipw2200: Copyright(c) 2003-2006 Intel Corporation
May  6 07:31:18 user kernel: [    8.933150] ipw2200 0000:01:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
May  6 07:31:18 user kernel: [    8.933203] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
May  6 07:31:18 user kernel: [    8.933252] firmware: requesting ipw2200-bss.fw
May  6 07:31:18 user kernel: [    9.327847] parport_pc 00:0b: reported by Plug and Play ACPI
May  6 07:31:18 user kernel: [    9.327890] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
May  6 07:31:18 user kernel: [   11.000747] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
May  6 07:31:18 user kernel: [   11.007227] usbcore: registered new interface driver cdc_acm
May  6 07:31:18 user kernel: [   11.007233] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
May  6 07:31:18 user kernel: [   11.298526] usbcore: registered new interface driver snd-usb-audio
May  6 07:31:18 user kernel: [   11.298560] usbcore: registered new interface driver hiddev
May  6 07:31:18 user kernel: [   11.307296] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.3/input/input5
May  6 07:31:18 user kernel: [   11.370314] input,hidraw0: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:02.0-2
May  6 07:31:18 user kernel: [   11.376546] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.0/input/input6
May  6 07:31:18 user kernel: [   11.430213] input,hidraw1: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:02.0-3
May  6 07:31:18 user kernel: [   11.430238] usbcore: registered new interface driver usbhid
May  6 07:31:18 user kernel: [   11.430242] usbhid: v2.6:USB HID core driver
May  6 07:31:18 user kernel: [   12.797095] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
May  6 07:31:18 user kernel: [   13.857192] loop: module loaded
May  6 07:31:18 user kernel: [   13.871212] lp0: using parport0 (interrupt-driven).
May  6 07:31:18 user kernel: [   14.388910] Adding 248936k swap on /dev/sda5.  Priority:-1 extents:1 across:248936k
May  6 07:31:18 user kernel: [   14.739745] EXT3 FS on sda6, internal journal
May  6 07:31:18 user kernel: [   15.902949] ip_tables: (C) 2000-2006 Netfilter Core Team
May  6 07:31:18 user kernel: [   15.953923] r8169: eth0: link up
May  6 07:31:18 user kernel: [   17.294069] NET: Registered protocol family 17
May  6 07:31:18 user kernel: [   17.450890] Velocity is AUTO mode
May  6 07:31:18 user kernel: [   17.895533] NET: Registered protocol family 10
May  6 07:31:18 user kernel: [   17.896024] lo: Disabled Privacy Extensions
May  6 07:31:18 user kernel: [   17.896579] ADDRCONF(NETDEV_UP): eth1: link is not ready
May  6 07:31:18 user kernel: [   18.986603] eth1: Link auto-negotiation speed 100M bps full duplex
May  6 07:31:18 user kernel: [   18.988185] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
May  6 07:31:21 user kernel: [   21.857128] warning: `dhcpd3' uses 32-bit capabilities (legacy support in use)
May  6 07:31:27 user kernel: [   28.700006] eth0: no IPv6 routers present
May  6 07:31:29 user kernel: [   29.760012] eth1: no IPv6 routers present
May  6 07:31:46 user kernel: [   47.371589] usb 1-1: USB disconnect, address 3
May  6 07:31:50 user kernel: [   51.300012] usb 3-1: new high speed USB device using ehci_hcd and address 5
May  6 07:31:50 user kernel: [   51.452627] usb 3-1: configuration #1 chosen from 1 choice
May  6 07:31:50 user kernel: [   51.536840] usbcore: registered new interface driver libusual
May  6 07:31:50 user kernel: [   51.552255] Initializing USB Mass Storage driver...
May  6 07:31:50 user kernel: [   51.552359] scsi4 : SCSI emulation for USB Mass Storage devices
May  6 07:31:50 user kernel: [   51.552456] usbcore: registered new interface driver usb-storage
May  6 07:31:50 user kernel: [   51.552460] USB Mass Storage support registered.
May  6 07:31:50 user kernel: [   51.555777] usb-storage: device found at 5
May  6 07:31:50 user kernel: [   51.555782] usb-storage: waiting for device to settle before scanning
May  6 07:31:55 user kernel: [   56.550124] usb-storage: device scan complete
May  6 07:31:55 user kernel: [   56.551354] scsi 4:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  0.00 PQ: 0 ANSI: 2
May  6 07:31:55 user kernel: [   56.556767] sd 4:0:0:0: [sdc] 31588351 512-byte hardware sectors (16173 MB)
May  6 07:31:55 user kernel: [   56.557464] sd 4:0:0:0: [sdc] Write Protect is off
May  6 07:31:55 user kernel: [   56.557469] sd 4:0:0:0: [sdc] Mode Sense: 00 00 00 00
May  6 07:31:55 user kernel: [   56.557472] sd 4:0:0:0: [sdc] Assuming drive cache: write through
May  6 07:31:55 user kernel: [   56.560343] sd 4:0:0:0: [sdc] 31588351 512-byte hardware sectors (16173 MB)
May  6 07:31:55 user kernel: [   56.561091] sd 4:0:0:0: [sdc] Write Protect is off
May  6 07:31:55 user kernel: [   56.561096] sd 4:0:0:0: [sdc] Mode Sense: 00 00 00 00
May  6 07:31:55 user kernel: [   56.561098] sd 4:0:0:0: [sdc] Assuming drive cache: write through
May  6 07:31:55 user kernel: [   56.561154]  sdc: sdc1
May  6 07:31:55 user kernel: [   56.624236] sd 4:0:0:0: [sdc] Attached SCSI removable disk
May  6 07:31:55 user kernel: [   56.624365] sd 4:0:0:0: Attached scsi generic sg3 type 0
May  6 07:39:16 user kernel: [  497.706084] eth1: failed to detect cable link
May  6 07:39:20 user kernel: [  501.233869] eth1: Link auto-negotiation speed 100M bps full duplex

```

---

### Post by Romala on 2009-05-06
*dpkg.log*

```
2009-02-24 13:24:32 startup archives install
2009-02-24 13:24:32 install base-files <none> 4.0.4ubuntu2
2009-02-24 13:24:32 status half-installed base-files 4.0.4ubuntu2
2009-02-24 13:24:32 status unpacked base-files 4.0.4ubuntu2
2009-02-24 13:24:32 status unpacked base-files 4.0.4ubuntu2
2009-02-24 13:24:32 install base-passwd <none> 3.5.18
2009-02-24 13:24:32 status half-installed base-passwd 3.5.18
2009-02-24 13:24:33 status unpacked base-passwd 3.5.18
2009-02-24 13:24:33 status unpacked base-passwd 3.5.18
2009-02-24 13:24:33 configure base-passwd 3.5.18 3.5.18
2009-02-24 13:24:33 status unpacked base-passwd 3.5.18
2009-02-24 13:24:33 status half-configured base-passwd 3.5.18
2009-02-24 13:24:33 status installed base-passwd 3.5.18
2009-02-24 13:24:33 configure base-files 4.0.4ubuntu2 4.0.4ubuntu2
2009-02-24 13:24:33 status unpacked base-files 4.0.4ubuntu2
2009-02-24 13:24:33 status unpacked base-files 4.0.4ubuntu2
2009-02-24 13:24:33 status unpacked base-files 4.0.4ubuntu2
2009-02-24 13:24:33 status unpacked base-files 4.0.4ubuntu2
2009-02-24 13:24:33 status unpacked base-files 4.0.4ubuntu2
2009-02-24 13:24:33 status unpacked base-files 4.0.4ubuntu2
2009-02-24 13:24:33 status half-configured base-files 4.0.4ubuntu2
2009-02-24 13:24:33 status installed base-files 4.0.4ubuntu2
2009-02-24 13:24:33 startup archives install
2009-02-24 13:24:33 upgrade dpkg 1.14.20ubuntu6 1.14.20ubuntu6
2009-02-24 13:24:33 status half-configured dpkg 1.14.20ubuntu6
2009-02-24 13:24:33 status unpacked dpkg 1.14.20ubuntu6
2009-02-24 13:24:33 status half-installed dpkg 1.14.20ubuntu6
2009-02-24 13:24:33 status half-installed dpkg 1.14.20ubuntu6
2009-02-24 13:24:34 status unpacked dpkg 1.14.20ubuntu6
2009-02-24 13:24:34 status unpacked dpkg 1.14.20ubuntu6
2009-02-24 13:24:34 configure dpkg 1.14.20ubuntu6 1.14.20ubuntu6
2009-02-24 13:24:34 status unpacked dpkg 1.14.20ubuntu6
2009-02-24 13:24:34 status unpacked dpkg 1.14.20ubuntu6
2009-02-24 13:24:34 status unpacked dpkg 1.14.20ubuntu6
2009-02-24 13:24:34 status unpacked dpkg 1.14.20ubuntu6
2009-02-24 13:24:34 status unpacked dpkg 1.14.20ubuntu6
2009-02-24 13:24:34 status half-configured dpkg 1.14.20ubuntu6
2009-02-24 13:24:34 status installed dpkg 1.14.20ubuntu6
2009-02-24 13:24:34 startup archives install
2009-02-24 13:24:34 install libc6 <none> 2.8~20080505-0ubuntu7
2009-02-24 13:24:34 status half-installed libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:35 status unpacked libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:35 status unpacked libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:35 configure libc6 2.8~20080505-0ubuntu7 2.8~20080505-0ubuntu7
2009-02-24 13:24:35 status unpacked libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:36 status unpacked libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:36 status unpacked libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:36 status unpacked libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:36 status unpacked libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:36 status unpacked libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:36 status half-configured libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:36 status installed libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:36 status triggers-pending libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:36 trigproc libc6 2.8~20080505-0ubuntu7 2.8~20080505-0ubuntu7
2009-02-24 13:24:36 status half-configured libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:36 status installed libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:36 startup archives install
2009-02-24 13:24:36 install perl-base <none> 5.10.0-11.1ubuntu2
2009-02-24 13:24:36 status half-installed perl-base 5.10.0-11.1ubuntu2
2009-02-24 13:24:36 status unpacked perl-base 5.10.0-11.1ubuntu2
2009-02-24 13:24:36 status unpacked perl-base 5.10.0-11.1ubuntu2
2009-02-24 13:24:36 configure perl-base 5.10.0-11.1ubuntu2 5.10.0-11.1ubuntu2
2009-02-24 13:24:36 status unpacked perl-base 5.10.0-11.1ubuntu2
2009-02-24 13:24:36 status half-configured perl-base 5.10.0-11.1ubuntu2
2009-02-24 13:24:36 status installed perl-base 5.10.0-11.1ubuntu2
2009-02-24 13:24:36 startup archives install
2009-02-24 13:24:36 install mawk <none> 1.3.3-11.1ubuntu1
2009-02-24 13:24:36 status half-installed mawk 1.3.3-11.1ubuntu1
2009-02-24 13:24:36 status unpacked mawk 1.3.3-11.1ubuntu1
2009-02-24 13:24:36 status unpacked mawk 1.3.3-11.1ubuntu1
2009-02-24 13:24:36 configure mawk 1.3.3-11.1ubuntu1 1.3.3-11.1ubuntu1
2009-02-24 13:24:36 status unpacked mawk 1.3.3-11.1ubuntu1
2009-02-24 13:24:36 status half-configured mawk 1.3.3-11.1ubuntu1
2009-02-24 13:24:36 status installed mawk 1.3.3-11.1ubuntu1
2009-02-24 13:24:36 startup archives install
2009-02-24 13:24:36 install debconf <none> 1.5.23ubuntu2
2009-02-24 13:24:36 status half-installed debconf 1.5.23ubuntu2
2009-02-24 13:24:37 status unpacked debconf 1.5.23ubuntu2
2009-02-24 13:24:37 status unpacked debconf 1.5.23ubuntu2
2009-02-24 13:24:37 configure debconf 1.5.23ubuntu2 1.5.23ubuntu2
2009-02-24 13:24:37 status unpacked debconf 1.5.23ubuntu2
2009-02-24 13:24:37 status unpacked debconf 1.5.23ubuntu2
2009-02-24 13:24:37 status unpacked debconf 1.5.23ubuntu2
2009-02-24 13:24:37 status unpacked debconf 1.5.23ubuntu2
2009-02-24 13:24:37 status half-configured debconf 1.5.23ubuntu2
2009-02-24 13:24:37 status installed debconf 1.5.23ubuntu2
2009-02-24 13:24:37 startup archives unpack
2009-02-24 13:24:37 install libacl1 <none> 2.2.47-2
2009-02-24 13:24:37 status half-installed libacl1 2.2.47-2
2009-02-24 13:24:37 status unpacked libacl1 2.2.47-2
2009-02-24 13:24:37 status unpacked libacl1 2.2.47-2
2009-02-24 13:24:37 install libattr1 <none> 1:2.4.41-1
2009-02-24 13:24:37 status half-installed libattr1 1:2.4.41-1
2009-02-24 13:24:37 status unpacked libattr1 1:2.4.41-1
2009-02-24 13:24:37 status unpacked libattr1 1:2.4.41-1
2009-02-24 13:24:37 upgrade base-files 4.0.4ubuntu2 4.0.4ubuntu2
2009-02-24 13:24:37 status half-configured base-files 4.0.4ubuntu2
2009-02-24 13:24:37 status unpacked base-files 4.0.4ubuntu2
2009-02-24 13:24:37 status half-installed base-files 4.0.4ubuntu2
2009-02-24 13:24:38 status half-installed base-files 4.0.4ubuntu2
2009-02-24 13:24:38 status unpacked base-files 4.0.4ubuntu2
2009-02-24 13:24:38 status unpacked base-files 4.0.4ubuntu2
2009-02-24 13:24:38 upgrade base-passwd 3.5.18 3.5.18
2009-02-24 13:24:38 status half-configured base-passwd 3.5.18
2009-02-24 13:24:38 status unpacked base-passwd 3.5.18
2009-02-24 13:24:38 status half-installed base-passwd 3.5.18
2009-02-24 13:24:38 status half-installed base-passwd 3.5.18
2009-02-24 13:24:38 status unpacked base-passwd 3.5.18
2009-02-24 13:24:38 status unpacked base-passwd 3.5.18
2009-02-24 13:24:38 install bash <none> 3.2-4ubuntu1
2009-02-24 13:24:38 status half-installed bash 3.2-4ubuntu1
2009-02-24 13:24:38 status unpacked bash 3.2-4ubuntu1
2009-02-24 13:24:38 status unpacked bash 3.2-4ubuntu1
2009-02-24 13:24:38 install belocs-locales-bin <none> 2.4-2.3ubuntu1
2009-02-24 13:24:38 status half-installed belocs-locales-bin 2.4-2.3ubuntu1
2009-02-24 13:24:38 status unpacked belocs-locales-bin 2.4-2.3ubuntu1
2009-02-24 13:24:38 status unpacked belocs-locales-bin 2.4-2.3ubuntu1
2009-02-24 13:24:38 install coreutils <none> 6.10-6ubuntu1
2009-02-24 13:24:38 status half-installed coreutils 6.10-6ubuntu1
2009-02-24 13:24:38 status unpacked coreutils 6.10-6ubuntu1
2009-02-24 13:24:39 status unpacked coreutils 6.10-6ubuntu1
2009-02-24 13:24:39 install dash <none> 0.5.4-9ubuntu1
2009-02-24 13:24:39 status half-installed dash 0.5.4-9ubuntu1
2009-02-24 13:24:39 status unpacked dash 0.5.4-9ubuntu1
2009-02-24 13:24:39 status unpacked dash 0.5.4-9ubuntu1
2009-02-24 13:24:39 install libdb4.7 <none> 4.7.25-3
2009-02-24 13:24:39 status half-installed libdb4.7 4.7.25-3
2009-02-24 13:24:39 status unpacked libdb4.7 4.7.25-3
2009-02-24 13:24:39 status unpacked libdb4.7 4.7.25-3
2009-02-24 13:24:39 install debconf-i18n <none> 1.5.23ubuntu2
2009-02-24 13:24:39 status half-installed debconf-i18n 1.5.23ubuntu2
2009-02-24 13:24:39 status unpacked debconf-i18n 1.5.23ubuntu2
2009-02-24 13:24:39 status unpacked debconf-i18n 1.5.23ubuntu2
2009-02-24 13:24:39 upgrade debconf 1.5.23ubuntu2 1.5.23ubuntu2
2009-02-24 13:24:39 status half-configured debconf 1.5.23ubuntu2
2009-02-24 13:24:39 status unpacked debconf 1.5.23ubuntu2
2009-02-24 13:24:39 status half-installed debconf 1.5.23ubuntu2
2009-02-24 13:24:39 status half-installed debconf 1.5.23ubuntu2
2009-02-24 13:24:39 status unpacked debconf 1.5.23ubuntu2
2009-02-24 13:24:39 status unpacked debconf 1.5.23ubuntu2
2009-02-24 13:24:39 install debianutils <none> 2.29ubuntu2
2009-02-24 13:24:39 status half-installed debianutils 2.29ubuntu2
2009-02-24 13:24:39 status unpacked debianutils 2.29ubuntu2
2009-02-24 13:24:39 status unpacked debianutils 2.29ubuntu2
2009-02-24 13:24:39 install diff <none> 2.8.1-12ubuntu1
2009-02-24 13:24:39 status half-installed diff 2.8.1-12ubuntu1
2009-02-24 13:24:39 status unpacked diff 2.8.1-12ubuntu1
2009-02-24 13:24:39 status unpacked diff 2.8.1-12ubuntu1
2009-02-24 13:24:39 upgrade dpkg 1.14.20ubuntu6 1.14.20ubuntu6
2009-02-24 13:24:39 status half-configured dpkg 1.14.20ubuntu6
2009-02-24 13:24:39 status unpacked dpkg 1.14.20ubuntu6
2009-02-24 13:24:39 status half-installed dpkg 1.14.20ubuntu6
2009-02-24 13:24:39 status half-installed dpkg 1.14.20ubuntu6
2009-02-24 13:24:40 status unpacked dpkg 1.14.20ubuntu6
2009-02-24 13:24:40 status unpacked dpkg 1.14.20ubuntu6
2009-02-24 13:24:40 install e2fslibs <none> 1.41.3-1ubuntu1
2009-02-24 13:24:40 status half-installed e2fslibs 1.41.3-1ubuntu1
2009-02-24 13:24:40 status unpacked e2fslibs 1.41.3-1ubuntu1
2009-02-24 13:24:40 status unpacked e2fslibs 1.41.3-1ubuntu1
2009-02-24 13:24:40 install e2fsprogs <none> 1.41.3-1ubuntu1
2009-02-24 13:24:40 status half-installed e2fsprogs 1.41.3-1ubuntu1
2009-02-24 13:24:40 status unpacked e2fsprogs 1.41.3-1ubuntu1
2009-02-24 13:24:40 status unpacked e2fsprogs 1.41.3-1ubuntu1
2009-02-24 13:24:40 install libblkid1 <none> 1.41.3-1ubuntu1
2009-02-24 13:24:40 status half-installed libblkid1 1.41.3-1ubuntu1
2009-02-24 13:24:40 status unpacked libblkid1 1.41.3-1ubuntu1
2009-02-24 13:24:40 status unpacked libblkid1 1.41.3-1ubuntu1
2009-02-24 13:24:40 install libcomerr2 <none> 1.41.3-1ubuntu1
2009-02-24 13:24:40 status half-installed libcomerr2 1.41.3-1ubuntu1
2009-02-24 13:24:40 status unpacked libcomerr2 1.41.3-1ubuntu1
2009-02-24 13:24:40 status unpacked libcomerr2 1.41.3-1ubuntu1
2009-02-24 13:24:40 install libss2 <none> 1.41.3-1ubuntu1
2009-02-24 13:24:40 status half-installed libss2 1.41.3-1ubuntu1
2009-02-24 13:24:40 status unpacked libss2 1.41.3-1ubuntu1
2009-02-24 13:24:40 status unpacked libss2 1.41.3-1ubuntu1
2009-02-24 13:24:40 install libuuid1 <none> 1.41.3-1ubuntu1
2009-02-24 13:24:40 status half-installed libuuid1 1.41.3-1ubuntu1
2009-02-24 13:24:40 status unpacked libuuid1 1.41.3-1ubuntu1
2009-02-24 13:24:40 status unpacked libuuid1 1.41.3-1ubuntu1
2009-02-24 13:24:40 install findutils <none> 4.4.0-2ubuntu3
2009-02-24 13:24:40 status half-installed findutils 4.4.0-2ubuntu3
2009-02-24 13:24:40 status unpacked findutils 4.4.0-2ubuntu3
2009-02-24 13:24:40 status unpacked findutils 4.4.0-2ubuntu3
2009-02-24 13:24:40 install gcc-4.3-base <none> 4.3.2-1ubuntu11
2009-02-24 13:24:40 status half-installed gcc-4.3-base 4.3.2-1ubuntu11
2009-02-24 13:24:40 status unpacked gcc-4.3-base 4.3.2-1ubuntu11
2009-02-24 13:24:40 status unpacked gcc-4.3-base 4.3.2-1ubuntu11
2009-02-24 13:24:40 install libgcc1 <none> 1:4.3.2-1ubuntu11
2009-02-24 13:24:40 status half-installed libgcc1 1:4.3.2-1ubuntu11
2009-02-24 13:24:40 status unpacked libgcc1 1:4.3.2-1ubuntu11
2009-02-24 13:24:40 status unpacked libgcc1 1:4.3.2-1ubuntu11
2009-02-24 13:24:40 install libstdc++6 <none> 4.3.2-1ubuntu11
2009-02-24 13:24:40 status half-installed libstdc++6 4.3.2-1ubuntu11
2009-02-24 13:24:40 status unpacked libstdc++6 4.3.2-1ubuntu11
2009-02-24 13:24:40 status unpacked libstdc++6 4.3.2-1ubuntu11
2009-02-24 13:24:40 upgrade libc6 2.8~20080505-0ubuntu7 2.8~20080505-0ubuntu7
2009-02-24 13:24:40 status half-configured libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:40 status unpacked libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:40 status half-installed libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:41 status half-installed libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:41 status unpacked libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:41 status unpacked libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:42 install grep <none> 2.5.3~dfsg-5ubuntu2
2009-02-24 13:24:42 status half-installed grep 2.5.3~dfsg-5ubuntu2
2009-02-24 13:24:42 status unpacked grep 2.5.3~dfsg-5ubuntu2
2009-02-24 13:24:42 status unpacked grep 2.5.3~dfsg-5ubuntu2
2009-02-24 13:24:42 install gzip <none> 1.3.12-6ubuntu2
2009-02-24 13:24:42 status half-installed gzip 1.3.12-6ubuntu2
2009-02-24 13:24:42 status unpacked gzip 1.3.12-6ubuntu2
2009-02-24 13:24:42 status unpacked gzip 1.3.12-6ubuntu2
2009-02-24 13:24:42 install hostname <none> 2.95
2009-02-24 13:24:42 status half-installed hostname 2.95
2009-02-24 13:24:42 status unpacked hostname 2.95
2009-02-24 13:24:42 status unpacked hostname 2.95
2009-02-24 13:24:42 install locales <none> 2.7.9-5
2009-02-24 13:24:42 status half-installed locales 2.7.9-5
2009-02-24 13:24:42 status unpacked locales 2.7.9-5
2009-02-24 13:24:42 status unpacked locales 2.7.9-5
2009-02-24 13:24:42 install liblocale-gettext-perl <none> 1.05-4build1
2009-02-24 13:24:42 status half-installed liblocale-gettext-perl 1.05-4build1
2009-02-24 13:24:42 status unpacked liblocale-gettext-perl 1.05-4build1
2009-02-24 13:24:42 status unpacked liblocale-gettext-perl 1.05-4build1
2009-02-24 13:24:42 install libselinux1 <none> 2.0.65-2
2009-02-24 13:24:42 status half-installed libselinux1 2.0.65-2
2009-02-24 13:24:42 status unpacked libselinux1 2.0.65-2
2009-02-24 13:24:42 status unpacked libselinux1 2.0.65-2
2009-02-24 13:24:42 install libsepol1 <none> 2.0.30-2
2009-02-24 13:24:42 status half-installed libsepol1 2.0.30-2
2009-02-24 13:24:43 status unpacked libsepol1 2.0.30-2
2009-02-24 13:24:43 status unpacked libsepol1 2.0.30-2
2009-02-24 13:24:43 install libtext-charwidth-perl <none> 0.04-5build1
2009-02-24 13:24:43 status half-installed libtext-charwidth-perl 0.04-5build1
2009-02-24 13:24:43 status unpacked libtext-charwidth-perl 0.04-5build1
2009-02-24 13:24:43 status unpacked libtext-charwidth-perl 0.04-5build1
2009-02-24 13:24:43 install libtext-iconv-perl <none> 1.7-1build1
2009-02-24 13:24:43 status half-installed libtext-iconv-perl 1.7-1build1
2009-02-24 13:24:43 status unpacked libtext-iconv-perl 1.7-1build1
2009-02-24 13:24:43 status unpacked libtext-iconv-perl 1.7-1build1
2009-02-24 13:24:43 install libtext-wrapi18n-perl <none> 0.06-6
2009-02-24 13:24:43 status half-installed libtext-wrapi18n-perl 0.06-6
2009-02-24 13:24:43 status unpacked libtext-wrapi18n-perl 0.06-6
2009-02-24 13:24:43 status unpacked libtext-wrapi18n-perl 0.06-6
2009-02-24 13:24:43 install libncurses5 <none> 5.6+20071124-1ubuntu2
2009-02-24 13:24:43 status half-installed libncurses5 5.6+20071124-1ubuntu2
2009-02-24 13:24:43 status unpacked libncurses5 5.6+20071124-1ubuntu2
2009-02-24 13:24:43 status unpacked libncurses5 5.6+20071124-1ubuntu2
2009-02-24 13:24:43 install libpam-modules <none> 1.0.1-4ubuntu5
2009-02-24 13:24:43 status half-installed libpam-modules 1.0.1-4ubuntu5
2009-02-24 13:24:43 status unpacked libpam-modules 1.0.1-4ubuntu5
2009-02-24 13:24:43 status unpacked libpam-modules 1.0.1-4ubuntu5
2009-02-24 13:24:43 install libpam-runtime <none> 1.0.1-4ubuntu5
2009-02-24 13:24:43 status half-installed libpam-runtime 1.0.1-4ubuntu5
2009-02-24 13:24:43 status unpacked libpam-runtime 1.0.1-4ubuntu5
2009-02-24 13:24:43 status unpacked libpam-runtime 1.0.1-4ubuntu5
2009-02-24 13:24:43 install libpam0g <none> 1.0.1-4ubuntu5
2009-02-24 13:24:43 status half-installed libpam0g 1.0.1-4ubuntu5
2009-02-24 13:24:43 status unpacked libpam0g 1.0.1-4ubuntu5
2009-02-24 13:24:43 status unpacked libpam0g 1.0.1-4ubuntu5
2009-02-24 13:24:43 install libpcre3 <none> 7.6-2.1ubuntu1
2009-02-24 13:24:43 status half-installed libpcre3 7.6-2.1ubuntu1
2009-02-24 13:24:43 status unpacked libpcre3 7.6-2.1ubuntu1
2009-02-24 13:24:43 status unpacked libpcre3 7.6-2.1ubuntu1
2009-02-24 13:24:43 install login <none> 1:4.1.1-1ubuntu1
2009-02-24 13:24:43 status half-installed login 1:4.1.1-1ubuntu1
2009-02-24 13:24:43 status unpacked login 1:4.1.1-1ubuntu1
2009-02-24 13:24:43 status unpacked login 1:4.1.1-1ubuntu1
2009-02-24 13:24:43 install libslang2 <none> 2.1.3-3ubuntu1
2009-02-24 13:24:43 status half-installed libslang2 2.1.3-3ubuntu1
2009-02-24 13:24:43 status unpacked libslang2 2.1.3-3ubuntu1
2009-02-24 13:24:43 status unpacked libslang2 2.1.3-3ubuntu1
2009-02-24 13:24:44 install initscripts <none> 2.86.ds1-59ubuntu13
2009-02-24 13:24:44 status half-installed initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:44 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:44 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:44 install bsdutils <none> 1:2.14-1ubuntu2
2009-02-24 13:24:44 status half-installed bsdutils 1:2.14-1ubuntu2
2009-02-24 13:24:44 status unpacked bsdutils 1:2.14-1ubuntu2
2009-02-24 13:24:44 status unpacked bsdutils 1:2.14-1ubuntu2
2009-02-24 13:24:44 install lsb-base <none> 3.2-14ubuntu2
2009-02-24 13:24:44 status half-installed lsb-base 3.2-14ubuntu2
2009-02-24 13:24:44 status unpacked lsb-base 3.2-14ubuntu2
2009-02-24 13:24:44 status unpacked lsb-base 3.2-14ubuntu2
2009-02-24 13:24:44 install lzma <none> 4.43-14ubuntu1
2009-02-24 13:24:44 status half-installed lzma 4.43-14ubuntu1
2009-02-24 13:24:44 status unpacked lzma 4.43-14ubuntu1
2009-02-24 13:24:44 status unpacked lzma 4.43-14ubuntu1
2009-02-24 13:24:44 install makedev <none> 2.3.1-88
2009-02-24 13:24:44 status half-installed makedev 2.3.1-88
2009-02-24 13:24:44 status unpacked makedev 2.3.1-88
2009-02-24 13:24:44 status unpacked makedev 2.3.1-88
2009-02-24 13:24:44 upgrade mawk 1.3.3-11.1ubuntu1 1.3.3-11.1ubuntu1
2009-02-24 13:24:44 status half-configured mawk 1.3.3-11.1ubuntu1
2009-02-24 13:24:44 status unpacked mawk 1.3.3-11.1ubuntu1
2009-02-24 13:24:44 status half-installed mawk 1.3.3-11.1ubuntu1
2009-02-24 13:24:44 status half-installed mawk 1.3.3-11.1ubuntu1
2009-02-24 13:24:44 status unpacked mawk 1.3.3-11.1ubuntu1
2009-02-24 13:24:44 status unpacked mawk 1.3.3-11.1ubuntu1
2009-02-24 13:24:44 install mktemp <none> 1.5-7
2009-02-24 13:24:44 status half-installed mktemp 1.5-7
2009-02-24 13:24:44 status unpacked mktemp 1.5-7
2009-02-24 13:24:44 status unpacked mktemp 1.5-7
2009-02-24 13:24:44 install ncurses-base <none> 5.6+20071124-1ubuntu2
2009-02-24 13:24:44 status half-installed ncurses-base 5.6+20071124-1ubuntu2
2009-02-24 13:24:44 status unpacked ncurses-base 5.6+20071124-1ubuntu2
2009-02-24 13:24:44 status unpacked ncurses-base 5.6+20071124-1ubuntu2
2009-02-24 13:24:44 install ncurses-bin <none> 5.6+20071124-1ubuntu2
2009-02-24 13:24:44 status half-installed ncurses-bin 5.6+20071124-1ubuntu2
2009-02-24 13:24:44 status unpacked ncurses-bin 5.6+20071124-1ubuntu2
2009-02-24 13:24:44 status unpacked ncurses-bin 5.6+20071124-1ubuntu2
2009-02-24 13:24:44 upgrade perl-base 5.10.0-11.1ubuntu2 5.10.0-11.1ubuntu2
2009-02-24 13:24:44 status half-configured perl-base 5.10.0-11.1ubuntu2
2009-02-24 13:24:44 status unpacked perl-base 5.10.0-11.1ubuntu2
2009-02-24 13:24:44 status half-installed perl-base 5.10.0-11.1ubuntu2
2009-02-24 13:24:44 status half-installed perl-base 5.10.0-11.1ubuntu2
2009-02-24 13:24:44 status unpacked perl-base 5.10.0-11.1ubuntu2
2009-02-24 13:24:44 status unpacked perl-base 5.10.0-11.1ubuntu2
2009-02-24 13:24:44 install procps <none> 1:3.2.7-9ubuntu2
2009-02-24 13:24:44 status half-installed procps 1:3.2.7-9ubuntu2
2009-02-24 13:24:44 status unpacked procps 1:3.2.7-9ubuntu2
2009-02-24 13:24:44 status unpacked procps 1:3.2.7-9ubuntu2
2009-02-24 13:24:44 install python-minimal <none> 2.5.2-1ubuntu1
2009-02-24 13:24:44 status half-installed python-minimal 2.5.2-1ubuntu1
2009-02-24 13:24:44 status unpacked python-minimal 2.5.2-1ubuntu1
2009-02-24 13:24:45 status unpacked python-minimal 2.5.2-1ubuntu1
2009-02-24 13:24:45 install python2.5-minimal <none> 2.5.2-11.1ubuntu1
2009-02-24 13:24:45 status half-installed python2.5-minimal 2.5.2-11.1ubuntu1
2009-02-24 13:24:46 status unpacked python2.5-minimal 2.5.2-11.1ubuntu1
2009-02-24 13:24:47 status unpacked python2.5-minimal 2.5.2-11.1ubuntu1
2009-02-24 13:24:47 install sed <none> 4.1.5-8
2009-02-24 13:24:47 status half-installed sed 4.1.5-8
2009-02-24 13:24:47 status unpacked sed 4.1.5-8
2009-02-24 13:24:47 status unpacked sed 4.1.5-8
2009-02-24 13:24:47 install passwd <none> 1:4.1.1-1ubuntu1
2009-02-24 13:24:47 status half-installed passwd 1:4.1.1-1ubuntu1
2009-02-24 13:24:47 status unpacked passwd 1:4.1.1-1ubuntu1
2009-02-24 13:24:47 status unpacked passwd 1:4.1.1-1ubuntu1
2009-02-24 13:24:47 install sysv-rc <none> 2.86.ds1-59ubuntu13
2009-02-24 13:24:47 status half-installed sysv-rc 2.86.ds1-59ubuntu13
2009-02-24 13:24:47 status unpacked sysv-rc 2.86.ds1-59ubuntu13
2009-02-24 13:24:47 status unpacked sysv-rc 2.86.ds1-59ubuntu13
2009-02-24 13:24:47 install sysvinit-utils <none> 2.86.ds1-59ubuntu13
2009-02-24 13:24:47 status half-installed sysvinit-utils 2.86.ds1-59ubuntu13
2009-02-24 13:24:47 status unpacked sysvinit-utils 2.86.ds1-59ubuntu13
2009-02-24 13:24:47 status unpacked sysvinit-utils 2.86.ds1-59ubuntu13
2009-02-24 13:24:48 install tar <none> 1.20-1
2009-02-24 13:24:48 status half-installed tar 1.20-1
2009-02-24 13:24:48 status unpacked tar 1.20-1
2009-02-24 13:24:48 status unpacked tar 1.20-1
2009-02-24 13:24:48 install tzdata <none> 2008h-2ubuntu1
2009-02-24 13:24:48 status half-installed tzdata 2008h-2ubuntu1
2009-02-24 13:24:48 status unpacked tzdata 2008h-2ubuntu1
2009-02-24 13:24:48 status unpacked tzdata 2008h-2ubuntu1
2009-02-24 13:24:48 install startup-tasks <none> 0.3.9-8
2009-02-24 13:24:48 status half-installed startup-tasks 0.3.9-8
2009-02-24 13:24:48 status unpacked startup-tasks 0.3.9-8
2009-02-24 13:24:48 status unpacked startup-tasks 0.3.9-8
2009-02-24 13:24:48 install system-services <none> 0.3.9-8
2009-02-24 13:24:48 status half-installed system-services 0.3.9-8
2009-02-24 13:24:48 status unpacked system-services 0.3.9-8
2009-02-24 13:24:48 status unpacked system-services 0.3.9-8
2009-02-24 13:24:48 install upstart-compat-sysv <none> 0.3.9-8
2009-02-24 13:24:48 status half-installed upstart-compat-sysv 0.3.9-8
2009-02-24 13:24:48 status unpacked upstart-compat-sysv 0.3.9-8
2009-02-24 13:24:48 status unpacked upstart-compat-sysv 0.3.9-8
2009-02-24 13:24:48 install upstart-logd <none> 0.3.9-8
2009-02-24 13:24:48 status half-installed upstart-logd 0.3.9-8
2009-02-24 13:24:48 status unpacked upstart-logd 0.3.9-8
2009-02-24 13:24:48 status unpacked upstart-logd 0.3.9-8
2009-02-24 13:24:48 install upstart <none> 0.3.9-8
2009-02-24 13:24:48 status half-installed upstart 0.3.9-8
2009-02-24 13:24:48 status unpacked upstart 0.3.9-8
2009-02-24 13:24:48 status unpacked upstart 0.3.9-8
2009-02-24 13:24:48 install mount <none> 2.14-1ubuntu2
2009-02-24 13:24:48 status half-installed mount 2.14-1ubuntu2
2009-02-24 13:24:49 status unpacked mount 2.14-1ubuntu2
2009-02-24 13:24:49 status unpacked mount 2.14-1ubuntu2
2009-02-24 13:24:49 install util-linux <none> 2.14-1ubuntu2
2009-02-24 13:24:49 status half-installed util-linux 2.14-1ubuntu2
2009-02-24 13:24:49 status unpacked util-linux 2.14-1ubuntu2
2009-02-24 13:24:49 status unpacked util-linux 2.14-1ubuntu2
2009-02-24 13:24:49 install zlib1g <none> 1:1.2.3.3.dfsg-12ubuntu1
2009-02-24 13:24:49 status half-installed zlib1g 1:1.2.3.3.dfsg-12ubuntu1
2009-02-24 13:24:49 status unpacked zlib1g 1:1.2.3.3.dfsg-12ubuntu1
2009-02-24 13:24:49 status unpacked zlib1g 1:1.2.3.3.dfsg-12ubuntu1
2009-02-24 13:24:49 startup packages configure
2009-02-24 13:24:49 configure sysv-rc 2.86.ds1-59ubuntu13 2.86.ds1-59ubuntu13
2009-02-24 13:24:49 status unpacked sysv-rc 2.86.ds1-59ubuntu13
2009-02-24 13:24:49 status half-configured sysv-rc 2.86.ds1-59ubuntu13
2009-02-24 13:24:49 status installed sysv-rc 2.86.ds1-59ubuntu13
2009-02-24 13:24:49 configure gcc-4.3-base 4.3.2-1ubuntu11 4.3.2-1ubuntu11
2009-02-24 13:24:49 status unpacked gcc-4.3-base 4.3.2-1ubuntu11
2009-02-24 13:24:49 status half-configured gcc-4.3-base 4.3.2-1ubuntu11
2009-02-24 13:24:49 status installed gcc-4.3-base 4.3.2-1ubuntu11
2009-02-24 13:24:49 configure libc6 2.8~20080505-0ubuntu7 2.8~20080505-0ubuntu7
2009-02-24 13:24:49 status unpacked libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:49 status unpacked libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:49 status unpacked libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:49 status unpacked libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:49 status unpacked libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:49 status unpacked libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:49 status half-configured libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:50 status installed libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:50 status triggers-pending libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:50 configure mktemp 1.5-7 1.5-7
2009-02-24 13:24:50 status unpacked mktemp 1.5-7
2009-02-24 13:24:50 status half-configured mktemp 1.5-7
2009-02-24 13:24:50 status installed mktemp 1.5-7
2009-02-24 13:24:50 configure debianutils 2.29ubuntu2 2.29ubuntu2
2009-02-24 13:24:50 status unpacked debianutils 2.29ubuntu2
2009-02-24 13:24:50 status half-configured debianutils 2.29ubuntu2
2009-02-24 13:24:50 status installed debianutils 2.29ubuntu2
2009-02-24 13:24:50 configure bsdutils 1:2.14-1ubuntu2 1:2.14-1ubuntu2
2009-02-24 13:24:50 status unpacked bsdutils 1:2.14-1ubuntu2
2009-02-24 13:24:50 status half-configured bsdutils 1:2.14-1ubuntu2
2009-02-24 13:24:50 status installed bsdutils 1:2.14-1ubuntu2
2009-02-24 13:24:50 configure perl-base 5.10.0-11.1ubuntu2 5.10.0-11.1ubuntu2
2009-02-24 13:24:50 status unpacked perl-base 5.10.0-11.1ubuntu2
2009-02-24 13:24:50 status half-configured perl-base 5.10.0-11.1ubuntu2
2009-02-24 13:24:50 status installed perl-base 5.10.0-11.1ubuntu2
2009-02-24 13:24:50 configure libsepol1 2.0.30-2 2.0.30-2
2009-02-24 13:24:50 status unpacked libsepol1 2.0.30-2
2009-02-24 13:24:50 status half-configured libsepol1 2.0.30-2
2009-02-24 13:24:50 status installed libsepol1 2.0.30-2
2009-02-24 13:24:50 configure tar 1.20-1 1.20-1
2009-02-24 13:24:50 status unpacked tar 1.20-1
2009-02-24 13:24:50 status unpacked tar 1.20-1
2009-02-24 13:24:50 status half-configured tar 1.20-1
2009-02-24 13:24:51 status installed tar 1.20-1
2009-02-24 13:24:51 configure zlib1g 1:1.2.3.3.dfsg-12ubuntu1 1:1.2.3.3.dfsg-12ubuntu1
2009-02-24 13:24:51 status unpacked zlib1g 1:1.2.3.3.dfsg-12ubuntu1
2009-02-24 13:24:51 status half-configured zlib1g 1:1.2.3.3.dfsg-12ubuntu1
2009-02-24 13:24:51 status installed zlib1g 1:1.2.3.3.dfsg-12ubuntu1
2009-02-24 13:24:51 configure libgcc1 1:4.3.2-1ubuntu11 1:4.3.2-1ubuntu11
2009-02-24 13:24:51 status unpacked libgcc1 1:4.3.2-1ubuntu11
2009-02-24 13:24:51 status half-configured libgcc1 1:4.3.2-1ubuntu11
2009-02-24 13:24:51 status installed libgcc1 1:4.3.2-1ubuntu11
2009-02-24 13:24:51 configure libtext-iconv-perl 1.7-1build1 1.7-1build1
2009-02-24 13:24:51 status unpacked libtext-iconv-perl 1.7-1build1
2009-02-24 13:24:51 status half-configured libtext-iconv-perl 1.7-1build1
2009-02-24 13:24:51 status installed libtext-iconv-perl 1.7-1build1
2009-02-24 13:24:51 configure libncurses5 5.6+20071124-1ubuntu2 5.6+20071124-1ubuntu2
2009-02-24 13:24:51 status unpacked libncurses5 5.6+20071124-1ubuntu2
2009-02-24 13:24:51 status half-configured libncurses5 5.6+20071124-1ubuntu2
2009-02-24 13:24:51 status installed libncurses5 5.6+20071124-1ubuntu2
2009-02-24 13:24:51 configure libattr1 1:2.4.41-1 1:2.4.41-1
2009-02-24 13:24:51 status unpacked libattr1 1:2.4.41-1
2009-02-24 13:24:51 status half-configured libattr1 1:2.4.41-1
2009-02-24 13:24:51 status installed libattr1 1:2.4.41-1
2009-02-24 13:24:51 configure sed 4.1.5-8 4.1.5-8
2009-02-24 13:24:51 status unpacked sed 4.1.5-8
2009-02-24 13:24:51 status half-configured sed 4.1.5-8
2009-02-24 13:24:51 status installed sed 4.1.5-8
2009-02-24 13:24:51 configure base-passwd 3.5.18 3.5.18
2009-02-24 13:24:51 status unpacked base-passwd 3.5.18
2009-02-24 13:24:51 status half-configured base-passwd 3.5.18
2009-02-24 13:24:51 status installed base-passwd 3.5.18
2009-02-24 13:24:51 configure libcomerr2 1.41.3-1ubuntu1 1.41.3-1ubuntu1
2009-02-24 13:24:51 status unpacked libcomerr2 1.41.3-1ubuntu1
2009-02-24 13:24:51 status half-configured libcomerr2 1.41.3-1ubuntu1
2009-02-24 13:24:51 status installed libcomerr2 1.41.3-1ubuntu1
2009-02-24 13:24:51 configure mawk 1.3.3-11.1ubuntu1 1.3.3-11.1ubuntu1
2009-02-24 13:24:51 status unpacked mawk 1.3.3-11.1ubuntu1
2009-02-24 13:24:51 status half-configured mawk 1.3.3-11.1ubuntu1
2009-02-24 13:24:51 status installed mawk 1.3.3-11.1ubuntu1
2009-02-24 13:24:51 configure libdb4.7 4.7.25-3 4.7.25-3
2009-02-24 13:24:51 status unpacked libdb4.7 4.7.25-3
2009-02-24 13:24:51 status half-configured libdb4.7 4.7.25-3
2009-02-24 13:24:51 status installed libdb4.7 4.7.25-3
2009-02-24 13:24:51 configure hostname 2.95 2.95
2009-02-24 13:24:51 status unpacked hostname 2.95
2009-02-24 13:24:51 status half-configured hostname 2.95
2009-02-24 13:24:51 status installed hostname 2.95
2009-02-24 13:24:51 configure libacl1 2.2.47-2 2.2.47-2
2009-02-24 13:24:51 status unpacked libacl1 2.2.47-2
2009-02-24 13:24:51 status half-configured libacl1 2.2.47-2
2009-02-24 13:24:51 status installed libacl1 2.2.47-2
2009-02-24 13:24:51 configure libslang2 2.1.3-3ubuntu1 2.1.3-3ubuntu1
2009-02-24 13:24:51 status unpacked libslang2 2.1.3-3ubuntu1
2009-02-24 13:24:51 status half-configured libslang2 2.1.3-3ubuntu1
2009-02-24 13:24:51 status installed libslang2 2.1.3-3ubuntu1
2009-02-24 13:24:51 configure libss2 1.41.3-1ubuntu1 1.41.3-1ubuntu1
2009-02-24 13:24:51 status unpacked libss2 1.41.3-1ubuntu1
2009-02-24 13:24:51 status half-configured libss2 1.41.3-1ubuntu1
2009-02-24 13:24:51 status installed libss2 1.41.3-1ubuntu1
2009-02-24 13:24:51 configure findutils 4.4.0-2ubuntu3 4.4.0-2ubuntu3
2009-02-24 13:24:51 status unpacked findutils 4.4.0-2ubuntu3
2009-02-24 13:24:51 status half-configured findutils 4.4.0-2ubuntu3
2009-02-24 13:24:51 status installed findutils 4.4.0-2ubuntu3
2009-02-24 13:24:51 configure gzip 1.3.12-6ubuntu2 1.3.12-6ubuntu2
2009-02-24 13:24:51 status unpacked gzip 1.3.12-6ubuntu2
2009-02-24 13:24:51 status half-configured gzip 1.3.12-6ubuntu2
2009-02-24 13:24:51 status installed gzip 1.3.12-6ubuntu2
2009-02-24 13:24:51 configure libpcre3 7.6-2.1ubuntu1 7.6-2.1ubuntu1
2009-02-24 13:24:51 status unpacked libpcre3 7.6-2.1ubuntu1
2009-02-24 13:24:51 status half-configured libpcre3 7.6-2.1ubuntu1
2009-02-24 13:24:51 status installed libpcre3 7.6-2.1ubuntu1
2009-02-24 13:24:51 configure liblocale-gettext-perl 1.05-4build1 1.05-4build1
2009-02-24 13:24:51 status unpacked liblocale-gettext-perl 1.05-4build1
2009-02-24 13:24:51 status half-configured liblocale-gettext-perl 1.05-4build1
2009-02-24 13:24:51 status installed liblocale-gettext-perl 1.05-4build1
2009-02-24 13:24:51 configure diff 2.8.1-12ubuntu1 2.8.1-12ubuntu1
2009-02-24 13:24:51 status unpacked diff 2.8.1-12ubuntu1
2009-02-24 13:24:51 status half-configured diff 2.8.1-12ubuntu1
2009-02-24 13:24:51 status installed diff 2.8.1-12ubuntu1
2009-02-24 13:24:51 configure libselinux1 2.0.65-2 2.0.65-2
2009-02-24 13:24:51 status unpacked libselinux1 2.0.65-2
2009-02-24 13:24:51 status half-configured libselinux1 2.0.65-2
2009-02-24 13:24:51 status installed libselinux1 2.0.65-2
2009-02-24 13:24:51 configure belocs-locales-bin 2.4-2.3ubuntu1 2.4-2.3ubuntu1
2009-02-24 13:24:51 status unpacked belocs-locales-bin 2.4-2.3ubuntu1
2009-02-24 13:24:51 status unpacked belocs-locales-bin 2.4-2.3ubuntu1
2009-02-24 13:24:51 status half-configured belocs-locales-bin 2.4-2.3ubuntu1
2009-02-24 13:24:51 status installed belocs-locales-bin 2.4-2.3ubuntu1
2009-02-24 13:24:51 configure libstdc++6 4.3.2-1ubuntu11 4.3.2-1ubuntu11
2009-02-24 13:24:51 status unpacked libstdc++6 4.3.2-1ubuntu11
2009-02-24 13:24:51 status half-configured libstdc++6 4.3.2-1ubuntu11
2009-02-24 13:24:51 status installed libstdc++6 4.3.2-1ubuntu11
2009-02-24 13:24:51 configure libtext-charwidth-perl 0.04-5build1 0.04-5build1
2009-02-24 13:24:51 status unpacked libtext-charwidth-perl 0.04-5build1
2009-02-24 13:24:51 status half-configured libtext-charwidth-perl 0.04-5build1
2009-02-24 13:24:51 status installed libtext-charwidth-perl 0.04-5build1
2009-02-24 13:24:51 configure libtext-wrapi18n-perl 0.06-6 0.06-6
2009-02-24 13:24:51 status unpacked libtext-wrapi18n-perl 0.06-6
2009-02-24 13:24:51 status half-configured libtext-wrapi18n-perl 0.06-6
2009-02-24 13:24:51 status installed libtext-wrapi18n-perl 0.06-6
2009-02-24 13:24:51 configure dash 0.5.4-9ubuntu1 0.5.4-9ubuntu1
2009-02-24 13:24:51 status unpacked dash 0.5.4-9ubuntu1
2009-02-24 13:24:51 status half-configured dash 0.5.4-9ubuntu1
2009-02-24 13:24:51 status installed dash 0.5.4-9ubuntu1
2009-02-24 13:24:51 configure coreutils 6.10-6ubuntu1 6.10-6ubuntu1
2009-02-24 13:24:51 status unpacked coreutils 6.10-6ubuntu1
2009-02-24 13:24:51 status half-configured coreutils 6.10-6ubuntu1
2009-02-24 13:24:52 status installed coreutils 6.10-6ubuntu1
2009-02-24 13:24:52 configure makedev 2.3.1-88 2.3.1-88
2009-02-24 13:24:52 status unpacked makedev 2.3.1-88
2009-02-24 13:24:52 status half-configured makedev 2.3.1-88
2009-02-24 13:24:54 status installed makedev 2.3.1-88
2009-02-24 13:24:54 configure lzma 4.43-14ubuntu1 4.43-14ubuntu1
2009-02-24 13:24:54 status unpacked lzma 4.43-14ubuntu1
2009-02-24 13:24:54 status half-configured lzma 4.43-14ubuntu1
2009-02-24 13:24:54 status installed lzma 4.43-14ubuntu1
2009-02-24 13:24:54 configure ncurses-base 5.6+20071124-1ubuntu2 5.6+20071124-1ubuntu2
2009-02-24 13:24:54 status unpacked ncurses-base 5.6+20071124-1ubuntu2
2009-02-24 13:24:54 status unpacked ncurses-base 5.6+20071124-1ubuntu2
2009-02-24 13:24:54 status half-configured ncurses-base 5.6+20071124-1ubuntu2
2009-02-24 13:24:54 status installed ncurses-base 5.6+20071124-1ubuntu2
2009-02-24 13:24:54 configure python2.5-minimal 2.5.2-11.1ubuntu1 2.5.2-11.1ubuntu1
2009-02-24 13:24:54 status unpacked python2.5-minimal 2.5.2-11.1ubuntu1
2009-02-24 13:24:54 status unpacked python2.5-minimal 2.5.2-11.1ubuntu1
2009-02-24 13:24:54 status half-configured python2.5-minimal 2.5.2-11.1ubuntu1
2009-02-24 13:24:54 status installed python2.5-minimal 2.5.2-11.1ubuntu1
2009-02-24 13:24:54 configure ncurses-bin 5.6+20071124-1ubuntu2 5.6+20071124-1ubuntu2
2009-02-24 13:24:54 status unpacked ncurses-bin 5.6+20071124-1ubuntu2
2009-02-24 13:24:54 status half-configured ncurses-bin 5.6+20071124-1ubuntu2
2009-02-24 13:24:54 status installed ncurses-bin 5.6+20071124-1ubuntu2
2009-02-24 13:24:54 configure mount 2.14-1ubuntu2 2.14-1ubuntu2
2009-02-24 13:24:54 status unpacked mount 2.14-1ubuntu2
2009-02-24 13:24:54 status half-configured mount 2.14-1ubuntu2
2009-02-24 13:24:54 status installed mount 2.14-1ubuntu2
2009-02-24 13:24:54 configure e2fslibs 1.41.3-1ubuntu1 1.41.3-1ubuntu1
2009-02-24 13:24:54 status unpacked e2fslibs 1.41.3-1ubuntu1
2009-02-24 13:24:54 status half-configured e2fslibs 1.41.3-1ubuntu1
2009-02-24 13:24:54 status installed e2fslibs 1.41.3-1ubuntu1
2009-02-24 13:24:54 configure debconf-i18n 1.5.23ubuntu2 1.5.23ubuntu2
2009-02-24 13:24:54 status unpacked debconf-i18n 1.5.23ubuntu2
2009-02-24 13:24:54 status half-configured debconf-i18n 1.5.23ubuntu2
2009-02-24 13:24:54 status installed debconf-i18n 1.5.23ubuntu2
2009-02-24 13:24:54 configure grep 2.5.3~dfsg-5ubuntu2 2.5.3~dfsg-5ubuntu2
2009-02-24 13:24:54 status unpacked grep 2.5.3~dfsg-5ubuntu2
2009-02-24 13:24:54 status half-configured grep 2.5.3~dfsg-5ubuntu2
2009-02-24 13:24:54 status installed grep 2.5.3~dfsg-5ubuntu2
2009-02-24 13:24:54 configure dpkg 1.14.20ubuntu6 1.14.20ubuntu6
2009-02-24 13:24:54 status unpacked dpkg 1.14.20ubuntu6
2009-02-24 13:24:54 status unpacked dpkg 1.14.20ubuntu6
2009-02-24 13:24:54 status unpacked dpkg 1.14.20ubuntu6
2009-02-24 13:24:54 status unpacked dpkg 1.14.20ubuntu6
2009-02-24 13:24:54 status unpacked dpkg 1.14.20ubuntu6
2009-02-24 13:24:54 status half-configured dpkg 1.14.20ubuntu6
2009-02-24 13:24:54 status installed dpkg 1.14.20ubuntu6
2009-02-24 13:24:54 configure sysvinit-utils 2.86.ds1-59ubuntu13 2.86.ds1-59ubuntu13
2009-02-24 13:24:54 status unpacked sysvinit-utils 2.86.ds1-59ubuntu13
2009-02-24 13:24:54 status half-configured sysvinit-utils 2.86.ds1-59ubuntu13
2009-02-24 13:24:54 status installed sysvinit-utils 2.86.ds1-59ubuntu13
2009-02-24 13:24:54 configure debconf 1.5.23ubuntu2 1.5.23ubuntu2
2009-02-24 13:24:54 status unpacked debconf 1.5.23ubuntu2
2009-02-24 13:24:54 status unpacked debconf 1.5.23ubuntu2
2009-02-24 13:24:54 status unpacked debconf 1.5.23ubuntu2
2009-02-24 13:24:54 status unpacked debconf 1.5.23ubuntu2
2009-02-24 13:24:54 status half-configured debconf 1.5.23ubuntu2
2009-02-24 13:24:55 status installed debconf 1.5.23ubuntu2
2009-02-24 13:24:55 configure python-minimal 2.5.2-1ubuntu1 2.5.2-1ubuntu1
2009-02-24 13:24:55 status unpacked python-minimal 2.5.2-1ubuntu1
2009-02-24 13:24:55 status half-configured python-minimal 2.5.2-1ubuntu1
2009-02-24 13:24:55 status installed python-minimal 2.5.2-1ubuntu1
2009-02-24 13:24:55 configure tzdata 2008h-2ubuntu1 2008h-2ubuntu1
2009-02-24 13:24:55 status unpacked tzdata 2008h-2ubuntu1
2009-02-24 13:24:55 status half-configured tzdata 2008h-2ubuntu1
2009-02-24 13:24:55 status installed tzdata 2008h-2ubuntu1
2009-02-24 13:24:55 configure locales 2.7.9-5 2.7.9-5
2009-02-24 13:24:55 status unpacked locales 2.7.9-5
2009-02-24 13:24:55 status unpacked locales 2.7.9-5
2009-02-24 13:24:55 status unpacked locales 2.7.9-5
2009-02-24 13:24:55 status half-configured locales 2.7.9-5
2009-02-24 13:24:55 status installed locales 2.7.9-5
2009-02-24 13:24:55 configure upstart 0.3.9-8 0.3.9-8
2009-02-24 13:24:55 status unpacked upstart 0.3.9-8
2009-02-24 13:24:55 status unpacked upstart 0.3.9-8
2009-02-24 13:24:55 status unpacked upstart 0.3.9-8
2009-02-24 13:24:55 status half-configured upstart 0.3.9-8
2009-02-24 13:24:55 status installed upstart 0.3.9-8
2009-02-24 13:24:55 configure libpam-runtime 1.0.1-4ubuntu5 1.0.1-4ubuntu5
2009-02-24 13:24:55 status unpacked libpam-runtime 1.0.1-4ubuntu5
2009-02-24 13:24:55 status unpacked libpam-runtime 1.0.1-4ubuntu5
2009-02-24 13:24:55 status unpacked libpam-runtime 1.0.1-4ubuntu5
2009-02-24 13:24:55 status half-configured libpam-runtime 1.0.1-4ubuntu5
2009-02-24 13:24:55 status installed libpam-runtime 1.0.1-4ubuntu5
2009-02-24 13:24:55 configure upstart-logd 0.3.9-8 0.3.9-8
2009-02-24 13:24:55 status unpacked upstart-logd 0.3.9-8
2009-02-24 13:24:55 status unpacked upstart-logd 0.3.9-8
2009-02-24 13:24:55 status half-configured upstart-logd 0.3.9-8
2009-02-24 13:24:55 status installed upstart-logd 0.3.9-8
2009-02-24 13:24:55 configure libpam0g 1.0.1-4ubuntu5 1.0.1-4ubuntu5
2009-02-24 13:24:55 status unpacked libpam0g 1.0.1-4ubuntu5
2009-02-24 13:24:55 status half-configured libpam0g 1.0.1-4ubuntu5
2009-02-24 13:24:55 status installed libpam0g 1.0.1-4ubuntu5
2009-02-24 13:24:55 configure libpam-modules 1.0.1-4ubuntu5 1.0.1-4ubuntu5
2009-02-24 13:24:55 status unpacked libpam-modules 1.0.1-4ubuntu5
2009-02-24 13:24:55 status unpacked libpam-modules 1.0.1-4ubuntu5
2009-02-24 13:24:55 status unpacked libpam-modules 1.0.1-4ubuntu5
2009-02-24 13:24:55 status unpacked libpam-modules 1.0.1-4ubuntu5
2009-02-24 13:24:55 status unpacked libpam-modules 1.0.1-4ubuntu5
2009-02-24 13:24:55 status unpacked libpam-modules 1.0.1-4ubuntu5
2009-02-24 13:24:55 status unpacked libpam-modules 1.0.1-4ubuntu5
2009-02-24 13:24:55 status unpacked libpam-modules 1.0.1-4ubuntu5
2009-02-24 13:24:55 status unpacked libpam-modules 1.0.1-4ubuntu5
2009-02-24 13:24:55 status half-configured libpam-modules 1.0.1-4ubuntu5
2009-02-24 13:24:55 status installed libpam-modules 1.0.1-4ubuntu5
2009-02-24 13:24:55 configure base-files 4.0.4ubuntu2 4.0.4ubuntu2
2009-02-24 13:24:55 status unpacked base-files 4.0.4ubuntu2
2009-02-24 13:24:55 status unpacked base-files 4.0.4ubuntu2
2009-02-24 13:24:55 status unpacked base-files 4.0.4ubuntu2
2009-02-24 13:24:55 status unpacked base-files 4.0.4ubuntu2
2009-02-24 13:24:55 status unpacked base-files 4.0.4ubuntu2
2009-02-24 13:24:55 status unpacked base-files 4.0.4ubuntu2
2009-02-24 13:24:55 status half-configured base-files 4.0.4ubuntu2
2009-02-24 13:24:55 status installed base-files 4.0.4ubuntu2
2009-02-24 13:24:55 configure startup-tasks 0.3.9-8 0.3.9-8
2009-02-24 13:24:55 status unpacked startup-tasks 0.3.9-8
2009-02-24 13:24:55 status half-configured startup-tasks 0.3.9-8
2009-02-24 13:24:55 status installed startup-tasks 0.3.9-8
2009-02-24 13:24:55 configure passwd 1:4.1.1-1ubuntu1 1:4.1.1-1ubuntu1
2009-02-24 13:24:55 status unpacked passwd 1:4.1.1-1ubuntu1
2009-02-24 13:24:55 status unpacked passwd 1:4.1.1-1ubuntu1
2009-02-24 13:24:55 status unpacked passwd 1:4.1.1-1ubuntu1
2009-02-24 13:24:55 status unpacked passwd 1:4.1.1-1ubuntu1
2009-02-24 13:24:55 status unpacked passwd 1:4.1.1-1ubuntu1
2009-02-24 13:24:55 status half-configured passwd 1:4.1.1-1ubuntu1
2009-02-24 13:24:56 status installed passwd 1:4.1.1-1ubuntu1
2009-02-24 13:24:56 configure bash 3.2-4ubuntu1 3.2-4ubuntu1
2009-02-24 13:24:56 status unpacked bash 3.2-4ubuntu1
2009-02-24 13:24:56 status unpacked bash 3.2-4ubuntu1
2009-02-24 13:24:56 status unpacked bash 3.2-4ubuntu1
2009-02-24 13:24:56 status unpacked bash 3.2-4ubuntu1
2009-02-24 13:24:56 status unpacked bash 3.2-4ubuntu1
2009-02-24 13:24:56 status half-configured bash 3.2-4ubuntu1
2009-02-24 13:24:56 status installed bash 3.2-4ubuntu1
2009-02-24 13:24:56 configure login 1:4.1.1-1ubuntu1 1:4.1.1-1ubuntu1
2009-02-24 13:24:56 status unpacked login 1:4.1.1-1ubuntu1
2009-02-24 13:24:56 status unpacked login 1:4.1.1-1ubuntu1
2009-02-24 13:24:56 status unpacked login 1:4.1.1-1ubuntu1
2009-02-24 13:24:56 status unpacked login 1:4.1.1-1ubuntu1
2009-02-24 13:24:56 status unpacked login 1:4.1.1-1ubuntu1
2009-02-24 13:24:56 status half-configured login 1:4.1.1-1ubuntu1
2009-02-24 13:24:56 status installed login 1:4.1.1-1ubuntu1
2009-02-24 13:24:56 configure libuuid1 1.41.3-1ubuntu1 1.41.3-1ubuntu1
2009-02-24 13:24:56 status unpacked libuuid1 1.41.3-1ubuntu1
2009-02-24 13:24:56 status half-configured libuuid1 1.41.3-1ubuntu1
2009-02-24 13:24:56 status installed libuuid1 1.41.3-1ubuntu1
2009-02-24 13:24:56 configure lsb-base 3.2-14ubuntu2 3.2-14ubuntu2
2009-02-24 13:24:56 status unpacked lsb-base 3.2-14ubuntu2
2009-02-24 13:24:56 status unpacked lsb-base 3.2-14ubuntu2
2009-02-24 13:24:56 status half-configured lsb-base 3.2-14ubuntu2
2009-02-24 13:24:56 status installed lsb-base 3.2-14ubuntu2
2009-02-24 13:24:56 configure procps 1:3.2.7-9ubuntu2 1:3.2.7-9ubuntu2
2009-02-24 13:24:56 status unpacked procps 1:3.2.7-9ubuntu2
2009-02-24 13:24:56 status unpacked procps 1:3.2.7-9ubuntu2
2009-02-24 13:24:56 status unpacked procps 1:3.2.7-9ubuntu2
2009-02-24 13:24:56 status unpacked procps 1:3.2.7-9ubuntu2
2009-02-24 13:24:56 status unpacked procps 1:3.2.7-9ubuntu2
2009-02-24 13:24:56 status unpacked procps 1:3.2.7-9ubuntu2
2009-02-24 13:24:56 status unpacked procps 1:3.2.7-9ubuntu2
2009-02-24 13:24:56 status unpacked procps 1:3.2.7-9ubuntu2
2009-02-24 13:24:56 status half-configured procps 1:3.2.7-9ubuntu2
2009-02-24 13:24:56 status installed procps 1:3.2.7-9ubuntu2
2009-02-24 13:24:56 configure libblkid1 1.41.3-1ubuntu1 1.41.3-1ubuntu1
2009-02-24 13:24:56 status unpacked libblkid1 1.41.3-1ubuntu1
2009-02-24 13:24:56 status half-configured libblkid1 1.41.3-1ubuntu1
2009-02-24 13:24:56 status installed libblkid1 1.41.3-1ubuntu1
2009-02-24 13:24:56 configure e2fsprogs 1.41.3-1ubuntu1 1.41.3-1ubuntu1
2009-02-24 13:24:56 status unpacked e2fsprogs 1.41.3-1ubuntu1
2009-02-24 13:24:56 status unpacked e2fsprogs 1.41.3-1ubuntu1
2009-02-24 13:24:56 status unpacked e2fsprogs 1.41.3-1ubuntu1
2009-02-24 13:24:56 status half-configured e2fsprogs 1.41.3-1ubuntu1
2009-02-24 13:24:56 status installed e2fsprogs 1.41.3-1ubuntu1
2009-02-24 13:24:56 configure util-linux 2.14-1ubuntu2 2.14-1ubuntu2
2009-02-24 13:24:56 status unpacked util-linux 2.14-1ubuntu2
2009-02-24 13:24:56 status unpacked util-linux 2.14-1ubuntu2
2009-02-24 13:24:56 status unpacked util-linux 2.14-1ubuntu2
2009-02-24 13:24:56 status unpacked util-linux 2.14-1ubuntu2
2009-02-24 13:24:56 status half-configured util-linux 2.14-1ubuntu2
2009-02-24 13:24:56 status installed util-linux 2.14-1ubuntu2
2009-02-24 13:24:56 configure initscripts 2.86.ds1-59ubuntu13 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status unpacked initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status half-configured initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 status installed initscripts 2.86.ds1-59ubuntu13
2009-02-24 13:24:56 configure upstart-compat-sysv 0.3.9-8 0.3.9-8
2009-02-24 13:24:56 status unpacked upstart-compat-sysv 0.3.9-8
2009-02-24 13:24:56 status unpacked upstart-compat-sysv 0.3.9-8
2009-02-24 13:24:56 status unpacked upstart-compat-sysv 0.3.9-8
2009-02-24 13:24:56 status unpacked upstart-compat-sysv 0.3.9-8
2009-02-24 13:24:56 status unpacked upstart-compat-sysv 0.3.9-8
2009-02-24 13:24:56 status unpacked upstart-compat-sysv 0.3.9-8
2009-02-24 13:24:56 status unpacked upstart-compat-sysv 0.3.9-8
2009-02-24 13:24:56 status unpacked upstart-compat-sysv 0.3.9-8
2009-02-24 13:24:56 status unpacked upstart-compat-sysv 0.3.9-8
2009-02-24 13:24:56 status unpacked upstart-compat-sysv 0.3.9-8
2009-02-24 13:24:56 status unpacked upstart-compat-sysv 0.3.9-8
2009-02-24 13:24:56 status half-configured upstart-compat-sysv 0.3.9-8
2009-02-24 13:24:56 status installed upstart-compat-sysv 0.3.9-8
2009-02-24 13:24:56 configure system-services 0.3.9-8 0.3.9-8
2009-02-24 13:24:56 status unpacked system-services 0.3.9-8
2009-02-24 13:24:56 status unpacked system-services 0.3.9-8
2009-02-24 13:24:57 status unpacked system-services 0.3.9-8
2009-02-24 13:24:57 status unpacked system-services 0.3.9-8
2009-02-24 13:24:57 status unpacked system-services 0.3.9-8
2009-02-24 13:24:57 status unpacked system-services 0.3.9-8
2009-02-24 13:24:57 status unpacked system-services 0.3.9-8
2009-02-24 13:24:57 status half-configured system-services 0.3.9-8
2009-02-24 13:24:57 status installed system-services 0.3.9-8
2009-02-24 13:24:57 trigproc libc6 2.8~20080505-0ubuntu7 2.8~20080505-0ubuntu7
2009-02-24 13:24:57 status half-configured libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:57 status installed libc6 2.8~20080505-0ubuntu7
2009-02-24 13:24:57 startup archives unpack
2009-02-24 13:24:57 install adduser <none> 3.108ubuntu1
2009-02-24 13:24:57 status half-installed adduser 3.108ubuntu1
2009-02-24 13:24:57 status unpacked adduser 3.108ubuntu1
2009-02-24 13:24:57 status unpacked adduser 3.108ubuntu1
2009-02-24 13:24:57 install apt-utils <none> 0.7.14ubuntu6
2009-02-24 13:24:57 status half-installed apt-utils 0.7.14ubuntu6
2009-02-24 13:24:57 status unpacked apt-utils 0.7.14ubuntu6
2009-02-24 13:24:57 status unpacked apt-utils 0.7.14ubuntu6
2009-02-24 13:24:57 install apt <none> 0.7.14ubuntu6
2009-02-24 13:24:57 status half-installed apt 0.7.14ubuntu6
2009-02-24 13:24:58 status unpacked apt 0.7.14ubuntu6
2009-02-24 13:24:58 status unpacked apt 0.7.14ubuntu6
2009-02-24 13:24:58 install busybox-initramfs <none> 1:1.10.2-1ubuntu6
2009-02-24 13:24:58 status half-installed busybox-initramfs 1:1.10.2-1ubuntu6
2009-02-24 13:24:58 status unpacked busybox-initramfs 1:1.10.2-1ubuntu6
2009-02-24 13:24:58 status unpacked busybox-initramfs 1:1.10.2-1ubuntu6
2009-02-24 13:24:58 install bzip2 <none> 1.0.5-0.1ubuntu1
2009-02-24 13:24:58 status half-installed bzip2 1.0.5-0.1ubuntu1
2009-02-24 13:24:58 status unpacked bzip2 1.0.5-0.1ubuntu1
2009-02-24 13:24:58 status unpacked bzip2 1.0.5-0.1ubuntu1
2009-02-24 13:24:58 install libbz2-1.0 <none> 1.0.5-0.1ubuntu1
2009-02-24 13:24:58 status half-installed libbz2-1.0 1.0.5-0.1ubuntu1
2009-02-24 13:24:58 status unpacked libbz2-1.0 1.0.5-0.1ubuntu1
2009-02-24 13:24:58 status unpacked libbz2-1.0 1.0.5-0.1ubuntu1
2009-02-24 13:24:58 install ca-certificates <none> 20080514-0ubuntu1
2009-02-24 13:24:58 status half-installed ca-certificates 20080514-0ubuntu1
2009-02-24 13:24:58 status unpacked ca-certificates 20080514-0ubuntu1
2009-02-24 13:24:58 status unpacked ca-certificates 20080514-0ubuntu1
2009-02-24 13:24:58 install console-setup <none> 1.25ubuntu3
2009-02-24 13:24:58 status half-installed console-setup 1.25ubuntu3
2009-02-24 13:24:58 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:24:58 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:24:58 install cpio <none> 2.9-13ubuntu2
2009-02-24 13:24:58 status half-installed cpio 2.9-13ubuntu2
2009-02-24 13:24:58 status unpacked cpio 2.9-13ubuntu2
2009-02-24 13:24:58 status unpacked cpio 2.9-13ubuntu2
2009-02-24 13:24:58 install libcurl3-gnutls <none> 7.18.2-1ubuntu4
2009-02-24 13:24:58 status half-installed libcurl3-gnutls 7.18.2-1ubuntu4
2009-02-24 13:24:58 status unpacked libcurl3-gnutls 7.18.2-1ubuntu4
2009-02-24 13:24:58 status unpacked libcurl3-gnutls 7.18.2-1ubuntu4
2009-02-24 13:24:58 install libsasl2-2 <none> 2.1.22.dfsg1-21ubuntu2
2009-02-24 13:24:58 status half-installed libsasl2-2 2.1.22.dfsg1-21ubuntu2
2009-02-24 13:24:58 status unpacked libsasl2-2 2.1.22.dfsg1-21ubuntu2
2009-02-24 13:24:58 status unpacked libsasl2-2 2.1.22.dfsg1-21ubuntu2
2009-02-24 13:24:58 install libsasl2-modules <none> 2.1.22.dfsg1-21ubuntu2
2009-02-24 13:24:58 status half-installed libsasl2-modules 2.1.22.dfsg1-21ubuntu2
2009-02-24 13:24:59 status unpacked libsasl2-modules 2.1.22.dfsg1-21ubuntu2
2009-02-24 13:24:59 status unpacked libsasl2-modules 2.1.22.dfsg1-21ubuntu2
2009-02-24 13:24:59 install libdb4.6 <none> 4.6.21-10
2009-02-24 13:24:59 status half-installed libdb4.6 4.6.21-10
2009-02-24 13:24:59 status unpacked libdb4.6 4.6.21-10
2009-02-24 13:24:59 status unpacked libdb4.6 4.6.21-10
2009-02-24 13:24:59 install dmsetup <none> 2:1.02.27-3ubuntu2
2009-02-24 13:24:59 status half-installed dmsetup 2:1.02.27-3ubuntu2
2009-02-24 13:24:59 status unpacked dmsetup 2:1.02.27-3ubuntu2
2009-02-24 13:24:59 status unpacked dmsetup 2:1.02.27-3ubuntu2
2009-02-24 13:24:59 install libdevmapper1.02.1 <none> 2:1.02.27-3ubuntu2
2009-02-24 13:24:59 status half-installed libdevmapper1.02.1 2:1.02.27-3ubuntu2
2009-02-24 13:24:59 status unpacked libdevmapper1.02.1 2:1.02.27-3ubuntu2
2009-02-24 13:24:59 status unpacked libdevmapper1.02.1 2:1.02.27-3ubuntu2
2009-02-24 13:24:59 install dhcp3-client <none> 3.1.1-1ubuntu2
2009-02-24 13:24:59 status half-installed dhcp3-client 3.1.1-1ubuntu2
2009-02-24 13:24:59 status unpacked dhcp3-client 3.1.1-1ubuntu2
2009-02-24 13:24:59 status unpacked dhcp3-client 3.1.1-1ubuntu2
2009-02-24 13:24:59 install dhcp3-common <none> 3.1.1-1ubuntu2
2009-02-24 13:24:59 status half-installed dhcp3-common 3.1.1-1ubuntu2
2009-02-24 13:24:59 status unpacked dhcp3-common 3.1.1-1ubuntu2
2009-02-24 13:24:59 status unpacked dhcp3-common 3.1.1-1ubuntu2
2009-02-24 13:24:59 install dmidecode <none> 2.9-1ubuntu1
2009-02-24 13:24:59 status half-installed dmidecode 2.9-1ubuntu1
2009-02-24 13:24:59 status unpacked dmidecode 2.9-1ubuntu1
2009-02-24 13:24:59 status unpacked dmidecode 2.9-1ubuntu1
2009-02-24 13:24:59 install eject <none> 2.1.5-9ubuntu2
2009-02-24 13:24:59 status half-installed eject 2.1.5-9ubuntu2
2009-02-24 13:24:59 status unpacked eject 2.1.5-9ubuntu2
2009-02-24 13:24:59 status unpacked eject 2.1.5-9ubuntu2
2009-02-24 13:24:59 install file <none> 4.24-4
2009-02-24 13:24:59 status half-installed file 4.24-4
2009-02-24 13:24:59 status unpacked file 4.24-4
2009-02-24 13:24:59 status unpacked file 4.24-4
2009-02-24 13:24:59 install libmagic1 <none> 4.24-4
2009-02-24 13:24:59 status half-installed libmagic1 4.24-4
2009-02-24 13:24:59 status unpacked libmagic1 4.24-4
2009-02-24 13:24:59 status unpacked libmagic1 4.24-4
2009-02-24 13:24:59 install libfribidi0 <none> 0.10.9-1
2009-02-24 13:24:59 status half-installed libfribidi0 0.10.9-1
2009-02-24 13:24:59 status unpacked libfribidi0 0.10.9-1
2009-02-24 13:24:59 status unpacked libfribidi0 0.10.9-1
2009-02-24 13:24:59 install libc6-i686 <none> 2.8~20080505-0ubuntu7
2009-02-24 13:24:59 status half-installed libc6-i686 2.8~20080505-0ubuntu7
2009-02-24 13:25:00 status unpacked libc6-i686 2.8~20080505-0ubuntu7
2009-02-24 13:25:00 status unpacked libc6-i686 2.8~20080505-0ubuntu7
2009-02-24 13:25:00 install gnupg <none> 1.4.9-3ubuntu1
2009-02-24 13:25:00 status half-installed gnupg 1.4.9-3ubuntu1
2009-02-24 13:25:00 status unpacked gnupg 1.4.9-3ubuntu1
2009-02-24 13:25:00 status unpacked gnupg 1.4.9-3ubuntu1
2009-02-24 13:25:00 install gpgv <none> 1.4.9-3ubuntu1
2009-02-24 13:25:00 status half-installed gpgv 1.4.9-3ubuntu1
2009-02-24 13:25:00 status unpacked gpgv 1.4.9-3ubuntu1
2009-02-24 13:25:00 status unpacked gpgv 1.4.9-3ubuntu1
2009-02-24 13:25:00 install libgnutls26 <none> 2.4.1-1build1
2009-02-24 13:25:00 status half-installed libgnutls26 2.4.1-1build1
2009-02-24 13:25:00 status unpacked libgnutls26 2.4.1-1build1
2009-02-24 13:25:00 status unpacked libgnutls26 2.4.1-1build1
2009-02-24 13:25:00 install ifupdown <none> 0.6.8ubuntu12
2009-02-24 13:25:00 status half-installed ifupdown 0.6.8ubuntu12
2009-02-24 13:25:00 status unpacked ifupdown 0.6.8ubuntu12
2009-02-24 13:25:00 status unpacked ifupdown 0.6.8ubuntu12
2009-02-24 13:25:00 install initramfs-tools <none> 0.92bubuntu15
2009-02-24 13:25:00 status half-installed initramfs-tools 0.92bubuntu15
2009-02-24 13:25:00 status unpacked initramfs-tools 0.92bubuntu15
2009-02-24 13:25:00 status unpacked initramfs-tools 0.92bubuntu15
2009-02-24 13:25:00 install iproute <none> 20080417-1
2009-02-24 13:25:00 status half-installed iproute 20080417-1
2009-02-24 13:25:00 status unpacked iproute 20080417-1
2009-02-24 13:25:00 status unpacked iproute 20080417-1
2009-02-24 13:25:00 install iputils-ping <none> 3:20071127-1
2009-02-24 13:25:00 status half-installed iputils-ping 3:20071127-1
2009-02-24 13:25:00 status unpacked iputils-ping 3:20071127-1
2009-02-24 13:25:00 status unpacked iputils-ping 3:20071127-1
2009-02-24 13:25:00 install kbd <none> 1.14.1-3ubuntu3
2009-02-24 13:25:00 status half-installed kbd 1.14.1-3ubuntu3
2009-02-24 13:25:01 status unpacked kbd 1.14.1-3ubuntu3
2009-02-24 13:25:01 status unpacked kbd 1.14.1-3ubuntu3
2009-02-24 13:25:01 install libkeyutils1 <none> 1.2-7
2009-02-24 13:25:01 status half-installed libkeyutils1 1.2-7
2009-02-24 13:25:01 status unpacked libkeyutils1 1.2-7
2009-02-24 13:25:01 status unpacked libkeyutils1 1.2-7
2009-02-24 13:25:01 install klibc-utils <none> 1.5.12-1ubuntu1
2009-02-24 13:25:01 status half-installed klibc-utils 1.5.12-1ubuntu1
2009-02-24 13:25:01 status unpacked klibc-utils 1.5.12-1ubuntu1
2009-02-24 13:25:01 status unpacked klibc-utils 1.5.12-1ubuntu1
2009-02-24 13:25:01 install libklibc <none> 1.5.12-1ubuntu1
2009-02-24 13:25:01 status half-installed libklibc 1.5.12-1ubuntu1
2009-02-24 13:25:01 status unpacked libklibc 1.5.12-1ubuntu1
2009-02-24 13:25:01 status unpacked libklibc 1.5.12-1ubuntu1
2009-02-24 13:25:01 install libkrb53 <none> 1.6.dfsg.4~beta1-3
2009-02-24 13:25:01 status half-installed libkrb53 1.6.dfsg.4~beta1-3
2009-02-24 13:25:01 status unpacked libkrb53 1.6.dfsg.4~beta1-3
2009-02-24 13:25:01 status unpacked libkrb53 1.6.dfsg.4~beta1-3
2009-02-24 13:25:01 install laptop-detect <none> 0.13.6ubuntu1
2009-02-24 13:25:01 status half-installed laptop-detect 0.13.6ubuntu1
2009-02-24 13:25:01 status unpacked laptop-detect 0.13.6ubuntu1
2009-02-24 13:25:01 status unpacked laptop-detect 0.13.6ubuntu1
2009-02-24 13:25:01 install less <none> 418-1
2009-02-24 13:25:01 status half-installed less 418-1
2009-02-24 13:25:01 status unpacked less 418-1
2009-02-24 13:25:01 status unpacked less 418-1
2009-02-24 13:25:01 install libatm1 <none> 2.4.1-17.2
2009-02-24 13:25:01 status half-installed libatm1 2.4.1-17.2
2009-02-24 13:25:01 status unpacked libatm1 2.4.1-17.2
2009-02-24 13:25:01 status unpacked libatm1 2.4.1-17.2
2009-02-24 13:25:01 install lockfile-progs <none> 0.1.11ubuntu2
2009-02-24 13:25:01 status half-installed lockfile-progs 0.1.11ubuntu2
2009-02-24 13:25:01 status unpacked lockfile-progs 0.1.11ubuntu2
2009-02-24 13:25:01 status unpacked lockfile-progs 0.1.11ubuntu2
2009-02-24 13:25:01 install libcap1 <none> 1:1.10-14build1
2009-02-24 13:25:01 status half-installed libcap1 1:1.10-14build1
2009-02-24 13:25:01 status unpacked libcap1 1:1.10-14build1
2009-02-24 13:25:01 status unpacked libcap1 1:1.10-14build1
2009-02-24 13:25:01 install libgcrypt11 <none> 1.4.1-1ubuntu1
2009-02-24 13:25:01 status half-installed libgcrypt11 1.4.1-1ubuntu1
2009-02-24 13:25:01 status unpacked libgcrypt11 1.4.1-1ubuntu1
2009-02-24 13:25:01 status unpacked libgcrypt11 1.4.1-1ubuntu1
2009-02-24 13:25:01 install libgpg-error0 <none> 1.4-2ubuntu7
2009-02-24 13:25:01 status half-installed libgpg-error0 1.4-2ubuntu7
2009-02-24 13:25:01 status unpacked libgpg-error0 1.4-2ubuntu7
2009-02-24 13:25:01 status unpacked libgpg-error0 1.4-2ubuntu7
2009-02-24 13:25:01 install libidn11 <none> 1.8+20080606-1
2009-02-24 13:25:01 status half-installed libidn11 1.8+20080606-1
2009-02-24 13:25:01 status unpacked libidn11 1.8+20080606-1
2009-02-24 13:25:01 status unpacked libidn11 1.8+20080606-1
2009-02-24 13:25:01 install liblockfile1 <none> 1.07-1
2009-02-24 13:25:01 status half-installed liblockfile1 1.07-1
2009-02-24 13:25:01 status unpacked liblockfile1 1.07-1
2009-02-24 13:25:01 status unpacked liblockfile1 1.07-1
2009-02-24 13:25:01 install libtasn1-3 <none> 1.4-1
2009-02-24 13:25:01 status half-installed libtasn1-3 1.4-1
2009-02-24 13:25:02 status unpacked libtasn1-3 1.4-1
2009-02-24 13:25:02 status unpacked libtasn1-3 1.4-1
2009-02-24 13:25:02 install libusb-0.1-4 <none> 2:0.1.12-12
2009-02-24 13:25:02 status half-installed libusb-0.1-4 2:0.1.12-12
2009-02-24 13:25:02 status unpacked libusb-0.1-4 2:0.1.12-12
2009-02-24 13:25:02 status unpacked libusb-0.1-4 2:0.1.12-12
2009-02-24 13:25:02 install libncursesw5 <none> 5.6+20071124-1ubuntu2
2009-02-24 13:25:02 status half-installed libncursesw5 5.6+20071124-1ubuntu2
2009-02-24 13:25:02 status unpacked libncursesw5 5.6+20071124-1ubuntu2
2009-02-24 13:25:02 status unpacked libncursesw5 5.6+20071124-1ubuntu2
2009-02-24 13:25:02 install libnewt0.52 <none> 0.52.2-11.3ubuntu1
2009-02-24 13:25:02 status half-installed libnewt0.52 0.52.2-11.3ubuntu1
2009-02-24 13:25:02 status unpacked libnewt0.52 0.52.2-11.3ubuntu1
2009-02-24 13:25:02 status unpacked libnewt0.52 0.52.2-11.3ubuntu1
2009-02-24 13:25:02 install libldap-2.4-2 <none> 2.4.11-0ubuntu6
2009-02-24 13:25:02 status half-installed libldap-2.4-2 2.4.11-0ubuntu6
2009-02-24 13:25:02 status unpacked libldap-2.4-2 2.4.11-0ubuntu6
2009-02-24 13:25:02 status unpacked libldap-2.4-2 2.4.11-0ubuntu6
2009-02-24 13:25:02 install libssl0.9.8 <none> 0.9.8g-10.1ubuntu2
2009-02-24 13:25:02 status half-installed libssl0.9.8 0.9.8g-10.1ubuntu2
2009-02-24 13:25:02 status unpacked libssl0.9.8 0.9.8g-10.1ubuntu2
2009-02-24 13:25:02 status unpacked libssl0.9.8 0.9.8g-10.1ubuntu2
2009-02-24 13:25:02 install libpopt0 <none> 1.14-4
2009-02-24 13:25:02 status half-installed libpopt0 1.14-4
2009-02-24 13:25:02 status unpacked libpopt0 1.14-4
2009-02-24 13:25:02 status unpacked libpopt0 1.14-4
2009-02-24 13:25:02 install libreadline5 <none> 5.2-3build1
2009-02-24 13:25:02 status half-installed libreadline5 5.2-3build1
2009-02-24 13:25:02 status unpacked libreadline5 5.2-3build1
2009-02-24 13:25:02 status unpacked libreadline5 5.2-3build1
2009-02-24 13:25:02 install libsqlite3-0 <none> 3.5.9-3
2009-02-24 13:25:02 status half-installed libsqlite3-0 3.5.9-3
2009-02-24 13:25:02 status unpacked libsqlite3-0 3.5.9-3
2009-02-24 13:25:02 status unpacked libsqlite3-0 3.5.9-3
2009-02-24 13:25:02 install klogd <none> 1.5-2ubuntu6
2009-02-24 13:25:02 status half-installed klogd 1.5-2ubuntu6
2009-02-24 13:25:03 status unpacked klogd 1.5-2ubuntu6
2009-02-24 13:25:03 status unpacked klogd 1.5-2ubuntu6
2009-02-24 13:25:03 install libvolume-id0 <none> 124-8
2009-02-24 13:25:03 status half-installed libvolume-id0 124-8
2009-02-24 13:25:03 status unpacked libvolume-id0 124-8
2009-02-24 13:25:03 status unpacked libvolume-id0 124-8
2009-02-24 13:25:03 install console-terminus <none> 4.26-1
2009-02-24 13:25:03 status half-installed console-terminus 4.26-1
2009-02-24 13:25:03 status unpacked console-terminus 4.26-1
2009-02-24 13:25:03 status unpacked console-terminus 4.26-1
2009-02-24 13:25:03 install uuid-runtime <none> 1.41.3-1ubuntu1
2009-02-24 13:25:03 status half-installed uuid-runtime 1.41.3-1ubuntu1
2009-02-24 13:25:03 status unpacked uuid-runtime 1.41.3-1ubuntu1
2009-02-24 13:25:03 status unpacked uuid-runtime 1.41.3-1ubuntu1
2009-02-24 13:25:03 install lsb-release <none> 3.2-14ubuntu2
2009-02-24 13:25:03 status half-installed lsb-release 3.2-14ubuntu2
2009-02-24 13:25:03 status unpacked lsb-release 3.2-14ubuntu2
2009-02-24 13:25:03 status unpacked lsb-release 3.2-14ubuntu2
2009-02-24 13:25:03 install mime-support <none> 3.44-1
2009-02-24 13:25:03 status half-installed mime-support 3.44-1
2009-02-24 13:25:03 status unpacked mime-support 3.44-1
2009-02-24 13:25:03 status unpacked mime-support 3.44-1
2009-02-24 13:25:03 install module-init-tools <none> 3.3-pre11-4ubuntu16
2009-02-24 13:25:03 status half-installed module-init-tools 3.3-pre11-4ubuntu16
2009-02-24 13:25:03 status unpacked module-init-tools 3.3-pre11-4ubuntu16
2009-02-24 13:25:03 status unpacked module-init-tools 3.3-pre11-4ubuntu16
2009-02-24 13:25:03 install net-tools <none> 1.60-19ubuntu3
2009-02-24 13:25:03 status half-installed net-tools 1.60-19ubuntu3
2009-02-24 13:25:03 status unpacked net-tools 1.60-19ubuntu3
2009-02-24 13:25:03 status unpacked net-tools 1.60-19ubuntu3
2009-02-24 13:25:03 install netbase <none> 4.32ubuntu1
2009-02-24 13:25:03 status half-installed netbase 4.32ubuntu1
2009-02-24 13:25:03 status unpacked netbase 4.32ubuntu1
2009-02-24 13:25:03 status unpacked netbase 4.32ubuntu1
2009-02-24 13:25:03 install netcat-traditional <none> 1.10-38
2009-02-24 13:25:03 status half-installed netcat-traditional 1.10-38
2009-02-24 13:25:03 status unpacked netcat-traditional 1.10-38
2009-02-24 13:25:03 status unpacked netcat-traditional 1.10-38
2009-02-24 13:25:03 install netcat <none> 1.10-38
2009-02-24 13:25:03 status half-installed netcat 1.10-38
2009-02-24 13:25:03 status unpacked netcat 1.10-38
2009-02-24 13:25:03 status unpacked netcat 1.10-38
2009-02-24 13:25:03 install whiptail <none> 0.52.2-11.3ubuntu1
2009-02-24 13:25:03 status half-installed whiptail 0.52.2-11.3ubuntu1
2009-02-24 13:25:03 status unpacked whiptail 0.52.2-11.3ubuntu1
2009-02-24 13:25:03 status unpacked whiptail 0.52.2-11.3ubuntu1
2009-02-24 13:25:03 install ntpdate <none> 1:4.2.4p4+dfsg-6ubuntu2
2009-02-24 13:25:03 status half-installed ntpdate 1:4.2.4p4+dfsg-6ubuntu2
2009-02-24 13:25:03 status unpacked ntpdate 1:4.2.4p4+dfsg-6ubuntu2
2009-02-24 13:25:03 status unpacked ntpdate 1:4.2.4p4+dfsg-6ubuntu2
2009-02-24 13:25:03 install openssl <none> 0.9.8g-10.1ubuntu2
2009-02-24 13:25:03 status half-installed openssl 0.9.8g-10.1ubuntu2
2009-02-24 13:25:04 status unpacked openssl 0.9.8g-10.1ubuntu2
2009-02-24 13:25:04 status unpacked openssl 0.9.8g-10.1ubuntu2
2009-02-24 13:25:04 install python <none> 2.5.2-1ubuntu1
2009-02-24 13:25:04 status half-installed python 2.5.2-1ubuntu1
2009-02-24 13:25:04 status unpacked python 2.5.2-1ubuntu1
2009-02-24 13:25:04 status unpacked python 2.5.2-1ubuntu1
2009-02-24 13:25:04 install python2.5 <none> 2.5.2-11.1ubuntu1
2009-02-24 13:25:04 status half-installed python2.5 2.5.2-11.1ubuntu1
2009-02-24 13:25:05 status unpacked python2.5 2.5.2-11.1ubuntu1
2009-02-24 13:25:05 status unpacked python2.5 2.5.2-11.1ubuntu1
2009-02-24 13:25:05 install readline-common <none> 5.2-3build1
2009-02-24 13:25:05 status half-installed readline-common 5.2-3build1
2009-02-24 13:25:05 status unpacked readline-common 5.2-3build1
2009-02-24 13:25:05 status unpacked readline-common 5.2-3build1
2009-02-24 13:25:05 install sudo <none> 1.6.9p17-1ubuntu2
2009-02-24 13:25:05 status half-installed sudo 1.6.9p17-1ubuntu2
2009-02-24 13:25:05 status unpacked sudo 1.6.9p17-1ubuntu2
2009-02-24 13:25:05 status unpacked sudo 1.6.9p17-1ubuntu2
2009-02-24 13:25:05 install sysklogd <none> 1.5-2ubuntu6
2009-02-24 13:25:05 status half-installed sysklogd 1.5-2ubuntu6
2009-02-24 13:25:05 status unpacked sysklogd 1.5-2ubuntu6
2009-02-24 13:25:05 status unpacked sysklogd 1.5-2ubuntu6
2009-02-24 13:25:05 install tasksel-data <none> 2.73ubuntu11
2009-02-24 13:25:05 status half-installed tasksel-data 2.73ubuntu11
2009-02-24 13:25:05 status unpacked tasksel-data 2.73ubuntu11
2009-02-24 13:25:05 status unpacked tasksel-data 2.73ubuntu11
2009-02-24 13:25:05 install tasksel <none> 2.73ubuntu11
2009-02-24 13:25:05 status half-installed tasksel 2.73ubuntu11
2009-02-24 13:25:05 status unpacked tasksel 2.73ubuntu11
2009-02-24 13:25:05 status unpacked tasksel 2.73ubuntu11
2009-02-24 13:25:05 install ubuntu-keyring <none> 2008.03.04
2009-02-24 13:25:05 status half-installed ubuntu-keyring 2008.03.04
2009-02-24 13:25:05 status unpacked ubuntu-keyring 2008.03.04
2009-02-24 13:25:05 status unpacked ubuntu-keyring 2008.03.04
2009-02-24 13:25:05 install ubuntu-minimal <none> 1.124
2009-02-24 13:25:05 status half-installed ubuntu-minimal 1.124
2009-02-24 13:25:05 status unpacked ubuntu-minimal 1.124
2009-02-24 13:25:05 status unpacked ubuntu-minimal 1.124
2009-02-24 13:25:05 install udev <none> 124-8
2009-02-24 13:25:05 status half-installed udev 124-8
2009-02-24 13:25:05 status unpacked udev 124-8
2009-02-24 13:25:05 status unpacked udev 124-8
2009-02-24 13:25:05 install vim-common <none> 1:7.1.314-3ubuntu3
2009-02-24 13:25:05 status half-installed vim-common 1:7.1.314-3ubuntu3
2009-02-24 13:25:05 status unpacked vim-common 1:7.1.314-3ubuntu3
2009-02-24 13:25:05 status unpacked vim-common 1:7.1.314-3ubuntu3
2009-02-24 13:25:05 install vim-tiny <none> 1:7.1.314-3ubuntu3
2009-02-24 13:25:05 status half-installed vim-tiny 1:7.1.314-3ubuntu3
2009-02-24 13:25:05 status unpacked vim-tiny 1:7.1.314-3ubuntu3
2009-02-24 13:25:05 status unpacked vim-tiny 1:7.1.314-3ubuntu3
2009-02-24 13:25:05 install xkb-data <none> 1.3-2ubuntu4
2009-02-24 13:25:05 status half-installed xkb-data 1.3-2ubuntu4
2009-02-24 13:25:06 status unpacked xkb-data 1.3-2ubuntu4
2009-02-24 13:25:06 status unpacked xkb-data 1.3-2ubuntu4
2009-02-24 13:25:06 startup packages configure
2009-02-24 13:25:06 configure sudo 1.6.9p17-1ubuntu2 1.6.9p17-1ubuntu2
2009-02-24 13:25:06 status unpacked sudo 1.6.9p17-1ubuntu2
2009-02-24 13:25:06 status unpacked sudo 1.6.9p17-1ubuntu2
2009-02-24 13:25:06 status half-configured sudo 1.6.9p17-1ubuntu2
2009-02-24 13:25:06 status installed sudo 1.6.9p17-1ubuntu2
2009-02-24 13:25:06 configure gpgv 1.4.9-3ubuntu1 1.4.9-3ubuntu1
2009-02-24 13:25:06 status unpacked gpgv 1.4.9-3ubuntu1
2009-02-24 13:25:06 status half-configured gpgv 1.4.9-3ubuntu1
2009-02-24 13:25:06 status installed gpgv 1.4.9-3ubuntu1
2009-02-24 13:25:06 configure module-init-tools 3.3-pre11-4ubuntu16 3.3-pre11-4ubuntu16
2009-02-24 13:25:06 status unpacked module-init-tools 3.3-pre11-4ubuntu16
2009-02-24 13:25:06 status unpacked module-init-tools 3.3-pre11-4ubuntu16
2009-02-24 13:25:06 status unpacked module-init-tools 3.3-pre11-4ubuntu16
2009-02-24 13:25:06 status unpacked module-init-tools 3.3-pre11-4ubuntu16
2009-02-24 13:25:06 status unpacked module-init-tools 3.3-pre11-4ubuntu16
2009-02-24 13:25:06 status unpacked module-init-tools 3.3-pre11-4ubuntu16
2009-02-24 13:25:06 status unpacked module-init-tools 3.3-pre11-4ubuntu16
2009-02-24 13:25:06 status unpacked module-init-tools 3.3-pre11-4ubuntu16
2009-02-24 13:25:06 status unpacked module-init-tools 3.3-pre11-4ubuntu16
2009-02-24 13:25:06 status unpacked module-init-tools 3.3-pre11-4ubuntu16
2009-02-24 13:25:06 status half-configured module-init-tools 3.3-pre11-4ubuntu16
2009-02-24 13:25:06 status installed module-init-tools 3.3-pre11-4ubuntu16
2009-02-24 13:25:06 configure libtasn1-3 1.4-1 1.4-1
2009-02-24 13:25:06 status unpacked libtasn1-3 1.4-1
2009-02-24 13:25:06 status half-configured libtasn1-3 1.4-1
2009-02-24 13:25:06 status installed libtasn1-3 1.4-1
2009-02-24 13:25:06 status triggers-pending libc6 2.8~20080505-0ubuntu7
2009-02-24 13:25:06 configure libpopt0 1.14-4 1.14-4
2009-02-24 13:25:06 status unpacked libpopt0 1.14-4
2009-02-24 13:25:06 status half-configured libpopt0 1.14-4
2009-02-24 13:25:06 status installed libpopt0 1.14-4
2009-02-24 13:25:06 configure libusb-0.1-4 2:0.1.12-12 2:0.1.12-12
2009-02-24 13:25:06 status unpacked libusb-0.1-4 2:0.1.12-12
2009-02-24 13:25:06 status half-configured libusb-0.1-4 2:0.1.12-12
2009-02-24 13:25:06 status installed libusb-0.1-4 2:0.1.12-12
2009-02-24 13:25:06 configure libgpg-error0 1.4-2ubuntu7 1.4-2ubuntu7
2009-02-24 13:25:06 status unpacked libgpg-error0 1.4-2ubuntu7
2009-02-24 13:25:06 status half-configured libgpg-error0 1.4-2ubuntu7
2009-02-24 13:25:06 status installed libgpg-error0 1.4-2ubuntu7
2009-02-24 13:25:06 configure libssl0.9.8 0.9.8g-10.1ubuntu2 0.9.8g-10.1ubuntu2
2009-02-24 13:25:06 status unpacked libssl0.9.8 0.9.8g-10.1ubuntu2
2009-02-24 13:25:06 status half-configured libssl0.9.8 0.9.8g-10.1ubuntu2
2009-02-24 13:25:07 status installed libssl0.9.8 0.9.8g-10.1ubuntu2
2009-02-24 13:25:07 configure vim-common 1:7.1.314-3ubuntu3 1:7.1.314-3ubuntu3
2009-02-24 13:25:07 status unpacked vim-common 1:7.1.314-3ubuntu3
2009-02-24 13:25:07 status unpacked vim-common 1:7.1.314-3ubuntu3
2009-02-24 13:25:07 status half-configured vim-common 1:7.1.314-3ubuntu3
2009-02-24 13:25:07 status installed vim-common 1:7.1.314-3ubuntu3
2009-02-24 13:25:07 configure openssl 0.9.8g-10.1ubuntu2 0.9.8g-10.1ubuntu2
2009-02-24 13:25:07 status unpacked openssl 0.9.8g-10.1ubuntu2
2009-02-24 13:25:07 status unpacked openssl 0.9.8g-10.1ubuntu2
2009-02-24 13:25:07 status half-configured openssl 0.9.8g-10.1ubuntu2
2009-02-24 13:25:07 status installed openssl 0.9.8g-10.1ubuntu2
2009-02-24 13:25:07 configure apt 0.7.14ubuntu6 0.7.14ubuntu6
2009-02-24 13:25:07 status unpacked apt 0.7.14ubuntu6
2009-02-24 13:25:07 status unpacked apt 0.7.14ubuntu6
2009-02-24 13:25:07 status unpacked apt 0.7.14ubuntu6
2009-02-24 13:25:07 status unpacked apt 0.7.14ubuntu6
2009-02-24 13:25:07 status unpacked apt 0.7.14ubuntu6
2009-02-24 13:25:07 status half-configured apt 0.7.14ubuntu6
2009-02-24 13:25:07 status installed apt 0.7.14ubuntu6
2009-02-24 13:25:07 configure libmagic1 4.24-4 4.24-4
2009-02-24 13:25:07 status unpacked libmagic1 4.24-4
2009-02-24 13:25:07 status half-configured libmagic1 4.24-4
2009-02-24 13:25:07 status installed libmagic1 4.24-4
2009-02-24 13:25:07 configure dmidecode 2.9-1ubuntu1 2.9-1ubuntu1
2009-02-24 13:25:07 status unpacked dmidecode 2.9-1ubuntu1
2009-02-24 13:25:07 status half-configured dmidecode 2.9-1ubuntu1
2009-02-24 13:25:07 status installed dmidecode 2.9-1ubuntu1
2009-02-24 13:25:07 configure file 4.24-4 4.24-4
2009-02-24 13:25:07 status unpacked file 4.24-4
2009-02-24 13:25:07 status unpacked file 4.24-4
2009-02-24 13:25:07 status unpacked file 4.24-4
2009-02-24 13:25:07 status half-configured file 4.24-4
2009-02-24 13:25:07 status installed file 4.24-4
2009-02-24 13:25:07 configure libfribidi0 0.10.9-1 0.10.9-1
2009-02-24 13:25:07 status unpacked libfribidi0 0.10.9-1
2009-02-24 13:25:07 status half-configured libfribidi0 0.10.9-1
2009-02-24 13:25:07 status installed libfribidi0 0.10.9-1
2009-02-24 13:25:07 configure adduser 3.108ubuntu1 3.108ubuntu1
2009-02-24 13:25:07 status unpacked adduser 3.108ubuntu1
2009-02-24 13:25:07 status unpacked adduser 3.108ubuntu1
2009-02-24 13:25:07 status half-configured adduser 3.108ubuntu1
2009-02-24 13:25:07 status installed adduser 3.108ubuntu1
2009-02-24 13:25:07 configure libklibc 1.5.12-1ubuntu1 1.5.12-1ubuntu1
2009-02-24 13:25:07 status unpacked libklibc 1.5.12-1ubuntu1
2009-02-24 13:25:07 status half-configured libklibc 1.5.12-1ubuntu1
2009-02-24 13:25:07 status installed libklibc 1.5.12-1ubuntu1
2009-02-24 13:25:07 configure libsqlite3-0 3.5.9-3 3.5.9-3
2009-02-24 13:25:07 status unpacked libsqlite3-0 3.5.9-3
2009-02-24 13:25:07 status half-configured libsqlite3-0 3.5.9-3
2009-02-24 13:25:07 status installed libsqlite3-0 3.5.9-3
2009-02-24 13:25:07 configure libkeyutils1 1.2-7 1.2-7
2009-02-24 13:25:07 status unpacked libkeyutils1 1.2-7
2009-02-24 13:25:07 status half-configured libkeyutils1 1.2-7
2009-02-24 13:25:07 status installed libkeyutils1 1.2-7
2009-02-24 13:25:07 configure libdevmapper1.02.1 2:1.02.27-3ubuntu2 2:1.02.27-3ubuntu2
2009-02-24 13:25:07 status unpacked libdevmapper1.02.1 2:1.02.27-3ubuntu2
2009-02-24 13:25:07 status half-configured libdevmapper1.02.1 2:1.02.27-3ubuntu2
2009-02-24 13:25:07 status installed libdevmapper1.02.1 2:1.02.27-3ubuntu2
2009-02-24 13:25:07 configure libidn11 1.8+20080606-1 1.8+20080606-1
2009-02-24 13:25:07 status unpacked libidn11 1.8+20080606-1
2009-02-24 13:25:07 status half-configured libidn11 1.8+20080606-1
2009-02-24 13:25:07 status installed libidn11 1.8+20080606-1
2009-02-24 13:25:07 configure libatm1 2.4.1-17.2 2.4.1-17.2
2009-02-24 13:25:07 status unpacked libatm1 2.4.1-17.2
2009-02-24 13:25:07 status half-configured libatm1 2.4.1-17.2
2009-02-24 13:25:07 status installed libatm1 2.4.1-17.2
2009-02-24 13:25:07 configure klibc-utils 1.5.12-1ubuntu1 1.5.12-1ubuntu1
2009-02-24 13:25:07 status unpacked klibc-utils 1.5.12-1ubuntu1
2009-02-24 13:25:07 status half-configured klibc-utils 1.5.12-1ubuntu1
2009-02-24 13:25:07 status installed klibc-utils 1.5.12-1ubuntu1
2009-02-24 13:25:07 configure uuid-runtime 1.41.3-1ubuntu1 1.41.3-1ubuntu1
2009-02-24 13:25:07 status unpacked uuid-runtime 1.41.3-1ubuntu1
2009-02-24 13:25:07 status half-configured uuid-runtime 1.41.3-1ubuntu1
2009-02-24 13:25:07 status installed uuid-runtime 1.41.3-1ubuntu1
2009-02-24 13:25:07 configure libnewt0.52 0.52.2-11.3ubuntu1 0.52.2-11.3ubuntu1
2009-02-24 13:25:07 status unpacked libnewt0.52 0.52.2-11.3ubuntu1
2009-02-24 13:25:07 status half-configured libnewt0.52 0.52.2-11.3ubuntu1
2009-02-24 13:25:07 status installed libnewt0.52 0.52.2-11.3ubuntu1
2009-02-24 13:25:07 configure libdb4.6 4.6.21-10 4.6.21-10
2009-02-24 13:25:07 status unpacked libdb4.6 4.6.21-10
2009-02-24 13:25:07 status half-configured libdb4.6 4.6.21-10
2009-02-24 13:25:07 status installed libdb4.6 4.6.21-10
2009-02-24 13:25:07 configure net-tools 1.60-19ubuntu3 1.60-19ubuntu3
2009-02-24 13:25:07 status unpacked net-tools 1.60-19ubuntu3
2009-02-24 13:25:07 status half-configured net-tools 1.60-19ubuntu3
2009-02-24 13:25:07 status installed net-tools 1.60-19ubuntu3
2009-02-24 13:25:07 configure xkb-data 1.3-2ubuntu4 1.3-2ubuntu4
2009-02-24 13:25:07 status unpacked xkb-data 1.3-2ubuntu4
2009-02-24 13:25:07 status unpacked xkb-data 1.3-2ubuntu4
2009-02-24 13:25:07 status half-configured xkb-data 1.3-2ubuntu4
2009-02-24 13:25:07 status installed xkb-data 1.3-2ubuntu4
2009-02-24 13:25:07 configure netcat-traditional 1.10-38 1.10-38
2009-02-24 13:25:07 status unpacked netcat-traditional 1.10-38
2009-02-24 13:25:07 status half-configured netcat-traditional 1.10-38
2009-02-24 13:25:07 status installed netcat-traditional 1.10-38
2009-02-24 13:25:07 configure libncursesw5 5.6+20071124-1ubuntu2 5.6+20071124-1ubuntu2
2009-02-24 13:25:07 status unpacked libncursesw5 5.6+20071124-1ubuntu2
2009-02-24 13:25:07 status half-configured libncursesw5 5.6+20071124-1ubuntu2
2009-02-24 13:25:07 status installed libncursesw5 5.6+20071124-1ubuntu2
2009-02-24 13:25:07 configure dmsetup 2:1.02.27-3ubuntu2 2:1.02.27-3ubuntu2
2009-02-24 13:25:07 status unpacked dmsetup 2:1.02.27-3ubuntu2
2009-02-24 13:25:07 status unpacked dmsetup 2:1.02.27-3ubuntu2
2009-02-24 13:25:07 status half-configured dmsetup 2:1.02.27-3ubuntu2
2009-02-24 13:25:07 status installed dmsetup 2:1.02.27-3ubuntu2
2009-02-24 13:25:07 configure eject 2.1.5-9ubuntu2 2.1.5-9ubuntu2
2009-02-24 13:25:07 status unpacked eject 2.1.5-9ubuntu2
2009-02-24 13:25:07 status half-configured eject 2.1.5-9ubuntu2
2009-02-24 13:25:07 status installed eject 2.1.5-9ubuntu2
2009-02-24 13:25:07 configure busybox-initramfs 1:1.10.2-1ubuntu6 1:1.10.2-1ubuntu6
2009-02-24 13:25:07 status unpacked busybox-initramfs 1:1.10.2-1ubuntu6
2009-02-24 13:25:07 status half-configured busybox-initramfs 1:1.10.2-1ubuntu6
2009-02-24 13:25:07 status installed busybox-initramfs 1:1.10.2-1ubuntu6
2009-02-24 13:25:07 configure iputils-ping 3:20071127-1 3:20071127-1
2009-02-24 13:25:07 status unpacked iputils-ping 3:20071127-1
2009-02-24 13:25:07 status half-configured iputils-ping 3:20071127-1
2009-02-24 13:25:07 status installed iputils-ping 3:20071127-1
2009-02-24 13:25:07 configure libbz2-1.0 1.0.5-0.1ubuntu1 1.0.5-0.1ubuntu1
2009-02-24 13:25:07 status unpacked libbz2-1.0 1.0.5-0.1ubuntu1
2009-02-24 13:25:07 status half-configured libbz2-1.0 1.0.5-0.1ubuntu1
2009-02-24 13:25:07 status installed libbz2-1.0 1.0.5-0.1ubuntu1
2009-02-24 13:25:07 configure libc6-i686 2.8~20080505-0ubuntu7 2.8~20080505-0ubuntu7
2009-02-24 13:25:07 status unpacked libc6-i686 2.8~20080505-0ubuntu7
2009-02-24 13:25:07 status half-configured libc6-i686 2.8~20080505-0ubuntu7
2009-02-24 13:25:07 status installed libc6-i686 2.8~20080505-0ubuntu7
2009-02-24 13:25:07 configure mime-support 3.44-1 3.44-1
2009-02-24 13:25:07 status unpacked mime-support 3.44-1
2009-02-24 13:25:07 status unpacked mime-support 3.44-1
2009-02-24 13:25:07 status unpacked mime-support 3.44-1
2009-02-24 13:25:07 status half-configured mime-support 3.44-1
2009-02-24 13:25:07 status installed mime-support 3.44-1
2009-02-24 13:25:07 configure libvolume-id0 124-8 124-8
2009-02-24 13:25:07 status unpacked libvolume-id0 124-8
2009-02-24 13:25:07 status half-configured libvolume-id0 124-8
2009-02-24 13:25:07 status installed libvolume-id0 124-8
2009-02-24 13:25:07 configure dhcp3-common 3.1.1-1ubuntu2 3.1.1-1ubuntu2
2009-02-24 13:25:07 status unpacked dhcp3-common 3.1.1-1ubuntu2
2009-02-24 13:25:07 status half-configured dhcp3-common 3.1.1-1ubuntu2
2009-02-24 13:25:07 status installed dhcp3-common 3.1.1-1ubuntu2
2009-02-24 13:25:07 configure apt-utils 0.7.14ubuntu6 0.7.14ubuntu6
2009-02-24 13:25:07 status unpacked apt-utils 0.7.14ubuntu6
2009-02-24 13:25:07 status half-configured apt-utils 0.7.14ubuntu6
2009-02-24 13:25:07 status installed apt-utils 0.7.14ubuntu6
2009-02-24 13:25:08 configure libkrb53 1.6.dfsg.4~beta1-3 1.6.dfsg.4~beta1-3
2009-02-24 13:25:08 status unpacked libkrb53 1.6.dfsg.4~beta1-3
2009-02-24 13:25:08 status half-configured libkrb53 1.6.dfsg.4~beta1-3
2009-02-24 13:25:08 status installed libkrb53 1.6.dfsg.4~beta1-3
2009-02-24 13:25:08 configure cpio 2.9-13ubuntu2 2.9-13ubuntu2
2009-02-24 13:25:08 status unpacked cpio 2.9-13ubuntu2
2009-02-24 13:25:08 status half-configured cpio 2.9-13ubuntu2
2009-02-24 13:25:08 status installed cpio 2.9-13ubuntu2
2009-02-24 13:25:08 configure ca-certificates 20080514-0ubuntu1 20080514-0ubuntu1
2009-02-24 13:25:08 status unpacked ca-certificates 20080514-0ubuntu1
2009-02-24 13:25:08 status half-configured ca-certificates 20080514-0ubuntu1
2009-02-24 13:25:09 status installed ca-certificates 20080514-0ubuntu1
2009-02-24 13:25:09 configure vim-tiny 1:7.1.314-3ubuntu3 1:7.1.314-3ubuntu3
2009-02-24 13:25:09 status unpacked vim-tiny 1:7.1.314-3ubuntu3
2009-02-24 13:25:09 status unpacked vim-tiny 1:7.1.314-3ubuntu3
2009-02-24 13:25:09 status half-configured vim-tiny 1:7.1.314-3ubuntu3
2009-02-24 13:25:10 status installed vim-tiny 1:7.1.314-3ubuntu3
2009-02-24 13:25:10 configure less 418-1 418-1
2009-02-24 13:25:10 status unpacked less 418-1
2009-02-24 13:25:10 status half-configured less 418-1
2009-02-24 13:25:10 status installed less 418-1
2009-02-24 13:25:10 configure readline-common 5.2-3build1 5.2-3build1
2009-02-24 13:25:10 status unpacked readline-common 5.2-3build1
2009-02-24 13:25:10 status half-configured readline-common 5.2-3build1
2009-02-24 13:25:10 status installed readline-common 5.2-3build1
2009-02-24 13:25:10 configure libcap1 1:1.10-14build1 1:1.10-14build1
2009-02-24 13:25:10 status unpacked libcap1 1:1.10-14build1
2009-02-24 13:25:10 status half-configured libcap1 1:1.10-14build1
2009-02-24 13:25:10 status installed libcap1 1:1.10-14build1
2009-02-24 13:25:10 configure netcat 1.10-38 1.10-38
2009-02-24 13:25:10 status unpacked netcat 1.10-38
2009-02-24 13:25:10 status half-configured netcat 1.10-38
2009-02-24 13:25:10 status installed netcat 1.10-38
2009-02-24 13:25:10 configure liblockfile1 1.07-1 1.07-1
2009-02-24 13:25:10 status unpacked liblockfile1 1.07-1
2009-02-24 13:25:10 status half-configured liblockfile1 1.07-1
2009-02-24 13:25:10 status installed liblockfile1 1.07-1
2009-02-24 13:25:10 configure laptop-detect 0.13.6ubuntu1 0.13.6ubuntu1
2009-02-24 13:25:10 status unpacked laptop-detect 0.13.6ubuntu1
2009-02-24 13:25:10 status half-configured laptop-detect 0.13.6ubuntu1
2009-02-24 13:25:10 status installed laptop-detect 0.13.6ubuntu1
2009-02-24 13:25:10 configure libgcrypt11 1.4.1-1ubuntu1 1.4.1-1ubuntu1
2009-02-24 13:25:10 status unpacked libgcrypt11 1.4.1-1ubuntu1
2009-02-24 13:25:10 status half-configured libgcrypt11 1.4.1-1ubuntu1
2009-02-24 13:25:10 status installed libgcrypt11 1.4.1-1ubuntu1
2009-02-24 13:25:10 configure bzip2 1.0.5-0.1ubuntu1 1.0.5-0.1ubuntu1
2009-02-24 13:25:10 status unpacked bzip2 1.0.5-0.1ubuntu1
2009-02-24 13:25:10 status half-configured bzip2 1.0.5-0.1ubuntu1
2009-02-24 13:25:10 status installed bzip2 1.0.5-0.1ubuntu1
2009-02-24 13:25:10 configure whiptail 0.52.2-11.3ubuntu1 0.52.2-11.3ubuntu1
2009-02-24 13:25:10 status unpacked whiptail 0.52.2-11.3ubuntu1
2009-02-24 13:25:10 status half-configured whiptail 0.52.2-11.3ubuntu1
2009-02-24 13:25:10 status installed whiptail 0.52.2-11.3ubuntu1
2009-02-24 13:25:10 configure dhcp3-client 3.1.1-1ubuntu2 3.1.1-1ubuntu2
2009-02-24 13:25:10 status unpacked dhcp3-client 3.1.1-1ubuntu2
2009-02-24 13:25:10 status unpacked dhcp3-client 3.1.1-1ubuntu2
2009-02-24 13:25:10 status unpacked dhcp3-client 3.1.1-1ubuntu2
2009-02-24 13:25:10 status unpacked dhcp3-client 3.1.1-1ubuntu2
2009-02-24 13:25:10 status half-configured dhcp3-client 3.1.1-1ubuntu2
2009-02-24 13:25:10 status installed dhcp3-client 3.1.1-1ubuntu2
2009-02-24 13:25:10 configure libreadline5 5.2-3build1 5.2-3build1
2009-02-24 13:25:10 status unpacked libreadline5 5.2-3build1
2009-02-24 13:25:10 status half-configured libreadline5 5.2-3build1
2009-02-24 13:25:10 status installed libreadline5 5.2-3build1
2009-02-24 13:25:10 configure lockfile-progs 0.1.11ubuntu2 0.1.11ubuntu2
2009-02-24 13:25:10 status unpacked lockfile-progs 0.1.11ubuntu2
2009-02-24 13:25:10 status half-configured lockfile-progs 0.1.11ubuntu2
2009-02-24 13:25:10 status installed lockfile-progs 0.1.11ubuntu2
2009-02-24 13:25:10 configure iproute 20080417-1 20080417-1
2009-02-24 13:25:10 status unpacked iproute 20080417-1
2009-02-24 13:25:10 status unpacked iproute 20080417-1
2009-02-24 13:25:10 status unpacked iproute 20080417-1
2009-02-24 13:25:10 status unpacked iproute 20080417-1
2009-02-24 13:25:10 status unpacked iproute 20080417-1
2009-02-24 13:25:10 status unpacked iproute 20080417-1
2009-02-24 13:25:10 status unpacked iproute 20080417-1
2009-02-24 13:25:10 status half-configured iproute 20080417-1
2009-02-24 13:25:10 status installed iproute 20080417-1
2009-02-24 13:25:10 configure libgnutls26 2.4.1-1build1 2.4.1-1build1
2009-02-24 13:25:10 status unpacked libgnutls26 2.4.1-1build1
2009-02-24 13:25:10 status half-configured libgnutls26 2.4.1-1build1
2009-02-24 13:25:10 status installed libgnutls26 2.4.1-1build1
2009-02-24 13:25:10 configure python2.5 2.5.2-11.1ubuntu1 2.5.2-11.1ubuntu1
2009-02-24 13:25:10 status unpacked python2.5 2.5.2-11.1ubuntu1
2009-02-24 13:25:10 status half-configured python2.5 2.5.2-11.1ubuntu1
2009-02-24 13:25:12 status installed python2.5 2.5.2-11.1ubuntu1
2009-02-24 13:25:13 configure python 2.5.2-1ubuntu1 2.5.2-1ubuntu1
2009-02-24 13:25:13 status unpacked python 2.5.2-1ubuntu1
2009-02-24 13:25:13 status half-configured python 2.5.2-1ubuntu1
2009-02-24 13:25:13 status installed python 2.5.2-1ubuntu1
2009-02-24 13:25:13 configure lsb-release 3.2-14ubuntu2 3.2-14ubuntu2
2009-02-24 13:25:13 status unpacked lsb-release 3.2-14ubuntu2
2009-02-24 13:25:13 status half-configured lsb-release 3.2-14ubuntu2
2009-02-24 13:25:13 status installed lsb-release 3.2-14ubuntu2
2009-02-24 13:25:13 configure kbd 1.14.1-3ubuntu3 1.14.1-3ubuntu3
2009-02-24 13:25:13 status unpacked kbd 1.14.1-3ubuntu3
2009-02-24 13:25:13 status unpacked kbd 1.14.1-3ubuntu3
2009-02-24 13:25:13 status unpacked kbd 1.14.1-3ubuntu3
2009-02-24 13:25:13 status unpacked kbd 1.14.1-3ubuntu3
2009-02-24 13:25:13 status half-configured kbd 1.14.1-3ubuntu3
2009-02-24 13:25:13 status installed kbd 1.14.1-3ubuntu3
2009-02-24 13:25:13 configure libsasl2-modules 2.1.22.dfsg1-21ubuntu2 2.1.22.dfsg1-21ubuntu2
2009-02-24 13:25:13 status unpacked libsasl2-modules 2.1.22.dfsg1-21ubuntu2
2009-02-24 13:25:13 status half-configured libsasl2-modules 2.1.22.dfsg1-21ubuntu2
2009-02-24 13:25:13 status installed libsasl2-modules 2.1.22.dfsg1-21ubuntu2
2009-02-24 13:25:13 configure libsasl2-2 2.1.22.dfsg1-21ubuntu2 2.1.22.dfsg1-21ubuntu2
2009-02-24 13:25:13 status unpacked libsasl2-2 2.1.22.dfsg1-21ubuntu2
2009-02-24 13:25:13 status half-configured libsasl2-2 2.1.22.dfsg1-21ubuntu2
2009-02-24 13:25:13 status installed libsasl2-2 2.1.22.dfsg1-21ubuntu2
2009-02-24 13:25:13 configure console-terminus 4.26-1 4.26-1
2009-02-24 13:25:13 status unpacked console-terminus 4.26-1
2009-02-24 13:25:13 status half-configured console-terminus 4.26-1
2009-02-24 13:25:13 status installed console-terminus 4.26-1
2009-02-24 13:25:13 configure sysklogd 1.5-2ubuntu6 1.5-2ubuntu6
2009-02-24 13:25:13 status unpacked sysklogd 1.5-2ubuntu6
2009-02-24 13:25:13 status unpacked sysklogd 1.5-2ubuntu6
2009-02-24 13:25:13 status unpacked sysklogd 1.5-2ubuntu6
2009-02-24 13:25:13 status unpacked sysklogd 1.5-2ubuntu6
2009-02-24 13:25:13 status unpacked sysklogd 1.5-2ubuntu6
2009-02-24 13:25:13 status unpacked sysklogd 1.5-2ubuntu6
2009-02-24 13:25:13 status half-configured sysklogd 1.5-2ubuntu6
2009-02-24 13:25:13 status installed sysklogd 1.5-2ubuntu6
2009-02-24 13:25:13 configure libldap-2.4-2 2.4.11-0ubuntu6 2.4.11-0ubuntu6
2009-02-24 13:25:13 status unpacked libldap-2.4-2 2.4.11-0ubuntu6
2009-02-24 13:25:13 status unpacked libldap-2.4-2 2.4.11-0ubuntu6
2009-02-24 13:25:13 status half-configured libldap-2.4-2 2.4.11-0ubuntu6
2009-02-24 13:25:13 status installed libldap-2.4-2 2.4.11-0ubuntu6
2009-02-24 13:25:13 configure klogd 1.5-2ubuntu6 1.5-2ubuntu6
2009-02-24 13:25:13 status unpacked klogd 1.5-2ubuntu6
2009-02-24 13:25:13 status unpacked klogd 1.5-2ubuntu6
2009-02-24 13:25:13 status unpacked klogd 1.5-2ubuntu6
2009-02-24 13:25:13 status half-configured klogd 1.5-2ubuntu6
2009-02-24 13:25:13 status installed klogd 1.5-2ubuntu6
2009-02-24 13:25:13 configure udev 124-8 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status unpacked udev 124-8
2009-02-24 13:25:13 status half-configured udev 124-8
2009-02-24 13:25:14 status installed udev 124-8
2009-02-24 13:25:14 configure initramfs-tools 0.92bubuntu15 0.92bubuntu15
2009-02-24 13:25:14 status unpacked initramfs-tools 0.92bubuntu15
2009-02-24 13:25:14 status unpacked initramfs-tools 0.92bubuntu15
2009-02-24 13:25:14 status unpacked initramfs-tools 0.92bubuntu15
2009-02-24 13:25:14 status half-configured initramfs-tools 0.92bubuntu15
2009-02-24 13:25:14 status installed initramfs-tools 0.92bubuntu15
2009-02-24 13:25:14 status triggers-pending initramfs-tools 0.92bubuntu15
2009-02-24 13:25:14 configure libcurl3-gnutls 7.18.2-1ubuntu4 7.18.2-1ubuntu4
2009-02-24 13:25:14 status unpacked libcurl3-gnutls 7.18.2-1ubuntu4
2009-02-24 13:25:14 status half-configured libcurl3-gnutls 7.18.2-1ubuntu4
2009-02-24 13:25:14 status installed libcurl3-gnutls 7.18.2-1ubuntu4
2009-02-24 13:25:14 configure netbase 4.32ubuntu1 4.32ubuntu1
2009-02-24 13:25:14 status unpacked netbase 4.32ubuntu1
2009-02-24 13:25:14 status unpacked netbase 4.32ubuntu1
2009-02-24 13:25:14 status unpacked netbase 4.32ubuntu1
2009-02-24 13:25:14 status unpacked netbase 4.32ubuntu1
2009-02-24 13:25:14 status unpacked netbase 4.32ubuntu1
2009-02-24 13:25:14 status half-configured netbase 4.32ubuntu1
2009-02-24 13:25:14 status installed netbase 4.32ubuntu1
2009-02-24 13:25:14 configure ifupdown 0.6.8ubuntu12 0.6.8ubuntu12
2009-02-24 13:25:14 status unpacked ifupdown 0.6.8ubuntu12
2009-02-24 13:25:14 status unpacked ifupdown 0.6.8ubuntu12
2009-02-24 13:25:14 status unpacked ifupdown 0.6.8ubuntu12
2009-02-24 13:25:14 status half-configured ifupdown 0.6.8ubuntu12
2009-02-24 13:25:14 status installed ifupdown 0.6.8ubuntu12
2009-02-24 13:25:14 configure console-setup 1.25ubuntu3 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status unpacked console-setup 1.25ubuntu3
2009-02-24 13:25:14 status half-configured console-setup 1.25ubuntu3
2009-02-24 13:25:16 status installed console-setup 1.25ubuntu3
2009-02-24 13:25:16 configure tasksel-data 2.73ubuntu11 2.73ubuntu11
2009-02-24 13:25:16 status unpacked tasksel-data 2.73ubuntu11
2009-02-24 13:25:16 status half-configured tasksel-data 2.73ubuntu11
2009-02-24 13:25:16 status installed tasksel-data 2.73ubuntu11
2009-02-24 13:25:16 configure gnupg 1.4.9-3ubuntu1 1.4.9-3ubuntu1
2009-02-24 13:25:16 status unpacked gnupg 1.4.9-3ubuntu1
2009-02-24 13:25:16 status half-configured gnupg 1.4.9-3ubuntu1
2009-02-24 13:25:16 status installed gnupg 1.4.9-3ubuntu1
2009-02-24 13:25:16 configure ubuntu-keyring 2008.03.04 2008.03.04
2009-02-24 13:25:16 status unpacked ubuntu-keyring 2008.03.04
2009-02-24 13:25:16 status half-configured ubuntu-keyring 2008.03.04
2009-02-24 13:25:16 status installed ubuntu-keyring 2008.03.04
2009-02-24 13:25:16 configure ntpdate 1:4.2.4p4+dfsg-6ubuntu2 1:4.2.4p4+dfsg-6ubuntu2
2009-02-24 13:25:16 status unpacked ntpdate 1:4.2.4p4+dfsg-6ubuntu2
2009-02-24 13:25:16 status unpacked ntpdate 1:4.2.4p4+dfsg-6ubuntu2
2009-02-24 13:25:16 status unpacked ntpdate 1:4.2.4p4+dfsg-6ubuntu2
2009-02-24 13:25:16 status unpacked ntpdate 1:4.2.4p4+dfsg-6ubuntu2
2009-02-24 13:25:16 status unpacked ntpdate 1:4.2.4p4+dfsg-6ubuntu2
2009-02-24 13:25:16 status half-configured ntpdate 1:4.2.4p4+dfsg-6ubuntu2
2009-02-24 13:25:16 status installed ntpdate 1:4.2.4p4+dfsg-6ubuntu2
2009-02-24 13:25:16 configure tasksel 2.73ubuntu11 2.73ubuntu11
2009-02-24 13:25:16 status unpacked tasksel 2.73ubuntu11
2009-02-24 13:25:16 status half-configured tasksel 2.73ubuntu11
2009-02-24 13:25:16 status installed tasksel 2.73ubuntu11
2009-02-24 13:25:16 configure ubuntu-minimal 1.124 1.124
2009-02-24 13:25:16 status unpacked ubuntu-minimal 1.124
2009-02-24 13:25:16 status half-configured ubuntu-minimal 1.124
2009-02-24 13:25:16 status installed ubuntu-minimal 1.124
2009-02-24 13:25:16 trigproc libc6 2.8~20080505-0ubuntu7 2.8~20080505-0ubuntu7
2009-02-24 13:25:16 status half-configured libc6 2.8~20080505-0ubuntu7
2009-02-24 13:25:16 status installed libc6 2.8~20080505-0ubuntu7
2009-02-24 13:25:16 trigproc initramfs-tools 0.92bubuntu15 0.92bubuntu15
2009-02-24 13:25:16 status half-configured initramfs-tools 0.92bubuntu15
2009-02-24 13:25:16 status installed initramfs-tools 0.92bubuntu15
2009-02-24 16:25:36 startup archives unpack
2009-02-24 16:25:36 install installation-report <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.35ubuntu2
2009-02-24 16:25:36 status half-installed installation-report 2.35ubuntu2
2009-02-24 16:25:36 status unpacked installation-report 2.35ubuntu2
2009-02-24 16:25:36 status unpacked installation-report 2.35ubuntu2
2009-02-24 16:25:36 startup packages configure
2009-02-24 16:25:36 configure installation-report 2.35ubuntu2 2.35ubuntu2
2009-02-24 16:25:36 status unpacked installation-report 2.35ubuntu2
2009-02-24 16:25:36 status half-configured installation-report 2.35ubuntu2
2009-02-24 16:25:36 status installed installation-report 2.35ubuntu2
2009-02-24 16:25:44 startup archives unpack
2009-02-24 16:25:44 install linux-image-2.6.27-7-server <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.6.27-7.14
2009-02-24 16:25:44 status half-installed linux-image-2.6.27-7-server 2.6.27-7.14
2009-02-24 16:25:55 status unpacked linux-image-2.6.27-7-server 2.6.27-7.14
2009-02-24 16:25:57 status unpacked linux-image-2.6.27-7-server 2.6.27-7.14
2009-02-24 16:25:57 install linux-firmware <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.2
2009-02-24 16:25:57 status half-installed linux-firmware 1.2
2009-02-24 16:25:58 status unpacked linux-firmware 1.2
2009-02-24 16:25:58 status unpacked linux-firmware 1.2
2009-02-24 16:25:58 install linux-image-server <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.6.27.7.11
2009-02-24 16:25:58 status half-installed linux-image-server 2.6.27.7.11
2009-02-24 16:25:58 status unpacked linux-image-server 2.6.27.7.11
2009-02-24 16:25:58 status unpacked linux-image-server 2.6.27.7.11
2009-02-24 16:25:58 install linux-server <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.6.27.7.11
2009-02-24 16:25:58 status half-installed linux-server 2.6.27.7.11
2009-02-24 16:25:58 status unpacked linux-server 2.6.27.7.11
2009-02-24 16:25:58 status unpacked linux-server 2.6.27.7.11
2009-02-24 16:25:59 startup packages configure
2009-02-24 16:25:59 configure linux-image-2.6.27-7-server 2.6.27-7.14 2.6.27-7.14
2009-02-24 16:25:59 status unpacked linux-image-2.6.27-7-server 2.6.27-7.14
2009-02-24 16:25:59 status half-configured linux-image-2.6.27-7-server 2.6.27-7.14
2009-02-24 16:26:09 status installed linux-image-2.6.27-7-server 2.6.27-7.14
2009-02-24 16:26:09 configure linux-firmware 1.2 1.2
2009-02-24 16:26:09 status unpacked linux-firmware 1.2
2009-02-24 16:26:09 status half-configured linux-firmware 1.2
2009-02-24 16:26:09 status installed linux-firmware 1.2
2009-02-24 16:26:09 configure linux-image-server 2.6.27.7.11 2.6.27.7.11
2009-02-24 16:26:09 status unpacked linux-image-server 2.6.27.7.11
2009-02-24 16:26:09 status half-configured linux-image-server 2.6.27.7.11
2009-02-24 16:26:09 status installed linux-image-server 2.6.27.7.11
2009-02-24 16:26:09 configure linux-server 2.6.27.7.11 2.6.27.7.11
2009-02-24 16:26:09 status unpacked linux-server 2.6.27.7.11
2009-02-24 16:26:09 status half-configured linux-server 2.6.27.7.11
2009-02-24 16:26:09 status installed linux-server 2.6.27.7.11
2009-02-24 16:26:13 startup archives unpack
2009-02-24 16:26:13 install usbutils <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.73-8ubuntu3
2009-02-24 16:26:13 status half-installed usbutils 0.73-8ubuntu3
2009-02-24 16:26:13 status unpacked usbutils 0.73-8ubuntu3
2009-02-24 16:26:13 status unpacked usbutils 0.73-8ubuntu3
2009-02-24 16:26:13 startup packages configure
2009-02-24 16:26:13 configure usbutils 0.73-8ubuntu3 0.73-8ubuntu3
2009-02-24 16:26:13 status unpacked usbutils 0.73-8ubuntu3
2009-02-24 16:26:13 status half-configured usbutils 0.73-8ubuntu3
2009-02-24 16:26:13 status installed usbutils 0.73-8ubuntu3
2009-02-24 16:28:53 startup packages configure
2009-02-24 16:28:54 startup packages configure
2009-02-24 16:30:40 startup archives unpack
2009-02-24 16:30:40 install libfuse2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.7.3-4ubuntu2
2009-02-24 16:30:40 status half-installed libfuse2 2.7.3-4ubuntu2
2009-02-24 16:30:40 status unpacked libfuse2 2.7.3-4ubuntu2
2009-02-24 16:30:40 status unpacked libfuse2 2.7.3-4ubuntu2
2009-02-24 16:30:40 install fuse-utils <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.7.3-4ubuntu2
2009-02-24 16:30:40 status half-installed fuse-utils 2.7.3-4ubuntu2
2009-02-24 16:30:40 status unpacked fuse-utils 2.7.3-4ubuntu2
2009-02-24 16:30:40 status unpacked fuse-utils 2.7.3-4ubuntu2
2009-02-24 16:30:40 install libntfs-3g28 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:1.2506-1ubuntu2
2009-02-24 16:30:40 status half-installed libntfs-3g28 1:1.2506-1ubuntu2
2009-02-24 16:30:40 status unpacked libntfs-3g28 1:1.2506-1ubuntu2
2009-02-24 16:30:40 status unpacked libntfs-3g28 1:1.2506-1ubuntu2
2009-02-24 16:30:40 startup packages configure
2009-02-24 16:30:40 configure libfuse2 2.7.3-4ubuntu2 2.7.3-4ubuntu2
2009-02-24 16:30:40 status unpacked libfuse2 2.7.3-4ubuntu2
2009-02-24 16:30:40 status half-configured libfuse2 2.7.3-4ubuntu2
2009-02-24 16:30:40 status installed libfuse2 2.7.3-4ubuntu2
2009-02-24 16:30:40 status triggers-pending libc6 2.8~20080505-0ubuntu7
2009-02-24 16:30:40 configure fuse-utils 2.7.3-4ubuntu2 2.7.3-4ubuntu2
2009-02-24 16:30:40 status unpacked fuse-utils 2.7.3-4ubuntu2
2009-02-24 16:30:40 status unpacked fuse-utils 2.7.3-4ubuntu2
2009-02-24 16:30:40 status unpacked fuse-utils 2.7.3-4ubuntu2
2009-02-24 16:30:40 status unpacked fuse-utils 2.7.3-4ubuntu2
2009-02-24 16:30:40 status half-configured fuse-utils 2.7.3-4ubuntu2
2009-02-24 16:30:40 status installed fuse-utils 2.7.3-4ubuntu2
2009-02-24 16:30:40 trigproc libc6 2.8~20080505-0ubuntu7 2.8~20080505-0ubuntu7
2009-02-24 16:30:40 status half-configured libc6 2.8~20080505-0ubuntu7
2009-02-24 16:30:41 status installed libc6 2.8~20080505-0ubuntu7
2009-02-24 16:30:41 startup archives unpack
2009-02-24 16:30:41 install ntfs-3g <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:1.2506-1ubuntu2
2009-02-24 16:30:41 status half-installed ntfs-3g 1:1.2506-1ubuntu2
2009-02-24 16:30:41 status unpacked ntfs-3g 1:1.2506-1ubuntu2
2009-02-24 16:30:41 status unpacked ntfs-3g 1:1.2506-1ubuntu2
2009-02-24 16:30:41 install x11-common <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:7.4~5ubuntu3
2009-02-24 16:30:41 status half-installed x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:42 status unpacked x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:42 status unpacked x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:42 install libxau6 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:1.0.3-3
2009-02-24 16:30:42 status half-installed libxau6 1:1.0.3-3
2009-02-24 16:30:42 status unpacked libxau6 1:1.0.3-3
2009-02-24 16:30:42 status unpacked libxau6 1:1.0.3-3
2009-02-24 16:30:42 install libxdmcp6 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:1.0.2-3
2009-02-24 16:30:42 status half-installed libxdmcp6 1:1.0.2-3
2009-02-24 16:30:42 status unpacked libxdmcp6 1:1.0.2-3
2009-02-24 16:30:42 status unpacked libxdmcp6 1:1.0.2-3
2009-02-24 16:30:42 install libxcb1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.1-1.1
2009-02-24 16:30:42 status half-installed libxcb1 1.1-1.1
2009-02-24 16:30:42 status unpacked libxcb1 1.1-1.1
2009-02-24 16:30:42 status unpacked libxcb1 1.1-1.1
2009-02-24 16:30:42 install libxcb-xlib0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.1-1.1
2009-02-24 16:30:42 status half-installed libxcb-xlib0 1.1-1.1
2009-02-24 16:30:42 status unpacked libxcb-xlib0 1.1-1.1
2009-02-24 16:30:42 status unpacked libxcb-xlib0 1.1-1.1
2009-02-24 16:30:42 install libx11-data <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2:1.1.5-2ubuntu1
2009-02-24 16:30:42 status half-installed libx11-data 2:1.1.5-2ubuntu1
2009-02-24 16:30:42 status unpacked libx11-data 2:1.1.5-2ubuntu1
2009-02-24 16:30:42 status unpacked libx11-data 2:1.1.5-2ubuntu1
2009-02-24 16:30:42 install libx11-6 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2:1.1.5-2ubuntu1
2009-02-24 16:30:42 status half-installed libx11-6 2:1.1.5-2ubuntu1
2009-02-24 16:30:42 status unpacked libx11-6 2:1.1.5-2ubuntu1
2009-02-24 16:30:42 status unpacked libx11-6 2:1.1.5-2ubuntu1
2009-02-24 16:30:42 install libxext6 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2:1.0.4-1
2009-02-24 16:30:42 status half-installed libxext6 2:1.0.4-1
2009-02-24 16:30:42 status unpacked libxext6 2:1.0.4-1
2009-02-24 16:30:42 status unpacked libxext6 2:1.0.4-1
2009-02-24 16:30:42 install libxmuu1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2:1.0.4-1
2009-02-24 16:30:42 status half-installed libxmuu1 2:1.0.4-1
2009-02-24 16:30:42 status unpacked libxmuu1 2:1.0.4-1
2009-02-24 16:30:42 status unpacked libxmuu1 2:1.0.4-1
2009-02-24 16:30:43 startup packages configure
2009-02-24 16:30:43 configure x11-common 1:7.4~5ubuntu3 1:7.4~5ubuntu3
2009-02-24 16:30:43 status unpacked x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:43 status unpacked x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:43 status unpacked x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:43 status unpacked x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:43 status unpacked x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:43 status unpacked x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:43 status unpacked x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:43 status unpacked x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:43 status unpacked x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:43 status unpacked x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:43 status unpacked x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:43 status unpacked x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:43 status unpacked x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:43 status unpacked x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:43 status unpacked x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:43 status half-configured x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:43 status installed x11-common 1:7.4~5ubuntu3
2009-02-24 16:30:44 startup archives unpack
2009-02-24 16:30:44 install xauth <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:1.0.3-2
2009-02-24 16:30:44 status half-installed xauth 1:1.0.3-2
2009-02-24 16:30:44 status unpacked xauth 1:1.0.3-2
2009-02-24 16:30:44 status unpacked xauth 1:1.0.3-2
2009-02-24 16:30:44 install python-support <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.8.4
2009-02-24 16:30:44 status half-installed python-support 0.8.4
2009-02-24 16:30:44 status unpacked python-support 0.8.4
2009-02-24 16:30:44 status unpacked python-support 0.8.4
2009-02-24 16:30:44 install libffi5 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 3.0.5-4
2009-02-24 16:30:44 status half-installed libffi5 3.0.5-4
2009-02-24 16:30:44 status unpacked libffi5 3.0.5-4
2009-02-24 16:30:44 status unpacked libffi5 3.0.5-4
2009-02-24 16:30:44 install libglib2.0-0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.18.2-0ubuntu1
2009-02-24 16:30:44 status half-installed libglib2.0-0 2.18.2-0ubuntu1
2009-02-24 16:30:44 status unpacked libglib2.0-0 2.18.2-0ubuntu1
2009-02-24 16:30:44 status unpacked libglib2.0-0 2.18.2-0ubuntu1
2009-02-24 16:30:44 install python-gobject <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.15.3-0ubuntu5
2009-02-24 16:30:44 status half-installed python-gobject 2.15.3-0ubuntu5
2009-02-24 16:30:44 status unpacked python-gobject 2.15.3-0ubuntu5
2009-02-24 16:30:44 status unpacked python-gobject 2.15.3-0ubuntu5
2009-02-24 16:30:44 install python-central <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.6.7ubuntu1
2009-02-24 16:30:44 status half-installed python-central 0.6.7ubuntu1
2009-02-24 16:30:44 status unpacked python-central 0.6.7ubuntu1
2009-02-24 16:30:44 status unpacked python-central 0.6.7ubuntu1
2009-02-24 16:30:44 install python-twisted-bin <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 8.1.0-4
2009-02-24 16:30:44 status half-installed python-twisted-bin 8.1.0-4
2009-02-24 16:30:45 status unpacked python-twisted-bin 8.1.0-4
2009-02-24 16:30:45 status unpacked python-twisted-bin 8.1.0-4
2009-02-24 16:30:45 install python-zopeinterface <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 3.3.1-7build1
2009-02-24 16:30:45 status half-installed python-zopeinterface 3.3.1-7build1
2009-02-24 16:30:45 status unpacked python-zopeinterface 3.3.1-7build1
2009-02-24 16:30:45 status unpacked python-zopeinterface 3.3.1-7build1
2009-02-24 16:30:45 install python-twisted-core <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 8.1.0-4
2009-02-24 16:30:45 status half-installed python-twisted-core 8.1.0-4
2009-02-24 16:30:45 status unpacked python-twisted-core 8.1.0-4
2009-02-24 16:30:45 status unpacked python-twisted-core 8.1.0-4
2009-02-24 16:30:45 install libdbus-1-3 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.2.4-0ubuntu1
2009-02-24 16:30:45 status half-installed libdbus-1-3 1.2.4-0ubuntu1
2009-02-24 16:30:45 status unpacked libdbus-1-3 1.2.4-0ubuntu1
2009-02-24 16:30:45 status unpacked libdbus-1-3 1.2.4-0ubuntu1
2009-02-24 16:30:46 install libdbus-glib-1-2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.76-1
2009-02-24 16:30:46 status half-installed libdbus-glib-1-2 0.76-1
2009-02-24 16:30:46 status unpacked libdbus-glib-1-2 0.76-1
2009-02-24 16:30:46 status unpacked libdbus-glib-1-2 0.76-1
2009-02-24 16:30:46 install python-dbus <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.82.4-2
2009-02-24 16:30:46 status half-installed python-dbus 0.82.4-2
2009-02-24 16:30:46 status unpacked python-dbus 0.82.4-2
2009-02-24 16:30:46 status unpacked python-dbus 0.82.4-2
2009-02-24 16:30:46 install libgdbm3 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.8.3-3
2009-02-24 16:30:46 status half-installed libgdbm3 1.8.3-3
2009-02-24 16:30:46 status unpacked libgdbm3 1.8.3-3
2009-02-24 16:30:46 status unpacked libgdbm3 1.8.3-3
2009-02-24 16:30:46 install perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 5.10.0-11.1ubuntu2
2009-02-24 16:30:46 status half-installed perl 5.10.0-11.1ubuntu2
2009-02-24 16:30:47 status unpacked perl 5.10.0-11.1ubuntu2
2009-02-24 16:30:47 status unpacked perl 5.10.0-11.1ubuntu2
2009-02-24 16:30:47 install perl-modules <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 5.10.0-11.1ubuntu2
2009-02-24 16:30:47 status half-installed perl-modules 5.10.0-11.1ubuntu2
2009-02-24 16:30:48 status unpacked perl-modules 5.10.0-11.1ubuntu2
2009-02-24 16:30:48 status unpacked perl-modules 5.10.0-11.1ubuntu2
2009-02-24 16:30:48 install python-gdbm <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.5.2-1ubuntu1
2009-02-24 16:30:48 status half-installed python-gdbm 2.5.2-1ubuntu1
2009-02-24 16:30:48 status unpacked python-gdbm 2.5.2-1ubuntu1
2009-02-24 16:30:48 status unpacked python-gdbm 2.5.2-1ubuntu1
2009-02-24 16:30:48 install cron <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 3.0pl1-104+ubuntu5
2009-02-24 16:30:48 status half-installed cron 3.0pl1-104+ubuntu5
2009-02-24 16:30:48 status unpacked cron 3.0pl1-104+ubuntu5
2009-02-24 16:30:48 status unpacked cron 3.0pl1-104+ubuntu5
2009-02-24 16:30:48 install update-motd <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.8
2009-02-24 16:30:48 status half-installed update-motd 1.8
2009-02-24 16:30:48 status unpacked update-motd 1.8
2009-02-24 16:30:48 status unpacked update-motd 1.8
2009-02-24 16:30:49 startup packages configure
2009-02-24 16:30:49 configure python-support 0.8.4 0.8.4
2009-02-24 16:30:49 status unpacked python-support 0.8.4
2009-02-24 16:30:49 status half-configured python-support 0.8.4
2009-02-24 16:30:49 status installed python-support 0.8.4
2009-02-24 16:30:49 configure libffi5 3.0.5-4 3.0.5-4
2009-02-24 16:30:49 status unpacked libffi5 3.0.5-4
2009-02-24 16:30:49 status half-configured libffi5 3.0.5-4
2009-02-24 16:30:49 status installed libffi5 3.0.5-4
2009-02-24 16:30:49 status triggers-pending libc6 2.8~20080505-0ubuntu7
2009-02-24 16:30:49 configure libglib2.0-0 2.18.2-0ubuntu1 2.18.2-0ubuntu1
2009-02-24 16:30:49 status unpacked libglib2.0-0 2.18.2-0ubuntu1
2009-02-24 16:30:49 status half-configured libglib2.0-0 2.18.2-0ubuntu1
2009-02-24 16:30:49 status installed libglib2.0-0 2.18.2-0ubuntu1
2009-02-24 16:30:49 configure python-gobject 2.15.3-0ubuntu5 2.15.3-0ubuntu5
2009-02-24 16:30:49 status unpacked python-gobject 2.15.3-0ubuntu5
2009-02-24 16:30:49 status half-configured python-gobject 2.15.3-0ubuntu5
2009-02-24 16:30:49 status installed python-gobject 2.15.3-0ubuntu5
2009-02-24 16:30:49 status triggers-pending python-support 0.8.4
2009-02-24 16:30:49 trigproc libc6 2.8~20080505-0ubuntu7 2.8~20080505-0ubuntu7
2009-02-24 16:30:49 status half-configured libc6 2.8~20080505-0ubuntu7
2009-02-24 16:30:49 status installed libc6 2.8~20080505-0ubuntu7
2009-02-24 16:30:49 trigproc python-support 0.8.4 0.8.4
2009-02-24 16:30:49 status half-configured python-support 0.8.4
2009-02-24 16:30:49 status installed python-support 0.8.4
2009-02-24 16:30:50 startup archives unpack
2009-02-24 16:30:50 install landscape-common <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.0.23-0ubuntu0.8.10.1
2009-02-24 16:30:50 status half-installed landscape-common 1.0.23-0ubuntu0.8.10.1
2009-02-24 16:30:50 status unpacked landscape-common 1.0.23-0ubuntu0.8.10.1
2009-02-24 16:30:50 status unpacked landscape-common 1.0.23-0ubuntu0.8.10.1
2009-02-24 16:30:50 install ubuntu-serverguide <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 8.10.2
2009-02-24 16:30:50 status half-installed ubuntu-serverguide 8.10.2
2009-02-24 16:30:50 status unpacked ubuntu-serverguide 8.10.2
2009-02-24 16:30:50 status unpacked ubuntu-serverguide 8.10.2
2009-02-24 16:30:50 install apparmor <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.3+1289-0ubuntu4
2009-02-24 16:30:50 status half-installed apparmor 2.3+1289-0ubuntu4
2009-02-24 16:30:50 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:30:50 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:30:50 install libterm-readkey-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.30-3ubuntu2
2009-02-24 16:30:50 status half-installed libterm-readkey-perl 2.30-3ubuntu2
2009-02-24 16:30:50 status unpacked libterm-readkey-perl 2.30-3ubuntu2
2009-02-24 16:30:50 status unpacked libterm-readkey-perl 2.30-3ubuntu2
2009-02-24 16:30:50 install libhtml-tagset-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 3.20-2
2009-02-24 16:30:50 status half-installed libhtml-tagset-perl 3.20-2
2009-02-24 16:30:50 status unpacked libhtml-tagset-perl 3.20-2
2009-02-24 16:30:50 status unpacked libhtml-tagset-perl 3.20-2
2009-02-24 16:30:50 install liburi-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.35.dfsg.1-1
2009-02-24 16:30:50 status half-installed liburi-perl 1.35.dfsg.1-1
2009-02-24 16:30:50 status unpacked liburi-perl 1.35.dfsg.1-1
2009-02-24 16:30:50 status unpacked liburi-perl 1.35.dfsg.1-1
2009-02-24 16:30:51 install libhtml-parser-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 3.56-1ubuntu2
2009-02-24 16:30:51 status half-installed libhtml-parser-perl 3.56-1ubuntu2
2009-02-24 16:30:51 status unpacked libhtml-parser-perl 3.56-1ubuntu2
2009-02-24 16:30:51 status unpacked libhtml-parser-perl 3.56-1ubuntu2
2009-02-24 16:30:51 install libhtml-tree-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 3.23-1
2009-02-24 16:30:51 status half-installed libhtml-tree-perl 3.23-1
2009-02-24 16:30:51 status unpacked libhtml-tree-perl 3.23-1
2009-02-24 16:30:51 status unpacked libhtml-tree-perl 3.23-1
2009-02-24 16:30:51 install libwww-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 5.812-1
2009-02-24 16:30:51 status half-installed libwww-perl 5.812-1
2009-02-24 16:30:51 status unpacked libwww-perl 5.812-1
2009-02-24 16:30:51 status unpacked libwww-perl 5.812-1
2009-02-24 16:30:51 install libexpat1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.0.1-4
2009-02-24 16:30:51 status half-installed libexpat1 2.0.1-4
2009-02-24 16:30:51 status unpacked libexpat1 2.0.1-4
2009-02-24 16:30:51 status unpacked libexpat1 2.0.1-4
2009-02-24 16:30:51 install libxml-parser-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.36-1.1build2
2009-02-24 16:30:51 status half-installed libxml-parser-perl 2.36-1.1build2
2009-02-24 16:30:51 status unpacked libxml-parser-perl 2.36-1.1build2
2009-02-24 16:30:51 status unpacked libxml-parser-perl 2.36-1.1build2
2009-02-24 16:30:51 install librpc-xml-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.60-3
2009-02-24 16:30:51 status half-installed librpc-xml-perl 0.60-3
2009-02-24 16:30:51 status unpacked librpc-xml-perl 0.60-3
2009-02-24 16:30:51 status unpacked librpc-xml-perl 0.60-3
2009-02-24 16:30:51 install libapparmor1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.3+1289-0ubuntu4
2009-02-24 16:30:51 status half-installed libapparmor1 2.3+1289-0ubuntu4
2009-02-24 16:30:51 status unpacked libapparmor1 2.3+1289-0ubuntu4
2009-02-24 16:30:51 status unpacked libapparmor1 2.3+1289-0ubuntu4
2009-02-24 16:30:51 install libapparmor-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.3+1289-0ubuntu4
2009-02-24 16:30:51 status half-installed libapparmor-perl 2.3+1289-0ubuntu4
2009-02-24 16:30:51 status unpacked libapparmor-perl 2.3+1289-0ubuntu4
2009-02-24 16:30:51 status unpacked libapparmor-perl 2.3+1289-0ubuntu4
2009-02-24 16:30:51 install apparmor-utils <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.3+1289-0ubuntu4
2009-02-24 16:30:51 status half-installed apparmor-utils 2.3+1289-0ubuntu4
2009-02-24 16:30:51 status unpacked apparmor-utils 2.3+1289-0ubuntu4
2009-02-24 16:30:51 status unpacked apparmor-utils 2.3+1289-0ubuntu4
2009-02-24 16:30:51 install libsigc++-2.0-0c2a <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.0.18-2
2009-02-24 16:30:51 status half-installed libsigc++-2.0-0c2a 2.0.18-2
2009-02-24 16:30:51 status unpacked libsigc++-2.0-0c2a 2.0.18-2
2009-02-24 16:30:51 status unpacked libsigc++-2.0-0c2a 2.0.18-2
2009-02-24 16:30:52 install libcwidget3 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.5.12-1ubuntu1
2009-02-24 16:30:52 status half-installed libcwidget3 0.5.12-1ubuntu1
2009-02-24 16:30:52 status unpacked libcwidget3 0.5.12-1ubuntu1
2009-02-24 16:30:52 status unpacked libcwidget3 0.5.12-1ubuntu1
2009-02-24 16:30:52 install libxapian15 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.0.7-4
2009-02-24 16:30:52 status half-installed libxapian15 1.0.7-4
2009-02-24 16:30:52 status unpacked libxapian15 1.0.7-4
2009-02-24 16:30:52 status unpacked libxapian15 1.0.7-4
2009-02-24 16:30:52 install libept0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.5.26
2009-02-24 16:30:52 status half-installed libept0 0.5.26
2009-02-24 16:30:52 status unpacked libept0 0.5.26
2009-02-24 16:30:52 status unpacked libept0 0.5.26
2009-02-24 16:30:52 install aptitude <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.4.11.3-1ubuntu3
2009-02-24 16:30:52 status half-installed aptitude 0.4.11.3-1ubuntu3
2009-02-24 16:30:52 status unpacked aptitude 0.4.11.3-1ubuntu3
2009-02-24 16:30:52 status unpacked aptitude 0.4.11.3-1ubuntu3
2009-02-24 16:30:52 install at <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 3.1.10.1ubuntu3
2009-02-24 16:30:52 status half-installed at 3.1.10.1ubuntu3
2009-02-24 16:30:52 status unpacked at 3.1.10.1ubuntu3
2009-02-24 16:30:52 status unpacked at 3.1.10.1ubuntu3
2009-02-24 16:30:52 install ucf <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 3.0010
2009-02-24 16:30:52 status half-installed ucf 3.0010
2009-02-24 16:30:52 status unpacked ucf 3.0010
2009-02-24 16:30:52 status unpacked ucf 3.0010
2009-02-24 16:30:52 install bash-completion <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 20060301-4ubuntu1
2009-02-24 16:30:52 status half-installed bash-completion 20060301-4ubuntu1
2009-02-24 16:30:52 status unpacked bash-completion 20060301-4ubuntu1
2009-02-24 16:30:52 status unpacked bash-completion 20060301-4ubuntu1
2009-02-24 16:30:52 install libcap2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.10-1
2009-02-24 16:30:52 status half-installed libcap2 2.10-1
2009-02-24 16:30:52 status unpacked libcap2 2.10-1
2009-02-24 16:30:52 status unpacked libcap2 2.10-1
2009-02-24 16:30:52 install libxml2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.6.32.dfsg-4ubuntu1
2009-02-24 16:30:52 status half-installed libxml2 2.6.32.dfsg-4ubuntu1
2009-02-24 16:30:53 status unpacked libxml2 2.6.32.dfsg-4ubuntu1
2009-02-24 16:30:53 status unpacked libxml2 2.6.32.dfsg-4ubuntu1
2009-02-24 16:30:53 install libisc44 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status half-installed libisc44 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status unpacked libisc44 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status unpacked libisc44 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 install libdns43 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status half-installed libdns43 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status unpacked libdns43 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status unpacked libdns43 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 install libisccc40 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status half-installed libisccc40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status unpacked libisccc40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status unpacked libisccc40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 install libisccfg40 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status half-installed libisccfg40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status unpacked libisccfg40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status unpacked libisccfg40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 install libbind9-40 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status half-installed libbind9-40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status unpacked libbind9-40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status unpacked libbind9-40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 install liblwres40 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status half-installed liblwres40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status unpacked liblwres40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status unpacked liblwres40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 install bind9-host <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status half-installed bind9-host 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status unpacked bind9-host 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 status unpacked bind9-host 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:53 install libgmp3c2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2:4.2.2+dfsg-3ubuntu1
2009-02-24 16:30:53 status half-installed libgmp3c2 2:4.2.2+dfsg-3ubuntu1
2009-02-24 16:30:53 status unpacked libgmp3c2 2:4.2.2+dfsg-3ubuntu1
2009-02-24 16:30:53 status unpacked libgmp3c2 2:4.2.2+dfsg-3ubuntu1
2009-02-24 16:30:53 install libmpfr1ldbl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.3.2.dfsg.1-1ubuntu1
2009-02-24 16:30:53 status half-installed libmpfr1ldbl 2.3.2.dfsg.1-1ubuntu1
2009-02-24 16:30:53 status unpacked libmpfr1ldbl 2.3.2.dfsg.1-1ubuntu1
2009-02-24 16:30:53 status unpacked libmpfr1ldbl 2.3.2.dfsg.1-1ubuntu1
2009-02-24 16:30:53 install cpp-4.3 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 4.3.2-1ubuntu11
2009-02-24 16:30:53 status half-installed cpp-4.3 4.3.2-1ubuntu11
2009-02-24 16:30:54 status unpacked cpp-4.3 4.3.2-1ubuntu11
2009-02-24 16:30:54 status unpacked cpp-4.3 4.3.2-1ubuntu11
2009-02-24 16:30:54 install cpp <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 4:4.3.1-1ubuntu2
2009-02-24 16:30:54 status half-installed cpp 4:4.3.1-1ubuntu2
2009-02-24 16:30:54 status unpacked cpp 4:4.3.1-1ubuntu2
2009-02-24 16:30:54 status unpacked cpp 4:4.3.1-1ubuntu2
2009-02-24 16:30:54 install bsdmainutils <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 6.1.10ubuntu2
2009-02-24 16:30:54 status half-installed bsdmainutils 6.1.10ubuntu2
2009-02-24 16:30:54 status unpacked bsdmainutils 6.1.10ubuntu2
2009-02-24 16:30:54 status unpacked bsdmainutils 6.1.10ubuntu2
2009-02-24 16:30:54 install python-apt <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.7.7.1ubuntu4
2009-02-24 16:30:54 status half-installed python-apt 0.7.7.1ubuntu4
2009-02-24 16:30:54 status unpacked python-apt 0.7.7.1ubuntu4
2009-02-24 16:30:54 status unpacked python-apt 0.7.7.1ubuntu4
2009-02-24 16:30:54 install command-not-found-data <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.2.26ubuntu1
2009-02-24 16:30:54 status half-installed command-not-found-data 0.2.26ubuntu1
2009-02-24 16:30:54 status unpacked command-not-found-data 0.2.26ubuntu1
2009-02-24 16:30:54 status unpacked command-not-found-data 0.2.26ubuntu1
2009-02-24 16:30:54 install command-not-found <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.2.26ubuntu1
2009-02-24 16:30:54 status half-installed command-not-found 0.2.26ubuntu1
2009-02-24 16:30:54 status unpacked command-not-found 0.2.26ubuntu1
2009-02-24 16:30:54 status unpacked command-not-found 0.2.26ubuntu1
2009-02-24 16:30:54 install dnsutils <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:54 status half-installed dnsutils 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:54 status unpacked dnsutils 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:54 status unpacked dnsutils 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:30:54 install dosfstools <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.11-5
2009-02-24 16:30:54 status half-installed dosfstools 2.11-5
2009-02-24 16:30:54 status unpacked dosfstools 2.11-5
2009-02-24 16:30:54 status unpacked dosfstools 2.11-5
2009-02-24 16:30:55 install ed <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.7-1ubuntu1
2009-02-24 16:30:55 status half-installed ed 0.7-1ubuntu1
2009-02-24 16:30:55 status unpacked ed 0.7-1ubuntu1
2009-02-24 16:30:55 status unpacked ed 0.7-1ubuntu1
2009-02-24 16:30:55 install friendly-recovery <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.2.6
2009-02-24 16:30:55 status half-installed friendly-recovery 0.2.6
2009-02-24 16:30:55 status unpacked friendly-recovery 0.2.6
2009-02-24 16:30:55 status unpacked friendly-recovery 0.2.6
2009-02-24 16:30:55 install ftp <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.17-18
2009-02-24 16:30:55 status half-installed ftp 0.17-18
2009-02-24 16:30:55 status unpacked ftp 0.17-18
2009-02-24 16:30:55 status unpacked ftp 0.17-18
2009-02-24 16:30:55 install gettext-base <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.17-3ubuntu2
2009-02-24 16:30:55 status half-installed gettext-base 0.17-3ubuntu2
2009-02-24 16:30:55 status unpacked gettext-base 0.17-3ubuntu2
2009-02-24 16:30:55 status unpacked gettext-base 0.17-3ubuntu2
2009-02-24 16:30:55 install groff-base <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.18.1.1-20
2009-02-24 16:30:55 status half-installed groff-base 1.18.1.1-20
2009-02-24 16:30:55 status unpacked groff-base 1.18.1.1-20
2009-02-24 16:30:55 status unpacked groff-base 1.18.1.1-20
2009-02-24 16:30:55 install hdparm <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 8.9-1ubuntu1
2009-02-24 16:30:55 status half-installed hdparm 8.9-1ubuntu1
2009-02-24 16:30:55 status unpacked hdparm 8.9-1ubuntu1
2009-02-24 16:30:55 status unpacked hdparm 8.9-1ubuntu1
2009-02-24 16:30:56 install info <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 4.11.dfsg.1-4
2009-02-24 16:30:56 status half-installed info 4.11.dfsg.1-4
2009-02-24 16:30:56 status unpacked info 4.11.dfsg.1-4
2009-02-24 16:30:56 status unpacked info 4.11.dfsg.1-4
2009-02-24 16:30:56 install iptables <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.4.0-4ubuntu2
2009-02-24 16:30:56 status half-installed iptables 1.4.0-4ubuntu2
2009-02-24 16:30:56 status unpacked iptables 1.4.0-4ubuntu2
2009-02-24 16:30:56 status unpacked iptables 1.4.0-4ubuntu2
2009-02-24 16:30:56 install iputils-arping <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 3:20071127-1
2009-02-24 16:30:56 status half-installed iputils-arping 3:20071127-1
2009-02-24 16:30:56 status unpacked iputils-arping 3:20071127-1
2009-02-24 16:30:56 status unpacked iputils-arping 3:20071127-1
2009-02-24 16:30:56 install iputils-tracepath <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 3:20071127-1
2009-02-24 16:30:56 status half-installed iputils-tracepath 3:20071127-1
2009-02-24 16:30:56 status unpacked iputils-tracepath 3:20071127-1
2009-02-24 16:30:56 status unpacked iputils-tracepath 3:20071127-1
2009-02-24 16:30:56 install libclass-accessor-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.31-2
2009-02-24 16:30:56 status half-installed libclass-accessor-perl 0.31-2
2009-02-24 16:30:56 status unpacked libclass-accessor-perl 0.31-2
2009-02-24 16:30:56 status unpacked libclass-accessor-perl 0.31-2
2009-02-24 16:30:56 install libcompress-raw-zlib-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.011-2build1
2009-02-24 16:30:56 status half-installed libcompress-raw-zlib-perl 2.011-2build1
2009-02-24 16:30:56 status unpacked libcompress-raw-zlib-perl 2.011-2build1
2009-02-24 16:30:56 status unpacked libcompress-raw-zlib-perl 2.011-2build1
2009-02-24 16:30:56 install libio-compress-base-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.011-1
2009-02-24 16:30:56 status half-installed libio-compress-base-perl 2.011-1
2009-02-24 16:30:56 status unpacked libio-compress-base-perl 2.011-1
2009-02-24 16:30:56 status unpacked libio-compress-base-perl 2.011-1
2009-02-24 16:30:56 install libio-compress-zlib-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.011-1
2009-02-24 16:30:56 status half-installed libio-compress-zlib-perl 2.011-1
2009-02-24 16:30:56 status unpacked libio-compress-zlib-perl 2.011-1
2009-02-24 16:30:56 status unpacked libio-compress-zlib-perl 2.011-1
2009-02-24 16:30:56 install libcompress-zlib-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.011-1
2009-02-24 16:30:56 status half-installed libcompress-zlib-perl 2.011-1
2009-02-24 16:30:56 status unpacked libcompress-zlib-perl 2.011-1
2009-02-24 16:30:56 status unpacked libcompress-zlib-perl 2.011-1
2009-02-24 16:30:56 install libedit2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.11~20080614-1ubuntu1
2009-02-24 16:30:56 status half-installed libedit2 2.11~20080614-1ubuntu1
2009-02-24 16:30:56 status unpacked libedit2 2.11~20080614-1ubuntu1
2009-02-24 16:30:56 status unpacked libedit2 2.11~20080614-1ubuntu1
2009-02-24 16:30:56 install libelf1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.131-4
2009-02-24 16:30:56 status half-installed libelf1 0.131-4
2009-02-24 16:30:56 status unpacked libelf1 0.131-4
2009-02-24 16:30:57 status unpacked libelf1 0.131-4
2009-02-24 16:30:57 install libfont-afm-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.20-1
2009-02-24 16:30:57 status half-installed libfont-afm-perl 1.20-1
2009-02-24 16:30:57 status unpacked libfont-afm-perl 1.20-1
2009-02-24 16:30:57 status unpacked libfont-afm-perl 1.20-1
2009-02-24 16:30:57 install libgc1c2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:6.8-1.1
2009-02-24 16:30:57 status half-installed libgc1c2 1:6.8-1.1
2009-02-24 16:30:57 status unpacked libgc1c2 1:6.8-1.1
2009-02-24 16:30:57 status unpacked libgc1c2 1:6.8-1.1
2009-02-24 16:30:57 install libgpm2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.20.4-2ubuntu1
2009-02-24 16:30:57 status half-installed libgpm2 1.20.4-2ubuntu1
2009-02-24 16:30:57 status unpacked libgpm2 1.20.4-2ubuntu1
2009-02-24 16:30:57 status unpacked libgpm2 1.20.4-2ubuntu1
2009-02-24 16:30:57 install libhtml-format-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.04-2
2009-02-24 16:30:57 status half-installed libhtml-format-perl 2.04-2
2009-02-24 16:30:57 status unpacked libhtml-format-perl 2.04-2
2009-02-24 16:30:57 status unpacked libhtml-format-perl 2.04-2
2009-02-24 16:30:57 install libhtml-template-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.9-1
2009-02-24 16:30:57 status half-installed libhtml-template-perl 2.9-1
2009-02-24 16:30:57 status unpacked libhtml-template-perl 2.9-1
2009-02-24 16:30:57 status unpacked libhtml-template-perl 2.9-1
2009-02-24 16:30:57 install libio-string-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.08-2
2009-02-24 16:30:57 status half-installed libio-string-perl 1.08-2
2009-02-24 16:30:57 status unpacked libio-string-perl 1.08-2
2009-02-24 16:30:57 status unpacked libio-string-perl 1.08-2
2009-02-24 16:30:57 install libtimedate-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.1600-9
2009-02-24 16:30:57 status half-installed libtimedate-perl 1.1600-9
2009-02-24 16:30:57 status unpacked libtimedate-perl 1.1600-9
2009-02-24 16:30:57 status unpacked libtimedate-perl 1.1600-9
2009-02-24 16:30:57 install libmailtools-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.03-1
2009-02-24 16:30:57 status half-installed libmailtools-perl 2.03-1
2009-02-24 16:30:57 status unpacked libmailtools-perl 2.03-1
2009-02-24 16:30:57 status unpacked libmailtools-perl 2.03-1
2009-02-24 16:30:57 install libparse-debianchangelog-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.1.1-2
2009-02-24 16:30:57 status half-installed libparse-debianchangelog-perl 1.1.1-2
2009-02-24 16:30:57 status unpacked libparse-debianchangelog-perl 1.1.1-2
2009-02-24 16:30:57 status unpacked libparse-debianchangelog-perl 1.1.1-2
2009-02-24 16:30:57 install libparted1.8-9 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.8.8.git.2008.03.24-7ubuntu7
2009-02-24 16:30:57 status half-installed libparted1.8-9 1.8.8.git.2008.03.24-7ubuntu7
2009-02-24 16:30:57 status unpacked libparted1.8-9 1.8.8.git.2008.03.24-7ubuntu7
2009-02-24 16:30:57 status unpacked libparted1.8-9 1.8.8.git.2008.03.24-7ubuntu7
2009-02-24 16:30:57 install libpcap0.8 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.9.8-5
2009-02-24 16:30:57 status half-installed libpcap0.8 0.9.8-5
2009-02-24 16:30:57 status unpacked libpcap0.8 0.9.8-5
2009-02-24 16:30:58 status unpacked libpcap0.8 0.9.8-5
2009-02-24 16:30:58 install libpci3 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:3.0.0-4ubuntu4
2009-02-24 16:30:58 status half-installed libpci3 1:3.0.0-4ubuntu4
2009-02-24 16:30:58 status unpacked libpci3 1:3.0.0-4ubuntu4
2009-02-24 16:30:58 status unpacked libpci3 1:3.0.0-4ubuntu4
2009-02-24 16:30:58 install libxml-namespacesupport-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.09-3
2009-02-24 16:30:58 status half-installed libxml-namespacesupport-perl 1.09-3
2009-02-24 16:30:58 status unpacked libxml-namespacesupport-perl 1.09-3
2009-02-24 16:30:58 status unpacked libxml-namespacesupport-perl 1.09-3
2009-02-24 16:30:58 install libxml-sax-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.16+dfsg-3
2009-02-24 16:30:58 status half-installed libxml-sax-perl 0.16+dfsg-3
2009-02-24 16:30:58 status unpacked libxml-sax-perl 0.16+dfsg-3
2009-02-24 16:30:58 status unpacked libxml-sax-perl 0.16+dfsg-3
2009-02-24 16:30:58 install libxml-sax-expat-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.39-1
2009-02-24 16:30:58 status half-installed libxml-sax-expat-perl 0.39-1
2009-02-24 16:30:58 status unpacked libxml-sax-expat-perl 0.39-1
2009-02-24 16:30:58 status unpacked libxml-sax-expat-perl 0.39-1
2009-02-24 16:30:58 install libxml-simple-perl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.18-1
2009-02-24 16:30:58 status half-installed libxml-simple-perl 2.18-1
2009-02-24 16:30:58 status unpacked libxml-simple-perl 2.18-1
2009-02-24 16:30:58 status unpacked libxml-simple-perl 2.18-1
2009-02-24 16:30:58 install logrotate <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 3.7.1-5ubuntu1
2009-02-24 16:30:58 status half-installed logrotate 3.7.1-5ubuntu1
2009-02-24 16:30:58 status unpacked logrotate 3.7.1-5ubuntu1
2009-02-24 16:30:58 status unpacked logrotate 3.7.1-5ubuntu1
2009-02-24 16:30:58 install pciutils <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:3.0.0-4ubuntu4
2009-02-24 16:30:58 status half-installed pciutils 1:3.0.0-4ubuntu4
2009-02-24 16:30:58 status unpacked pciutils 1:3.0.0-4ubuntu4
2009-02-24 16:30:58 status unpacked pciutils 1:3.0.0-4ubuntu4
2009-02-24 16:30:58 install lshw <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 02.13-2ubuntu1
2009-02-24 16:30:58 status half-installed lshw 02.13-2ubuntu1
2009-02-24 16:30:58 status unpacked lshw 02.13-2ubuntu1
2009-02-24 16:30:58 status unpacked lshw 02.13-2ubuntu1
2009-02-24 16:30:58 install lsof <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 4.78.dfsg.1-4
2009-02-24 16:30:58 status half-installed lsof 4.78.dfsg.1-4
2009-02-24 16:30:58 status unpacked lsof 4.78.dfsg.1-4
2009-02-24 16:30:58 status unpacked lsof 4.78.dfsg.1-4
2009-02-24 16:30:58 install ltrace <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.5-3.1ubuntu2
2009-02-24 16:30:58 status half-installed ltrace 0.5-3.1ubuntu2
2009-02-24 16:30:58 status unpacked ltrace 0.5-3.1ubuntu2
2009-02-24 16:30:58 status unpacked ltrace 0.5-3.1ubuntu2
2009-02-24 16:30:58 install man-db <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.5.2-2
2009-02-24 16:30:58 status half-installed man-db 2.5.2-2
2009-02-24 16:30:59 status unpacked man-db 2.5.2-2
2009-02-24 16:30:59 status unpacked man-db 2.5.2-2
2009-02-24 16:30:59 install manpages <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 3.01-1
2009-02-24 16:30:59 status half-installed manpages 3.01-1
2009-02-24 16:30:59 status unpacked manpages 3.01-1
2009-02-24 16:30:59 status unpacked manpages 3.01-1
2009-02-24 16:30:59 install memtest86+ <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.01-1ubuntu2
2009-02-24 16:30:59 status half-installed memtest86+ 2.01-1ubuntu2
2009-02-24 16:30:59 status unpacked memtest86+ 2.01-1ubuntu2
2009-02-24 16:30:59 status unpacked memtest86+ 2.01-1ubuntu2
2009-02-24 16:30:59 install mlocate <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.20-2ubuntu1
2009-02-24 16:30:59 status half-installed mlocate 0.20-2ubuntu1
2009-02-24 16:30:59 status unpacked mlocate 0.20-2ubuntu1
2009-02-24 16:30:59 status unpacked mlocate 0.20-2ubuntu1
2009-02-24 16:30:59 install mtr-tiny <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.73-1
2009-02-24 16:30:59 status half-installed mtr-tiny 0.73-1
2009-02-24 16:30:59 status unpacked mtr-tiny 0.73-1
2009-02-24 16:30:59 status unpacked mtr-tiny 0.73-1
2009-02-24 16:30:59 install nano <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.0.7-4
2009-02-24 16:30:59 status half-installed nano 2.0.7-4
2009-02-24 16:30:59 status unpacked nano 2.0.7-4
2009-02-24 16:30:59 status unpacked nano 2.0.7-4
2009-02-24 16:30:59 install openssh-client <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:5.1p1-3ubuntu1
2009-02-24 16:30:59 status half-installed openssh-client 1:5.1p1-3ubuntu1
2009-02-24 16:30:59 status unpacked openssh-client 1:5.1p1-3ubuntu1
2009-02-24 16:30:59 status unpacked openssh-client 1:5.1p1-3ubuntu1
2009-02-24 16:31:00 install parted <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.8.8.git.2008.03.24-7ubuntu7
2009-02-24 16:31:00 status half-installed parted 1.8.8.git.2008.03.24-7ubuntu7
2009-02-24 16:31:00 status unpacked parted 1.8.8.git.2008.03.24-7ubuntu7
2009-02-24 16:31:00 status unpacked parted 1.8.8.git.2008.03.24-7ubuntu7
2009-02-24 16:31:00 install popularity-contest <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.44ubuntu2
2009-02-24 16:31:00 status half-installed popularity-contest 1.44ubuntu2
2009-02-24 16:31:00 status unpacked popularity-contest 1.44ubuntu2
2009-02-24 16:31:00 status unpacked popularity-contest 1.44ubuntu2
2009-02-24 16:31:00 install ppp <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.4.4rel-10ubuntu2
2009-02-24 16:31:00 status half-installed ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:01 status unpacked ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:02 status unpacked ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:02 install pppconfig <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.3.18ubuntu1
2009-02-24 16:31:02 status half-installed pppconfig 2.3.18ubuntu1
2009-02-24 16:31:02 status unpacked pppconfig 2.3.18ubuntu1
2009-02-24 16:31:02 status unpacked pppconfig 2.3.18ubuntu1
2009-02-24 16:31:02 install pppoeconf <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.18ubuntu1
2009-02-24 16:31:02 status half-installed pppoeconf 1.18ubuntu1
2009-02-24 16:31:03 status unpacked pppoeconf 1.18ubuntu1
2009-02-24 16:31:03 status unpacked pppoeconf 1.18ubuntu1
2009-02-24 16:31:03 install psmisc <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 22.6-1
2009-02-24 16:31:03 status half-installed psmisc 22.6-1
2009-02-24 16:31:03 status unpacked psmisc 22.6-1
2009-02-24 16:31:03 status unpacked psmisc 22.6-1
2009-02-24 16:31:03 install python-gnupginterface <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.3.2-9ubuntu1
2009-02-24 16:31:03 status half-installed python-gnupginterface 0.3.2-9ubuntu1
2009-02-24 16:31:03 status unpacked python-gnupginterface 0.3.2-9ubuntu1
2009-02-24 16:31:03 status unpacked python-gnupginterface 0.3.2-9ubuntu1
2009-02-24 16:31:03 install reiserfsprogs <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:3.6.19-6
2009-02-24 16:31:03 status half-installed reiserfsprogs 1:3.6.19-6
2009-02-24 16:31:03 status unpacked reiserfsprogs 1:3.6.19-6
2009-02-24 16:31:03 status unpacked reiserfsprogs 1:3.6.19-6
2009-02-24 16:31:03 install rsync <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 3.0.3-2ubuntu1
2009-02-24 16:31:03 status half-installed rsync 3.0.3-2ubuntu1
2009-02-24 16:31:03 status unpacked rsync 3.0.3-2ubuntu1
2009-02-24 16:31:03 status unpacked rsync 3.0.3-2ubuntu1
2009-02-24 16:31:03 install sgml-base <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.26
2009-02-24 16:31:03 status half-installed sgml-base 1.26
2009-02-24 16:31:03 status unpacked sgml-base 1.26
2009-02-24 16:31:03 status unpacked sgml-base 1.26
2009-02-24 16:31:03 install strace <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 4.5.15-1.2ubuntu1
2009-02-24 16:31:03 status half-installed strace 4.5.15-1.2ubuntu1
2009-02-24 16:31:03 status unpacked strace 4.5.15-1.2ubuntu1
2009-02-24 16:31:03 status unpacked strace 4.5.15-1.2ubuntu1
2009-02-24 16:31:03 install tcpdump <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 3.9.8-4
2009-02-24 16:31:03 status half-installed tcpdump 3.9.8-4
2009-02-24 16:31:03 status unpacked tcpdump 3.9.8-4
2009-02-24 16:31:03 status unpacked tcpdump 3.9.8-4
2009-02-24 16:31:03 install telnet <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.17-35ubuntu1
2009-02-24 16:31:03 status half-installed telnet 0.17-35ubuntu1
2009-02-24 16:31:03 status unpacked telnet 0.17-35ubuntu1
2009-02-24 16:31:03 status unpacked telnet 0.17-35ubuntu1
2009-02-24 16:31:03 install time <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.7-22
2009-02-24 16:31:03 status half-installed time 1.7-22
2009-02-24 16:31:03 status unpacked time 1.7-22
2009-02-24 16:31:03 status unpacked time 1.7-22
2009-02-24 16:31:03 install w3m <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.5.2-2build1
2009-02-24 16:31:03 status half-installed w3m 0.5.2-2build1
2009-02-24 16:31:04 status unpacked w3m 0.5.2-2build1
2009-02-24 16:31:04 status unpacked w3m 0.5.2-2build1
2009-02-24 16:31:04 install wget <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.11.4-1ubuntu1
2009-02-24 16:31:04 status half-installed wget 1.11.4-1ubuntu1
2009-02-24 16:31:04 status unpacked wget 1.11.4-1ubuntu1
2009-02-24 16:31:04 status unpacked wget 1.11.4-1ubuntu1
2009-02-24 16:31:04 install ubuntu-standard <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.124
2009-02-24 16:31:04 status half-installed ubuntu-standard 1.124
2009-02-24 16:31:04 status unpacked ubuntu-standard 1.124
2009-02-24 16:31:04 status unpacked ubuntu-standard 1.124
2009-02-24 16:31:04 install ufw <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.23.2
2009-02-24 16:31:04 status half-installed ufw 0.23.2
2009-02-24 16:31:04 status unpacked ufw 0.23.2
2009-02-24 16:31:04 status unpacked ufw 0.23.2
2009-02-24 16:31:04 install update-manager-core <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:0.93.32
2009-02-24 16:31:04 status half-installed update-manager-core 1:0.93.32
2009-02-24 16:31:04 status unpacked update-manager-core 1:0.93.32
2009-02-24 16:31:04 status unpacked update-manager-core 1:0.93.32
2009-02-24 16:31:04 install xml-core <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.11ubuntu1
2009-02-24 16:31:04 status half-installed xml-core 0.11ubuntu1
2009-02-24 16:31:04 status unpacked xml-core 0.11ubuntu1
2009-02-24 16:31:04 status unpacked xml-core 0.11ubuntu1
2009-02-24 16:31:04 install libck-connector0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.2.10-1ubuntu9
2009-02-24 16:31:04 status half-installed libck-connector0 0.2.10-1ubuntu9
2009-02-24 16:31:04 status unpacked libck-connector0 0.2.10-1ubuntu9
2009-02-24 16:31:04 status unpacked libck-connector0 0.2.10-1ubuntu9
2009-02-24 16:31:04 install libpolkit2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.9-1ubuntu3
2009-02-24 16:31:04 status half-installed libpolkit2 0.9-1ubuntu3
2009-02-24 16:31:04 status unpacked libpolkit2 0.9-1ubuntu3
2009-02-24 16:31:04 status unpacked libpolkit2 0.9-1ubuntu3
2009-02-24 16:31:04 install dbus <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.2.4-0ubuntu1
2009-02-24 16:31:04 status half-installed dbus 1.2.4-0ubuntu1
2009-02-24 16:31:05 status unpacked dbus 1.2.4-0ubuntu1
2009-02-24 16:31:05 status unpacked dbus 1.2.4-0ubuntu1
2009-02-24 16:31:05 install consolekit <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.2.10-1ubuntu9
2009-02-24 16:31:05 status half-installed consolekit 0.2.10-1ubuntu9
2009-02-24 16:31:05 status unpacked consolekit 0.2.10-1ubuntu9
2009-02-24 16:31:05 status unpacked consolekit 0.2.10-1ubuntu9
2009-02-24 16:31:05 install dbus-x11 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.2.4-0ubuntu1
2009-02-24 16:31:05 status half-installed dbus-x11 1.2.4-0ubuntu1
2009-02-24 16:31:05 status unpacked dbus-x11 1.2.4-0ubuntu1
2009-02-24 16:31:05 status unpacked dbus-x11 1.2.4-0ubuntu1
2009-02-24 16:31:05 install libglib2.0-data <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.18.2-0ubuntu1
2009-02-24 16:31:05 status half-installed libglib2.0-data 2.18.2-0ubuntu1
2009-02-24 16:31:05 status unpacked libglib2.0-data 2.18.2-0ubuntu1
2009-02-24 16:31:05 status unpacked libglib2.0-data 2.18.2-0ubuntu1
2009-02-24 16:31:05 install libiw29 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 29-1ubuntu2
2009-02-24 16:31:05 status half-installed libiw29 29-1ubuntu2
2009-02-24 16:31:05 status unpacked libiw29 29-1ubuntu2
2009-02-24 16:31:05 status unpacked libiw29 29-1ubuntu2
2009-02-24 16:31:06 install libpam-ck-connector <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.2.10-1ubuntu9
2009-02-24 16:31:06 status half-installed libpam-ck-connector 0.2.10-1ubuntu9
2009-02-24 16:31:06 status unpacked libpam-ck-connector 0.2.10-1ubuntu9
2009-02-24 16:31:06 status unpacked libpam-ck-connector 0.2.10-1ubuntu9
2009-02-24 16:31:06 install libpcsclite1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.4.102-1ubuntu1
2009-02-24 16:31:06 status half-installed libpcsclite1 1.4.102-1ubuntu1
2009-02-24 16:31:06 status unpacked libpcsclite1 1.4.102-1ubuntu1
2009-02-24 16:31:06 status unpacked libpcsclite1 1.4.102-1ubuntu1
2009-02-24 16:31:06 install patch <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.5.9-5
2009-02-24 16:31:06 status half-installed patch 2.5.9-5
2009-02-24 16:31:06 status unpacked patch 2.5.9-5
2009-02-24 16:31:06 status unpacked patch 2.5.9-5
2009-02-24 16:31:06 install python-openssl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.7-2
2009-02-24 16:31:06 status half-installed python-openssl 0.7-2
2009-02-24 16:31:06 status unpacked python-openssl 0.7-2
2009-02-24 16:31:06 status unpacked python-openssl 0.7-2
2009-02-24 16:31:06 install python-pam <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.4.2-12ubuntu2
2009-02-24 16:31:06 status half-installed python-pam 0.4.2-12ubuntu2
2009-02-24 16:31:06 status unpacked python-pam 0.4.2-12ubuntu2
2009-02-24 16:31:06 status unpacked python-pam 0.4.2-12ubuntu2
2009-02-24 16:31:06 install python-pyopenssl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.7-2
2009-02-24 16:31:06 status half-installed python-pyopenssl 0.7-2
2009-02-24 16:31:06 status unpacked python-pyopenssl 0.7-2
2009-02-24 16:31:06 status unpacked python-pyopenssl 0.7-2
2009-02-24 16:31:06 install python-serial <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.3-1
2009-02-24 16:31:06 status half-installed python-serial 2.3-1
2009-02-24 16:31:06 status unpacked python-serial 2.3-1
2009-02-24 16:31:06 status unpacked python-serial 2.3-1
2009-02-24 16:31:06 install screen <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 4.0.3-11
2009-02-24 16:31:06 status half-installed screen 4.0.3-11
2009-02-24 16:31:06 status unpacked screen 4.0.3-11
2009-02-24 16:31:06 status unpacked screen 4.0.3-11
2009-02-24 16:31:06 install wireless-tools <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 29-1ubuntu2
2009-02-24 16:31:06 status half-installed wireless-tools 29-1ubuntu2
2009-02-24 16:31:07 status unpacked wireless-tools 29-1ubuntu2
2009-02-24 16:31:07 status unpacked wireless-tools 29-1ubuntu2
2009-02-24 16:31:07 install wpasupplicant <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.6.4-2
2009-02-24 16:31:07 status half-installed wpasupplicant 0.6.4-2
2009-02-24 16:31:07 status unpacked wpasupplicant 0.6.4-2
2009-02-24 16:31:07 status unpacked wpasupplicant 0.6.4-2
2009-02-24 16:31:07 startup packages configure
2009-02-24 16:31:07 configure libntfs-3g28 1:1.2506-1ubuntu2 1:1.2506-1ubuntu2
2009-02-24 16:31:07 status unpacked libntfs-3g28 1:1.2506-1ubuntu2
2009-02-24 16:31:07 status half-configured libntfs-3g28 1:1.2506-1ubuntu2
2009-02-24 16:31:07 status installed libntfs-3g28 1:1.2506-1ubuntu2
2009-02-24 16:31:07 status triggers-pending libc6 2.8~20080505-0ubuntu7
2009-02-24 16:31:07 configure ntfs-3g 1:1.2506-1ubuntu2 1:1.2506-1ubuntu2
2009-02-24 16:31:07 status unpacked ntfs-3g 1:1.2506-1ubuntu2
2009-02-24 16:31:07 status half-configured ntfs-3g 1:1.2506-1ubuntu2
2009-02-24 16:31:07 status installed ntfs-3g 1:1.2506-1ubuntu2
2009-02-24 16:31:07 configure libxau6 1:1.0.3-3 1:1.0.3-3
2009-02-24 16:31:07 status unpacked libxau6 1:1.0.3-3
2009-02-24 16:31:07 status half-configured libxau6 1:1.0.3-3
2009-02-24 16:31:07 status installed libxau6 1:1.0.3-3
2009-02-24 16:31:07 configure libxdmcp6 1:1.0.2-3 1:1.0.2-3
2009-02-24 16:31:07 status unpacked libxdmcp6 1:1.0.2-3
2009-02-24 16:31:07 status half-configured libxdmcp6 1:1.0.2-3
2009-02-24 16:31:07 status installed libxdmcp6 1:1.0.2-3
2009-02-24 16:31:07 configure libxcb1 1.1-1.1 1.1-1.1
2009-02-24 16:31:07 status unpacked libxcb1 1.1-1.1
2009-02-24 16:31:07 status half-configured libxcb1 1.1-1.1
2009-02-24 16:31:07 status installed libxcb1 1.1-1.1
2009-02-24 16:31:07 configure libxcb-xlib0 1.1-1.1 1.1-1.1
2009-02-24 16:31:07 status unpacked libxcb-xlib0 1.1-1.1
2009-02-24 16:31:08 status half-configured libxcb-xlib0 1.1-1.1
2009-02-24 16:31:08 status installed libxcb-xlib0 1.1-1.1
2009-02-24 16:31:08 configure libx11-data 2:1.1.5-2ubuntu1 2:1.1.5-2ubuntu1
2009-02-24 16:31:08 status unpacked libx11-data 2:1.1.5-2ubuntu1
2009-02-24 16:31:08 status half-configured libx11-data 2:1.1.5-2ubuntu1
2009-02-24 16:31:08 status installed libx11-data 2:1.1.5-2ubuntu1
2009-02-24 16:31:08 configure libx11-6 2:1.1.5-2ubuntu1 2:1.1.5-2ubuntu1
2009-02-24 16:31:08 status unpacked libx11-6 2:1.1.5-2ubuntu1
2009-02-24 16:31:08 status half-configured libx11-6 2:1.1.5-2ubuntu1
2009-02-24 16:31:08 status installed libx11-6 2:1.1.5-2ubuntu1
2009-02-24 16:31:08 configure libxext6 2:1.0.4-1 2:1.0.4-1
2009-02-24 16:31:08 status unpacked libxext6 2:1.0.4-1
2009-02-24 16:31:08 status half-configured libxext6 2:1.0.4-1
2009-02-24 16:31:08 status installed libxext6 2:1.0.4-1
2009-02-24 16:31:08 configure libxmuu1 2:1.0.4-1 2:1.0.4-1
2009-02-24 16:31:08 status unpacked libxmuu1 2:1.0.4-1
2009-02-24 16:31:08 status half-configured libxmuu1 2:1.0.4-1
2009-02-24 16:31:08 status installed libxmuu1 2:1.0.4-1
2009-02-24 16:31:08 configure xauth 1:1.0.3-2 1:1.0.3-2
2009-02-24 16:31:08 status unpacked xauth 1:1.0.3-2
2009-02-24 16:31:08 status half-configured xauth 1:1.0.3-2
2009-02-24 16:31:08 status installed xauth 1:1.0.3-2
2009-02-24 16:31:08 configure python-central 0.6.7ubuntu1 0.6.7ubuntu1
2009-02-24 16:31:08 status unpacked python-central 0.6.7ubuntu1
2009-02-24 16:31:08 status half-configured python-central 0.6.7ubuntu1
2009-02-24 16:31:08 status installed python-central 0.6.7ubuntu1
2009-02-24 16:31:08 configure python-twisted-bin 8.1.0-4 8.1.0-4
2009-02-24 16:31:08 status unpacked python-twisted-bin 8.1.0-4
2009-02-24 16:31:08 status half-configured python-twisted-bin 8.1.0-4
2009-02-24 16:31:08 status installed python-twisted-bin 8.1.0-4
2009-02-24 16:31:08 configure python-zopeinterface 3.3.1-7build1 3.3.1-7build1
2009-02-24 16:31:08 status unpacked python-zopeinterface 3.3.1-7build1
2009-02-24 16:31:08 status half-configured python-zopeinterface 3.3.1-7build1
2009-02-24 16:31:08 status installed python-zopeinterface 3.3.1-7build1
2009-02-24 16:31:08 configure python-twisted-core 8.1.0-4 8.1.0-4
2009-02-24 16:31:08 status unpacked python-twisted-core 8.1.0-4
2009-02-24 16:31:08 status half-configured python-twisted-core 8.1.0-4
2009-02-24 16:31:10 status installed python-twisted-core 8.1.0-4
2009-02-24 16:31:10 configure libdbus-1-3 1.2.4-0ubuntu1 1.2.4-0ubuntu1
2009-02-24 16:31:10 status unpacked libdbus-1-3 1.2.4-0ubuntu1
2009-02-24 16:31:10 status half-configured libdbus-1-3 1.2.4-0ubuntu1
2009-02-24 16:31:10 status installed libdbus-1-3 1.2.4-0ubuntu1
2009-02-24 16:31:10 configure libdbus-glib-1-2 0.76-1 0.76-1
2009-02-24 16:31:10 status unpacked libdbus-glib-1-2 0.76-1
2009-02-24 16:31:10 status half-configured libdbus-glib-1-2 0.76-1
2009-02-24 16:31:10 status installed libdbus-glib-1-2 0.76-1
2009-02-24 16:31:10 configure python-dbus 0.82.4-2 0.82.4-2
2009-02-24 16:31:10 status unpacked python-dbus 0.82.4-2
2009-02-24 16:31:10 status half-configured python-dbus 0.82.4-2
2009-02-24 16:31:10 status installed python-dbus 0.82.4-2
2009-02-24 16:31:10 status triggers-pending python-support 0.8.4
2009-02-24 16:31:10 configure libgdbm3 1.8.3-3 1.8.3-3
2009-02-24 16:31:10 status unpacked libgdbm3 1.8.3-3
2009-02-24 16:31:10 status half-configured libgdbm3 1.8.3-3
2009-02-24 16:31:10 status installed libgdbm3 1.8.3-3
2009-02-24 16:31:10 configure python-gdbm 2.5.2-1ubuntu1 2.5.2-1ubuntu1
2009-02-24 16:31:10 status unpacked python-gdbm 2.5.2-1ubuntu1
2009-02-24 16:31:10 status half-configured python-gdbm 2.5.2-1ubuntu1
2009-02-24 16:31:10 status installed python-gdbm 2.5.2-1ubuntu1
2009-02-24 16:31:10 configure cron 3.0pl1-104+ubuntu5 3.0pl1-104+ubuntu5
2009-02-24 16:31:10 status unpacked cron 3.0pl1-104+ubuntu5
2009-02-24 16:31:10 status unpacked cron 3.0pl1-104+ubuntu5
2009-02-24 16:31:10 status unpacked cron 3.0pl1-104+ubuntu5
2009-02-24 16:31:10 status unpacked cron 3.0pl1-104+ubuntu5
2009-02-24 16:31:10 status unpacked cron 3.0pl1-104+ubuntu5
2009-02-24 16:31:10 status unpacked cron 3.0pl1-104+ubuntu5
2009-02-24 16:31:10 status unpacked cron 3.0pl1-104+ubuntu5
2009-02-24 16:31:10 status unpacked cron 3.0pl1-104+ubuntu5
2009-02-24 16:31:10 status unpacked cron 3.0pl1-104+ubuntu5
2009-02-24 16:31:10 status unpacked cron 3.0pl1-104+ubuntu5
2009-02-24 16:31:10 status unpacked cron 3.0pl1-104+ubuntu5
2009-02-24 16:31:10 status unpacked cron 3.0pl1-104+ubuntu5
2009-02-24 16:31:10 status half-configured cron 3.0pl1-104+ubuntu5
2009-02-24 16:31:10 status installed cron 3.0pl1-104+ubuntu5
2009-02-24 16:31:10 configure update-motd 1.8 1.8
2009-02-24 16:31:10 status unpacked update-motd 1.8
2009-02-24 16:31:10 status unpacked update-motd 1.8
2009-02-24 16:31:10 status half-configured update-motd 1.8
2009-02-24 16:31:10 status installed update-motd 1.8
2009-02-24 16:31:10 configure ubuntu-serverguide 8.10.2 8.10.2
2009-02-24 16:31:10 status unpacked ubuntu-serverguide 8.10.2
2009-02-24 16:31:10 status half-configured ubuntu-serverguide 8.10.2
2009-02-24 16:31:10 status installed ubuntu-serverguide 8.10.2
2009-02-24 16:31:10 configure apparmor 2.3+1289-0ubuntu4 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:10 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status unpacked apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status half-configured apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status installed apparmor 2.3+1289-0ubuntu4
2009-02-24 16:31:11 configure libexpat1 2.0.1-4 2.0.1-4
2009-02-24 16:31:11 status unpacked libexpat1 2.0.1-4
2009-02-24 16:31:11 status half-configured libexpat1 2.0.1-4
2009-02-24 16:31:11 status installed libexpat1 2.0.1-4
2009-02-24 16:31:11 configure libapparmor1 2.3+1289-0ubuntu4 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status unpacked libapparmor1 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status half-configured libapparmor1 2.3+1289-0ubuntu4
2009-02-24 16:31:11 status installed libapparmor1 2.3+1289-0ubuntu4
2009-02-24 16:31:11 configure libsigc++-2.0-0c2a 2.0.18-2 2.0.18-2
2009-02-24 16:31:11 status unpacked libsigc++-2.0-0c2a 2.0.18-2
2009-02-24 16:31:11 status half-configured libsigc++-2.0-0c2a 2.0.18-2
2009-02-24 16:31:11 status installed libsigc++-2.0-0c2a 2.0.18-2
2009-02-24 16:31:11 configure libcwidget3 0.5.12-1ubuntu1 0.5.12-1ubuntu1
2009-02-24 16:31:11 status unpacked libcwidget3 0.5.12-1ubuntu1
2009-02-24 16:31:11 status half-configured libcwidget3 0.5.12-1ubuntu1
2009-02-24 16:31:11 status installed libcwidget3 0.5.12-1ubuntu1
2009-02-24 16:31:11 configure libxapian15 1.0.7-4 1.0.7-4
2009-02-24 16:31:11 status unpacked libxapian15 1.0.7-4
2009-02-24 16:31:11 status half-configured libxapian15 1.0.7-4
2009-02-24 16:31:11 status installed libxapian15 1.0.7-4
2009-02-24 16:31:11 configure libept0 0.5.26 0.5.26
2009-02-24 16:31:11 status unpacked libept0 0.5.26
2009-02-24 16:31:11 status half-configured libept0 0.5.26
2009-02-24 16:31:11 status installed libept0 0.5.26
2009-02-24 16:31:11 configure aptitude 0.4.11.3-1ubuntu3 0.4.11.3-1ubuntu3
2009-02-24 16:31:11 status unpacked aptitude 0.4.11.3-1ubuntu3
2009-02-24 16:31:11 status unpacked aptitude 0.4.11.3-1ubuntu3
2009-02-24 16:31:11 status unpacked aptitude 0.4.11.3-1ubuntu3
2009-02-24 16:31:11 status unpacked aptitude 0.4.11.3-1ubuntu3
2009-02-24 16:31:11 status half-configured aptitude 0.4.11.3-1ubuntu3
2009-02-24 16:31:11 status installed aptitude 0.4.11.3-1ubuntu3
2009-02-24 16:31:11 configure at 3.1.10.1ubuntu3 3.1.10.1ubuntu3
2009-02-24 16:31:11 status unpacked at 3.1.10.1ubuntu3
2009-02-24 16:31:11 status unpacked at 3.1.10.1ubuntu3
2009-02-24 16:31:11 status unpacked at 3.1.10.1ubuntu3
2009-02-24 16:31:11 status unpacked at 3.1.10.1ubuntu3
2009-02-24 16:31:11 status half-configured at 3.1.10.1ubuntu3
2009-02-24 16:31:11 status installed at 3.1.10.1ubuntu3
2009-02-24 16:31:11 configure ucf 3.0010 3.0010
2009-02-24 16:31:11 status unpacked ucf 3.0010
2009-02-24 16:31:11 status unpacked ucf 3.0010
2009-02-24 16:31:11 status half-configured ucf 3.0010
2009-02-24 16:31:11 status installed ucf 3.0010
2009-02-24 16:31:11 configure bash-completion 20060301-4ubuntu1 20060301-4ubuntu1
2009-02-24 16:31:11 status unpacked bash-completion 20060301-4ubuntu1
2009-02-24 16:31:11 status unpacked bash-completion 20060301-4ubuntu1
2009-02-24 16:31:11 status half-configured bash-completion 20060301-4ubuntu1
2009-02-24 16:31:12 status installed bash-completion 20060301-4ubuntu1
2009-02-24 16:31:12 configure libcap2 2.10-1 2.10-1
2009-02-24 16:31:12 status unpacked libcap2 2.10-1
2009-02-24 16:31:12 status half-configured libcap2 2.10-1
2009-02-24 16:31:12 status installed libcap2 2.10-1
2009-02-24 16:31:12 configure libxml2 2.6.32.dfsg-4ubuntu1 2.6.32.dfsg-4ubuntu1
2009-02-24 16:31:12 status unpacked libxml2 2.6.32.dfsg-4ubuntu1
2009-02-24 16:31:12 status half-configured libxml2 2.6.32.dfsg-4ubuntu1
2009-02-24 16:31:12 status installed libxml2 2.6.32.dfsg-4ubuntu1
2009-02-24 16:31:12 configure libisc44 1:9.5.0.dfsg.P2-1ubuntu2 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status unpacked libisc44 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status half-configured libisc44 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status installed libisc44 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 configure libdns43 1:9.5.0.dfsg.P2-1ubuntu2 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status unpacked libdns43 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status half-configured libdns43 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status installed libdns43 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 configure libisccc40 1:9.5.0.dfsg.P2-1ubuntu2 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status unpacked libisccc40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status half-configured libisccc40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status installed libisccc40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 configure libisccfg40 1:9.5.0.dfsg.P2-1ubuntu2 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status unpacked libisccfg40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status half-configured libisccfg40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status installed libisccfg40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 configure libbind9-40 1:9.5.0.dfsg.P2-1ubuntu2 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status unpacked libbind9-40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status half-configured libbind9-40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status installed libbind9-40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 configure liblwres40 1:9.5.0.dfsg.P2-1ubuntu2 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status unpacked liblwres40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status half-configured liblwres40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status installed liblwres40 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 configure bind9-host 1:9.5.0.dfsg.P2-1ubuntu2 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status unpacked bind9-host 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status half-configured bind9-host 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status installed bind9-host 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 configure libgmp3c2 2:4.2.2+dfsg-3ubuntu1 2:4.2.2+dfsg-3ubuntu1
2009-02-24 16:31:12 status unpacked libgmp3c2 2:4.2.2+dfsg-3ubuntu1
2009-02-24 16:31:12 status half-configured libgmp3c2 2:4.2.2+dfsg-3ubuntu1
2009-02-24 16:31:12 status installed libgmp3c2 2:4.2.2+dfsg-3ubuntu1
2009-02-24 16:31:12 configure libmpfr1ldbl 2.3.2.dfsg.1-1ubuntu1 2.3.2.dfsg.1-1ubuntu1
2009-02-24 16:31:12 status unpacked libmpfr1ldbl 2.3.2.dfsg.1-1ubuntu1
2009-02-24 16:31:12 status half-configured libmpfr1ldbl 2.3.2.dfsg.1-1ubuntu1
2009-02-24 16:31:12 status installed libmpfr1ldbl 2.3.2.dfsg.1-1ubuntu1
2009-02-24 16:31:12 configure cpp-4.3 4.3.2-1ubuntu11 4.3.2-1ubuntu11
2009-02-24 16:31:12 status unpacked cpp-4.3 4.3.2-1ubuntu11
2009-02-24 16:31:12 status half-configured cpp-4.3 4.3.2-1ubuntu11
2009-02-24 16:31:12 status installed cpp-4.3 4.3.2-1ubuntu11
2009-02-24 16:31:12 configure cpp 4:4.3.1-1ubuntu2 4:4.3.1-1ubuntu2
2009-02-24 16:31:12 status unpacked cpp 4:4.3.1-1ubuntu2
2009-02-24 16:31:12 status half-configured cpp 4:4.3.1-1ubuntu2
2009-02-24 16:31:12 status installed cpp 4:4.3.1-1ubuntu2
2009-02-24 16:31:12 configure bsdmainutils 6.1.10ubuntu2 6.1.10ubuntu2
2009-02-24 16:31:12 status unpacked bsdmainutils 6.1.10ubuntu2
2009-02-24 16:31:12 status unpacked bsdmainutils 6.1.10ubuntu2
2009-02-24 16:31:12 status unpacked bsdmainutils 6.1.10ubuntu2
2009-02-24 16:31:12 status half-configured bsdmainutils 6.1.10ubuntu2
2009-02-24 16:31:12 status installed bsdmainutils 6.1.10ubuntu2
2009-02-24 16:31:12 configure python-apt 0.7.7.1ubuntu4 0.7.7.1ubuntu4
2009-02-24 16:31:12 status unpacked python-apt 0.7.7.1ubuntu4
2009-02-24 16:31:12 status half-configured python-apt 0.7.7.1ubuntu4
2009-02-24 16:31:12 status installed python-apt 0.7.7.1ubuntu4
2009-02-24 16:31:12 configure command-not-found-data 0.2.26ubuntu1 0.2.26ubuntu1
2009-02-24 16:31:12 status unpacked command-not-found-data 0.2.26ubuntu1
2009-02-24 16:31:12 status half-configured command-not-found-data 0.2.26ubuntu1
2009-02-24 16:31:12 status installed command-not-found-data 0.2.26ubuntu1
2009-02-24 16:31:12 configure command-not-found 0.2.26ubuntu1 0.2.26ubuntu1
2009-02-24 16:31:12 status unpacked command-not-found 0.2.26ubuntu1
2009-02-24 16:31:12 status unpacked command-not-found 0.2.26ubuntu1
2009-02-24 16:31:12 status half-configured command-not-found 0.2.26ubuntu1
2009-02-24 16:31:12 status installed command-not-found 0.2.26ubuntu1
2009-02-24 16:31:12 configure dnsutils 1:9.5.0.dfsg.P2-1ubuntu2 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status unpacked dnsutils 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status half-configured dnsutils 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 status installed dnsutils 1:9.5.0.dfsg.P2-1ubuntu2
2009-02-24 16:31:12 configure dosfstools 2.11-5 2.11-5
2009-02-24 16:31:12 status unpacked dosfstools 2.11-5
2009-02-24 16:31:12 status half-configured dosfstools 2.11-5
2009-02-24 16:31:12 status installed dosfstools 2.11-5
2009-02-24 16:31:12 configure ed 0.7-1ubuntu1 0.7-1ubuntu1
2009-02-24 16:31:12 status unpacked ed 0.7-1ubuntu1
2009-02-24 16:31:12 status half-configured ed 0.7-1ubuntu1
2009-02-24 16:31:12 status installed ed 0.7-1ubuntu1
2009-02-24 16:31:12 configure friendly-recovery 0.2.6 0.2.6
2009-02-24 16:31:12 status unpacked friendly-recovery 0.2.6
2009-02-24 16:31:12 status half-configured friendly-recovery 0.2.6
2009-02-24 16:31:12 status installed friendly-recovery 0.2.6
2009-02-24 16:31:12 configure ftp 0.17-18 0.17-18
2009-02-24 16:31:12 status unpacked ftp 0.17-18
2009-02-24 16:31:12 status half-configured ftp 0.17-18
2009-02-24 16:31:13 status installed ftp 0.17-18
2009-02-24 16:31:13 configure gettext-base 0.17-3ubuntu2 0.17-3ubuntu2
2009-02-24 16:31:13 status unpacked gettext-base 0.17-3ubuntu2
2009-02-24 16:31:13 status half-configured gettext-base 0.17-3ubuntu2
2009-02-24 16:31:13 status installed gettext-base 0.17-3ubuntu2
2009-02-24 16:31:13 configure groff-base 1.18.1.1-20 1.18.1.1-20
2009-02-24 16:31:13 status unpacked groff-base 1.18.1.1-20
2009-02-24 16:31:13 status unpacked groff-base 1.18.1.1-20
2009-02-24 16:31:13 status unpacked groff-base 1.18.1.1-20
2009-02-24 16:31:13 status half-configured groff-base 1.18.1.1-20
2009-02-24 16:31:13 status installed groff-base 1.18.1.1-20
2009-02-24 16:31:13 configure hdparm 8.9-1ubuntu1 8.9-1ubuntu1
2009-02-24 16:31:13 status unpacked hdparm 8.9-1ubuntu1
2009-02-24 16:31:13 status unpacked hdparm 8.9-1ubuntu1
2009-02-24 16:31:13 status unpacked hdparm 8.9-1ubuntu1
2009-02-24 16:31:13 status unpacked hdparm 8.9-1ubuntu1
2009-02-24 16:31:13 status half-configured hdparm 8.9-1ubuntu1
2009-02-24 16:31:13 status installed hdparm 8.9-1ubuntu1
2009-02-24 16:31:13 configure info 4.11.dfsg.1-4 4.11.dfsg.1-4
2009-02-24 16:31:13 status unpacked info 4.11.dfsg.1-4
2009-02-24 16:31:13 status half-configured info 4.11.dfsg.1-4
2009-02-24 16:31:13 status installed info 4.11.dfsg.1-4
2009-02-24 16:31:13 configure iptables 1.4.0-4ubuntu2 1.4.0-4ubuntu2
2009-02-24 16:31:13 status unpacked iptables 1.4.0-4ubuntu2
2009-02-24 16:31:13 status half-configured iptables 1.4.0-4ubuntu2
2009-02-24 16:31:13 status installed iptables 1.4.0-4ubuntu2
2009-02-24 16:31:13 configure iputils-arping 3:20071127-1 3:20071127-1
2009-02-24 16:31:13 status unpacked iputils-arping 3:20071127-1
2009-02-24 16:31:13 status half-configured iputils-arping 3:20071127-1
2009-02-24 16:31:13 status installed iputils-arping 3:20071127-1
2009-02-24 16:31:13 configure iputils-tracepath 3:20071127-1 3:20071127-1
2009-02-24 16:31:13 status unpacked iputils-tracepath 3:20071127-1
2009-02-24 16:31:13 status half-configured iputils-tracepath 3:20071127-1
2009-02-24 16:31:13 status installed iputils-tracepath 3:20071127-1
2009-02-24 16:31:13 configure libedit2 2.11~20080614-1ubuntu1 2.11~20080614-1ubuntu1
2009-02-24 16:31:13 status unpacked libedit2 2.11~20080614-1ubuntu1
2009-02-24 16:31:13 status half-configured libedit2 2.11~20080614-1ubuntu1
2009-02-24 16:31:13 status installed libedit2 2.11~20080614-1ubuntu1
2009-02-24 16:31:13 configure libelf1 0.131-4 0.131-4
2009-02-24 16:31:13 status unpacked libelf1 0.131-4
2009-02-24 16:31:13 status half-configured libelf1 0.131-4
2009-02-24 16:31:13 status installed libelf1 0.131-4
2009-02-24 16:31:13 configure libgc1c2 1:6.8-1.1 1:6.8-1.1
2009-02-24 16:31:13 status unpacked libgc1c2 1:6.8-1.1
2009-02-24 16:31:13 status half-configured libgc1c2 1:6.8-1.1
2009-02-24 16:31:13 status installed libgc1c2 1:6.8-1.1
2009-02-24 16:31:13 configure libgpm2 1.20.4-2ubuntu1 1.20.4-2ubuntu1
2009-02-24 16:31:13 status unpacked libgpm2 1.20.4-2ubuntu1
2009-02-24 16:31:13 status half-configured libgpm2 1.20.4-2ubuntu1
2009-02-24 16:31:13 status installed libgpm2 1.20.4-2ubuntu1
2009-02-24 16:31:13 configure libparted1.8-9 1.8.8.git.2008.03.24-7ubuntu7 1.8.8.git.2008.03.24-7ubuntu7
2009-02-24 16:31:13 status unpacked libparted1.8-9 1.8.8.git.2008.03.24-7ubuntu7
2009-02-24 16:31:13 status half-configured libparted1.8-9 1.8.8.git.2008.03.24-7ubuntu7
2009-02-24 16:31:13 status installed libparted1.8-9 1.8.8.git.2008.03.24-7ubuntu7
2009-02-24 16:31:13 configure libpcap0.8 0.9.8-5 0.9.8-5
2009-02-24 16:31:13 status unpacked libpcap0.8 0.9.8-5
2009-02-24 16:31:13 status half-configured libpcap0.8 0.9.8-5
2009-02-24 16:31:13 status installed libpcap0.8 0.9.8-5
2009-02-24 16:31:13 configure libpci3 1:3.0.0-4ubuntu4 1:3.0.0-4ubuntu4
2009-02-24 16:31:13 status unpacked libpci3 1:3.0.0-4ubuntu4
2009-02-24 16:31:13 status half-configured libpci3 1:3.0.0-4ubuntu4
2009-02-24 16:31:13 status installed libpci3 1:3.0.0-4ubuntu4
2009-02-24 16:31:13 configure logrotate 3.7.1-5ubuntu1 3.7.1-5ubuntu1
2009-02-24 16:31:13 status unpacked logrotate 3.7.1-5ubuntu1
2009-02-24 16:31:13 status unpacked logrotate 3.7.1-5ubuntu1
2009-02-24 16:31:13 status unpacked logrotate 3.7.1-5ubuntu1
2009-02-24 16:31:13 status half-configured logrotate 3.7.1-5ubuntu1
2009-02-24 16:31:13 status installed logrotate 3.7.1-5ubuntu1
2009-02-24 16:31:13 configure pciutils 1:3.0.0-4ubuntu4 1:3.0.0-4ubuntu4
2009-02-24 16:31:13 status unpacked pciutils 1:3.0.0-4ubuntu4
2009-02-24 16:31:13 status half-configured pciutils 1:3.0.0-4ubuntu4
2009-02-24 16:31:13 status installed pciutils 1:3.0.0-4ubuntu4
2009-02-24 16:31:13 configure lshw 02.13-2ubuntu1 02.13-2ubuntu1
2009-02-24 16:31:13 status unpacked lshw 02.13-2ubuntu1
2009-02-24 16:31:13 status half-configured lshw 02.13-2ubuntu1
2009-02-24 16:31:13 status installed lshw 02.13-2ubuntu1
2009-02-24 16:31:13 configure lsof 4.78.dfsg.1-4 4.78.dfsg.1-4
2009-02-24 16:31:13 status unpacked lsof 4.78.dfsg.1-4
2009-02-24 16:31:13 status half-configured lsof 4.78.dfsg.1-4
2009-02-24 16:31:13 status installed lsof 4.78.dfsg.1-4
2009-02-24 16:31:13 configure ltrace 0.5-3.1ubuntu2 0.5-3.1ubuntu2
2009-02-24 16:31:13 status unpacked ltrace 0.5-3.1ubuntu2
2009-02-24 16:31:13 status unpacked ltrace 0.5-3.1ubuntu2
2009-02-24 16:31:13 status half-configured ltrace 0.5-3.1ubuntu2
2009-02-24 16:31:13 status installed ltrace 0.5-3.1ubuntu2
2009-02-24 16:31:13 configure man-db 2.5.2-2 2.5.2-2
2009-02-24 16:31:13 status unpacked man-db 2.5.2-2
2009-02-24 16:31:13 status unpacked man-db 2.5.2-2
2009-02-24 16:31:13 status unpacked man-db 2.5.2-2
2009-02-24 16:31:13 status unpacked man-db 2.5.2-2
2009-02-24 16:31:13 status half-configured man-db 2.5.2-2
2009-02-24 16:31:22 status installed man-db 2.5.2-2
2009-02-24 16:31:22 configure manpages 3.01-1 3.01-1
2009-02-24 16:31:22 status unpacked manpages 3.01-1
2009-02-24 16:31:22 status half-configured manpages 3.01-1
2009-02-24 16:31:22 status installed manpages 3.01-1
2009-02-24 16:31:22 configure memtest86+ 2.01-1ubuntu2 2.01-1ubuntu2
2009-02-24 16:31:22 status unpacked memtest86+ 2.01-1ubuntu2
2009-02-24 16:31:22 status unpacked memtest86+ 2.01-1ubuntu2
2009-02-24 16:31:22 status half-configured memtest86+ 2.01-1ubuntu2
2009-02-24 16:31:22 status installed memtest86+ 2.01-1ubuntu2
2009-02-24 16:31:22 configure mlocate 0.20-2ubuntu1 0.20-2ubuntu1
2009-02-24 16:31:22 status unpacked mlocate 0.20-2ubuntu1
2009-02-24 16:31:22 status unpacked mlocate 0.20-2ubuntu1
2009-02-24 16:31:22 status unpacked mlocate 0.20-2ubuntu1
2009-02-24 16:31:22 status half-configured mlocate 0.20-2ubuntu1
2009-02-24 16:31:23 status installed mlocate 0.20-2ubuntu1
2009-02-24 16:31:23 configure mtr-tiny 0.73-1 0.73-1
2009-02-24 16:31:23 status unpacked mtr-tiny 0.73-1
2009-02-24 16:31:23 status half-configured mtr-tiny 0.73-1
2009-02-24 16:31:23 status installed mtr-tiny 0.73-1
2009-02-24 16:31:23 configure nano 2.0.7-4 2.0.7-4
2009-02-24 16:31:23 status unpacked nano 2.0.7-4
2009-02-24 16:31:23 status unpacked nano 2.0.7-4
2009-02-24 16:31:23 status half-configured nano 2.0.7-4
2009-02-24 16:31:23 status installed nano 2.0.7-4
2009-02-24 16:31:23 configure openssh-client 1:5.1p1-3ubuntu1 1:5.1p1-3ubuntu1
2009-02-24 16:31:23 status unpacked openssh-client 1:5.1p1-3ubuntu1
2009-02-24 16:31:23 status unpacked openssh-client 1:5.1p1-3ubuntu1
2009-02-24 16:31:23 status unpacked openssh-client 1:5.1p1-3ubuntu1
2009-02-24 16:31:23 status half-configured openssh-client 1:5.1p1-3ubuntu1
2009-02-24 16:31:24 status installed openssh-client 1:5.1p1-3ubuntu1
2009-02-24 16:31:24 configure parted 1.8.8.git.2008.03.24-7ubuntu7 1.8.8.git.2008.03.24-7ubuntu7
2009-02-24 16:31:24 status unpacked parted 1.8.8.git.2008.03.24-7ubuntu7
2009-02-24 16:31:24 status half-configured parted 1.8.8.git.2008.03.24-7ubuntu7
2009-02-24 16:31:24 status installed parted 1.8.8.git.2008.03.24-7ubuntu7
2009-02-24 16:31:24 configure popularity-contest 1.44ubuntu2 1.44ubuntu2
2009-02-24 16:31:24 status unpacked popularity-contest 1.44ubuntu2
2009-02-24 16:31:24 status unpacked popularity-contest 1.44ubuntu2
2009-02-24 16:31:24 status half-configured popularity-contest 1.44ubuntu2
2009-02-24 16:31:24 status installed popularity-contest 1.44ubuntu2
2009-02-24 16:31:24 configure ppp 2.4.4rel-10ubuntu2 2.4.4rel-10ubuntu2
2009-02-24 16:31:24 status unpacked ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:24 status unpacked ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:24 status unpacked ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:24 status unpacked ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:24 status unpacked ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:24 status unpacked ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:24 status unpacked ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:24 status unpacked ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:24 status unpacked ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:24 status unpacked ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:24 status unpacked ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:24 status unpacked ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:24 status unpacked ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:24 status unpacked ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:24 status unpacked ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:24 status half-configured ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:24 status installed ppp 2.4.4rel-10ubuntu2
2009-02-24 16:31:24 configure pppconfig 2.3.18ubuntu1 2.3.18ubuntu1
2009-02-24 16:31:24 status unpacked pppconfig 2.3.18ubuntu1
2009-02-24 16:31:24 status unpacked pppconfig 2.3.18ubuntu1
2009-02-24 16:31:24 status unpacked pppconfig 2.3.18ubuntu1
2009-02-24 16:31:24 status unpacked pppconfig 2.3.18ubuntu1
2009-02-24 16:31:24 status half-configured pppconfig 2.3.18ubuntu1
2009-02-24 16:31:24 status installed pppconfig 2.3.18ubuntu1
2009-02-24 16:31:24 configure pppoeconf 1.18ubuntu1 1.18ubuntu1
2009-02-24 16:31:24 status unpacked pppoeconf 1.18ubuntu1
2009-02-24 16:31:24 status half-configured pppoeconf 1.18ubuntu1
2009-02-24 16:31:24 status installed pppoeconf 1.18ubuntu1
2009-02-24 16:31:24 configure psmisc 22.6-1 22.6-1
2009-02-24 16:31:24 status unpacked psmisc 22.6-1
2009-02-24 16:31:24 status half-configured psmisc 22.6-1
2009-02-24 16:31:24 status installed psmisc 22.6-1
2009-02-24 16:31:24 configure python-gnupginterface 0.3.2-9ubuntu1 0.3.2-9ubuntu1
2009-02-24 16:31:24 status unpacked python-gnupginterface 0.3.2-9ubuntu1
2009-02-24 16:31:24 status half-configured python-gnupginterface 0.3.2-9ubuntu1
2009-02-24 16:31:24 status installed python-gnupginterface 0.3.2-9ubuntu1
2009-02-24 16:31:24 configure reiserfsprogs 1:3.6.19-6 1:3.6.19-6
2009-02-24 16:31:24 status unpacked reiserfsprogs 1:3.6.19-6
2009-02-24 16:31:24 status half-configured reiserfsprogs 1:3.6.19-6
2009-02-24 16:31:24 status installed reiserfsprogs 1:3.6.19-6
2009-02-24 16:31:24 configure rsync 3.0.3-2ubuntu1 3.0.3-2ubuntu1
2009-02-24 16:31:24 status unpacked rsync 3.0.3-2ubuntu1
2009-02-24 16:31:24 status unpacked rsync 3.0.3-2ubuntu1
2009-02-24 16:31:24 status unpacked rsync 3.0.3-2ubuntu1
2009-02-24 16:31:24 status half-configured rsync 3.0.3-2ubuntu1
2009-02-24 16:31:24 status installed rsync 3.0.3-2ubuntu1
2009-02-24 16:31:24 configure strace 4.5.15-1.2ubuntu1 4.5.15-1.2ubuntu1
2009-02-24 16:31:24 status unpacked strace 4.5.15-1.2ubuntu1
2009-02-24 16:31:24 status half-configured strace 4.5.15-1.2ubuntu1
2009-02-24 16:31:24 status installed strace 4.5.15-1.2ubuntu1
2009-02-24 16:31:24 configure tcpdump 3.9.8-4 3.9.8-4
2009-02-24 16:31:24 status unpacked tcpdump 3.9.8-4
2009-02-24 16:31:24 status half-configured tcpdump 3.9.8-4
2009-02-24 16:31:24 status installed tcpdump 3.9.8-4
2009-02-24 16:31:24 configure telnet 0.17-35ubuntu1 0.17-35ubuntu1
2009-02-24 16:31:24 status unpacked telnet 0.17-35ubuntu1
2009-02-24 16:31:24 status half-configured telnet 0.17-35ubuntu1
2009-02-24 16:31:24 status installed telnet 0.17-35ubuntu1
2009-02-24 16:31:24 configure time 1.7-22 1.7-22
2009-02-24 16:31:24 status unpacked time 1.7-22
2009-02-24 16:31:24 status half-configured time 1.7-22
2009-02-24 16:31:24 status installed time 1.7-22
2009-02-24 16:31:24 configure w3m 0.5.2-2build1 0.5.2-2build1
2009-02-24 16:31:24 status unpacked w3m 0.5.2-2build1
2009-02-24 16:31:24 status unpacked w3m 0.5.2-2build1
2009-02-24 16:31:24 status unpacked w3m 0.5.2-2build1
2009-02-24 16:31:24 status half-configured w3m 0.5.2-2build1
2009-02-24 16:31:24 status installed w3m 0.5.2-2build1
2009-02-24 16:31:24 configure wget 1.11.4-1ubuntu1 1.11.4-1ubuntu1
2009-02-24 16:31:24 status unpacked wget 1.11.4-1ubuntu1
2009-02-24 16:31:24 status unpacked wget 1.11.4-1ubuntu1
2009-02-24 16:31:24 status half-configured wget 1.11.4-1ubuntu1
2009-02-24 16:31:25 status installed wget 1.11.4-1ubuntu1
2009-02-24 16:31:25 configure ubuntu-standard 1.124 1.124
2009-02-24 16:31:25 status unpacked ubuntu-standard 1.124
2009-02-24 16:31:25 status half-configured ubuntu-standard 1.124
2009-02-24 16:31:25 status installed ubuntu-standard 1.124
2009-02-24 16:31:25 configure ufw 0.23.2 0.23.2
2009-02-24 16:31:25 status unpacked ufw 0.23.2
2009-02-24 16:31:25 status unpacked ufw 0.23.2
2009-02-24 16:31:25 status unpacked ufw 0.23.2
2009-02-24 16:31:25 status unpacked ufw 0.23.2
2009-02-24 16:31:25 status half-configured ufw 0.23.2
2009-02-24 16:31:25 status installed ufw 0.23.2
2009-02-24 16:31:25 configure update-manager-core 1:0.93.32 1:0.93.32
2009-02-24 16:31:25 status unpacked update-manager-core 1:0.93.32
2009-02-24 16:31:25 status unpacked update-manager-core 1:0.93.32
2009-02-24 16:31:25 status unpacked update-manager-core 1:0.93.32
2009-02-24 16:31:25 status half-configured update-manager-core 1:0.93.32
2009-02-24 16:31:26 status installed update-manager-core 1:0.93.32
2009-02-24 16:31:26 configure libck-connector0 0.2.10-1ubuntu9 0.2.10-1ubuntu9
2009-02-24 16:31:26 status unpacked libck-connector0 0.2.10-1ubuntu9
2009-02-24 16:31:26 status half-configured libck-connector0 0.2.10-1ubuntu9
2009-02-24 16:31:26 status installed libck-connector0 0.2.10-1ubuntu9
2009-02-24 16:31:26 configure libpolkit2 0.9-1ubuntu3 0.9-1ubuntu3
2009-02-24 16:31:26 status unpacked libpolkit2 0.9-1ubuntu3
2009-02-24 16:31:26 status half-configured libpolkit2 0.9-1ubuntu3
2009-02-24 16:31:26 status installed libpolkit2 0.9-1ubuntu3
2009-02-24 16:31:26 configure libglib2.0-data 2.18.2-0ubuntu1 2.18.2-0ubuntu1
2009-02-24 16:31:26 status unpacked libglib2.0-data 2.18.2-0ubuntu1
2009-02-24 16:31:26 status half-configured libglib2.0-data 2.18.2-0ubuntu1
2009-02-24 16:31:26 status installed libglib2.0-data 2.18.2-0ubuntu1
2009-02-24 16:31:26 configure libiw29 29-1ubuntu2 29-1ubuntu2
2009-02-24 16:31:26 status unpacked libiw29 29-1ubuntu2
2009-02-24 16:31:26 status half-configured libiw29 29-1ubuntu2
2009-02-24 16:31:26 status installed libiw29 29-1ubuntu2
2009-02-24 16:31:26 configure libpam-ck-connector 0.2.10-1ubuntu9 0.2.10-1ubuntu9
2009-02-24 16:31:26 status unpacked libpam-ck-connector 0.2.10-1ubuntu9
2009-02-24 16:31:26 status half-configured libpam-ck-connector 0.2.10-1ubuntu9
2009-02-24 16:31:26 status installed libpam-ck-connector 0.2.10-1ubuntu9
2009-02-24 16:31:26 configure libpcsclite1 1.4.102-1ubuntu1 1.4.102-1ubuntu1
2009-02-24 16:31:26 status unpacked libpcsclite1 1.4.102-1ubuntu1
2009-02-24 16:31:26 status half-configured libpcsclite1 1.4.102-1ubuntu1
2009-02-24 16:31:26 status installed libpcsclite1 1.4.102-1ubuntu1
2009-02-24 16:31:26 configure patch 2.5.9-5 2.5.9-5
2009-02-24 16:31:26 status unpacked patch 2.5.9-5
2009-02-24 16:31:26 status half-configured patch 2.5.9-5
2009-02-24 16:31:26 status installed patch 2.5.9-5
2009-02-24 16:31:26 configure python-openssl 0.7-2 0.7-2
2009-02-24 16:31:26 status unpacked python-openssl 0.7-2
2009-02-24 16:31:26 status half-configured python-openssl 0.7-2
2009-02-24 16:31:26 status installed python-openssl 0.7-2
2009-02-24 16:31:26 configure python-pam 0.4.2-12ubuntu2 0.4.2-12ubuntu2
2009-02-24 16:31:26 status unpacked python-pam 0.4.2-12ubuntu2
2009-02-24 16:31:26 status half-configured python-pam 0.4.2-12ubuntu2
2009-02-24 16:31:26 status installed python-pam 0.4.2-12ubuntu2
2009-02-24 16:31:26 configure python-pyopenssl 0.7-2 0.7-2
2009-02-24 16:31:26 status unpacked python-pyopenssl 0.7-2
2009-02-24 16:31:26 status half-configured python-pyopenssl 0.7-2
2009-02-24 16:31:26 status installed python-pyopenssl 0.7-2
2009-02-24 16:31:26 configure python-serial 2.3-1 2.3-1
2009-02-24 16:31:26 status unpacked python-serial 2.3-1
2009-02-24 16:31:26 status half-configured python-serial 2.3-1
2009-02-24 16:31:26 status installed python-serial 2.3-1
2009-02-24 16:31:26 configure screen 4.0.3-11 4.0.3-11
2009-02-24 16:31:26 status unpacked screen 4.0.3-11
2009-02-24 16:31:26 status unpacked screen 4.0.3-11
2009-02-24 16:31:26 status unpacked screen 4.0.3-11
2009-02-24 16:31:26 status half-configured screen 4.0.3-11
2009-02-24 16:31:27 status installed screen 4.0.3-11
2009-02-24 16:31:27 configure wireless-tools 29-1ubuntu2 29-1ubuntu2
2009-02-24 16:31:27 status unpacked wireless-tools 29-1ubuntu2
2009-02-24 16:31:27 status unpacked wireless-tools 29-1ubuntu2
2009-02-24 16:31:27 status unpacked wireless-tools 29-1ubuntu2
2009-02-24 16:31:27 status half-configured wireless-tools 29-1ubuntu2
2009-02-24 16:31:27 status installed wireless-tools 29-1ubuntu2
2009-02-24 16:31:27 configure wpasupplicant 0.6.4-2 0.6.4-2
2009-02-24 16:31:27 status unpacked wpasupplicant 0.6.4-2
2009-02-24 16:31:27 status unpacked wpasupplicant 0.6.4-2
2009-02-24 16:31:27 status unpacked wpasupplicant 0.6.4-2
2009-02-24 16:31:27 status unpacked wpasupplicant 0.6.4-2
2009-02-24 16:31:27 status unpacked wpasupplicant 0.6.4-2
2009-02-24 16:31:27 status unpacked wpasupplicant 0.6.4-2
2009-02-24 16:31:27 status unpacked wpasupplicant 0.6.4-2
2009-02-24 16:31:27 status half-configured wpasupplicant 0.6.4-2
2009-02-24 16:31:27 status installed wpasupplicant 0.6.4-2
2009-02-24 16:31:27 configure consolekit 0.2.10-1ubuntu9 0.2.10-1ubuntu9
2009-02-24 16:31:27 status unpacked consolekit 0.2.10-1ubuntu9
2009-02-24 16:31:27 status unpacked consolekit 0.2.10-1ubuntu9
2009-02-24 16:31:27 status unpacked consolekit 0.2.10-1ubuntu9
2009-02-24 16:31:27 status unpacked consolekit 0.2.10-1ubuntu9
2009-02-24 16:31:27 status half-configured consolekit 0.2.10-1ubuntu9
2009-02-24 16:31:27 status installed consolekit 0.2.10-1ubuntu9
2009-02-24 16:31:27 configure dbus 1.2.4-0ubuntu1 1.2.4-0ubuntu1
2009-02-24 16:31:27 status unpacked dbus 1.2.4-0ubuntu1
2009-02-24 16:31:27 status unpacked dbus 1.2.4-0ubuntu1
2009-02-24 16:31:27 status unpacked dbus 1.2.4-0ubuntu1
2009-02-24 16:31:27 status unpacked dbus 1.2.4-0ubuntu1
2009-02-24 16:31:27 status unpacked dbus 1.2.4-0ubuntu1
2009-02-24 16:31:27 status half-configured dbus 1.2.4-0ubuntu1
2009-02-24 16:31:27 status installed dbus 1.2.4-0ubuntu1
2009-02-24 16:31:27 configure dbus-x11 1.2.4-0ubuntu1 1.2.4-0ubuntu1
2009-02-24 16:31:27 status unpacked dbus-x11 1.2.4-0ubuntu1
2009-02-24 16:31:27 status unpacked dbus-x11 1.2.4-0ubuntu1
2009-02-24 16:31:27 status half-configured dbus-x11 1.2.4-0ubuntu1
2009-02-24 16:31:27 status installed dbus-x11 1.2.4-0ubuntu1
2009-02-24 16:31:27 configure perl-modules 5.10.0-11.1ubuntu2 5.10.0-11.1ubuntu2
2009-02-24 16:31:27 status unpacked perl-modules 5.10.0-11.1ubuntu2
2009-02-24 16:31:27 status unpacked perl-modules 5.10.0-11.1ubuntu2
2009-02-24 16:31:27 status half-configured perl-modules 5.10.0-11.1ubuntu2
2009-02-24 16:31:27 status installed perl-modules 5.10.0-11.1ubuntu2
2009-02-24 16:31:27 configure perl 5.10.0-11.1ubuntu2 5.10.0-11.1ubuntu2
2009-02-24 16:31:27 status unpacked perl 5.10.0-11.1ubuntu2
2009-02-24 16:31:27 status half-configured perl 5.10.0-11.1ubuntu2
2009-02-24 16:31:27 status installed perl 5.10.0-11.1ubuntu2
2009-02-24 16:31:27 configure landscape-common 1.0.23-0ubuntu0.8.10.1 1.0.23-0ubuntu0.8.10.1
2009-02-24 16:31:27 status unpacked landscape-common 1.0.23-0ubuntu0.8.10.1
2009-02-24 16:31:27 status half-configured landscape-common 1.0.23-0ubuntu0.8.10.1
2009-02-24 16:31:28 status installed landscape-common 1.0.23-0ubuntu0.8.10.1
2009-02-24 16:31:28 configure libterm-readkey-perl 2.30-3ubuntu2 2.30-3ubuntu2
2009-02-24 16:31:28 status unpacked libterm-readkey-perl 2.30-3ubuntu2
2009-02-24 16:31:28 status half-configured libterm-readkey-perl 2.30-3ubuntu2
2009-02-24 16:31:28 status installed libterm-readkey-perl 2.30-3ubuntu2
2009-02-24 16:31:28 configure libhtml-tagset-perl 3.20-2 3.20-2
2009-02-24 16:31:28 status unpacked libhtml-tagset-perl 3.20-2
2009-02-24 16:31:28 status half-configured libhtml-tagset-perl 3.20-2
2009-02-24 16:31:28 status installed libhtml-tagset-perl 3.20-2
2009-02-24 16:31:28 configure liburi-perl 1.35.dfsg.1-1 1.35.dfsg.1-1
2009-02-24 16:31:28 status unpacked liburi-perl 1.35.dfsg.1-1
2009-02-24 16:31:28 status half-configured liburi-perl 1.35.dfsg.1-1
2009-02-24 16:31:28 status installed liburi-perl 1.35.dfsg.1-1
2009-02-24 16:31:28 configure libhtml-parser-perl 3.56-1ubuntu2 3.56-1ubuntu2
2009-02-24 16:31:28 status unpacked libhtml-parser-perl 3.56-1ubuntu2
2009-02-24 16:31:28 status half-configured libhtml-parser-perl 3.56-1ubuntu2
2009-02-24 16:31:28 status installed libhtml-parser-perl 3.56-1ubuntu2
2009-02-24 16:31:28 configure libhtml-tree-perl 3.23-1 3.23-1
2009-02-24 16:31:28 status unpacked libhtml-tree-perl 3.23-1
2009-02-24 16:31:28 status half-configured libhtml-tree-perl 3.23-1
2009-02-24 16:31:28 status installed libhtml-tree-perl 3.23-1
2009-02-24 16:31:28 configure libwww-perl 5.812-1 5.812-1
2009-02-24 16:31:28 status unpacked libwww-perl 5.812-1
2009-02-24 16:31:28 status half-configured libwww-perl 5.812-1
2009-02-24 16:31:28 status installed libwww-perl 5.812-1
2009-02-24 16:31:28 configure libxml-parser-perl 2.36-1.1build2 2.36-1.1build2
2009-02-24 16:31:28 status unpacked libxml-parser-perl 2.36-1.1build2
2009-02-24 16:31:28 status half-configured libxml-parser-perl 2.36-1.1build2
2009-02-24 16:31:28 status installed libxml-parser-perl 2.36-1.1build2
2009-02-24 16:31:28 configure librpc-xml-perl 0.60-3 0.60-3
2009-02-24 16:31:28 status unpacked librpc-xml-perl 0.60-3
2009-02-24 16:31:28 status half-configured librpc-xml-perl 0.60-3
2009-02-24 16:31:28 status installed librpc-xml-perl 0.60-3
2009-02-24 16:31:28 configure libapparmor-perl 2.3+1289-0ubuntu4 2.3+1289-0ubuntu4
2009-02-24 16:31:28 status unpacked libapparmor-perl 2.3+1289-0ubuntu4
2009-02-24 16:31:28 status half-configured libapparmor-perl 2.3+1289-0ubuntu4
2009-02-24 16:31:28 status installed libapparmor-perl 2.3+1289-0ubuntu4
2009-02-24 16:31:28 configure apparmor-utils 2.3+1289-0ubuntu4 2.3+1289-0ubuntu4
2009-02-24 16:31:28 status unpacked apparmor-utils 2.3+1289-0ubuntu4
2009-02-24 16:31:28 status unpacked apparmor-utils 2.3+1289-0ubuntu4
2009-02-24 16:31:28 status unpacked apparmor-utils 2.3+1289-0ubuntu4
2009-02-24 16:31:28 status half-configured apparmor-utils 2.3+1289-0ubuntu4
2009-02-24 16:31:28 status installed apparmor-utils 2.3+1289-0ubuntu4
2009-02-24 16:31:28 configure libclass-accessor-perl 0.31-2 0.31-2
2009-02-24 16:31:28 status unpacked libclass-accessor-perl 0.31-2
2009-02-24 16:31:28 status half-configured libclass-accessor-perl 0.31-2
2009-02-24 16:31:28 status installed libclass-accessor-perl 0.31-2
2009-02-24 16:31:28 configure libcompress-raw-zlib-perl 2.011-2build1 2.011-2build1
2009-02-24 16:31:28 status unpacked libcompress-raw-zlib-perl 2.011-2build1
2009-02-24 16:31:28 status half-configured libcompress-raw-zlib-perl 2.011-2build1
2009-02-24 16:31:28 status installed libcompress-raw-zlib-perl 2.011-2build1
2009-02-24 16:31:28 configure libio-compress-base-perl 2.011-1 2.011-1
2009-02-24 16:31:28 status unpacked libio-compress-base-perl 2.011-1
2009-02-24 16:31:28 status half-configured libio-compress-base-perl 2.011-1
2009-02-24 16:31:28 status installed libio-compress-base-perl 2.011-1
2009-02-24 16:31:28 configure libio-compress-zlib-perl 2.011-1 2.011-1
2009-02-24 16:31:28 status unpacked libio-compress-zlib-perl 2.011-1
2009-02-24 16:31:28 status half-configured libio-compress-zlib-perl 2.011-1
2009-02-24 16:31:28 status installed libio-compress-zlib-perl 2.011-1
2009-02-24 16:31:28 configure libcompress-zlib-perl 2.011-1 2.011-1
2009-02-24 16:31:28 status unpacked libcompress-zlib-perl 2.011-1
2009-02-24 16:31:28 status half-configured libcompress-zlib-perl 2.011-1
2009-02-24 16:31:28 status installed libcompress-zlib-perl 2.011-1
2009-02-24 16:31:28 configure libfont-afm-perl 1.20-1 1.20-1
2009-02-24 16:31:28 status unpacked libfont-afm-perl 1.20-1
2009-02-24 16:31:28 status half-configured libfont-afm-perl 1.20-1
2009-02-24 16:31:28 status installed libfont-afm-perl 1.20-1
2009-02-24 16:31:28 configure libhtml-format-perl 2.04-2 2.04-2
2009-02-24 16:31:28 status unpacked libhtml-format-perl 2.04-2
2009-02-24 16:31:28 status half-configured libhtml-format-perl 2.04-2
2009-02-24 16:31:28 status installed libhtml-format-perl 2.04-2
2009-02-24 16:31:28 configure libhtml-template-perl 2.9-1 2.9-1
2009-02-24 16:31:28 status unpacked libhtml-template-perl 2.9-1
2009-02-24 16:31:28 status half-configured libhtml-template-perl 2.9-1
2009-02-24 16:31:28 status installed libhtml-template-perl 2.9-1
2009-02-24 16:31:28 configure libio-string-perl 1.08-2 1.08-2
2009-02-24 16:31:28 status unpacked libio-string-perl 1.08-2
2009-02-24 16:31:28 status half-configured libio-string-perl 1.08-2
2009-02-24 16:31:28 status installed libio-string-perl 1.08-2
2009-02-24 16:31:28 configure libtimedate-perl 1.1600-9 1.1600-9
2009-02-24 16:31:28 status unpacked libtimedate-perl 1.1600-9
2009-02-24 16:31:28 status half-configured libtimedate-perl 1.1600-9
2009-02-24 16:31:28 status installed libtimedate-perl 1.1600-9
2009-02-24 16:31:28 configure libmailtools-perl 2.03-1 2.03-1
2009-02-24 16:31:28 status unpacked libmailtools-perl 2.03-1
2009-02-24 16:31:28 status half-configured libmailtools-perl 2.03-1
2009-02-24 16:31:28 status installed libmailtools-perl 2.03-1
2009-02-24 16:31:28 configure libparse-debianchangelog-perl 1.1.1-2 1.1.1-2
2009-02-24 16:31:28 status unpacked libparse-debianchangelog-perl 1.1.1-2
2009-02-24 16:31:28 status half-configured libparse-debianchangelog-perl 1.1.1-2
2009-02-24 16:31:28 status installed libparse-debianchangelog-perl 1.1.1-2
2009-02-24 16:31:28 configure libxml-namespacesupport-perl 1.09-3 1.09-3
2009-02-24 16:31:28 status unpacked libxml-namespacesupport-perl 1.09-3
2009-02-24 16:31:28 status half-configured libxml-namespacesupport-perl 1.09-3
2009-02-24 16:31:28 status installed libxml-namespacesupport-perl 1.09-3
2009-02-24 16:31:28 configure libxml-sax-perl 0.16+dfsg-3 0.16+dfsg-3
2009-02-24 16:31:28 status unpacked libxml-sax-perl 0.16+dfsg-3
2009-02-24 16:31:28 status half-configured libxml-sax-perl 0.16+dfsg-3
2009-02-24 16:31:29 status installed libxml-sax-perl 0.16+dfsg-3
2009-02-24 16:31:29 configure libxml-sax-expat-perl 0.39-1 0.39-1
2009-02-24 16:31:29 status unpacked libxml-sax-expat-perl 0.39-1
2009-02-24 16:31:29 status half-configured libxml-sax-expat-perl 0.39-1
2009-02-24 16:31:30 status installed libxml-sax-expat-perl 0.39-1
2009-02-24 16:31:30 configure libxml-simple-perl 2.18-1 2.18-1
2009-02-24 16:31:30 status unpacked libxml-simple-perl 2.18-1
2009-02-24 16:31:30 status half-configured libxml-simple-perl 2.18-1
2009-02-24 16:31:30 status installed libxml-simple-perl 2.18-1
2009-02-24 16:31:30 configure sgml-base 1.26 1.26
2009-02-24 16:31:30 status unpacked sgml-base 1.26
2009-02-24 16:31:30 status half-configured sgml-base 1.26
2009-02-24 16:31:30 status installed sgml-base 1.26
2009-02-24 16:31:30 configure xml-core 0.11ubuntu1 0.11ubuntu1
2009-02-24 16:31:30 status unpacked xml-core 0.11ubuntu1
2009-02-24 16:31:30 status half-configured xml-core 0.11ubuntu1
2009-02-24 16:31:30 status installed xml-core 0.11ubuntu1
2009-02-24 16:31:30 trigproc libc6 2.8~20080505-0ubuntu7 2.8~20080505-0ubuntu7
2009-02-24 16:31:30 status half-configured libc6 2.8~20080505-0ubuntu7
2009-02-24 16:31:30 status installed libc6 2.8~20080505-0ubuntu7
2009-02-24 16:31:30 trigproc python-support 0.8.4 0.8.4
2009-02-24 16:31:30 status half-configured python-support 0.8.4
2009-02-24 16:31:30 status installed python-support 0.8.4
2009-02-24 16:31:47 startup packages purge
2009-02-24 16:31:50 startup archives unpack
2009-02-24 16:31:50 install grub <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.97-29ubuntu45
2009-02-24 16:31:50 status half-installed grub 0.97-29ubuntu45
2009-02-24 16:31:50 status triggers-pending man-db 2.5.2-2
2009-02-24 16:31:50 status half-installed grub 0.97-29ubuntu45
2009-02-24 16:31:50 status unpacked grub 0.97-29ubuntu45
2009-02-24 16:31:50 status unpacked grub 0.97-29ubuntu45
2009-02-24 16:31:50 trigproc man-db 2.5.2-2 2.5.2-2
2009-02-24 16:31:50 status half-configured man-db 2.5.2-2
2009-02-24 16:31:51 status installed man-db 2.5.2-2
2009-02-24 16:31:51 startup packages configure
2009-02-24 16:31:51 configure grub 0.97-29ubuntu45 0.97-29ubuntu45
2009-02-24 16:31:51 status unpacked grub 0.97-29ubuntu45
2009-02-24 16:31:51 status unpacked grub 0.97-29ubuntu45
2009-02-24 16:31:51 status unpacked grub 0.97-29ubuntu45
2009-02-24 16:31:51 status unpacked grub 0.97-29ubuntu45
2009-02-24 16:31:51 status half-configured grub 0.97-29ubuntu45
2009-02-24 16:31:51 status installed grub 0.97-29ubuntu45
2009-02-24 16:32:21 startup archives unpack
2009-02-24 16:32:21 upgrade console-setup 1.25ubuntu3 1.25ubuntu4
2009-02-24 16:32:21 status half-configured console-setup 1.25ubuntu3
2009-02-24 16:32:21 status unpacked console-setup 1.25ubuntu3
2009-02-24 16:32:21 status half-installed console-setup 1.25ubuntu3
2009-02-24 16:32:21 status triggers-pending man-db 2.5.2-2
2009-02-24 16:32:21 status half-installed console-setup 1.25ubuntu3
2009-02-24 16:32:21 status half-installed console-setup 1.25ubuntu3
2009-02-24 16:32:21 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:21 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:21 trigproc man-db 2.5.2-2 2.5.2-2
2009-02-24 16:32:21 status half-configured man-db 2.5.2-2
2009-02-24 16:32:22 status installed man-db 2.5.2-2
2009-02-24 16:32:22 startup packages configure
2009-02-24 16:32:22 configure console-setup 1.25ubuntu4 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status unpacked console-setup 1.25ubuntu4
2009-02-24 16:32:22 status half-configured console-setup 1.25ubuntu4
2009-02-24 16:32:24 status installed console-setup 1.25ubuntu4
2009-02-24 16:32:24 status triggers-pending initramfs-tools 0.92bubuntu15
2009-02-24 16:32:24 trigproc initramfs-tools 0.92bubuntu15 0.92bubuntu15
2009-02-24 16:32:24 status half-configured initramfs-tools 0.92bubuntu15
2009-02-24 16:32:33 status installed initramfs-tools 0.92bubuntu15
2009-03-11 14:59:11 startup archives unpack
2009-03-11 14:59:13 upgrade ppp 2.4.4rel-10ubuntu2 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:13 status half-configured ppp 2.4.4rel-10ubuntu2
2009-03-11 14:59:13 status unpacked ppp 2.4.4rel-10ubuntu2
2009-03-11 14:59:13 status half-installed ppp 2.4.4rel-10ubuntu2
2009-03-11 14:59:13 status triggers-pending man-db 2.5.2-2
2009-03-11 14:59:13 status half-installed ppp 2.4.4rel-10ubuntu2
2009-03-11 14:59:13 status half-installed ppp 2.4.4rel-10ubuntu2
2009-03-11 14:59:13 status unpacked ppp 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:13 status unpacked ppp 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:13 install bcrelay <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.3.4-2.1ubuntu1
2009-03-11 14:59:13 status half-installed bcrelay 1.3.4-2.1ubuntu1
2009-03-11 14:59:14 status unpacked bcrelay 1.3.4-2.1ubuntu1
2009-03-11 14:59:14 status unpacked bcrelay 1.3.4-2.1ubuntu1
2009-03-11 14:59:14 install libwrap0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 7.6.q-15
2009-03-11 14:59:14 status half-installed libwrap0 7.6.q-15
2009-03-11 14:59:14 status unpacked libwrap0 7.6.q-15
2009-03-11 14:59:14 status unpacked libwrap0 7.6.q-15
2009-03-11 14:59:14 install pptpd <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.3.4-2.1ubuntu1
2009-03-11 14:59:14 status half-installed pptpd 1.3.4-2.1ubuntu1
2009-03-11 14:59:14 status half-installed pptpd 1.3.4-2.1ubuntu1
2009-03-11 14:59:14 status unpacked pptpd 1.3.4-2.1ubuntu1
2009-03-11 14:59:14 status unpacked pptpd 1.3.4-2.1ubuntu1
2009-03-11 14:59:14 install tcpd <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 7.6.q-15
2009-03-11 14:59:14 status half-installed tcpd 7.6.q-15
2009-03-11 14:59:14 status half-installed tcpd 7.6.q-15
2009-03-11 14:59:14 status unpacked tcpd 7.6.q-15
2009-03-11 14:59:14 status unpacked tcpd 7.6.q-15
2009-03-11 14:59:14 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-11 14:59:14 status half-configured man-db 2.5.2-2
2009-03-11 14:59:15 status installed man-db 2.5.2-2
2009-03-11 14:59:16 startup packages configure
2009-03-11 14:59:16 configure ppp 2.4.4rel-10ubuntu2.8.10.1 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:16 status unpacked ppp 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:16 status unpacked ppp 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:16 status unpacked ppp 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:16 status unpacked ppp 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:16 status unpacked ppp 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:16 status unpacked ppp 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:16 status unpacked ppp 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:16 status unpacked ppp 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:16 status unpacked ppp 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:16 status unpacked ppp 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:16 status unpacked ppp 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:16 status unpacked ppp 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:16 status unpacked ppp 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:16 status unpacked ppp 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:16 status unpacked ppp 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:16 status half-configured ppp 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:16 status installed ppp 2.4.4rel-10ubuntu2.8.10.1
2009-03-11 14:59:16 configure bcrelay 1.3.4-2.1ubuntu1 1.3.4-2.1ubuntu1
2009-03-11 14:59:16 status unpacked bcrelay 1.3.4-2.1ubuntu1
2009-03-11 14:59:16 status half-configured bcrelay 1.3.4-2.1ubuntu1
2009-03-11 14:59:16 status installed bcrelay 1.3.4-2.1ubuntu1
2009-03-11 14:59:16 configure libwrap0 7.6.q-15 7.6.q-15
2009-03-11 14:59:16 status unpacked libwrap0 7.6.q-15
2009-03-11 14:59:16 status half-configured libwrap0 7.6.q-15
2009-03-11 14:59:16 status installed libwrap0 7.6.q-15
2009-03-11 14:59:16 status triggers-pending libc6 2.8~20080505-0ubuntu7
2009-03-11 14:59:16 configure pptpd 1.3.4-2.1ubuntu1 1.3.4-2.1ubuntu1
2009-03-11 14:59:16 status unpacked pptpd 1.3.4-2.1ubuntu1
2009-03-11 14:59:16 status unpacked pptpd 1.3.4-2.1ubuntu1
2009-03-11 14:59:16 status unpacked pptpd 1.3.4-2.1ubuntu1
2009-03-11 14:59:16 status unpacked pptpd 1.3.4-2.1ubuntu1
2009-03-11 14:59:16 status half-configured pptpd 1.3.4-2.1ubuntu1
2009-03-11 14:59:16 status installed pptpd 1.3.4-2.1ubuntu1
2009-03-11 14:59:16 configure tcpd 7.6.q-15 7.6.q-15
2009-03-11 14:59:16 status unpacked tcpd 7.6.q-15
2009-03-11 14:59:16 status half-configured tcpd 7.6.q-15
2009-03-11 14:59:17 status installed tcpd 7.6.q-15
2009-03-11 14:59:17 trigproc libc6 2.8~20080505-0ubuntu7 2.8~20080505-0ubuntu7
2009-03-11 14:59:17 status half-configured libc6 2.8~20080505-0ubuntu7
2009-03-11 14:59:17 status installed libc6 2.8~20080505-0ubuntu7
2009-03-11 15:23:20 startup archives unpack
2009-03-11 15:23:22 install libxfixes3 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:4.0.3-2
2009-03-11 15:23:22 status half-installed libxfixes3 1:4.0.3-2
2009-03-11 15:23:22 status unpacked libxfixes3 1:4.0.3-2
2009-03-11 15:23:22 status unpacked libxfixes3 1:4.0.3-2
2009-03-11 15:23:22 install acl <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.2.47-2
2009-03-11 15:23:22 status half-installed acl 2.2.47-2
2009-03-11 15:23:22 status triggers-pending man-db 2.5.2-2
2009-03-11 15:23:22 status half-installed acl 2.2.47-2
2009-03-11 15:23:22 status unpacked acl 2.2.47-2
2009-03-11 15:23:22 status unpacked acl 2.2.47-2
2009-03-11 15:23:22 install libaspell15 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.60.6-1
2009-03-11 15:23:22 status half-installed libaspell15 0.60.6-1
2009-03-11 15:23:22 status unpacked libaspell15 0.60.6-1
2009-03-11 15:23:22 status unpacked libaspell15 0.60.6-1
2009-03-11 15:23:22 install dictionaries-common <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.98.9ubuntu1
2009-03-11 15:23:22 status half-installed dictionaries-common 0.98.9ubuntu1
2009-03-11 15:23:22 status half-installed dictionaries-common 0.98.9ubuntu1
2009-03-11 15:23:22 status unpacked dictionaries-common 0.98.9ubuntu1
2009-03-11 15:23:22 status unpacked dictionaries-common 0.98.9ubuntu1
2009-03-11 15:23:22 install aspell <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.60.6-1
2009-03-11 15:23:22 status half-installed aspell 0.60.6-1
2009-03-11 15:23:22 status half-installed aspell 0.60.6-1
2009-03-11 15:23:22 status unpacked aspell 0.60.6-1
2009-03-11 15:23:22 status unpacked aspell 0.60.6-1
2009-03-11 15:23:22 install aspell-en <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 6.0-0-5.1
2009-03-11 15:23:22 status half-installed aspell-en 6.0-0-5.1
2009-03-11 15:23:22 status unpacked aspell-en 6.0-0-5.1
2009-03-11 15:23:22 status unpacked aspell-en 6.0-0-5.1
2009-03-11 15:23:23 install defoma <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.11.10-0.2ubuntu1
2009-03-11 15:23:23 status half-installed defoma 0.11.10-0.2ubuntu1
2009-03-11 15:23:23 status half-installed defoma 0.11.10-0.2ubuntu1
2009-03-11 15:23:23 status unpacked defoma 0.11.10-0.2ubuntu1
2009-03-11 15:23:23 status unpacked defoma 0.11.10-0.2ubuntu1
2009-03-11 15:23:23 install sgml-data <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.0.3
2009-03-11 15:23:23 status half-installed sgml-data 2.0.3
2009-03-11 15:23:23 status unpacked sgml-data 2.0.3
2009-03-11 15:23:23 status unpacked sgml-data 2.0.3
2009-03-11 15:23:23 install docbook-xml <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 4.5-5
2009-03-11 15:23:23 status half-installed docbook-xml 4.5-5
2009-03-11 15:23:23 status unpacked docbook-xml 4.5-5
2009-03-11 15:23:23 status unpacked docbook-xml 4.5-5
2009-03-11 15:23:23 install libaudiofile0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.2.6-7ubuntu1
2009-03-11 15:23:23 status half-installed libaudiofile0 0.2.6-7ubuntu1
2009-03-11 15:23:23 status unpacked libaudiofile0 0.2.6-7ubuntu1
2009-03-11 15:23:23 status unpacked libaudiofile0 0.2.6-7ubuntu1
2009-03-11 15:23:23 install libasound2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.0.17a-0ubuntu4
2009-03-11 15:23:23 status half-installed libasound2 1.0.17a-0ubuntu4
2009-03-11 15:23:24 status unpacked libasound2 1.0.17a-0ubuntu4
2009-03-11 15:23:24 status unpacked libasound2 1.0.17a-0ubuntu4
2009-03-11 15:23:24 install esound-common <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.2.40-0ubuntu1
2009-03-11 15:23:24 status half-installed esound-common 0.2.40-0ubuntu1
2009-03-11 15:23:24 status unpacked esound-common 0.2.40-0ubuntu1
2009-03-11 15:23:24 status unpacked esound-common 0.2.40-0ubuntu1
2009-03-11 15:23:24 install libesd-alsa0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.2.40-0ubuntu1
2009-03-11 15:23:24 status half-installed libesd-alsa0 0.2.40-0ubuntu1
2009-03-11 15:23:24 status unpacked libesd-alsa0 0.2.40-0ubuntu1
2009-03-11 15:23:24 status unpacked libesd-alsa0 0.2.40-0ubuntu1
2009-03-11 15:23:24 install esound-clients <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.2.40-0ubuntu1
2009-03-11 15:23:24 status half-installed esound-clients 0.2.40-0ubuntu1
2009-03-11 15:23:24 status half-installed esound-clients 0.2.40-0ubuntu1
2009-03-11 15:23:24 status unpacked esound-clients 0.2.40-0ubuntu1
2009-03-11 15:23:24 status unpacked esound-clients 0.2.40-0ubuntu1
2009-03-11 15:23:24 install libfreetype6 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.3.7-2ubuntu1
2009-03-11 15:23:24 status half-installed libfreetype6 2.3.7-2ubuntu1
2009-03-11 15:23:24 status unpacked libfreetype6 2.3.7-2ubuntu1
2009-03-11 15:23:24 status unpacked libfreetype6 2.3.7-2ubuntu1
2009-03-11 15:23:24 install ttf-dejavu-core <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.25-1
2009-03-11 15:23:24 status half-installed ttf-dejavu-core 2.25-1
2009-03-11 15:23:24 status unpacked ttf-dejavu-core 2.25-1
2009-03-11 15:23:24 status unpacked ttf-dejavu-core 2.25-1
2009-03-11 15:23:24 install ttf-dejavu-extra <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.25-1
2009-03-11 15:23:24 status half-installed ttf-dejavu-extra 2.25-1
2009-03-11 15:23:24 status unpacked ttf-dejavu-extra 2.25-1
2009-03-11 15:23:24 status unpacked ttf-dejavu-extra 2.25-1
2009-03-11 15:23:24 install ttf-dejavu <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.25-1
2009-03-11 15:23:24 status half-installed ttf-dejavu 2.25-1
2009-03-11 15:23:25 status unpacked ttf-dejavu 2.25-1
2009-03-11 15:23:25 status unpacked ttf-dejavu 2.25-1
2009-03-11 15:23:25 install fontconfig-config <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.6.0-1ubuntu4
2009-03-11 15:23:25 status half-installed fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:25 status half-installed fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:25 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:25 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:25 install libfontconfig1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.6.0-1ubuntu4
2009-03-11 15:23:25 status half-installed libfontconfig1 2.6.0-1ubuntu4
2009-03-11 15:23:25 status unpacked libfontconfig1 2.6.0-1ubuntu4
2009-03-11 15:23:25 status unpacked libfontconfig1 2.6.0-1ubuntu4
2009-03-11 15:23:25 install fontconfig <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.6.0-1ubuntu4
2009-03-11 15:23:25 status half-installed fontconfig 2.6.0-1ubuntu4
2009-03-11 15:23:25 status half-installed fontconfig 2.6.0-1ubuntu4
2009-03-11 15:23:25 status unpacked fontconfig 2.6.0-1ubuntu4
2009-03-11 15:23:25 status unpacked fontconfig 2.6.0-1ubuntu4
2009-03-11 15:23:25 install libgamin0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.1.9-2ubuntu2
2009-03-11 15:23:25 status half-installed libgamin0 0.1.9-2ubuntu2
2009-03-11 15:23:25 status unpacked libgamin0 0.1.9-2ubuntu2
2009-03-11 15:23:25 status unpacked libgamin0 0.1.9-2ubuntu2
2009-03-11 15:23:25 install gamin <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.1.9-2ubuntu2
2009-03-11 15:23:25 status half-installed gamin 0.1.9-2ubuntu2
2009-03-11 15:23:25 status unpacked gamin 0.1.9-2ubuntu2
2009-03-11 15:23:25 status unpacked gamin 0.1.9-2ubuntu2
2009-03-11 15:23:25 install libidl0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.8.10-0.1
2009-03-11 15:23:25 status half-installed libidl0 0.8.10-0.1
2009-03-11 15:23:25 status unpacked libidl0 0.8.10-0.1
2009-03-11 15:23:25 status unpacked libidl0 0.8.10-0.1
2009-03-11 15:23:25 install liborbit2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:2.14.16-0ubuntu1
2009-03-11 15:23:25 status half-installed liborbit2 1:2.14.16-0ubuntu1
2009-03-11 15:23:25 status unpacked liborbit2 1:2.14.16-0ubuntu1
2009-03-11 15:23:25 status unpacked liborbit2 1:2.14.16-0ubuntu1
2009-03-11 15:23:25 install libpolkit-dbus2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.9-1ubuntu3
2009-03-11 15:23:25 status half-installed libpolkit-dbus2 0.9-1ubuntu3
2009-03-11 15:23:25 status unpacked libpolkit-dbus2 0.9-1ubuntu3
2009-03-11 15:23:25 status unpacked libpolkit-dbus2 0.9-1ubuntu3
2009-03-11 15:23:25 install gconf2-common <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.0-0ubuntu1
2009-03-11 15:23:25 status half-installed gconf2-common 2.24.0-0ubuntu1
2009-03-11 15:23:25 status unpacked gconf2-common 2.24.0-0ubuntu1
2009-03-11 15:23:25 status unpacked gconf2-common 2.24.0-0ubuntu1
2009-03-11 15:23:25 install libgconf2-4 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.0-0ubuntu1
2009-03-11 15:23:25 status half-installed libgconf2-4 2.24.0-0ubuntu1
2009-03-11 15:23:25 status unpacked libgconf2-4 2.24.0-0ubuntu1
2009-03-11 15:23:25 status unpacked libgconf2-4 2.24.0-0ubuntu1
2009-03-11 15:23:25 install gconf2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.0-0ubuntu1
2009-03-11 15:23:25 status half-installed gconf2 2.24.0-0ubuntu1
2009-03-11 15:23:25 status half-installed gconf2 2.24.0-0ubuntu1
2009-03-11 15:23:25 status unpacked gconf2 2.24.0-0ubuntu1
2009-03-11 15:23:25 status unpacked gconf2 2.24.0-0ubuntu1
2009-03-11 15:23:25 install libatk1.0-0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.24.0-0ubuntu1
2009-03-11 15:23:25 status half-installed libatk1.0-0 1.24.0-0ubuntu1
2009-03-11 15:23:25 status unpacked libatk1.0-0 1.24.0-0ubuntu1
2009-03-11 15:23:25 status unpacked libatk1.0-0 1.24.0-0ubuntu1
2009-03-11 15:23:25 install libpixman-1-0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.12.0-1
2009-03-11 15:23:25 status half-installed libpixman-1-0 0.12.0-1
2009-03-11 15:23:26 status unpacked libpixman-1-0 0.12.0-1
2009-03-11 15:23:26 status unpacked libpixman-1-0 0.12.0-1
2009-03-11 15:23:26 install libpng12-0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.2.27-1
2009-03-11 15:23:26 status half-installed libpng12-0 1.2.27-1
2009-03-11 15:23:26 status unpacked libpng12-0 1.2.27-1
2009-03-11 15:23:26 status unpacked libpng12-0 1.2.27-1
2009-03-11 15:23:26 install libxcb-render0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.1-1.1
2009-03-11 15:23:26 status half-installed libxcb-render0 1.1-1.1
2009-03-11 15:23:26 status unpacked libxcb-render0 1.1-1.1
2009-03-11 15:23:26 status unpacked libxcb-render0 1.1-1.1
2009-03-11 15:23:26 install libxcb-render-util0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.2+git36-1
2009-03-11 15:23:26 status half-installed libxcb-render-util0 0.2+git36-1
2009-03-11 15:23:26 status unpacked libxcb-render-util0 0.2+git36-1
2009-03-11 15:23:26 status unpacked libxcb-render-util0 0.2+git36-1
2009-03-11 15:23:26 install libxrender1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:0.9.4-2
2009-03-11 15:23:26 status half-installed libxrender1 1:0.9.4-2
2009-03-11 15:23:26 status unpacked libxrender1 1:0.9.4-2
2009-03-11 15:23:26 status unpacked libxrender1 1:0.9.4-2
2009-03-11 15:23:26 install libcairo2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.8.0-0ubuntu1.1
2009-03-11 15:23:26 status half-installed libcairo2 1.8.0-0ubuntu1.1
2009-03-11 15:23:26 status unpacked libcairo2 1.8.0-0ubuntu1.1
2009-03-11 15:23:26 status unpacked libcairo2 1.8.0-0ubuntu1.1
2009-03-11 15:23:26 install libhunspell-1.2-0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.2.6-1ubuntu1
2009-03-11 15:23:26 status half-installed libhunspell-1.2-0 1.2.6-1ubuntu1
2009-03-11 15:23:26 status unpacked libhunspell-1.2-0 1.2.6-1ubuntu1
2009-03-11 15:23:26 status unpacked libhunspell-1.2-0 1.2.6-1ubuntu1
2009-03-11 15:23:26 install libenchant1c2a <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.4.2-3.1ubuntu2
2009-03-11 15:23:26 status half-installed libenchant1c2a 1.4.2-3.1ubuntu2
2009-03-11 15:23:26 status half-installed libenchant1c2a 1.4.2-3.1ubuntu2
2009-03-11 15:23:26 status unpacked libenchant1c2a 1.4.2-3.1ubuntu2
2009-03-11 15:23:26 status unpacked libenchant1c2a 1.4.2-3.1ubuntu2
2009-03-11 15:23:26 install libgtk2.0-common <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.14.4-0ubuntu1
2009-03-11 15:23:26 status half-installed libgtk2.0-common 2.14.4-0ubuntu1
2009-03-11 15:23:26 status unpacked libgtk2.0-common 2.14.4-0ubuntu1
2009-03-11 15:23:26 status unpacked libgtk2.0-common 2.14.4-0ubuntu1
2009-03-11 15:23:26 install libcups2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.3.9-2ubuntu7
2009-03-11 15:23:26 status half-installed libcups2 1.3.9-2ubuntu7
2009-03-11 15:23:26 status unpacked libcups2 1.3.9-2ubuntu7
2009-03-11 15:23:26 status unpacked libcups2 1.3.9-2ubuntu7
2009-03-11 15:23:26 install libjpeg62 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 6b-14
2009-03-11 15:23:26 status half-installed libjpeg62 6b-14
2009-03-11 15:23:26 status unpacked libjpeg62 6b-14
2009-03-11 15:23:26 status unpacked libjpeg62 6b-14
2009-03-11 15:23:26 install libpango1.0-common <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.22.2-0ubuntu1
2009-03-11 15:23:26 status half-installed libpango1.0-common 1.22.2-0ubuntu1
2009-03-11 15:23:26 status half-installed libpango1.0-common 1.22.2-0ubuntu1
2009-03-11 15:23:26 status unpacked libpango1.0-common 1.22.2-0ubuntu1
2009-03-11 15:23:26 status unpacked libpango1.0-common 1.22.2-0ubuntu1
2009-03-11 15:23:26 install libdatrie0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.1.3-2
2009-03-11 15:23:26 status half-installed libdatrie0 0.1.3-2
2009-03-11 15:23:26 status unpacked libdatrie0 0.1.3-2
2009-03-11 15:23:26 status unpacked libdatrie0 0.1.3-2
2009-03-11 15:23:26 install libthai-data <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.1.9-4
2009-03-11 15:23:26 status half-installed libthai-data 0.1.9-4
2009-03-11 15:23:27 status unpacked libthai-data 0.1.9-4
2009-03-11 15:23:27 status unpacked libthai-data 0.1.9-4
2009-03-11 15:23:27 install libthai0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.1.9-4
2009-03-11 15:23:27 status half-installed libthai0 0.1.9-4
2009-03-11 15:23:27 status unpacked libthai0 0.1.9-4
2009-03-11 15:23:27 status unpacked libthai0 0.1.9-4
2009-03-11 15:23:27 install libxft2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.1.12-3ubuntu1
2009-03-11 15:23:27 status half-installed libxft2 2.1.12-3ubuntu1
2009-03-11 15:23:27 status unpacked libxft2 2.1.12-3ubuntu1
2009-03-11 15:23:27 status unpacked libxft2 2.1.12-3ubuntu1
2009-03-11 15:23:27 install libpango1.0-0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.22.2-0ubuntu1
2009-03-11 15:23:27 status half-installed libpango1.0-0 1.22.2-0ubuntu1
2009-03-11 15:23:27 status unpacked libpango1.0-0 1.22.2-0ubuntu1
2009-03-11 15:23:27 status unpacked libpango1.0-0 1.22.2-0ubuntu1
2009-03-11 15:23:27 install libtiff4 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 3.8.2-11
2009-03-11 15:23:27 status half-installed libtiff4 3.8.2-11
2009-03-11 15:23:27 status unpacked libtiff4 3.8.2-11
2009-03-11 15:23:27 status unpacked libtiff4 3.8.2-11
2009-03-11 15:23:27 install libxcomposite1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:0.4.0-3
2009-03-11 15:23:27 status half-installed libxcomposite1 1:0.4.0-3
2009-03-11 15:23:27 status unpacked libxcomposite1 1:0.4.0-3
2009-03-11 15:23:27 status unpacked libxcomposite1 1:0.4.0-3
2009-03-11 15:23:27 install libxcursor1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:1.1.9-1
2009-03-11 15:23:27 status half-installed libxcursor1 1:1.1.9-1
2009-03-11 15:23:27 status unpacked libxcursor1 1:1.1.9-1
2009-03-11 15:23:27 status unpacked libxcursor1 1:1.1.9-1
2009-03-11 15:23:27 install libxdamage1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:1.1.1-4
2009-03-11 15:23:27 status half-installed libxdamage1 1:1.1.1-4
2009-03-11 15:23:27 status unpacked libxdamage1 1:1.1.1-4
2009-03-11 15:23:27 status unpacked libxdamage1 1:1.1.1-4
2009-03-11 15:23:27 install libxi6 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2:1.1.3-2build1
2009-03-11 15:23:27 status half-installed libxi6 2:1.1.3-2build1
2009-03-11 15:23:27 status unpacked libxi6 2:1.1.3-2build1
2009-03-11 15:23:27 status unpacked libxi6 2:1.1.3-2build1
2009-03-11 15:23:27 install libxinerama1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2:1.0.3-2
2009-03-11 15:23:27 status half-installed libxinerama1 2:1.0.3-2
2009-03-11 15:23:27 status unpacked libxinerama1 2:1.0.3-2
2009-03-11 15:23:27 status unpacked libxinerama1 2:1.0.3-2
2009-03-11 15:23:27 install libxrandr2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2:1.2.3-1
2009-03-11 15:23:27 status half-installed libxrandr2 2:1.2.3-1
2009-03-11 15:23:27 status unpacked libxrandr2 2:1.2.3-1
2009-03-11 15:23:27 status unpacked libxrandr2 2:1.2.3-1
2009-03-11 15:23:27 install libgtk2.0-0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.14.4-0ubuntu1
2009-03-11 15:23:27 status half-installed libgtk2.0-0 2.14.4-0ubuntu1
2009-03-11 15:23:28 status unpacked libgtk2.0-0 2.14.4-0ubuntu1
2009-03-11 15:23:28 status unpacked libgtk2.0-0 2.14.4-0ubuntu1
2009-03-11 15:23:28 install libgtksourceview2.0-common <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.4.1-0ubuntu1
2009-03-11 15:23:28 status half-installed libgtksourceview2.0-common 2.4.1-0ubuntu1
2009-03-11 15:23:29 status unpacked libgtksourceview2.0-common 2.4.1-0ubuntu1
2009-03-11 15:23:29 status unpacked libgtksourceview2.0-common 2.4.1-0ubuntu1
2009-03-11 15:23:29 install libgtksourceview2.0-0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.4.1-0ubuntu1
2009-03-11 15:23:29 status half-installed libgtksourceview2.0-0 2.4.1-0ubuntu1
2009-03-11 15:23:29 status unpacked libgtksourceview2.0-0 2.4.1-0ubuntu1
2009-03-11 15:23:29 status unpacked libgtksourceview2.0-0 2.4.1-0ubuntu1
2009-03-11 15:23:29 install libice6 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2:1.0.4-1
2009-03-11 15:23:29 status half-installed libice6 2:1.0.4-1
2009-03-11 15:23:29 status unpacked libice6 2:1.0.4-1
2009-03-11 15:23:29 status unpacked libice6 2:1.0.4-1
2009-03-11 15:23:29 install liblaunchpad-integration1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.1.21
2009-03-11 15:23:29 status half-installed liblaunchpad-integration1 0.1.21
2009-03-11 15:23:29 status unpacked liblaunchpad-integration1 0.1.21
2009-03-11 15:23:29 status unpacked liblaunchpad-integration1 0.1.21
2009-03-11 15:23:29 install libsm6 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2:1.0.3-2
2009-03-11 15:23:29 status half-installed libsm6 2:1.0.3-2
2009-03-11 15:23:29 status unpacked libsm6 2:1.0.3-2
2009-03-11 15:23:29 status unpacked libsm6 2:1.0.3-2
2009-03-11 15:23:29 install libxslt1.1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.1.24-1ubuntu2
2009-03-11 15:23:29 status half-installed libxslt1.1 1.1.24-1ubuntu2
2009-03-11 15:23:29 status unpacked libxslt1.1 1.1.24-1ubuntu2
2009-03-11 15:23:29 status unpacked libxslt1.1 1.1.24-1ubuntu2
2009-03-11 15:23:29 install libscrollkeeper0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.3.14-16ubuntu1
2009-03-11 15:23:29 status half-installed libscrollkeeper0 0.3.14-16ubuntu1
2009-03-11 15:23:29 status unpacked libscrollkeeper0 0.3.14-16ubuntu1
2009-03-11 15:23:29 status unpacked libscrollkeeper0 0.3.14-16ubuntu1
2009-03-11 15:23:29 install scrollkeeper <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.3.14-16ubuntu1
2009-03-11 15:23:29 status half-installed scrollkeeper 0.3.14-16ubuntu1
2009-03-11 15:23:29 status half-installed scrollkeeper 0.3.14-16ubuntu1
2009-03-11 15:23:30 status unpacked scrollkeeper 0.3.14-16ubuntu1
2009-03-11 15:23:30 status unpacked scrollkeeper 0.3.14-16ubuntu1
2009-03-11 15:23:30 install gedit-common <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.2-0ubuntu1
2009-03-11 15:23:30 status half-installed gedit-common 2.24.2-0ubuntu1
2009-03-11 15:23:30 status half-installed gedit-common 2.24.2-0ubuntu1
2009-03-11 15:23:30 status unpacked gedit-common 2.24.2-0ubuntu1
2009-03-11 15:23:30 status unpacked gedit-common 2.24.2-0ubuntu1
2009-03-11 15:23:30 install python-cairo <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.4.12-1
2009-03-11 15:23:30 status half-installed python-cairo 1.4.12-1
2009-03-11 15:23:31 status unpacked python-cairo 1.4.12-1
2009-03-11 15:23:31 status unpacked python-cairo 1.4.12-1
2009-03-11 15:23:31 install python-numeric <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 24.2-9
2009-03-11 15:23:31 status half-installed python-numeric 24.2-9
2009-03-11 15:23:31 status unpacked python-numeric 24.2-9
2009-03-11 15:23:31 status unpacked python-numeric 24.2-9
2009-03-11 15:23:31 install python-gtk2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.13.0-0ubuntu8
2009-03-11 15:23:31 status half-installed python-gtk2 2.13.0-0ubuntu8
2009-03-11 15:23:32 status unpacked python-gtk2 2.13.0-0ubuntu8
2009-03-11 15:23:32 status unpacked python-gtk2 2.13.0-0ubuntu8
2009-03-11 15:23:32 install python-gtksourceview2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.4.0-0ubuntu1
2009-03-11 15:23:32 status half-installed python-gtksourceview2 2.4.0-0ubuntu1
2009-03-11 15:23:32 status unpacked python-gtksourceview2 2.4.0-0ubuntu1
2009-03-11 15:23:32 status unpacked python-gtksourceview2 2.4.0-0ubuntu1
2009-03-11 15:23:32 install iso-codes <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 3.2-1
2009-03-11 15:23:32 status half-installed iso-codes 3.2-1
2009-03-11 15:23:33 status unpacked iso-codes 3.2-1
2009-03-11 15:23:33 status unpacked iso-codes 3.2-1
2009-03-11 15:23:33 install gedit <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.2-0ubuntu1
2009-03-11 15:23:33 status half-installed gedit 2.24.2-0ubuntu1
2009-03-11 15:23:33 status unpacked gedit 2.24.2-0ubuntu1
2009-03-11 15:23:33 status unpacked gedit 2.24.2-0ubuntu1
2009-03-11 15:23:33 install libgp11-0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.1-0ubuntu1
2009-03-11 15:23:33 status half-installed libgp11-0 2.24.1-0ubuntu1
2009-03-11 15:23:33 status unpacked libgp11-0 2.24.1-0ubuntu1
2009-03-11 15:23:33 status unpacked libgp11-0 2.24.1-0ubuntu1
2009-03-11 15:23:33 install libhal1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.5.11-4ubuntu4
2009-03-11 15:23:33 status half-installed libhal1 0.5.11-4ubuntu4
2009-03-11 15:23:33 status unpacked libhal1 0.5.11-4ubuntu4
2009-03-11 15:23:33 status unpacked libhal1 0.5.11-4ubuntu4
2009-03-11 15:23:33 install libhal-storage1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.5.11-4ubuntu4
2009-03-11 15:23:33 status half-installed libhal-storage1 0.5.11-4ubuntu4
2009-03-11 15:23:33 status unpacked libhal-storage1 0.5.11-4ubuntu4
2009-03-11 15:23:33 status unpacked libhal-storage1 0.5.11-4ubuntu4
2009-03-11 15:23:33 install gnome-keyring <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.1-0ubuntu1
2009-03-11 15:23:33 status half-installed gnome-keyring 2.24.1-0ubuntu1
2009-03-11 15:23:33 status half-installed gnome-keyring 2.24.1-0ubuntu1
2009-03-11 15:23:33 status unpacked gnome-keyring 2.24.1-0ubuntu1
2009-03-11 15:23:33 status unpacked gnome-keyring 2.24.1-0ubuntu1
2009-03-11 15:23:33 install gnome-mime-data <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.18.0-1
2009-03-11 15:23:33 status half-installed gnome-mime-data 2.18.0-1
2009-03-11 15:23:34 status unpacked gnome-mime-data 2.18.0-1
2009-03-11 15:23:34 status unpacked gnome-mime-data 2.18.0-1
2009-03-11 15:23:34 install libgnome-keyring0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.1-0ubuntu1
2009-03-11 15:23:34 status half-installed libgnome-keyring0 2.24.1-0ubuntu1
2009-03-11 15:23:34 status unpacked libgnome-keyring0 2.24.1-0ubuntu1
2009-03-11 15:23:34 status unpacked libgnome-keyring0 2.24.1-0ubuntu1
2009-03-11 15:23:34 install libnotify1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.4.4-3build1
2009-03-11 15:23:34 status half-installed libnotify1 0.4.4-3build1
2009-03-11 15:23:34 status unpacked libnotify1 0.4.4-3build1
2009-03-11 15:23:34 status unpacked libnotify1 0.4.4-3build1
2009-03-11 15:23:34 install libsmbios2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.0.3-0ubuntu1
2009-03-11 15:23:34 status half-installed libsmbios2 2.0.3-0ubuntu1
2009-03-11 15:23:34 status unpacked libsmbios2 2.0.3-0ubuntu1
2009-03-11 15:23:34 status unpacked libsmbios2 2.0.3-0ubuntu1
2009-03-11 15:23:34 install hal-info <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 20090128-0ubuntu1~intrepid2
2009-03-11 15:23:34 status half-installed hal-info 20090128-0ubuntu1~intrepid2
2009-03-11 15:23:34 status unpacked hal-info 20090128-0ubuntu1~intrepid2
2009-03-11 15:23:34 status unpacked hal-info 20090128-0ubuntu1~intrepid2
2009-03-11 15:23:34 install powermgmt-base <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.30
2009-03-11 15:23:34 status half-installed powermgmt-base 1.30
2009-03-11 15:23:34 status half-installed powermgmt-base 1.30
2009-03-11 15:23:34 status unpacked powermgmt-base 1.30
2009-03-11 15:23:34 status unpacked powermgmt-base 1.30
2009-03-11 15:23:34 install pm-utils <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.1.2.4-1ubuntu8
2009-03-11 15:23:34 status half-installed pm-utils 1.1.2.4-1ubuntu8
2009-03-11 15:23:34 status half-installed pm-utils 1.1.2.4-1ubuntu8
2009-03-11 15:23:34 status unpacked pm-utils 1.1.2.4-1ubuntu8
2009-03-11 15:23:34 status unpacked pm-utils 1.1.2.4-1ubuntu8
2009-03-11 15:23:34 install libpolkit-grant2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.9-1ubuntu3
2009-03-11 15:23:34 status half-installed libpolkit-grant2 0.9-1ubuntu3
2009-03-11 15:23:34 status unpacked libpolkit-grant2 0.9-1ubuntu3
2009-03-11 15:23:34 status unpacked libpolkit-grant2 0.9-1ubuntu3
2009-03-11 15:23:34 install policykit <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.9-1ubuntu3
2009-03-11 15:23:34 status half-installed policykit 0.9-1ubuntu3
2009-03-11 15:23:34 status half-installed policykit 0.9-1ubuntu3
2009-03-11 15:23:34 status unpacked policykit 0.9-1ubuntu3
2009-03-11 15:23:34 status unpacked policykit 0.9-1ubuntu3
2009-03-11 15:23:34 install hal <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.5.11-4ubuntu4
2009-03-11 15:23:34 status half-installed hal 0.5.11-4ubuntu4
2009-03-11 15:23:35 status half-installed hal 0.5.11-4ubuntu4
2009-03-11 15:23:35 status unpacked hal 0.5.11-4ubuntu4
2009-03-11 15:23:35 status unpacked hal 0.5.11-4ubuntu4
2009-03-11 15:23:35 install libavahi-common-data <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.6.23-2ubuntu2.1
2009-03-11 15:23:35 status half-installed libavahi-common-data 0.6.23-2ubuntu2.1
2009-03-11 15:23:35 status unpacked libavahi-common-data 0.6.23-2ubuntu2.1
2009-03-11 15:23:35 status unpacked libavahi-common-data 0.6.23-2ubuntu2.1
2009-03-11 15:23:35 install libavahi-common3 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.6.23-2ubuntu2.1
2009-03-11 15:23:35 status half-installed libavahi-common3 0.6.23-2ubuntu2.1
2009-03-11 15:23:35 status unpacked libavahi-common3 0.6.23-2ubuntu2.1
2009-03-11 15:23:35 status unpacked libavahi-common3 0.6.23-2ubuntu2.1
2009-03-11 15:23:35 install libavahi-client3 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.6.23-2ubuntu2.1
2009-03-11 15:23:35 status half-installed libavahi-client3 0.6.23-2ubuntu2.1
2009-03-11 15:23:35 status unpacked libavahi-client3 0.6.23-2ubuntu2.1
2009-03-11 15:23:35 status unpacked libavahi-client3 0.6.23-2ubuntu2.1
2009-03-11 15:23:35 install libavahi-glib1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.6.23-2ubuntu2.1
2009-03-11 15:23:35 status half-installed libavahi-glib1 0.6.23-2ubuntu2.1
2009-03-11 15:23:35 status unpacked libavahi-glib1 0.6.23-2ubuntu2.1
2009-03-11 15:23:35 status unpacked libavahi-glib1 0.6.23-2ubuntu2.1
2009-03-11 15:23:35 install shared-mime-info <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.51-0ubuntu1
2009-03-11 15:23:35 status half-installed shared-mime-info 0.51-0ubuntu1
2009-03-11 15:23:35 status half-installed shared-mime-info 0.51-0ubuntu1
2009-03-11 15:23:35 status unpacked shared-mime-info 0.51-0ubuntu1
2009-03-11 15:23:35 status unpacked shared-mime-info 0.51-0ubuntu1
2009-03-11 15:23:35 install libgnomevfs2-common <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:2.24.0-0ubuntu1
2009-03-11 15:23:35 status half-installed libgnomevfs2-common 1:2.24.0-0ubuntu1
2009-03-11 15:23:35 status unpacked libgnomevfs2-common 1:2.24.0-0ubuntu1
2009-03-11 15:23:35 status unpacked libgnomevfs2-common 1:2.24.0-0ubuntu1
2009-03-11 15:23:35 install libgnomevfs2-0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:2.24.0-0ubuntu1
2009-03-11 15:23:35 status half-installed libgnomevfs2-0 1:2.24.0-0ubuntu1
2009-03-11 15:23:35 status unpacked libgnomevfs2-0 1:2.24.0-0ubuntu1
2009-03-11 15:23:35 status unpacked libgnomevfs2-0 1:2.24.0-0ubuntu1
2009-03-11 15:23:35 install libpolkit-gnome0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.9-1ubuntu1
2009-03-11 15:23:35 status half-installed libpolkit-gnome0 0.9-1ubuntu1
2009-03-11 15:23:35 status unpacked libpolkit-gnome0 0.9-1ubuntu1
2009-03-11 15:23:36 status unpacked libpolkit-gnome0 0.9-1ubuntu1
2009-03-11 15:23:36 install libsexy2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.1.11-2
2009-03-11 15:23:36 status half-installed libsexy2 0.1.11-2
2009-03-11 15:23:36 status unpacked libsexy2 0.1.11-2
2009-03-11 15:23:36 status unpacked libsexy2 0.1.11-2
2009-03-11 15:23:36 install policykit-gnome <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.9-1ubuntu1
2009-03-11 15:23:36 status half-installed policykit-gnome 0.9-1ubuntu1
2009-03-11 15:23:36 status unpacked policykit-gnome 0.9-1ubuntu1
2009-03-11 15:23:36 status unpacked policykit-gnome 0.9-1ubuntu1
2009-03-11 15:23:36 install gnome-mount <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.8-1ubuntu1
2009-03-11 15:23:36 status half-installed gnome-mount 0.8-1ubuntu1
2009-03-11 15:23:36 status half-installed gnome-mount 0.8-1ubuntu1
2009-03-11 15:23:36 status unpacked gnome-mount 0.8-1ubuntu1
2009-03-11 15:23:36 status unpacked gnome-mount 0.8-1ubuntu1
2009-03-11 15:23:36 install hicolor-icon-theme <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.10-1ubuntu1
2009-03-11 15:23:36 status half-installed hicolor-icon-theme 0.10-1ubuntu1
2009-03-11 15:23:36 status unpacked hicolor-icon-theme 0.10-1ubuntu1
2009-03-11 15:23:36 status unpacked hicolor-icon-theme 0.10-1ubuntu1
2009-03-11 15:23:36 install launchpad-integration <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.1.21
2009-03-11 15:23:36 status half-installed launchpad-integration 0.1.21
2009-03-11 15:23:36 status unpacked launchpad-integration 0.1.21
2009-03-11 15:23:36 status unpacked launchpad-integration 0.1.21
2009-03-11 15:23:36 install libart-2.0-2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.3.20-2
2009-03-11 15:23:36 status half-installed libart-2.0-2 2.3.20-2
2009-03-11 15:23:36 status unpacked libart-2.0-2 2.3.20-2
2009-03-11 15:23:36 status unpacked libart-2.0-2 2.3.20-2
2009-03-11 15:23:36 install libatk1.0-data <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.24.0-0ubuntu1
2009-03-11 15:23:36 status half-installed libatk1.0-data 1.24.0-0ubuntu1
2009-03-11 15:23:36 status unpacked libatk1.0-data 1.24.0-0ubuntu1
2009-03-11 15:23:36 status unpacked libatk1.0-data 1.24.0-0ubuntu1
2009-03-11 15:23:36 install libbonobo2-common <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.0-0ubuntu1
2009-03-11 15:23:36 status half-installed libbonobo2-common 2.24.0-0ubuntu1
2009-03-11 15:23:36 status half-installed libbonobo2-common 2.24.0-0ubuntu1
2009-03-11 15:23:36 status unpacked libbonobo2-common 2.24.0-0ubuntu1
2009-03-11 15:23:36 status unpacked libbonobo2-common 2.24.0-0ubuntu1
2009-03-11 15:23:36 install libbonobo2-0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.0-0ubuntu1
2009-03-11 15:23:36 status half-installed libbonobo2-0 2.24.0-0ubuntu1
2009-03-11 15:23:36 status unpacked libbonobo2-0 2.24.0-0ubuntu1
2009-03-11 15:23:36 status unpacked libbonobo2-0 2.24.0-0ubuntu1
2009-03-11 15:23:36 install libglade2-0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:2.6.3-0ubuntu1
2009-03-11 15:23:36 status half-installed libglade2-0 1:2.6.3-0ubuntu1
2009-03-11 15:23:36 status unpacked libglade2-0 1:2.6.3-0ubuntu1
2009-03-11 15:23:37 status unpacked libglade2-0 1:2.6.3-0ubuntu1
2009-03-11 15:23:37 install libgnome2-common <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.1-0ubuntu4
2009-03-11 15:23:37 status half-installed libgnome2-common 2.24.1-0ubuntu4
2009-03-11 15:23:37 status half-installed libgnome2-common 2.24.1-0ubuntu4
2009-03-11 15:23:37 status unpacked libgnome2-common 2.24.1-0ubuntu4
2009-03-11 15:23:37 status unpacked libgnome2-common 2.24.1-0ubuntu4
2009-03-11 15:23:37 install libgnome2-0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.1-0ubuntu4
2009-03-11 15:23:37 status half-installed libgnome2-0 2.24.1-0ubuntu4
2009-03-11 15:23:37 status unpacked libgnome2-0 2.24.1-0ubuntu4
2009-03-11 15:23:37 status unpacked libgnome2-0 2.24.1-0ubuntu4
2009-03-11 15:23:37 install libgnomecanvas2-common <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.20.1.1-1ubuntu3
2009-03-11 15:23:37 status half-installed libgnomecanvas2-common 2.20.1.1-1ubuntu3
2009-03-11 15:23:37 status unpacked libgnomecanvas2-common 2.20.1.1-1ubuntu3
2009-03-11 15:23:37 status unpacked libgnomecanvas2-common 2.20.1.1-1ubuntu3
2009-03-11 15:23:37 install libgnomecanvas2-0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.20.1.1-1ubuntu3
2009-03-11 15:23:37 status half-installed libgnomecanvas2-0 2.20.1.1-1ubuntu3
2009-03-11 15:23:37 status unpacked libgnomecanvas2-0 2.20.1.1-1ubuntu3
2009-03-11 15:23:37 status unpacked libgnomecanvas2-0 2.20.1.1-1ubuntu3
2009-03-11 15:23:37 install libbonoboui2-common <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.0-0ubuntu1
2009-03-11 15:23:37 status half-installed libbonoboui2-common 2.24.0-0ubuntu1
2009-03-11 15:23:37 status unpacked libbonoboui2-common 2.24.0-0ubuntu1
2009-03-11 15:23:37 status unpacked libbonoboui2-common 2.24.0-0ubuntu1
2009-03-11 15:23:37 install libbonoboui2-0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.0-0ubuntu1
2009-03-11 15:23:37 status half-installed libbonoboui2-0 2.24.0-0ubuntu1
2009-03-11 15:23:37 status unpacked libbonoboui2-0 2.24.0-0ubuntu1
2009-03-11 15:23:37 status unpacked libbonoboui2-0 2.24.0-0ubuntu1
2009-03-11 15:23:37 install libfontenc1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:1.0.4-3
2009-03-11 15:23:37 status half-installed libfontenc1 1:1.0.4-3
2009-03-11 15:23:37 status unpacked libfontenc1 1:1.0.4-3
2009-03-11 15:23:37 status unpacked libfontenc1 1:1.0.4-3
2009-03-11 15:23:37 install libgnomeui-common <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.0-0ubuntu1
2009-03-11 15:23:37 status half-installed libgnomeui-common 2.24.0-0ubuntu1
2009-03-11 15:23:37 status unpacked libgnomeui-common 2.24.0-0ubuntu1
2009-03-11 15:23:37 status unpacked libgnomeui-common 2.24.0-0ubuntu1
2009-03-11 15:23:37 install libgnomeui-0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.0-0ubuntu1
2009-03-11 15:23:37 status half-installed libgnomeui-0 2.24.0-0ubuntu1
2009-03-11 15:23:37 status unpacked libgnomeui-0 2.24.0-0ubuntu1
2009-03-11 15:23:37 status unpacked libgnomeui-0 2.24.0-0ubuntu1
2009-03-11 15:23:37 install libtalloc1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.2.0~git20080616-1
2009-03-11 15:23:37 status half-installed libtalloc1 1.2.0~git20080616-1
2009-03-11 15:23:37 status unpacked libtalloc1 1.2.0~git20080616-1
2009-03-11 15:23:37 status unpacked libtalloc1 1.2.0~git20080616-1
2009-03-11 15:23:37 install libwbclient0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2:3.2.3-1ubuntu3.4
2009-03-11 15:23:37 status half-installed libwbclient0 2:3.2.3-1ubuntu3.4
2009-03-11 15:23:37 status unpacked libwbclient0 2:3.2.3-1ubuntu3.4
2009-03-11 15:23:37 status unpacked libwbclient0 2:3.2.3-1ubuntu3.4
2009-03-11 15:23:37 install libsmbclient <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2:3.2.3-1ubuntu3.4
2009-03-11 15:23:37 status half-installed libsmbclient 2:3.2.3-1ubuntu3.4
2009-03-11 15:23:38 status half-installed libsmbclient 2:3.2.3-1ubuntu3.4
2009-03-11 15:23:38 status unpacked libsmbclient 2:3.2.3-1ubuntu3.4
2009-03-11 15:23:38 status unpacked libsmbclient 2:3.2.3-1ubuntu3.4
2009-03-11 15:23:38 install libgnomevfs2-extra <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:2.24.0-0ubuntu1
2009-03-11 15:23:38 status half-installed libgnomevfs2-extra 1:2.24.0-0ubuntu1
2009-03-11 15:23:38 status unpacked libgnomevfs2-extra 1:2.24.0-0ubuntu1
2009-03-11 15:23:38 status unpacked libgnomevfs2-extra 1:2.24.0-0ubuntu1
2009-03-11 15:23:38 install libgtk2.0-bin <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.14.4-0ubuntu1
2009-03-11 15:23:38 status half-installed libgtk2.0-bin 2.14.4-0ubuntu1
2009-03-11 15:23:38 status half-installed libgtk2.0-bin 2.14.4-0ubuntu1
2009-03-11 15:23:38 status unpacked libgtk2.0-bin 2.14.4-0ubuntu1
2009-03-11 15:23:38 status unpacked libgtk2.0-bin 2.14.4-0ubuntu1
2009-03-11 15:23:38 install libpam-gnome-keyring <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.1-0ubuntu1
2009-03-11 15:23:38 status half-installed libpam-gnome-keyring 2.24.1-0ubuntu1
2009-03-11 15:23:38 status unpacked libpam-gnome-keyring 2.24.1-0ubuntu1
2009-03-11 15:23:38 status unpacked libpam-gnome-keyring 2.24.1-0ubuntu1
2009-03-11 15:23:38 install libsmbios-bin <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.0.3-0ubuntu1
2009-03-11 15:23:38 status half-installed libsmbios-bin 2.0.3-0ubuntu1
2009-03-11 15:23:38 status half-installed libsmbios-bin 2.0.3-0ubuntu1
2009-03-11 15:23:38 status unpacked libsmbios-bin 2.0.3-0ubuntu1
2009-03-11 15:23:38 status unpacked libsmbios-bin 2.0.3-0ubuntu1
2009-03-11 15:23:38 install libstartup-notification0 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.9-1
2009-03-11 15:23:38 status half-installed libstartup-notification0 0.9-1
2009-03-11 15:23:38 status unpacked libstartup-notification0 0.9-1
2009-03-11 15:23:38 status unpacked libstartup-notification0 0.9-1
2009-03-11 15:23:38 install libwnck-common <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.1-0ubuntu1
2009-03-11 15:23:38 status half-installed libwnck-common 2.24.1-0ubuntu1
2009-03-11 15:23:38 status unpacked libwnck-common 2.24.1-0ubuntu1
2009-03-11 15:23:38 status unpacked libwnck-common 2.24.1-0ubuntu1
2009-03-11 15:23:38 install libxres1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2:1.0.3-1
2009-03-11 15:23:38 status half-installed libxres1 2:1.0.3-1
2009-03-11 15:23:38 status unpacked libxres1 2:1.0.3-1
2009-03-11 15:23:38 status unpacked libxres1 2:1.0.3-1
2009-03-11 15:23:38 install libwnck22 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.1-0ubuntu1
2009-03-11 15:23:38 status half-installed libwnck22 2.24.1-0ubuntu1
2009-03-11 15:23:38 status unpacked libwnck22 2.24.1-0ubuntu1
2009-03-11 15:23:38 status unpacked libwnck22 2.24.1-0ubuntu1
2009-03-11 15:23:38 install libx86-1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.1+ds1-2
2009-03-11 15:23:38 status half-installed libx86-1 1.1+ds1-2
2009-03-11 15:23:38 status unpacked libx86-1 1.1+ds1-2
2009-03-11 15:23:38 status unpacked libx86-1 1.1+ds1-2
2009-03-11 15:23:38 install libxfont1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:1.3.3-1ubuntu1
2009-03-11 15:23:38 status half-installed libxfont1 1:1.3.3-1ubuntu1
2009-03-11 15:23:38 status unpacked libxfont1 1:1.3.3-1ubuntu1
2009-03-11 15:23:38 status unpacked libxfont1 1:1.3.3-1ubuntu1
2009-03-11 15:23:38 install myspell-en-us <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:2.4.0-2ubuntu4
2009-03-11 15:23:38 status half-installed myspell-en-us 1:2.4.0-2ubuntu4
2009-03-11 15:23:38 status unpacked myspell-en-us 1:2.4.0-2ubuntu4
2009-03-11 15:23:38 status unpacked myspell-en-us 1:2.4.0-2ubuntu4
2009-03-11 15:23:38 install notification-daemon <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.3.7-1ubuntu15
2009-03-11 15:23:38 status half-installed notification-daemon 0.3.7-1ubuntu15
2009-03-11 15:23:38 status unpacked notification-daemon 0.3.7-1ubuntu15
2009-03-11 15:23:38 status unpacked notification-daemon 0.3.7-1ubuntu15
2009-03-11 15:23:39 install python-pyorbit <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.0-0ubuntu1
2009-03-11 15:23:39 status half-installed python-pyorbit 2.24.0-0ubuntu1
2009-03-11 15:23:39 status unpacked python-pyorbit 2.24.0-0ubuntu1
2009-03-11 15:23:39 status unpacked python-pyorbit 2.24.0-0ubuntu1
2009-03-11 15:23:39 install python-gconf <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.22.3-0ubuntu1
2009-03-11 15:23:39 status half-installed python-gconf 2.22.3-0ubuntu1
2009-03-11 15:23:39 status unpacked python-gconf 2.22.3-0ubuntu1
2009-03-11 15:23:39 status unpacked python-gconf 2.22.3-0ubuntu1
2009-03-11 15:23:39 install python-gnomecanvas <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.22.3-0ubuntu1
2009-03-11 15:23:39 status half-installed python-gnomecanvas 2.22.3-0ubuntu1
2009-03-11 15:23:39 status unpacked python-gnomecanvas 2.22.3-0ubuntu1
2009-03-11 15:23:39 status unpacked python-gnomecanvas 2.22.3-0ubuntu1
2009-03-11 15:23:39 install python-gnome2 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.22.3-0ubuntu1
2009-03-11 15:23:39 status half-installed python-gnome2 2.22.3-0ubuntu1
2009-03-11 15:23:39 status unpacked python-gnome2 2.22.3-0ubuntu1
2009-03-11 15:23:39 status unpacked python-gnome2 2.22.3-0ubuntu1
2009-03-11 15:23:39 install radeontool <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.5-5build1
2009-03-11 15:23:39 status half-installed radeontool 1.5-5build1
2009-03-11 15:23:39 status half-installed radeontool 1.5-5build1
2009-03-11 15:23:39 status unpacked radeontool 1.5-5build1
2009-03-11 15:23:39 status unpacked radeontool 1.5-5build1
2009-03-11 15:23:39 install vbetool <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.0-3
2009-03-11 15:23:39 status half-installed vbetool 1.0-3
2009-03-11 15:23:39 status half-installed vbetool 1.0-3
2009-03-11 15:23:39 status unpacked vbetool 1.0-3
2009-03-11 15:23:39 status unpacked vbetool 1.0-3
2009-03-11 15:23:39 install xfonts-encodings <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:1.0.2-3
2009-03-11 15:23:39 status half-installed xfonts-encodings 1:1.0.2-3
2009-03-11 15:23:39 status unpacked xfonts-encodings 1:1.0.2-3
2009-03-11 15:23:39 status unpacked xfonts-encodings 1:1.0.2-3
2009-03-11 15:23:39 install xfonts-utils <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1:7.4+1ubuntu1
2009-03-11 15:23:39 status half-installed xfonts-utils 1:7.4+1ubuntu1
2009-03-11 15:23:39 status half-installed xfonts-utils 1:7.4+1ubuntu1
2009-03-11 15:23:39 status unpacked xfonts-utils 1:7.4+1ubuntu1
2009-03-11 15:23:39 status unpacked xfonts-utils 1:7.4+1ubuntu1
2009-03-11 15:23:39 install x-ttcidfont-conf <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 29
2009-03-11 15:23:39 status half-installed x-ttcidfont-conf 29
2009-03-11 15:23:39 status unpacked x-ttcidfont-conf 29
2009-03-11 15:23:39 status unpacked x-ttcidfont-conf 29
2009-03-11 15:23:39 install zenity <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.24.0-0ubuntu1
2009-03-11 15:23:39 status half-installed zenity 2.24.0-0ubuntu1
2009-03-11 15:23:39 status half-installed zenity 2.24.0-0ubuntu1
2009-03-11 15:23:40 status unpacked zenity 2.24.0-0ubuntu1
2009-03-11 15:23:40 status unpacked zenity 2.24.0-0ubuntu1
2009-03-11 15:23:40 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-11 15:23:40 status half-configured man-db 2.5.2-2
2009-03-11 15:23:41 status installed man-db 2.5.2-2
2009-03-11 15:23:42 startup packages configure
2009-03-11 15:23:42 configure libxfixes3 1:4.0.3-2 1:4.0.3-2
2009-03-11 15:23:42 status unpacked libxfixes3 1:4.0.3-2
2009-03-11 15:23:42 status half-configured libxfixes3 1:4.0.3-2
2009-03-11 15:23:42 status installed libxfixes3 1:4.0.3-2
2009-03-11 15:23:42 status triggers-pending libc6 2.8~20080505-0ubuntu7
2009-03-11 15:23:42 configure acl 2.2.47-2 2.2.47-2
2009-03-11 15:23:42 status unpacked acl 2.2.47-2
2009-03-11 15:23:42 status half-configured acl 2.2.47-2
2009-03-11 15:23:42 status installed acl 2.2.47-2
2009-03-11 15:23:42 configure libaspell15 0.60.6-1 0.60.6-1
2009-03-11 15:23:42 status unpacked libaspell15 0.60.6-1
2009-03-11 15:23:42 status half-configured libaspell15 0.60.6-1
2009-03-11 15:23:42 status installed libaspell15 0.60.6-1
2009-03-11 15:23:42 configure dictionaries-common 0.98.9ubuntu1 0.98.9ubuntu1
2009-03-11 15:23:42 status unpacked dictionaries-common 0.98.9ubuntu1
2009-03-11 15:23:42 status unpacked dictionaries-common 0.98.9ubuntu1
2009-03-11 15:23:42 status half-configured dictionaries-common 0.98.9ubuntu1
2009-03-11 15:23:44 status installed dictionaries-common 0.98.9ubuntu1
2009-03-11 15:23:44 configure aspell 0.60.6-1 0.60.6-1
2009-03-11 15:23:44 status unpacked aspell 0.60.6-1
2009-03-11 15:23:44 status half-configured aspell 0.60.6-1
2009-03-11 15:23:44 status installed aspell 0.60.6-1
2009-03-11 15:23:44 configure aspell-en 6.0-0-5.1 6.0-0-5.1
2009-03-11 15:23:44 status unpacked aspell-en 6.0-0-5.1
2009-03-11 15:23:44 status half-configured aspell-en 6.0-0-5.1
2009-03-11 15:23:44 status installed aspell-en 6.0-0-5.1
2009-03-11 15:23:44 configure defoma 0.11.10-0.2ubuntu1 0.11.10-0.2ubuntu1
2009-03-11 15:23:44 status unpacked defoma 0.11.10-0.2ubuntu1
2009-03-11 15:23:44 status unpacked defoma 0.11.10-0.2ubuntu1
2009-03-11 15:23:44 status unpacked defoma 0.11.10-0.2ubuntu1
2009-03-11 15:23:44 status unpacked defoma 0.11.10-0.2ubuntu1
2009-03-11 15:23:44 status unpacked defoma 0.11.10-0.2ubuntu1
2009-03-11 15:23:44 status half-configured defoma 0.11.10-0.2ubuntu1
2009-03-11 15:23:44 status installed defoma 0.11.10-0.2ubuntu1
2009-03-11 15:23:44 configure sgml-data 2.0.3 2.0.3
2009-03-11 15:23:44 status unpacked sgml-data 2.0.3
2009-03-11 15:23:44 status half-configured sgml-data 2.0.3
2009-03-11 15:23:45 status installed sgml-data 2.0.3
2009-03-11 15:23:45 configure docbook-xml 4.5-5 4.5-5
2009-03-11 15:23:45 status unpacked docbook-xml 4.5-5
2009-03-11 15:23:45 status unpacked docbook-xml 4.5-5
2009-03-11 15:23:45 status unpacked docbook-xml 4.5-5
2009-03-11 15:23:45 status unpacked docbook-xml 4.5-5
2009-03-11 15:23:45 status unpacked docbook-xml 4.5-5
2009-03-11 15:23:45 status unpacked docbook-xml 4.5-5
2009-03-11 15:23:45 status unpacked docbook-xml 4.5-5
2009-03-11 15:23:45 status half-configured docbook-xml 4.5-5
2009-03-11 15:23:48 status installed docbook-xml 4.5-5
2009-03-11 15:23:48 configure libaudiofile0 0.2.6-7ubuntu1 0.2.6-7ubuntu1
2009-03-11 15:23:48 status unpacked libaudiofile0 0.2.6-7ubuntu1
2009-03-11 15:23:48 status half-configured libaudiofile0 0.2.6-7ubuntu1
2009-03-11 15:23:48 status installed libaudiofile0 0.2.6-7ubuntu1
2009-03-11 15:23:48 configure libasound2 1.0.17a-0ubuntu4 1.0.17a-0ubuntu4
2009-03-11 15:23:48 status unpacked libasound2 1.0.17a-0ubuntu4
2009-03-11 15:23:48 status unpacked libasound2 1.0.17a-0ubuntu4
2009-03-11 15:23:48 status half-configured libasound2 1.0.17a-0ubuntu4
2009-03-11 15:23:48 status installed libasound2 1.0.17a-0ubuntu4
2009-03-11 15:23:48 configure esound-common 0.2.40-0ubuntu1 0.2.40-0ubuntu1
2009-03-11 15:23:48 status unpacked esound-common 0.2.40-0ubuntu1
2009-03-11 15:23:48 status unpacked esound-common 0.2.40-0ubuntu1
2009-03-11 15:23:48 status half-configured esound-common 0.2.40-0ubuntu1
2009-03-11 15:23:48 status installed esound-common 0.2.40-0ubuntu1
2009-03-11 15:23:48 configure libesd-alsa0 0.2.40-0ubuntu1 0.2.40-0ubuntu1
2009-03-11 15:23:48 status unpacked libesd-alsa0 0.2.40-0ubuntu1
2009-03-11 15:23:48 status half-configured libesd-alsa0 0.2.40-0ubuntu1
2009-03-11 15:23:48 status installed libesd-alsa0 0.2.40-0ubuntu1
2009-03-11 15:23:48 configure esound-clients 0.2.40-0ubuntu1 0.2.40-0ubuntu1
2009-03-11 15:23:48 status unpacked esound-clients 0.2.40-0ubuntu1
2009-03-11 15:23:48 status half-configured esound-clients 0.2.40-0ubuntu1
2009-03-11 15:23:48 status installed esound-clients 0.2.40-0ubuntu1
2009-03-11 15:23:48 configure libfreetype6 2.3.7-2ubuntu1 2.3.7-2ubuntu1
2009-03-11 15:23:48 status unpacked libfreetype6 2.3.7-2ubuntu1
2009-03-11 15:23:48 status half-configured libfreetype6 2.3.7-2ubuntu1
2009-03-11 15:23:48 status installed libfreetype6 2.3.7-2ubuntu1
2009-03-11 15:23:48 configure ttf-dejavu-core 2.25-1 2.25-1
2009-03-11 15:23:48 status unpacked ttf-dejavu-core 2.25-1
2009-03-11 15:23:48 status unpacked ttf-dejavu-core 2.25-1
2009-03-11 15:23:48 status half-configured ttf-dejavu-core 2.25-1
2009-03-11 15:23:48 status installed ttf-dejavu-core 2.25-1
2009-03-11 15:23:48 configure ttf-dejavu-extra 2.25-1 2.25-1
2009-03-11 15:23:48 status unpacked ttf-dejavu-extra 2.25-1
2009-03-11 15:23:48 status unpacked ttf-dejavu-extra 2.25-1
2009-03-11 15:23:48 status half-configured ttf-dejavu-extra 2.25-1
2009-03-11 15:23:48 status installed ttf-dejavu-extra 2.25-1
2009-03-11 15:23:48 configure ttf-dejavu 2.25-1 2.25-1
2009-03-11 15:23:48 status unpacked ttf-dejavu 2.25-1
2009-03-11 15:23:48 status half-configured ttf-dejavu 2.25-1
2009-03-11 15:23:48 status installed ttf-dejavu 2.25-1
2009-03-11 15:23:48 configure fontconfig-config 2.6.0-1ubuntu4 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status unpacked fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:48 status half-configured fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:49 status installed fontconfig-config 2.6.0-1ubuntu4
2009-03-11 15:23:49 configure libfontconfig1 2.6.0-1ubuntu4 2.6.0-1ubuntu4
2009-03-11 15:23:49 status unpacked libfontconfig1 2.6.0-1ubuntu4
2009-03-11 15:23:49 status half-configured libfontconfig1 2.6.0-1ubuntu4
2009-03-11 15:23:49 status installed libfontconfig1 2.6.0-1ubuntu4
2009-03-11 15:23:49 configure fontconfig 2.6.0-1ubuntu4 2.6.0-1ubuntu4
2009-03-11 15:23:49 status unpacked fontconfig 2.6.0-1ubuntu4
2009-03-11 15:23:49 status half-configured fontconfig 2.6.0-1ubuntu4
2009-03-11 15:23:59 status installed fontconfig 2.6.0-1ubuntu4
2009-03-11 15:23:59 configure libidl0 0.8.10-0.1 0.8.10-0.1
2009-03-11 15:23:59 status unpacked libidl0 0.8.10-0.1
2009-03-11 15:23:59 status half-configured libidl0 0.8.10-0.1
2009-03-11 15:23:59 status installed libidl0 0.8.10-0.1
2009-03-11 15:23:59 configure liborbit2 1:2.14.16-0ubuntu1 1:2.14.16-0ubuntu1
2009-03-11 15:23:59 status unpacked liborbit2 1:2.14.16-0ubuntu1
2009-03-11 15:23:59 status half-configured liborbit2 1:2.14.16-0ubuntu1
2009-03-11 15:23:59 status installed liborbit2 1:2.14.16-0ubuntu1
2009-03-11 15:23:59 configure libpolkit-dbus2 0.9-1ubuntu3 0.9-1ubuntu3
2009-03-11 15:23:59 status unpacked libpolkit-dbus2 0.9-1ubuntu3
2009-03-11 15:23:59 status half-configured libpolkit-dbus2 0.9-1ubuntu3
2009-03-11 15:23:59 status installed libpolkit-dbus2 0.9-1ubuntu3
2009-03-11 15:23:59 configure gconf2-common 2.24.0-0ubuntu1 2.24.0-0ubuntu1
2009-03-11 15:23:59 status unpacked gconf2-common 2.24.0-0ubuntu1
2009-03-11 15:23:59 status unpacked gconf2-common 2.24.0-0ubuntu1
2009-03-11 15:23:59 status unpacked gconf2-common 2.24.0-0ubuntu1
2009-03-11 15:23:59 status half-configured gconf2-common 2.24.0-0ubuntu1
2009-03-11 15:24:00 status installed gconf2-common 2.24.0-0ubuntu1
2009-03-11 15:24:00 configure libgconf2-4 2.24.0-0ubuntu1 2.24.0-0ubuntu1
2009-03-11 15:24:00 status unpacked libgconf2-4 2.24.0-0ubuntu1
2009-03-11 15:24:00 status half-configured libgconf2-4 2.24.0-0ubuntu1
2009-03-11 15:24:00 status installed libgconf2-4 2.24.0-0ubuntu1
2009-03-11 15:24:00 configure gconf2 2.24.0-0ubuntu1 2.24.0-0ubuntu1
2009-03-11 15:24:00 status unpacked gconf2 2.24.0-0ubuntu1
2009-03-11 15:24:00 status half-configured gconf2 2.24.0-0ubuntu1
2009-03-11 15:24:01 status installed gconf2 2.24.0-0ubuntu1
2009-03-11 15:24:02 configure libatk1.0-0 1.24.0-0ubuntu1 1.24.0-0ubuntu1
2009-03-11 15:24:02 status unpacked libatk1.0-0 1.24.0-0ubuntu1
2009-03-11 15:24:02 status half-configured libatk1.0-0 1.24.0-0ubuntu1
2009-03-11 15:24:02 status installed libatk1.0-0 1.24.0-0ubuntu1
2009-03-11 15:24:02 configure libpixman-1-0 0.12.0-1 0.12.0-1
2009-03-11 15:24:02 status unpacked libpixman-1-0 0.12.0-1
2009-03-11 15:24:02 status half-configured libpixman-1-0 0.12.0-1
2009-03-11 15:24:02 status installed libpixman-1-0 0.12.0-1
2009-03-11 15:24:02 configure libpng12-0 1.2.27-1 1.2.27-1
2009-03-11 15:24:02 status unpacked libpng12-0 1.2.27-1
2009-03-11 15:24:02 status half-configured libpng12-0 1.2.27-1
2009-03-11 15:24:02 status installed libpng12-0 1.2.27-1
2009-03-11 15:24:02 configure libxcb-render0 1.1-1.1 1.1-1.1
2009-03-11 15:24:02 status unpacked libxcb-render0 1.1-1.1
2009-03-11 15:24:02 status half-configured libxcb-render0 1.1-1.1
2009-03-11 15:24:02 status installed libxcb-render0 1.1-1.1
2009-03-11 15:24:02 configure libxcb-render-util0 0.2+git36-1 0.2+git36-1
2009-03-11 15:24:02 status unpacked libxcb-render-util0 0.2+git36-1
2009-03-11 15:24:02 status half-configured libxcb-render-util0 0.2+git36-1
2009-03-11 15:24:02 status installed libxcb-render-util0 0.2+git36-1
2009-03-11 15:24:02 configure libxrender1 1:0.9.4-2 1:0.9.4-2
2009-03-11 15:24:02 status unpacked libxrender1 1:0.9.4-2
2009-03-11 15:24:02 status half-configured libxrender1 1:0.9.4-2
2009-03-11 15:24:02 status installed libxrender1 1:0.9.4-2
2009-03-11 15:24:02 configure libcairo2 1.8.0-0ubuntu1.1 1.8.0-0ubuntu1.1
2009-03-11 15:24:02 status unpacked libcairo2 1.8.0-0ubuntu1.1
2009-03-11 15:24:02 status half-configured libcairo2 1.8.0-0ubuntu1.1
2009-03-11 15:24:02 status installed libcairo2 1.8.0-0ubuntu1.1
2009-03-11 15:24:02 configure libhunspell-1.2-0 1.2.6-1ubuntu1 1.2.6-1ubuntu1
2009-03-11 15:24:02 status unpacked libhunspell-1.2-0 1.2.6-1ubuntu1
2009-03-11 15:24:02 status half-configured libhunspell-1.2-0 1.2.6-1ubuntu1
2009-03-11 15:24:02 status installed libhunspell-1.2-0 1.2.6-1ubuntu1
2009-03-11 15:24:02 configure libenchant1c2a 1.4.2-3.1ubuntu2 1.4.2-3.1ubuntu2
2009-03-11 15:24:02 status unpacked libenchant1c2a 1.4.2-3.1ubuntu2
2009-03-11 15:24:02 status half-configured libenchant1c2a 1.4.2-3.1ubuntu2
2009-03-11 15:24:02 status installed libenchant1c2a 1.4.2-3.1ubuntu2
2009-03-11 15:24:02 configure libgtk2.0-common 2.14.4-0ubuntu1 2.14.4-0ubuntu1
2009-03-11 15:24:02 status unpacked libgtk2.0-common 2.14.4-0ubuntu1
2009-03-11 15:24:02 status half-configured libgtk2.0-common 2.14.4-0ubuntu1
2009-03-11 15:24:02 status installed libgtk2.0-common 2.14.4-0ubuntu1
2009-03-11 15:24:02 configure libcups2 1.3.9-2ubuntu7 1.3.9-2ubuntu7
2009-03-11 15:24:02 status unpacked libcups2 1.3.9-2ubuntu7
2009-03-11 15:24:02 status half-configured libcups2 1.3.9-2ubuntu7
2009-03-11 15:24:02 status installed libcups2 1.3.9-2ubuntu7
2009-03-11 15:24:02 configure libjpeg62 6b-14 6b-14
2009-03-11 15:24:02 status unpacked libjpeg62 6b-14
2009-03-11 15:24:02 status half-configured libjpeg62 6b-14
2009-03-11 15:24:02 status installed libjpeg62 6b-14
2009-03-11 15:24:02 configure libpango1.0-common 1.22.2-0ubuntu1 1.22.2-0ubuntu1
2009-03-11 15:24:02 status unpacked libpango1.0-common 1.22.2-0ubuntu1
2009-03-11 15:24:02 status unpacked libpango1.0-common 1.22.2-0ubuntu1
2009-03-11 15:24:02 status half-configured libpango1.0-common 1.22.2-0ubuntu1
2009-03-11 15:24:02 status installed libpango1.0-common 1.22.2-0ubuntu1
2009-03-11 15:24:02 configure libdatrie0 0.1.3-2 0.1.3-2
2009-03-11 15:24:02 status unpacked libdatrie0 0.1.3-2
2009-03-11 15:24:02 status half-configured libdatrie0 0.1.3-2
2009-03-11 15:24:02 status installed libdatrie0 0.1.3-2
2009-03-11 15:24:02 configure libthai-data 0.1.9-4 0.1.9-4
2009-03-11 15:24:02 status unpacked libthai-data 0.1.9-4
2009-03-11 15:24:02 status half-configured libthai-data 0.1.9-4
2009-03-11 15:24:02 status installed libthai-data 0.1.9-4
2009-03-11 15:24:02 configure libthai0 0.1.9-4 0.1.9-4
2009-03-11 15:24:02 status unpacked libthai0 0.1.9-4
2009-03-11 15:24:02 status half-configured libthai0 0.1.9-4
2009-03-11 15:24:02 status installed libthai0 0.1.9-4
2009-03-11 15:24:02 configure libxft2 2.1.12-3ubuntu1 2.1.12-3ubuntu1
2009-03-11 15:24:02 status unpacked libxft2 2.1.12-3ubuntu1
2009-03-11 15:24:02 status half-configured libxft2 2.1.12-3ubuntu1
2009-03-11 15:24:02 status installed libxft2 2.1.12-3ubuntu1
2009-03-11 15:24:02 configure libpango1.0-0 1.22.2-0ubuntu1 1.22.2-0ubuntu1
2009-03-11 15:24:02 status unpacked libpango1.0-0 1.22.2-0ubuntu1
2009-03-11 15:24:02 status half-configured libpango1.0-0 1.22.2-0ubuntu1
2009-03-11 15:24:02 status installed libpango1.0-0 1.22.2-0ubuntu1
2009-03-11 15:24:02 configure libtiff4 3.8.2-11 3.8.2-11
2009-03-11 15:24:02 status unpacked libtiff4 3.8.2-11
2009-03-11 15:24:02 status half-configured libtiff4 3.8.2-11
2009-03-11 15:24:02 status installed libtiff4 3.8.2-11
2009-03-11 15:24:02 configure libxcomposite1 1:0.4.0-3 1:0.4.0-3
2009-03-11 15:24:02 status unpacked libxcomposite1 1:0.4.0-3
2009-03-11 15:24:02 status half-configured libxcomposite1 1:0.4.0-3
2009-03-11 15:24:02 status installed libxcomposite1 1:0.4.0-3
2009-03-11 15:24:02 configure libxcursor1 1:1.1.9-1 1:1.1.9-1
2009-03-11 15:24:02 status unpacked libxcursor1 1:1.1.9-1
2009-03-11 15:24:02 status half-configured libxcursor1 1:1.1.9-1
2009-03-11 15:24:02 status installed libxcursor1 1:1.1.9-1
2009-03-11 15:24:02 configure libxdamage1 1:1.1.1-4 1:1.1.1-4
2009-03-11 15:24:02 status unpacked libxdamage1 1:1.1.1-4
2009-03-11 15:24:02 status half-configured libxdamage1 1:1.1.1-4
2009-03-11 15:24:02 status installed libxdamage1 1:1.1.1-4
2009-03-11 15:24:02 configure libxi6 2:1.1.3-2build1 2:1.1.3-2build1
2009-03-11 15:24:02 status unpacked libxi6 2:1.1.3-2build1
2009-03-11 15:24:02 status half-configured libxi6 2:1.1.3-2build1
2009-03-11 15:24:02 status installed libxi6 2:1.1.3-2build1
2009-03-11 15:24:02 configure libxinerama1 2:1.0.3-2 2:1.0.3-2
2009-03-11 15:24:02 status unpacked libxinerama1 2:1.0.3-2
2009-03-11 15:24:02 status half-configured libxinerama1 2:1.0.3-2
2009-03-11 15:24:02 status installed libxinerama1 2:1.0.3-2
2009-03-11 15:24:02 configure libxrandr2 2:1.2.3-1 2:1.2.3-1
2009-03-11 15:24:02 status unpacked libxrandr2 2:1.2.3-1
2009-03-11 15:24:02 status half-configured libxrandr2 2:1.2.3-1
2009-03-11 15:24:02 status installed libxrandr2 2:1.2.3-1
2009-03-11 15:24:02 configure libgtk2.0-0 2.14.4-0ubuntu1 2.14.4-0ubuntu1
2009-03-11 15:24:02 status unpacked libgtk2.0-0 2.14.4-0ubuntu1
2009-03-11 15:24:02 status unpacked libgtk2.0-0 2.14.4-0ubuntu1
2009-03-11 15:24:02 status half-configured libgtk2.0-0 2.14.4-0ubuntu1
2009-03-11 15:24:02 status installed libgtk2.0-0 2.14.4-0ubuntu1
2009-03-11 15:24:02 configure libgtksourceview2.0-common 2.4.1-0ubuntu1 2.4.1-0ubuntu1
2009-03-11 15:24:02 status unpacked libgtksourceview2.0-common 2.4.1-0ubuntu1
2009-03-11 15:24:02 status half-configured libgtksourceview2.0-common 2.4.1-0ubuntu1
2009-03-11 15:24:02 status installed libgtksourceview2.0-common 2.4.1-0ubuntu1
2009-03-11 15:24:02 configure libgtksourceview2.0-0 2.4.1-0ubuntu1 2.4.1-0ubuntu1
2009-03-11 15:24:02 status unpacked libgtksourceview2.0-0 2.4.1-0ubuntu1
2009-03-11 15:24:02 status half-configured libgtksourceview2.0-0 2.4.1-0ubuntu1
2009-03-11 15:24:02 status installed libgtksourceview2.0-0 2.4.1-0ubuntu1
2009-03-11 15:24:02 configure libice6 2:1.0.4-1 2:1.0.4-1
2009-03-11 15:24:02 status unpacked libice6 2:1.0.4-1
2009-03-11 15:24:02 status half-configured libice6 2:1.0.4-1
2009-03-11 15:24:02 status installed libice6 2:1.0.4-1
2009-03-11 15:24:02 configure liblaunchpad-integration1 0.1.21 0.1.21
2009-03-11 15:24:02 status unpacked liblaunchpad-integration1 0.1.21
2009-03-11 15:24:02 status half-configured liblaunchpad-integration1 0.1.21
2009-03-11 15:24:02 status installed liblaunchpad-integration1 0.1.21
2009-03-11 15:24:02 configure libsm6 2:1.0.3-2 2:1.0.3-2
2009-03-11 15:24:02 status unpacked libsm6 2:1.0.3-2
2009-03-11 15:24:02 status half-configured libsm6 2:1.0.3-2
2009-03-11 15:24:02 status installed libsm6 2:1.0.3-2
2009-03-11 15:24:02 configure libxslt1.1 1.1.24-1ubuntu2 1.1.24-1ubuntu2
2009-03-11 15:24:02 status unpacked libxslt1.1 1.1.24-1ubuntu2
2009-03-11 15:24:02 status half-configured libxslt1.1 1.1.24-1ubuntu2
2009-03-11 15:24:02 status installed libxslt1.1 1.1.24-1ubuntu2
2009-03-11 15:24:02 configure libscrollkeeper0 0.3.14-16ubuntu1 0.3.14-16ubuntu1
2009-03-11 15:24:02 status unpacked libscrollkeeper0 0.3.14-16ubuntu1
2009-03-11 15:24:02 status half-configured libscrollkeeper0 0.3.14-16ubuntu1
2009-03-11 15:24:02 status installed libscrollkeeper0 0.3.14-16ubuntu1
2009-03-11 15:24:02 configure scrollkeeper 0.3.14-16ubuntu1 0.3.14-16ubuntu1
2009-03-11 15:24:02 status unpacked scrollkeeper 0.3.14-16ubuntu1
2009-03-11 15:24:02 status unpacked scrollkeeper 0.3.14-16ubuntu1
2009-03-11 15:24:02 status unpacked scrollkeeper 0.3.14-16ubuntu1
2009-03-11 15:24:02 status unpacked scrollkeeper 0.3.14-16ubuntu1
2009-03-11 15:24:02 status half-configured scrollkeeper 0.3.14-16ubuntu1
2009-03-11 15:24:06 status installed scrollkeeper 0.3.14-16ubuntu1
2009-03-11 15:24:06 configure gedit-common 2.24.2-0ubuntu1 2.24.2-0ubuntu1
2009-03-11 15:24:06 status unpacked gedit-common 2.24.2-0ubuntu1
2009-03-11 15:24:06 status half-configured gedit-common 2.24.2-0ubuntu1
2009-03-11 15:24:06 status installed gedit-common 2.24.2-0ubuntu1
2009-03-11 15:24:06 configure python-cairo 1.4.12-1 1.4.12-1
2009-03-11 15:24:06 status unpacked python-cairo 1.4.12-1
2009-03-11 15:24:06 status half-configured python-cairo 1.4.12-1
2009-03-11 15:24:06 status installed python-cairo 1.4.12-1
2009-03-11 15:24:06 configure python-numeric 24.2-9 24.2-9
2009-03-11 15:24:06 status unpacked python-numeric 24.2-9
2009-03-11 15:24:06 status half-configured python-numeric 24.2-9
2009-03-11 15:24:07 status installed python-numeric 24.2-9
2009-03-11 15:24:07 configure python-gtk2 2.13.0-0ubuntu8 2.13.0-0ubuntu8
2009-03-11 15:24:07 status unpacked python-gtk2 2.13.0-0ubuntu8
2009-03-11 15:24:07 status half-configured python-gtk2 2.13.0-0ubuntu8
2009-03-11 15:24:07 status installed python-gtk2 2.13.0-0ubuntu8
2009-03-11 15:24:07 status triggers-pending python-support 0.8.4
2009-03-11 15:24:07 configure python-gtksourceview2 2.4.0-0ubuntu1 2.4.0-0ubuntu1
2009-03-11 15:24:07 status unpacked python-gtksourceview2 2.4.0-0ubuntu1
2009-03-11 15:24:07 status half-configured python-gtksourceview2 2.4.0-0ubuntu1
2009-03-11 15:24:07 status installed python-gtksourceview2 2.4.0-0ubuntu1
2009-03-11 15:24:07 configure iso-codes 3.2-1 3.2-1
2009-03-11 15:24:07 status unpacked iso-codes 3.2-1
2009-03-11 15:24:07 status half-configured iso-codes 3.2-1
2009-03-11 15:24:07 status installed iso-codes 3.2-1
2009-03-11 15:24:07 configure gedit 2.24.2-0ubuntu1 2.24.2-0ubuntu1
2009-03-11 15:24:07 status unpacked gedit 2.24.2-0ubuntu1
2009-03-11 15:24:07 status half-configured gedit 2.24.2-0ubuntu1
2009-03-11 15:24:08 status installed gedit 2.24.2-0ubuntu1
2009-03-11 15:24:11 configure libgp11-0 2.24.1-0ubuntu1 2.24.1-0ubuntu1
2009-03-11 15:24:11 status unpacked libgp11-0 2.24.1-0ubuntu1
2009-03-11 15:24:11 status half-configured libgp11-0 2.24.1-0ubuntu1
2009-03-11 15:24:11 status installed libgp11-0 2.24.1-0ubuntu1
2009-03-11 15:24:11 configure libhal1 0.5.11-4ubuntu4 0.5.11-4ubuntu4
2009-03-11 15:24:11 status unpacked libhal1 0.5.11-4ubuntu4
2009-03-11 15:24:11 status half-configured libhal1 0.5.11-4ubuntu4
2009-03-11 15:24:11 status installed libhal1 0.5.11-4ubuntu4
2009-03-11 15:24:11 configure libhal-storage1 0.5.11-4ubuntu4 0.5.11-4ubuntu4
2009-03-11 15:24:11 status unpacked libhal-storage1 0.5.11-4ubuntu4
2009-03-11 15:24:11 status half-configured libhal-storage1 0.5.11-4ubuntu4
2009-03-11 15:24:11 status installed libhal-storage1 0.5.11-4ubuntu4
2009-03-11 15:24:11 configure gnome-keyring 2.24.1-0ubuntu1 2.24.1-0ubuntu1
2009-03-11 15:24:11 status unpacked gnome-keyring 2.24.1-0ubuntu1
2009-03-11 15:24:11 status half-configured gnome-keyring 2.24.1-0ubuntu1
2009-03-11 15:24:11 status installed gnome-keyring 2.24.1-0ubuntu1
2009-03-11 15:24:11 configure gnome-mime-data 2.18.0-1 2.18.0-1
2009-03-11 15:24:11 status unpacked gnome-mime-data 2.18.0-1
2009-03-11 15:24:11 status unpacked gnome-mime-data 2.18.0-1
2009-03-11 15:24:11 status half-configured gnome-mime-data 2.18.0-1
2009-03-11 15:24:11 status installed gnome-mime-data 2.18.0-1
2009-03-11 15:24:11 configure libgnome-keyring0 2.24.1-0ubuntu1 2.24.1-0ubuntu1
2009-03-11 15:24:11 status unpacked libgnome-keyring0 2.24.1-0ubuntu1
2009-03-11 15:24:11 status half-configured libgnome-keyring0 2.24.1-0ubuntu1
2009-03-11 15:24:11 status installed libgnome-keyring0 2.24.1-0ubuntu1
2009-03-11 15:24:11 configure libnotify1 0.4.4-3build1 0.4.4-3build1
2009-03-11 15:24:11 status unpacked libnotify1 0.4.4-3build1
2009-03-11 15:24:11 status half-configured libnotify1 0.4.4-3build1
2009-03-11 15:24:12 status installed libnotify1 0.4.4-3build1
2009-03-11 15:24:12 configure libsmbios2 2.0.3-0ubuntu1 2.0.3-0ubuntu1
2009-03-11 15:24:12 status unpacked libsmbios2 2.0.3-0ubuntu1
2009-03-11 15:24:12 status half-configured libsmbios2 2.0.3-0ubuntu1
2009-03-11 15:24:12 status installed libsmbios2 2.0.3-0ubuntu1
2009-03-11 15:24:12 configure hal-info 20090128-0ubuntu1~intrepid2 20090128-0ubuntu1~intrepid2
2009-03-11 15:24:12 status unpacked hal-info 20090128-0ubuntu1~intrepid2
2009-03-11 15:24:12 status half-configured hal-info 20090128-0ubuntu1~intrepid2
2009-03-11 15:24:12 status installed hal-info 20090128-0ubuntu1~intrepid2
2009-03-11 15:24:12 configure powermgmt-base 1.30 1.30
2009-03-11 15:24:12 status unpacked powermgmt-base 1.30
2009-03-11 15:24:12 status half-configured powermgmt-base 1.30
2009-03-11 15:24:12 status installed powermgmt-base 1.30
2009-03-11 15:24:12 configure pm-utils 1.1.2.4-1ubuntu8 1.1.2.4-1ubuntu8
2009-03-11 15:24:12 status unpacked pm-utils 1.1.2.4-1ubuntu8
2009-03-11 15:24:12 status unpacked pm-utils 1.1.2.4-1ubuntu8
2009-03-11 15:24:12 status half-configured pm-utils 1.1.2.4-1ubuntu8
2009-03-11 15:24:12 status installed pm-utils 1.1.2.4-1ubuntu8
2009-03-11 15:24:12 configure libpolkit-grant2 0.9-1ubuntu3 0.9-1ubuntu3
2009-03-11 15:24:12 status unpacked libpolkit-grant2 0.9-1ubuntu3
2009-03-11 15:24:12 status half-configured libpolkit-grant2 0.9-1ubuntu3
2009-03-11 15:24:12 status installed libpolkit-grant2 0.9-1ubuntu3
2009-03-11 15:24:12 configure policykit 0.9-1ubuntu3 0.9-1ubuntu3
2009-03-11 15:24:12 status unpacked policykit 0.9-1ubuntu3
2009-03-11 15:24:12 status unpacked policykit 0.9-1ubuntu3
2009-03-11 15:24:12 status unpacked policykit 0.9-1ubuntu3
2009-03-11 15:24:12 status unpacked policykit 0.9-1ubuntu3
2009-03-11 15:24:12 status unpacked policykit 0.9-1ubuntu3
2009-03-11 15:24:12 status half-configured policykit 0.9-1ubuntu3
2009-03-11 15:24:13 status installed policykit 0.9-1ubuntu3
2009-03-11 15:24:13 configure hal 0.5.11-4ubuntu4 0.5.11-4ubuntu4
2009-03-11 15:24:13 status unpacked hal 0.5.11-4ubuntu4
2009-03-11 15:24:13 status unpacked hal 0.5.11-4ubuntu4
2009-03-11 15:24:13 status unpacked hal 0.5.11-4ubuntu4
2009-03-11 15:24:13 status unpacked hal 0.5.11-4ubuntu4
2009-03-11 15:24:13 status unpacked hal 0.5.11-4ubuntu4
2009-03-11 15:24:13 status unpacked hal 0.5.11-4ubuntu4
2009-03-11 15:24:13 status half-configured hal 0.5.11-4ubuntu4
2009-03-11 15:24:14 status installed hal 0.5.11-4ubuntu4
2009-03-11 15:24:14 configure libavahi-common-data 0.6.23-2ubuntu2.1 0.6.23-2ubuntu2.1
2009-03-11 15:24:14 status unpacked libavahi-common-data 0.6.23-2ubuntu2.1
2009-03-11 15:24:14 status half-configured libavahi-common-data 0.6.23-2ubuntu2.1
2009-03-11 15:24:14 status installed libavahi-common-data 0.6.23-2ubuntu2.1
2009-03-11 15:24:14 configure libavahi-common3 0.6.23-2ubuntu2.1 0.6.23-2ubuntu2.1
2009-03-11 15:24:14 status unpacked libavahi-common3 0.6.23-2ubuntu2.1
2009-03-11 15:24:14 status half-configured libavahi-common3 0.6.23-2ubuntu2.1
2009-03-11 15:24:14 status installed libavahi-common3 0.6.23-2ubuntu2.1
2009-03-11 15:24:14 configure libavahi-client3 0.6.23-2ubuntu2.1 0.6.23-2ubuntu2.1
2009-03-11 15:24:14 status unpacked libavahi-client3 0.6.23-2ubuntu2.1
2009-03-11 15:24:14 status half-configured libavahi-client3 0.6.23-2ubuntu2.1
2009-03-11 15:24:14 status installed libavahi-client3 0.6.23-2ubuntu2.1
2009-03-11 15:24:14 configure libavahi-glib1 0.6.23-2ubuntu2.1 0.6.23-2ubuntu2.1
2009-03-11 15:24:14 status unpacked libavahi-glib1 0.6.23-2ubuntu2.1
2009-03-11 15:24:14 status half-configured libavahi-glib1 0.6.23-2ubuntu2.1
2009-03-11 15:24:14 status installed libavahi-glib1 0.6.23-2ubuntu2.1
2009-03-11 15:24:14 configure shared-mime-info 0.51-0ubuntu1 0.51-0ubuntu1
2009-03-11 15:24:14 status unpacked shared-mime-info 0.51-0ubuntu1
2009-03-11 15:24:14 status half-configured shared-mime-info 0.51-0ubuntu1
2009-03-11 15:24:15 status installed shared-mime-info 0.51-0ubuntu1
2009-03-11 15:24:15 configure libgnomevfs2-common 1:2.24.0-0ubuntu1 1:2.24.0-0ubuntu1
2009-03-11 15:24:15 status unpacked libgnomevfs2-common 1:2.24.0-0ubuntu1
2009-03-11 15:24:15 status unpacked libgnomevfs2-common 1:2.24.0-0ubuntu1
2009-03-11 15:24:15 status half-configured libgnomevfs2-common 1:2.24.0-0ubuntu1
2009-03-11 15:24:16 status installed libgnomevfs2-common 1:2.24.0-0ubuntu1
2009-03-11 15:24:16 configure libpolkit-gnome0 0.9-1ubuntu1 0.9-1ubuntu1
2009-03-11 15:24:16 status unpacked libpolkit-gnome0 0.9-1ubuntu1
2009-03-11 15:24:16 status half-configured libpolkit-gnome0 0.9-1ubuntu1
2009-03-11 15:24:16 status installed libpolkit-gnome0 0.9-1ubuntu1
2009-03-11 15:24:16 configure libsexy2 0.1.11-2 0.1.11-2
2009-03-11 15:24:16 status unpacked libsexy2 0.1.11-2
2009-03-11 15:24:16 status half-configured libsexy2 0.1.11-2
2009-03-11 15:24:16 status installed libsexy2 0.1.11-2
2009-03-11 15:24:16 configure hicolor-icon-theme 0.10-1ubuntu1 0.10-1ubuntu1
2009-03-11 15:24:16 status unpacked hicolor-icon-theme 0.10-1ubuntu1
2009-03-11 15:24:16 status half-configured hicolor-icon-theme 0.10-1ubuntu1
2009-03-11 15:24:16 status installed hicolor-icon-theme 0.10-1ubuntu1
2009-03-11 15:24:16 configure launchpad-integration 0.1.21 0.1.21
2009-03-11 15:24:16 status unpacked launchpad-integration 0.1.21
2009-03-11 15:24:16 status half-configured launchpad-integration 0.1.21
2009-03-11 15:24:16 status installed launchpad-integration 0.1.21
2009-03-11 15:24:16 configure libart-2.0-2 2.3.20-2 2.3.20-2
2009-03-11 15:24:16 status unpacked libart-2.0-2 2.3.20-2
2009-03-11 15:24:16 status half-configured libart-2.0-2 2.3.20-2
2009-03-11 15:24:16 status installed libart-2.0-2 2.3.20-2
2009-03-11 15:24:16 configure libatk1.0-data 1.24.0-0ubuntu1 1.24.0-0ubuntu1
2009-03-11 15:24:16 status unpacked libatk1.0-data 1.24.0-0ubuntu1
2009-03-11 15:24:16 status half-configured libatk1.0-data 1.24.0-0ubuntu1
2009-03-11 15:24:16 status installed libatk1.0-data 1.24.0-0ubuntu1
2009-03-11 15:24:16 configure libbonobo2-common 2.24.0-0ubuntu1 2.24.0-0ubuntu1
2009-03-11 15:24:16 status unpacked libbonobo2-common 2.24.0-0ubuntu1
2009-03-11 15:24:16 status unpacked libbonobo2-common 2.24.0-0ubuntu1
2009-03-11 15:24:16 status half-configured libbonobo2-common 2.24.0-0ubuntu1
2009-03-11 15:24:16 status installed libbonobo2-common 2.24.0-0ubuntu1
2009-03-11 15:24:16 configure libbonobo2-0 2.24.0-0ubuntu1 2.24.0-0ubuntu1
2009-03-11 15:24:16 status unpacked libbonobo2-0 2.24.0-0ubuntu1
2009-03-11 15:24:16 status half-configured libbonobo2-0 2.24.0-0ubuntu1
2009-03-11 15:24:16 status installed libbonobo2-0 2.24.0-0ubuntu1
2009-03-11 15:24:16 configure libglade2-0 1:2.6.3-0ubuntu1 1:2.6.3-0ubuntu1
2009-03-11 15:24:16 status unpacked libglade2-0 1:2.6.3-0ubuntu1
2009-03-11 15:24:16 status half-configured libglade2-0 1:2.6.3-0ubuntu1
2009-03-11 15:24:16 status installed libglade2-0 1:2.6.3-0ubuntu1
2009-03-11 15:24:16 configure libgnome2-common 2.24.1-0ubuntu4 2.24.1-0ubuntu4
2009-03-11 15:24:16 status unpacked libgnome2-common 2.24.1-0ubuntu4
2009-03-11 15:24:16 status unpacked libgnome2-common 2.24.1-0ubuntu4
2009-03-11 15:24:16 status unpacked libgnome2-common 2.24.1-0ubuntu4
2009-03-11 15:24:16 status half-configured libgnome2-common 2.24.1-0ubuntu4
2009-03-11 15:24:17 status installed libgnome2-common 2.24.1-0ubuntu4
2009-03-11 15:24:18 configure libgnomecanvas2-common 2.20.1.1-1ubuntu3 2.20.1.1-1ubuntu3
2009-03-11 15:24:18 status unpacked libgnomecanvas2-common 2.20.1.1-1ubuntu3
2009-03-11 15:24:18 status half-configured libgnomecanvas2-common 2.20.1.1-1ubuntu3
2009-03-11 15:24:18 status installed libgnomecanvas2-common 2.20.1.1-1ubuntu3
2009-03-11 15:24:18 configure libgnomecanvas2-0 2.20.1.1-1ubuntu3 2.20.1.1-1ubuntu3
2009-03-11 15:24:18 status unpacked libgnomecanvas2-0 2.20.1.1-1ubuntu3
2009-03-11 15:24:18 status half-configured libgnomecanvas2-0 2.20.1.1-1ubuntu3
2009-03-11 15:24:18 status installed libgnomecanvas2-0 2.20.1.1-1ubuntu3
2009-03-11 15:24:18 configure libbonoboui2-common 2.24.0-0ubuntu1 2.24.0-0ubuntu1
2009-03-11 15:24:18 status unpacked libbonoboui2-common 2.24.0-0ubuntu1
2009-03-11 15:24:18 status half-configured libbonoboui2-common 2.24.0-0ubuntu1
2009-03-11 15:24:18 status installed libbonoboui2-common 2.24.0-0ubuntu1
2009-03-11 15:24:18 configure libfontenc1 1:1.0.4-3 1:1.0.4-3
2009-03-11 15:24:18 status unpacked libfontenc1 1:1.0.4-3
2009-03-11 15:24:18 status half-configured libfontenc1 1:1.0.4-3
2009-03-11 15:24:18 status installed libfontenc1 1:1.0.4-3
2009-03-11 15:24:18 configure libgnomeui-common 2.24.0-0ubuntu1 2.24.0-0ubuntu1
2009-03-11 15:24:18 status unpacked libgnomeui-common 2.24.0-0ubuntu1
2009-03-11 15:24:18 status half-configured libgnomeui-common 2.24.0-0ubuntu1
2009-03-11 15:24:18 status installed libgnomeui-common 2.24.0-0ubuntu1
2009-03-11 15:24:18 configure libtalloc1 1.2.0~git20080616-1 1.2.0~git20080616-1
2009-03-11 15:24:18 status unpacked libtalloc1 1.2.0~git20080616-1
2009-03-11 15:24:18 status half-configured libtalloc1 1.2.0~git20080616-1
2009-03-11 15:24:18 status installed libtalloc1 1.2.0~git20080616-1
2009-03-11 15:24:18 configure libwbclient0 2:3.2.3-1ubuntu3.4 2:3.2.3-1ubuntu3.4
2009-03-11 15:24:18 status unpacked libwbclient0 2:3.2.3-1ubuntu3.4
2009-03-11 15:24:18 status half-configured libwbclient0 2:3.2.3-1ubuntu3.4
2009-03-11 15:24:18 status installed libwbclient0 2:3.2.3-1ubuntu3.4
2009-03-11 15:24:18 configure libsmbclient 2:3.2.3-1ubuntu3.4 2:3.2.3-1ubuntu3.4
2009-03-11 15:24:18 status unpacked libsmbclient 2:3.2.3-1ubuntu3.4
2009-03-11 15:24:18 status half-configured libsmbclient 2:3.2.3-1ubuntu3.4
2009-03-11 15:24:18 status installed libsmbclient 2:3.2.3-1ubuntu3.4
2009-03-11 15:24:18 configure libgtk2.0-bin 2.14.4-0ubuntu1 2.14.4-0ubuntu1
2009-03-11 15:24:18 status unpacked libgtk2.0-bin 2.14.4-0ubuntu1
2009-03-11 15:24:18 status half-configured libgtk2.0-bin 2.14.4-0ubuntu1
2009-03-11 15:24:18 status installed libgtk2.0-bin 2.14.4-0ubuntu1
2009-03-11 15:24:18 configure libpam-gnome-keyring 2.24.1-0ubuntu1 2.24.1-0ubuntu1
2009-03-11 15:24:18 status unpacked libpam-gnome-keyring 2.24.1-0ubuntu1
2009-03-11 15:24:18 status half-configured libpam-gnome-keyring 2.24.1-0ubuntu1
2009-03-11 15:24:18 status installed libpam-gnome-keyring 2.24.1-0ubuntu1
2009-03-11 15:24:18 configure libsmbios-bin 2.0.3-0ubuntu1 2.0.3-0ubuntu1
2009-03-11 15:24:18 status unpacked libsmbios-bin 2.0.3-0ubuntu1
2009-03-11 15:24:18 status half-configured libsmbios-bin 2.0.3-0ubuntu1
2009-03-11 15:24:18 status installed libsmbios-bin 2.0.3-0ubuntu1
2009-03-11 15:24:18 configure libstartup-notification0 0.9-1 0.9-1
2009-03-11 15:24:18 status unpacked libstartup-notification0 0.9-1
2009-03-11 15:24:18 status half-configured libstartup-notification0 0.9-1
2009-03-11 15:24:18 status installed libstartup-notification0 0.9-1
2009-03-11 15:24:18 configure libwnck-common 2.24.1-0ubuntu1 2.24.1-0ubuntu1
2009-03-11 15:24:18 status unpacked libwnck-common 2.24.1-0ubuntu1
2009-03-11 15:24:18 status half-configured libwnck-common 2.24.1-0ubuntu1
2009-03-11 15:24:18 status installed libwnck-common 2.24.1-0ubuntu1
2009-03-11 15:24:18 configure libxres1 2:1.0.3-1 2:1.0.3-1
2009-03-11 15:24:18 status unpacked libxres1 2:1.0.3-1
2009-03-11 15:24:18 status half-configured libxres1 2:1.0.3-1
2009-03-11 15:24:18 status installed libxres1 2:1.0.3-1
2009-03-11 15:24:18 configure libwnck22 2.24.1-0ubuntu1 2.24.1-0ubuntu1
2009-03-11 15:24:18 status unpacked libwnck22 2.24.1-0ubuntu1
2009-03-11 15:24:18 status half-configured libwnck22 2.24.1-0ubuntu1
2009-03-11 15:24:18 status installed libwnck22 2.24.1-0ubuntu1
2009-03-11 15:24:18 configure libx86-1 1.1+ds1-2 1.1+ds1-2
2009-03-11 15:24:18 status unpacked libx86-1 1.1+ds1-2
2009-03-11 15:24:18 status half-configured libx86-1 1.1+ds1-2
2009-03-11 15:24:18 status installed libx86-1 1.1+ds1-2
2009-03-11 15:24:18 configure libxfont1 1:1.3.3-1ubuntu1 1:1.3.3-1ubuntu1
2009-03-11 15:24:18 status unpacked libxfont1 1:1.3.3-1ubuntu1
2009-03-11 15:24:18 status half-configured libxfont1 1:1.3.3-1ubuntu1
2009-03-11 15:24:18 status installed libxfont1 1:1.3.3-1ubuntu1
2009-03-11 15:24:18 configure myspell-en-us 1:2.4.0-2ubuntu4 1:2.4.0-2ubuntu4
2009-03-11 15:24:18 status unpacked myspell-en-us 1:2.4.0-2ubuntu4
2009-03-11 15:24:18 status half-configured myspell-en-us 1:2.4.0-2ubuntu4
2009-03-11 15:24:18 status installed myspell-en-us 1:2.4.0-2ubuntu4
2009-03-11 15:24:18 configure notification-daemon 0.3.7-1ubuntu15 0.3.7-1ubuntu15
2009-03-11 15:24:18 status unpacked notification-daemon 0.3.7-1ubuntu15
2009-03-11 15:24:18 status half-configured notification-daemon 0.3.7-1ubuntu15
2009-03-11 15:24:18 status installed notification-daemon 0.3.7-1ubuntu15
2009-03-11 15:24:18 configure python-pyorbit 2.24.0-0ubuntu1 2.24.0-0ubuntu1
2009-03-11 15:24:18 status unpacked python-pyorbit 2.24.0-0ubuntu1
2009-03-11 15:24:18 status half-configured python-pyorbit 2.24.0-0ubuntu1
2009-03-11 15:24:18 status installed python-pyorbit 2.24.0-0ubuntu1
2009-03-11 15:24:18 configure python-gconf 2.22.3-0ubuntu1 2.22.3-0ubuntu1
2009-03-11 15:24:18 status unpacked python-gconf 2.22.3-0ubuntu1
2009-03-11 15:24:18 status half-configured python-gconf 2.22.3-0ubuntu1
2009-03-11 15:24:18 status installed python-gconf 2.22.3-0ubuntu1
2009-03-11 15:24:18 configure python-gnomecanvas 2.22.3-0ubuntu1 2.22.3-0ubuntu1
2009-03-11 15:24:18 status unpacked python-gnomecanvas 2.22.3-0ubuntu1
2009-03-11 15:24:18 status half-configured python-gnomecanvas 2.22.3-0ubuntu1
2009-03-11 15:24:18 status installed python-gnomecanvas 2.22.3-0ubuntu1
2009-03-11 15:24:18 configure radeontool 1.5-5build1 1.5-5build1
2009-03-11 15:24:18 status unpacked radeontool 1.5-5build1
2009-03-11 15:24:18 status half-configured radeontool 1.5-5build1
2009-03-11 15:24:18 status installed radeontool 1.5-5build1
2009-03-11 15:24:18 configure vbetool 1.0-3 1.0-3
2009-03-11 15:24:18 status unpacked vbetool 1.0-3
2009-03-11 15:24:18 status half-configured vbetool 1.0-3
2009-03-11 15:24:18 status installed vbetool 1.0-3
2009-03-11 15:24:18 configure xfonts-encodings 1:1.0.2-3 1:1.0.2-3
2009-03-11 15:24:18 status unpacked xfonts-encodings 1:1.0.2-3
2009-03-11 15:24:18 status half-configured xfonts-encodings 1:1.0.2-3
2009-03-11 15:24:18 status installed xfonts-encodings 1:1.0.2-3
2009-03-11 15:24:18 configure xfonts-utils 1:7.4+1ubuntu1 1:7.4+1ubuntu1
2009-03-11 15:24:18 status unpacked xfonts-utils 1:7.4+1ubuntu1
2009-03-11 15:24:18 status half-configured xfonts-utils 1:7.4+1ubuntu1
2009-03-11 15:24:18 status installed xfonts-utils 1:7.4+1ubuntu1
2009-03-11 15:24:18 configure x-ttcidfont-conf 29 29
2009-03-11 15:24:18 status unpacked x-ttcidfont-conf 29
2009-03-11 15:24:18 status unpacked x-ttcidfont-conf 29
2009-03-11 15:24:18 status half-configured x-ttcidfont-conf 29
2009-03-11 15:24:19 status installed x-ttcidfont-conf 29
2009-03-11 15:24:19 configure zenity 2.24.0-0ubuntu1 2.24.0-0ubuntu1
2009-03-11 15:24:19 status unpacked zenity 2.24.0-0ubuntu1
2009-03-11 15:24:19 status half-configured zenity 2.24.0-0ubuntu1
2009-03-11 15:24:19 status installed zenity 2.24.0-0ubuntu1
2009-03-11 15:24:19 configure gamin 0.1.9-2ubuntu2 0.1.9-2ubuntu2
2009-03-11 15:24:19 status unpacked gamin 0.1.9-2ubuntu2
2009-03-11 15:24:19 status unpacked gamin 0.1.9-2ubuntu2
2009-03-11 15:24:19 status half-configured gamin 0.1.9-2ubuntu2
2009-03-11 15:24:19 status installed gamin 0.1.9-2ubuntu2
2009-03-11 15:24:19 configure libgamin0 0.1.9-2ubuntu2 0.1.9-2ubuntu2
2009-03-11 15:24:19 status unpacked libgamin0 0.1.9-2ubuntu2
2009-03-11 15:24:19 status half-configured libgamin0 0.1.9-2ubuntu2
2009-03-11 15:24:19 status installed libgamin0 0.1.9-2ubuntu2
2009-03-11 15:24:19 configure libgnomevfs2-0 1:2.24.0-0ubuntu1 1:2.24.0-0ubuntu1
2009-03-11 15:24:19 status unpacked libgnomevfs2-0 1:2.24.0-0ubuntu1
2009-03-11 15:24:19 status half-configured libgnomevfs2-0 1:2.24.0-0ubuntu1
2009-03-11 15:24:19 status installed libgnomevfs2-0 1:2.24.0-0ubuntu1
2009-03-11 15:24:19 configure policykit-gnome 0.9-1ubuntu1 0.9-1ubuntu1
2009-03-11 15:24:19 status unpacked policykit-gnome 0.9-1ubuntu1
2009-03-11 15:24:19 status half-configured policykit-gnome 0.9-1ubuntu1
2009-03-11 15:24:19 status installed policykit-gnome 0.9-1ubuntu1
2009-03-11 15:24:19 configure gnome-mount 0.8-1ubuntu1 0.8-1ubuntu1
2009-03-11 15:24:19 status unpacked gnome-mount 0.8-1ubuntu1
2009-03-11 15:24:19 status half-configured gnome-mount 0.8-1ubuntu1
2009-03-11 15:24:19 status installed gnome-mount 0.8-1ubuntu1
2009-03-11 15:24:20 configure libgnome2-0 2.24.1-0ubuntu4 2.24.1-0ubuntu4
2009-03-11 15:24:20 status unpacked libgnome2-0 2.24.1-0ubuntu4
2009-03-11 15:24:20 status half-configured libgnome2-0 2.24.1-0ubuntu4
2009-03-11 15:24:20 status installed libgnome2-0 2.24.1-0ubuntu4
2009-03-11 15:24:20 configure libbonoboui2-0 2.24.0-0ubuntu1 2.24.0-0ubuntu1
2009-03-11 15:24:20 status unpacked libbonoboui2-0 2.24.0-0ubuntu1
2009-03-11 15:24:20 status half-configured libbonoboui2-0 2.24.0-0ubuntu1
2009-03-11 15:24:20 status installed libbonoboui2-0 2.24.0-0ubuntu1
2009-03-11 15:24:20 configure libgnomeui-0 2.24.0-0ubuntu1 2.24.0-0ubuntu1
2009-03-11 15:24:20 status unpacked libgnomeui-0 2.24.0-0ubuntu1
2009-03-11 15:24:20 status half-configured libgnomeui-0 2.24.0-0ubuntu1
2009-03-11 15:24:20 status installed libgnomeui-0 2.24.0-0ubuntu1
2009-03-11 15:24:20 configure libgnomevfs2-extra 1:2.24.0-0ubuntu1 1:2.24.0-0ubuntu1
2009-03-11 15:24:20 status unpacked libgnomevfs2-extra 1:2.24.0-0ubuntu1
2009-03-11 15:24:20 status unpacked libgnomevfs2-extra 1:2.24.0-0ubuntu1
2009-03-11 15:24:20 status half-configured libgnomevfs2-extra 1:2.24.0-0ubuntu1
2009-03-11 15:24:20 status installed libgnomevfs2-extra 1:2.24.0-0ubuntu1
2009-03-11 15:24:20 configure python-gnome2 2.22.3-0ubuntu1 2.22.3-0ubuntu1
2009-03-11 15:24:20 status unpacked python-gnome2 2.22.3-0ubuntu1
2009-03-11 15:24:20 status half-configured python-gnome2 2.22.3-0ubuntu1
2009-03-11 15:24:20 status installed python-gnome2 2.22.3-0ubuntu1
2009-03-11 15:24:20 trigproc libc6 2.8~20080505-0ubuntu7 2.8~20080505-0ubuntu7
2009-03-11 15:24:20 status half-configured libc6 2.8~20080505-0ubuntu7
2009-03-11 15:24:20 status installed libc6 2.8~20080505-0ubuntu7
2009-03-11 15:24:20 trigproc python-support 0.8.4 0.8.4
2009-03-11 15:24:20 status half-configured python-support 0.8.4
2009-03-11 15:24:20 status installed python-support 0.8.4
2009-03-19 07:40:25 startup archives unpack
2009-03-19 07:40:28 install dhcp3-server <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 3.1.1-1ubuntu2
2009-03-19 07:40:28 status half-installed dhcp3-server 3.1.1-1ubuntu2
2009-03-19 07:40:28 status triggers-pending man-db 2.5.2-2
2009-03-19 07:40:28 status half-installed dhcp3-server 3.1.1-1ubuntu2
2009-03-19 07:40:28 status unpacked dhcp3-server 3.1.1-1ubuntu2
2009-03-19 07:40:28 status unpacked dhcp3-server 3.1.1-1ubuntu2
2009-03-19 07:40:28 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-19 07:40:28 status half-configured man-db 2.5.2-2
2009-03-19 07:40:29 status installed man-db 2.5.2-2
2009-03-19 07:40:30 startup packages configure
2009-03-19 07:40:30 configure dhcp3-server 3.1.1-1ubuntu2 3.1.1-1ubuntu2
2009-03-19 07:40:30 status unpacked dhcp3-server 3.1.1-1ubuntu2
2009-03-19 07:40:30 status unpacked dhcp3-server 3.1.1-1ubuntu2
2009-03-19 07:40:30 status unpacked dhcp3-server 3.1.1-1ubuntu2
2009-03-19 07:40:30 status half-configured dhcp3-server 3.1.1-1ubuntu2
2009-03-19 07:40:33 status installed dhcp3-server 3.1.1-1ubuntu2
2009-03-30 06:41:42 startup archives unpack
2009-03-30 06:41:45 upgrade dash 0.5.4-9ubuntu1 0.5.4-9ubuntu1.1
2009-03-30 06:41:45 status half-configured dash 0.5.4-9ubuntu1
2009-03-30 06:41:45 status unpacked dash 0.5.4-9ubuntu1
2009-03-30 06:41:45 status half-installed dash 0.5.4-9ubuntu1
2009-03-30 06:41:45 status triggers-pending man-db 2.5.2-2
2009-03-30 06:41:45 status half-installed dash 0.5.4-9ubuntu1
2009-03-30 06:41:45 status half-installed dash 0.5.4-9ubuntu1
2009-03-30 06:41:45 status unpacked dash 0.5.4-9ubuntu1.1
2009-03-30 06:41:45 status unpacked dash 0.5.4-9ubuntu1.1
2009-03-30 06:41:45 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-30 06:41:45 status half-configured man-db 2.5.2-2
2009-03-30 06:41:46 status installed man-db 2.5.2-2
2009-03-30 06:41:47 startup packages configure
2009-03-30 06:41:47 configure dash 0.5.4-9ubuntu1.1 0.5.4-9ubuntu1.1
2009-03-30 06:41:47 status unpacked dash 0.5.4-9ubuntu1.1
2009-03-30 06:41:47 status half-configured dash 0.5.4-9ubuntu1.1
2009-03-30 06:41:47 status installed dash 0.5.4-9ubuntu1.1
2009-03-30 06:41:48 startup archives unpack
2009-03-30 06:41:48 upgrade dpkg 1.14.20ubuntu6 1.14.20ubuntu6.1
2009-03-30 06:41:48 status half-configured dpkg 1.14.20ubuntu6
2009-03-30 06:41:48 status unpacked dpkg 1.14.20ubuntu6
2009-03-30 06:41:48 status half-installed dpkg 1.14.20ubuntu6
2009-03-30 06:41:48 status triggers-pending man-db 2.5.2-2
2009-03-30 06:41:48 status half-installed dpkg 1.14.20ubuntu6
2009-03-30 06:41:49 status half-installed dpkg 1.14.20ubuntu6
2009-03-30 06:41:49 status unpacked dpkg 1.14.20ubuntu6.1
2009-03-30 06:41:49 status unpacked dpkg 1.14.20ubuntu6.1
2009-03-30 06:41:49 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-30 06:41:49 status half-configured man-db 2.5.2-2
2009-03-30 06:41:49 status installed man-db 2.5.2-2
2009-03-30 06:41:50 startup packages configure
2009-03-30 06:41:50 configure dpkg 1.14.20ubuntu6.1 1.14.20ubuntu6.1
2009-03-30 06:41:50 status unpacked dpkg 1.14.20ubuntu6.1
2009-03-30 06:41:50 status unpacked dpkg 1.14.20ubuntu6.1
2009-03-30 06:41:50 status unpacked dpkg 1.14.20ubuntu6.1
2009-03-30 06:41:50 status unpacked dpkg 1.14.20ubuntu6.1
2009-03-30 06:41:50 status unpacked dpkg 1.14.20ubuntu6.1
2009-03-30 06:41:50 status half-configured dpkg 1.14.20ubuntu6.1
2009-03-30 06:41:50 status installed dpkg 1.14.20ubuntu6.1
2009-03-30 06:41:51 startup archives unpack
2009-03-30 06:41:51 upgrade login 1:4.1.1-1ubuntu1 1:4.1.1-1ubuntu1.2
2009-03-30 06:41:51 status half-configured login 1:4.1.1-1ubuntu1
2009-03-30 06:41:51 status unpacked login 1:4.1.1-1ubuntu1
2009-03-30 06:41:51 status half-installed login 1:4.1.1-1ubuntu1
2009-03-30 06:41:51 status triggers-pending man-db 2.5.2-2
2009-03-30 06:41:51 status half-installed login 1:4.1.1-1ubuntu1
2009-03-30 06:41:51 status half-installed login 1:4.1.1-1ubuntu1
2009-03-30 06:41:51 status unpacked login 1:4.1.1-1ubuntu1.2
2009-03-30 06:41:51 status unpacked login 1:4.1.1-1ubuntu1.2
2009-03-30 06:41:51 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-30 06:41:51 status half-configured man-db 2.5.2-2
2009-03-30 06:41:52 status installed man-db 2.5.2-2
2009-03-30 06:41:52 startup packages configure
2009-03-30 06:41:52 configure login 1:4.1.1-1ubuntu1.2 1:4.1.1-1ubuntu1.2
2009-03-30 06:41:52 status unpacked login 1:4.1.1-1ubuntu1.2
2009-03-30 06:41:52 status unpacked login 1:4.1.1-1ubuntu1.2
2009-03-30 06:41:52 status unpacked login 1:4.1.1-1ubuntu1.2
2009-03-30 06:41:52 status unpacked login 1:4.1.1-1ubuntu1.2
2009-03-30 06:41:52 status unpacked login 1:4.1.1-1ubuntu1.2
2009-03-30 06:41:52 status half-configured login 1:4.1.1-1ubuntu1.2
2009-03-30 06:41:52 status installed login 1:4.1.1-1ubuntu1.2
2009-03-30 06:41:53 startup archives unpack
2009-03-30 06:41:53 upgrade perl-modules 5.10.0-11.1ubuntu2 5.10.0-11.1ubuntu2.2
2009-03-30 06:41:53 status half-configured perl-modules 5.10.0-11.1ubuntu2
2009-03-30 06:41:53 status unpacked perl-modules 5.10.0-11.1ubuntu2
2009-03-30 06:41:53 status half-installed perl-modules 5.10.0-11.1ubuntu2
2009-03-30 06:41:54 status half-installed perl-modules 5.10.0-11.1ubuntu2
2009-03-30 06:41:54 status unpacked perl-modules 5.10.0-11.1ubuntu2.2
2009-03-30 06:41:55 status unpacked perl-modules 5.10.0-11.1ubuntu2.2
2009-03-30 06:41:55 upgrade libc6 2.8~20080505-0ubuntu7 2.8~20080505-0ubuntu9
2009-03-30 06:41:55 status half-configured libc6 2.8~20080505-0ubuntu7
2009-03-30 06:41:55 status unpacked libc6 2.8~20080505-0ubuntu7
2009-03-30 06:41:55 status half-installed libc6 2.8~20080505-0ubuntu7
2009-03-30 06:41:56 status triggers-pending man-db 2.5.2-2
2009-03-30 06:41:56 status half-installed libc6 2.8~20080505-0ubuntu7
2009-03-30 06:41:56 status half-installed libc6 2.8~20080505-0ubuntu7
2009-03-30 06:41:56 status unpacked libc6 2.8~20080505-0ubuntu9
2009-03-30 06:41:57 status unpacked libc6 2.8~20080505-0ubuntu9
2009-03-30 06:41:57 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-30 06:41:57 status half-configured man-db 2.5.2-2
2009-03-30 06:41:57 status installed man-db 2.5.2-2
2009-03-30 06:41:57 startup packages configure
2009-03-30 06:41:57 configure libc6 2.8~20080505-0ubuntu9 2.8~20080505-0ubuntu9
2009-03-30 06:41:57 status unpacked libc6 2.8~20080505-0ubuntu9
2009-03-30 06:41:57 status unpacked libc6 2.8~20080505-0ubuntu9
2009-03-30 06:41:57 status unpacked libc6 2.8~20080505-0ubuntu9
2009-03-30 06:41:57 status unpacked libc6 2.8~20080505-0ubuntu9
2009-03-30 06:41:57 status unpacked libc6 2.8~20080505-0ubuntu9
2009-03-30 06:41:57 status unpacked libc6 2.8~20080505-0ubuntu9
2009-03-30 06:41:57 status half-configured libc6 2.8~20080505-0ubuntu9
2009-03-30 06:41:59 status installed libc6 2.8~20080505-0ubuntu9
2009-03-30 06:41:59 status triggers-pending libc6 2.8~20080505-0ubuntu9
2009-03-30 06:41:59 trigproc libc6 2.8~20080505-0ubuntu9 2.8~20080505-0ubuntu9
2009-03-30 06:41:59 status half-configured libc6 2.8~20080505-0ubuntu9
2009-03-30 06:41:59 status installed libc6 2.8~20080505-0ubuntu9
2009-03-30 06:42:00 startup archives unpack
2009-03-30 06:42:00 upgrade libc6-i686 2.8~20080505-0ubuntu7 2.8~20080505-0ubuntu9
2009-03-30 06:42:00 status half-configured libc6-i686 2.8~20080505-0ubuntu7
2009-03-30 06:42:00 status unpacked libc6-i686 2.8~20080505-0ubuntu7
2009-03-30 06:42:00 status half-installed libc6-i686 2.8~20080505-0ubuntu7
2009-03-30 06:42:00 status half-installed libc6-i686 2.8~20080505-0ubuntu7
2009-03-30 06:42:00 status unpacked libc6-i686 2.8~20080505-0ubuntu9
2009-03-30 06:42:00 status unpacked libc6-i686 2.8~20080505-0ubuntu9
2009-03-30 06:42:00 upgrade gcc-4.3-base 4.3.2-1ubuntu11 4.3.2-1ubuntu12
2009-03-30 06:42:00 status half-configured gcc-4.3-base 4.3.2-1ubuntu11
2009-03-30 06:42:00 status unpacked gcc-4.3-base 4.3.2-1ubuntu11
2009-03-30 06:42:00 status half-installed gcc-4.3-base 4.3.2-1ubuntu11
2009-03-30 06:42:00 status half-installed gcc-4.3-base 4.3.2-1ubuntu11
2009-03-30 06:42:00 status unpacked gcc-4.3-base 4.3.2-1ubuntu12
2009-03-30 06:42:00 status unpacked gcc-4.3-base 4.3.2-1ubuntu12
2009-03-30 06:42:01 startup packages configure
2009-03-30 06:42:01 configure gcc-4.3-base 4.3.2-1ubuntu12 4.3.2-1ubuntu12
2009-03-30 06:42:01 status unpacked gcc-4.3-base 4.3.2-1ubuntu12
2009-03-30 06:42:01 status half-configured gcc-4.3-base 4.3.2-1ubuntu12
2009-03-30 06:42:01 status installed gcc-4.3-base 4.3.2-1ubuntu12
2009-03-30 06:42:01 startup archives unpack
2009-03-30 06:42:01 upgrade libgcc1 1:4.3.2-1ubuntu11 1:4.3.2-1ubuntu12
2009-03-30 06:42:01 status half-configured libgcc1 1:4.3.2-1ubuntu11
2009-03-30 06:42:01 status unpacked libgcc1 1:4.3.2-1ubuntu11
2009-03-30 06:42:01 status half-installed libgcc1 1:4.3.2-1ubuntu11
2009-03-30 06:42:01 status half-installed libgcc1 1:4.3.2-1ubuntu11
2009-03-30 06:42:02 status unpacked libgcc1 1:4.3.2-1ubuntu12
2009-03-30 06:42:02 status unpacked libgcc1 1:4.3.2-1ubuntu12
2009-03-30 06:42:02 startup packages configure
2009-03-30 06:42:02 configure libgcc1 1:4.3.2-1ubuntu12 1:4.3.2-1ubuntu12
2009-03-30 06:42:02 status unpacked libgcc1 1:4.3.2-1ubuntu12
2009-03-30 06:42:02 status half-configured libgcc1 1:4.3.2-1ubuntu12
2009-03-30 06:42:02 status installed libgcc1 1:4.3.2-1ubuntu12
2009-03-30 06:42:02 status triggers-pending libc6 2.8~20080505-0ubuntu9
2009-03-30 06:42:02 trigproc libc6 2.8~20080505-0ubuntu9 2.8~20080505-0ubuntu9
2009-03-30 06:42:02 status half-configured libc6 2.8~20080505-0ubuntu9
2009-03-30 06:42:02 status installed libc6 2.8~20080505-0ubuntu9
2009-03-30 06:42:03 startup archives unpack
2009-03-30 06:42:03 upgrade cpp-4.3 4.3.2-1ubuntu11 4.3.2-1ubuntu12
2009-03-30 06:42:03 status half-configured cpp-4.3 4.3.2-1ubuntu11
2009-03-30 06:42:03 status unpacked cpp-4.3 4.3.2-1ubuntu11
2009-03-30 06:42:03 status half-installed cpp-4.3 4.3.2-1ubuntu11
2009-03-30 06:42:03 status triggers-pending man-db 2.5.2-2
2009-03-30 06:42:03 status half-installed cpp-4.3 4.3.2-1ubuntu11
2009-03-30 06:42:03 status half-installed cpp-4.3 4.3.2-1ubuntu11
2009-03-30 06:42:03 status unpacked cpp-4.3 4.3.2-1ubuntu12
2009-03-30 06:42:03 status unpacked cpp-4.3 4.3.2-1ubuntu12
2009-03-30 06:42:03 upgrade libstdc++6 4.3.2-1ubuntu11 4.3.2-1ubuntu12
2009-03-30 06:42:03 status half-configured libstdc++6 4.3.2-1ubuntu11
2009-03-30 06:42:03 status unpacked libstdc++6 4.3.2-1ubuntu11
2009-03-30 06:42:03 status half-installed libstdc++6 4.3.2-1ubuntu11
2009-03-30 06:42:03 status half-installed libstdc++6 4.3.2-1ubuntu11
2009-03-30 06:42:03 status unpacked libstdc++6 4.3.2-1ubuntu12
2009-03-30 06:42:03 status unpacked libstdc++6 4.3.2-1ubuntu12
2009-03-30 06:42:03 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-30 06:42:03 status half-configured man-db 2.5.2-2
2009-03-30 06:42:03 status installed man-db 2.5.2-2
2009-03-30 06:42:04 startup packages configure
2009-03-30 06:42:04 configure libstdc++6 4.3.2-1ubuntu12 4.3.2-1ubuntu12
2009-03-30 06:42:04 status unpacked libstdc++6 4.3.2-1ubuntu12
2009-03-30 06:42:04 status half-configured libstdc++6 4.3.2-1ubuntu12
2009-03-30 06:42:04 status installed libstdc++6 4.3.2-1ubuntu12
2009-03-30 06:42:04 status triggers-pending libc6 2.8~20080505-0ubuntu9
2009-03-30 06:42:04 trigproc libc6 2.8~20080505-0ubuntu9 2.8~20080505-0ubuntu9
2009-03-30 06:42:04 status half-configured libc6 2.8~20080505-0ubuntu9
2009-03-30 06:42:04 status installed libc6 2.8~20080505-0ubuntu9
2009-03-30 06:42:05 startup archives unpack
2009-03-30 06:42:05 upgrade perl 5.10.0-11.1ubuntu2 5.10.0-11.1ubuntu2.2
2009-03-30 06:42:05 status half-configured perl 5.10.0-11.1ubuntu2
2009-03-30 06:42:05 status unpacked perl 5.10.0-11.1ubuntu2
2009-03-30 06:42:05 status half-installed perl 5.10.0-11.1ubuntu2
2009-03-30 06:42:05 status triggers-pending man-db 2.5.2-2
2009-03-30 06:42:06 status half-installed perl 5.10.0-11.1ubuntu2
2009-03-30 06:42:06 status half-installed perl 5.10.0-11.1ubuntu2
2009-03-30 06:42:06 status unpacked perl 5.10.0-11.1ubuntu2.2
2009-03-30 06:42:06 status unpacked perl 5.10.0-11.1ubuntu2.2
2009-03-30 06:42:06 upgrade perl-base 5.10.0-11.1ubuntu2 5.10.0-11.1ubuntu2.2
2009-03-30 06:42:06 status half-configured perl-base 5.10.0-11.1ubuntu2
2009-03-30 06:42:06 status unpacked perl-base 5.10.0-11.1ubuntu2
2009-03-30 06:42:06 status half-installed perl-base 5.10.0-11.1ubuntu2
2009-03-30 06:42:06 status half-installed perl-base 5.10.0-11.1ubuntu2
2009-03-30 06:42:06 status half-installed perl-base 5.10.0-11.1ubuntu2
2009-03-30 06:42:06 status unpacked perl-base 5.10.0-11.1ubuntu2.2
2009-03-30 06:42:06 status unpacked perl-base 5.10.0-11.1ubuntu2.2
2009-03-30 06:42:06 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-30 06:42:06 status half-configured man-db 2.5.2-2
2009-03-30 06:42:07 status installed man-db 2.5.2-2
2009-03-30 06:42:07 startup packages configure
2009-03-30 06:42:07 configure perl-base 5.10.0-11.1ubuntu2.2 5.10.0-11.1ubuntu2.2
2009-03-30 06:42:07 status unpacked perl-base 5.10.0-11.1ubuntu2.2
2009-03-30 06:42:07 status half-configured perl-base 5.10.0-11.1ubuntu2.2
2009-03-30 06:42:07 status installed perl-base 5.10.0-11.1ubuntu2.2
2009-03-30 06:42:08 startup archives unpack
2009-03-30 06:42:08 upgrade libpam-runtime 1.0.1-4ubuntu5 1.0.1-4ubuntu5.3
2009-03-30 06:42:08 status half-configured libpam-runtime 1.0.1-4ubuntu5
2009-03-30 06:42:08 status unpacked libpam-runtime 1.0.1-4ubuntu5
2009-03-30 06:42:08 status half-installed libpam-runtime 1.0.1-4ubuntu5
2009-03-30 06:42:08 status triggers-pending man-db 2.5.2-2
2009-03-30 06:42:08 status half-installed libpam-runtime 1.0.1-4ubuntu5
2009-03-30 06:42:08 status half-installed libpam-runtime 1.0.1-4ubuntu5
2009-03-30 06:42:08 status unpacked libpam-runtime 1.0.1-4ubuntu5.3
2009-03-30 06:42:08 status unpacked libpam-runtime 1.0.1-4ubuntu5.3
2009-03-30 06:42:08 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-30 06:42:08 status half-configured man-db 2.5.2-2
2009-03-30 06:42:08 status installed man-db 2.5.2-2
2009-03-30 06:42:09 startup packages configure
2009-03-30 06:42:09 configure libpam-runtime 1.0.1-4ubuntu5.3 1.0.1-4ubuntu5.3
2009-03-30 06:42:09 status unpacked libpam-runtime 1.0.1-4ubuntu5.3
2009-03-30 06:42:09 status unpacked libpam-runtime 1.0.1-4ubuntu5.3
2009-03-30 06:42:09 status unpacked libpam-runtime 1.0.1-4ubuntu5.3
2009-03-30 06:42:09 status half-configured libpam-runtime 1.0.1-4ubuntu5.3
2009-03-30 06:42:09 status installed libpam-runtime 1.0.1-4ubuntu5.3
2009-03-30 06:42:10 startup archives unpack
2009-03-30 06:42:10 upgrade libpam0g 1.0.1-4ubuntu5 1.0.1-4ubuntu5.3
2009-03-30 06:42:10 status half-configured libpam0g 1.0.1-4ubuntu5
2009-03-30 06:42:10 status unpacked libpam0g 1.0.1-4ubuntu5
2009-03-30 06:42:10 status half-installed libpam0g 1.0.1-4ubuntu5
2009-03-30 06:42:10 status half-installed libpam0g 1.0.1-4ubuntu5
2009-03-30 06:42:10 status unpacked libpam0g 1.0.1-4ubuntu5.3
2009-03-30 06:42:10 status unpacked libpam0g 1.0.1-4ubuntu5.3
2009-03-30 06:42:10 startup packages configure
2009-03-30 06:42:10 configure libpam0g 1.0.1-4ubuntu5.3 1.0.1-4ubuntu5.3
2009-03-30 06:42:10 status unpacked libpam0g 1.0.1-4ubuntu5.3
2009-03-30 06:42:10 status half-configured libpam0g 1.0.1-4ubuntu5.3
2009-03-30 06:42:11 status installed libpam0g 1.0.1-4ubuntu5.3
2009-03-30 06:42:11 status triggers-pending libc6 2.8~20080505-0ubuntu9
2009-03-30 06:42:11 trigproc libc6 2.8~20080505-0ubuntu9 2.8~20080505-0ubuntu9
2009-03-30 06:42:11 status half-configured libc6 2.8~20080505-0ubuntu9
2009-03-30 06:42:11 status installed libc6 2.8~20080505-0ubuntu9
2009-03-30 06:42:11 startup archives unpack
2009-03-30 06:42:11 upgrade libpam-modules 1.0.1-4ubuntu5 1.0.1-4ubuntu5.3
2009-03-30 06:42:11 status half-configured libpam-modules 1.0.1-4ubuntu5
2009-03-30 06:42:11 status unpacked libpam-modules 1.0.1-4ubuntu5
2009-03-30 06:42:11 status half-installed libpam-modules 1.0.1-4ubuntu5
2009-03-30 06:42:11 status triggers-pending man-db 2.5.2-2
2009-03-30 06:42:11 status half-installed libpam-modules 1.0.1-4ubuntu5
2009-03-30 06:42:11 status half-installed libpam-modules 1.0.1-4ubuntu5
2009-03-30 06:42:12 status unpacked libpam-modules 1.0.1-4ubuntu5.3
2009-03-30 06:42:12 status unpacked libpam-modules 1.0.1-4ubuntu5.3
2009-03-30 06:42:12 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-30 06:42:12 status half-configured man-db 2.5.2-2
2009-03-30 06:42:12 status installed man-db 2.5.2-2
2009-03-30 06:42:12 startup packages configure
2009-03-30 06:42:12 configure libpam-modules 1.0.1-4ubuntu5.3 1.0.1-4ubuntu5.3
2009-03-30 06:42:12 status unpacked libpam-modules 1.0.1-4ubuntu5.3
2009-03-30 06:42:12 status unpacked libpam-modules 1.0.1-4ubuntu5.3
2009-03-30 06:42:12 status unpacked libpam-modules 1.0.1-4ubuntu5.3
2009-03-30 06:42:12 status unpacked libpam-modules 1.0.1-4ubuntu5.3
2009-03-30 06:42:12 status unpacked libpam-modules 1.0.1-4ubuntu5.3
2009-03-30 06:42:12 status unpacked libpam-modules 1.0.1-4ubuntu5.3
2009-03-30 06:42:12 status unpacked libpam-modules 1.0.1-4ubuntu5.3
2009-03-30 06:42:12 status unpacked libpam-modules 1.0.1-4ubuntu5.3
2009-03-30 06:42:12 status unpacked libpam-modules 1.0.1-4ubuntu5.3
2009-03-30 06:42:12 status half-configured libpam-modules 1.0.1-4ubuntu5.3
2009-03-30 06:42:13 status installed libpam-modules 1.0.1-4ubuntu5.3
2009-03-30 06:42:13 startup archives unpack
2009-03-30 06:42:13 upgrade base-files 4.0.4ubuntu2 4.0.4ubuntu2.2
2009-03-30 06:42:13 status half-configured base-files 4.0.4ubuntu2
2009-03-30 06:42:13 status unpacked base-files 4.0.4ubuntu2
2009-03-30 06:42:13 status half-installed base-files 4.0.4ubuntu2
2009-03-30 06:42:13 status triggers-pending man-db 2.5.2-2
2009-03-30 06:42:13 status half-installed base-files 4.0.4ubuntu2
2009-03-30 06:42:13 status half-installed base-files 4.0.4ubuntu2
2009-03-30 06:42:13 status unpacked base-files 4.0.4ubuntu2.2
2009-03-30 06:42:13 status unpacked base-files 4.0.4ubuntu2.2
2009-03-30 06:42:13 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-30 06:42:13 status half-configured man-db 2.5.2-2
2009-03-30 06:42:13 status installed man-db 2.5.2-2
2009-03-30 06:42:14 startup packages configure
2009-03-30 06:42:14 configure base-files 4.0.4ubuntu2.2 4.0.4ubuntu2.2
2009-03-30 06:42:14 status unpacked base-files 4.0.4ubuntu2.2
2009-03-30 06:42:14 status unpacked base-files 4.0.4ubuntu2.2
2009-03-30 06:42:14 status unpacked base-files 4.0.4ubuntu2.2
2009-03-30 06:42:14 status unpacked base-files 4.0.4ubuntu2.2
2009-03-30 06:42:14 status unpacked base-files 4.0.4ubuntu2.2
2009-03-30 06:42:14 status unpacked base-files 4.0.4ubuntu2.2
2009-03-30 06:42:14 status half-configured base-files 4.0.4ubuntu2.2
2009-03-30 06:42:15 status installed base-files 4.0.4ubuntu2.2
2009-03-30 06:42:16 startup archives unpack
2009-03-30 06:42:16 upgrade busybox-initramfs 1:1.10.2-1ubuntu6 1:1.10.2-1ubuntu7
2009-03-30 06:42:16 status half-configured busybox-initramfs 1:1.10.2-1ubuntu6
2009-03-30 06:42:16 status unpacked busybox-initramfs 1:1.10.2-1ubuntu6
2009-03-30 06:42:16 status half-installed busybox-initramfs 1:1.10.2-1ubuntu6
2009-03-30 06:42:16 status half-installed busybox-initramfs 1:1.10.2-1ubuntu6
2009-03-30 06:42:16 status unpacked busybox-initramfs 1:1.10.2-1ubuntu7
2009-03-30 06:42:16 status unpacked busybox-initramfs 1:1.10.2-1ubuntu7
2009-03-30 06:42:16 upgrade libvolume-id0 124-8 124-9
2009-03-30 06:42:16 status half-configured libvolume-id0 124-8
2009-03-30 06:42:16 status unpacked libvolume-id0 124-8
2009-03-30 06:42:16 status half-installed libvolume-id0 124-8
2009-03-30 06:42:16 status half-installed libvolume-id0 124-8
2009-03-30 06:42:16 status unpacked libvolume-id0 124-9
2009-03-30 06:42:16 status unpacked libvolume-id0 124-9
2009-03-30 06:42:16 upgrade procps 1:3.2.7-9ubuntu2 1:3.2.7-9ubuntu2.1
2009-03-30 06:42:16 status half-configured procps 1:3.2.7-9ubuntu2
2009-03-30 06:42:16 status unpacked procps 1:3.2.7-9ubuntu2
2009-03-30 06:42:16 status half-installed procps 1:3.2.7-9ubuntu2
2009-03-30 06:42:16 status triggers-pending man-db 2.5.2-2
2009-03-30 06:42:16 status half-installed procps 1:3.2.7-9ubuntu2
2009-03-30 06:42:16 status half-installed procps 1:3.2.7-9ubuntu2
2009-03-30 06:42:16 status unpacked procps 1:3.2.7-9ubuntu2.1
2009-03-30 06:42:16 status unpacked procps 1:3.2.7-9ubuntu2.1
2009-03-30 06:42:16 upgrade udev 124-8 124-9
2009-03-30 06:42:16 status half-configured udev 124-8
2009-03-30 06:42:16 status unpacked udev 124-8
2009-03-30 06:42:16 status half-installed udev 124-8
2009-03-30 06:42:16 status half-installed udev 124-8
2009-03-30 06:42:17 status half-installed udev 124-8
2009-03-30 06:42:17 status unpacked udev 124-9
2009-03-30 06:42:17 status unpacked udev 124-9
2009-03-30 06:42:17 upgrade initramfs-tools 0.92bubuntu15 0.92bubuntu16
2009-03-30 06:42:17 status half-configured initramfs-tools 0.92bubuntu15
2009-03-30 06:42:17 status unpacked initramfs-tools 0.92bubuntu15
2009-03-30 06:42:17 status half-installed initramfs-tools 0.92bubuntu15
2009-03-30 06:42:17 status half-installed initramfs-tools 0.92bubuntu15
2009-03-30 06:42:17 status half-installed initramfs-tools 0.92bubuntu15
2009-03-30 06:42:17 status unpacked initramfs-tools 0.92bubuntu16
2009-03-30 06:42:17 status unpacked initramfs-tools 0.92bubuntu16
2009-03-30 06:42:17 upgrade linux-image-2.6.27-7-server 2.6.27-7.14 2.6.27-7.16
2009-03-30 06:42:17 status half-configured linux-image-2.6.27-7-server 2.6.27-7.14
2009-03-30 06:42:17 status unpacked linux-image-2.6.27-7-server 2.6.27-7.14
2009-03-30 06:42:17 status half-installed linux-image-2.6.27-7-server 2.6.27-7.14
2009-03-30 06:42:29 status half-installed linux-image-2.6.27-7-server 2.6.27-7.14
2009-03-30 06:42:35 status unpacked linux-image-2.6.27-7-server 2.6.27-7.16
2009-03-30 06:42:36 status unpacked linux-image-2.6.27-7-server 2.6.27-7.16
2009-03-30 06:42:37 upgrade passwd 1:4.1.1-1ubuntu1 1:4.1.1-1ubuntu1.2
2009-03-30 06:42:37 status half-configured passwd 1:4.1.1-1ubuntu1
2009-03-30 06:42:37 status unpacked passwd 1:4.1.1-1ubuntu1
2009-03-30 06:42:37 status half-installed passwd 1:4.1.1-1ubuntu1
2009-03-30 06:42:37 status half-installed passwd 1:4.1.1-1ubuntu1
2009-03-30 06:42:37 status half-installed passwd 1:4.1.1-1ubuntu1
2009-03-30 06:42:37 status unpacked passwd 1:4.1.1-1ubuntu1.2
2009-03-30 06:42:37 status unpacked passwd 1:4.1.1-1ubuntu1.2
2009-03-30 06:42:37 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-30 06:42:37 status half-configured man-db 2.5.2-2
2009-03-30 06:42:38 status installed man-db 2.5.2-2
2009-03-30 06:42:39 startup packages configure
2009-03-30 06:42:39 configure passwd 1:4.1.1-1ubuntu1.2 1:4.1.1-1ubuntu1.2
2009-03-30 06:42:39 status unpacked passwd 1:4.1.1-1ubuntu1.2
2009-03-30 06:42:39 status unpacked passwd 1:4.1.1-1ubuntu1.2
2009-03-30 06:42:39 status unpacked passwd 1:4.1.1-1ubuntu1.2
2009-03-30 06:42:39 status unpacked passwd 1:4.1.1-1ubuntu1.2
2009-03-30 06:42:39 status unpacked passwd 1:4.1.1-1ubuntu1.2
2009-03-30 06:42:39 status half-configured passwd 1:4.1.1-1ubuntu1.2
2009-03-30 06:42:39 status installed passwd 1:4.1.1-1ubuntu1.2
2009-03-30 06:42:39 startup archives unpack
2009-03-30 06:42:39 upgrade tzdata 2008h-2ubuntu1 2009b-0ubuntu0.8.10
2009-03-30 06:42:39 status half-configured tzdata 2008h-2ubuntu1
2009-03-30 06:42:39 status unpacked tzdata 2008h-2ubuntu1
2009-03-30 06:42:39 status half-installed tzdata 2008h-2ubuntu1
2009-03-30 06:42:40 status half-installed tzdata 2008h-2ubuntu1
2009-03-30 06:42:40 status unpacked tzdata 2009b-0ubuntu0.8.10
2009-03-30 06:42:40 status unpacked tzdata 2009b-0ubuntu0.8.10
2009-03-30 06:42:41 startup packages configure
2009-03-30 06:42:41 configure tzdata 2009b-0ubuntu0.8.10 2009b-0ubuntu0.8.10
2009-03-30 06:42:41 status unpacked tzdata 2009b-0ubuntu0.8.10
2009-03-30 06:42:41 status half-configured tzdata 2009b-0ubuntu0.8.10
2009-03-30 06:42:41 status installed tzdata 2009b-0ubuntu0.8.10
2009-03-30 06:42:42 startup archives unpack
2009-03-30 06:42:42 upgrade libssl0.9.8 0.9.8g-10.1ubuntu2 0.9.8g-10.1ubuntu2.1
2009-03-30 06:42:42 status half-configured libssl0.9.8 0.9.8g-10.1ubuntu2
2009-03-30 06:42:42 status unpacked libssl0.9.8 0.9.8g-10.1ubuntu2
2009-03-30 06:42:42 status half-installed libssl0.9.8 0.9.8g-10.1ubuntu2
2009-03-30 06:42:42 status half-installed libssl0.9.8 0.9.8g-10.1ubuntu2
2009-03-30 06:42:42 status unpacked libssl0.9.8 0.9.8g-10.1ubuntu2.1
2009-03-30 06:42:42 status unpacked libssl0.9.8 0.9.8g-10.1ubuntu2.1
2009-03-30 06:42:42 upgrade openssl 0.9.8g-10.1ubuntu2 0.9.8g-10.1ubuntu2.1
2009-03-30 06:42:42 status half-configured openssl 0.9.8g-10.1ubuntu2
2009-03-30 06:42:42 status unpacked openssl 0.9.8g-10.1ubuntu2
2009-03-30 06:42:42 status half-installed openssl 0.9.8g-10.1ubuntu2
2009-03-30 06:42:42 status triggers-pending man-db 2.5.2-2
2009-03-30 06:42:42 status half-installed openssl 0.9.8g-10.1ubuntu2
2009-03-30 06:42:42 status half-installed openssl 0.9.8g-10.1ubuntu2
2009-03-30 06:42:43 status unpacked openssl 0.9.8g-10.1ubuntu2.1
2009-03-30 06:42:43 status unpacked openssl 0.9.8g-10.1ubuntu2.1
2009-03-30 06:42:43 upgrade ca-certificates 20080514-0ubuntu1 20080514-0ubuntu1.1
2009-03-30 06:42:43 status half-configured ca-certificates 20080514-0ubuntu1
2009-03-30 06:42:43 status unpacked ca-certificates 20080514-0ubuntu1
2009-03-30 06:42:43 status half-installed ca-certificates 20080514-0ubuntu1
2009-03-30 06:42:43 status half-installed ca-certificates 20080514-0ubuntu1
2009-03-30 06:42:43 status half-installed ca-certificates 20080514-0ubuntu1
2009-03-30 06:42:43 status unpacked ca-certificates 20080514-0ubuntu1.1
2009-03-30 06:42:43 status unpacked ca-certificates 20080514-0ubuntu1.1
2009-03-30 06:42:43 upgrade libgnutls26 2.4.1-1build1 2.4.1-1ubuntu0.2
2009-03-30 06:42:43 status half-configured libgnutls26 2.4.1-1build1
2009-03-30 06:42:43 status unpacked libgnutls26 2.4.1-1build1
2009-03-30 06:42:43 status half-installed libgnutls26 2.4.1-1build1
2009-03-30 06:42:43 status half-installed libgnutls26 2.4.1-1build1
2009-03-30 06:42:43 status unpacked libgnutls26 2.4.1-1ubuntu0.2
2009-03-30 06:42:43 status unpacked libgnutls26 2.4.1-1ubuntu0.2
2009-03-30 06:42:43 upgrade libldap-2.4-2 2.4.11-0ubuntu6 2.4.11-0ubuntu6.1
2009-03-30 06:42:43 status half-configured libldap-2.4-2 2.4.11-0ubuntu6
2009-03-30 06:42:43 status unpacked libldap-2.4-2 2.4.11-0ubuntu6
2009-03-30 06:42:43 status half-installed libldap-2.4-2 2.4.11-0ubuntu6
2009-03-30 06:42:43 status half-installed libldap-2.4-2 2.4.11-0ubuntu6
2009-03-30 06:42:43 status half-installed libldap-2.4-2 2.4.11-0ubuntu6
2009-03-30 06:42:43 status unpacked libldap-2.4-2 2.4.11-0ubuntu6.1
2009-03-30 06:42:43 status unpacked libldap-2.4-2 2.4.11-0ubuntu6.1
2009-03-30 06:42:43 upgrade libsqlite3-0 3.5.9-3 3.5.9-3ubuntu1
2009-03-30 06:42:43 status half-configured libsqlite3-0 3.5.9-3
2009-03-30 06:42:43 status unpacked libsqlite3-0 3.5.9-3
2009-03-30 06:42:43 status half-installed libsqlite3-0 3.5.9-3
2009-03-30 06:42:43 status half-installed libsqlite3-0 3.5.9-3
2009-03-30 06:42:43 status unpacked libsqlite3-0 3.5.9-3ubuntu1
2009-03-30 06:42:43 status unpacked libsqlite3-0 3.5.9-3ubuntu1
2009-03-30 06:42:43 upgrade vim-tiny 1:7.1.314-3ubuntu3 1:7.1.314-3ubuntu3.1
2009-03-30 06:42:43 status half-configured vim-tiny 1:7.1.314-3ubuntu3
2009-03-30 06:42:43 status unpacked vim-tiny 1:7.1.314-3ubuntu3
2009-03-30 06:42:43 status half-installed vim-tiny 1:7.1.314-3ubuntu3
2009-03-30 06:42:43 status half-installed vim-tiny 1:7.1.314-3ubuntu3
2009-03-30 06:42:43 status unpacked vim-tiny 1:7.1.314-3ubuntu3.1
2009-03-30 06:42:43 status unpacked vim-tiny 1:7.1.314-3ubuntu3.1
2009-03-30 06:42:43 upgrade vim-common 1:7.1.314-3ubuntu3 1:7.1.314-3ubuntu3.1
2009-03-30 06:42:43 status half-configured vim-common 1:7.1.314-3ubuntu3
2009-03-30 06:42:43 status unpacked vim-common 1:7.1.314-3ubuntu3
2009-03-30 06:42:43 status half-installed vim-common 1:7.1.314-3ubuntu3
2009-03-30 06:42:43 status half-installed vim-common 1:7.1.314-3ubuntu3
2009-03-30 06:42:44 status half-installed vim-common 1:7.1.314-3ubuntu3
2009-03-30 06:42:44 status unpacked vim-common 1:7.1.314-3ubuntu3.1
2009-03-30 06:42:44 status unpacked vim-common 1:7.1.314-3ubuntu3.1
2009-03-30 06:42:44 upgrade xkb-data 1.3-2ubuntu4 1.3-2ubuntu4.4
2009-03-30 06:42:44 status half-configured xkb-data 1.3-2ubuntu4
2009-03-30 06:42:44 status unpacked xkb-data 1.3-2ubuntu4
2009-03-30 06:42:44 status half-installed xkb-data 1.3-2ubuntu4
2009-03-30 06:42:44 status half-installed xkb-data 1.3-2ubuntu4
2009-03-30 06:42:44 status unpacked xkb-data 1.3-2ubuntu4.4
2009-03-30 06:42:44 status unpacked xkb-data 1.3-2ubuntu4.4
2009-03-30 06:42:44 upgrade apparmor 2.3+1289-0ubuntu4 2.3+1289-0ubuntu4.1
2009-03-30 06:42:44 status half-configured apparmor 2.3+1289-0ubuntu4
2009-03-30 06:42:44 status unpacked apparmor 2.3+1289-0ubuntu4
2009-03-30 06:42:44 status half-installed apparmor 2.3+1289-0ubuntu4
2009-03-30 06:42:44 status half-installed apparmor 2.3+1289-0ubuntu4
2009-03-30 06:42:44 status half-installed apparmor 2.3+1289-0ubuntu4
2009-03-30 06:42:44 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:44 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:44 upgrade libapparmor1 2.3+1289-0ubuntu4 2.3+1289-0ubuntu4.1
2009-03-30 06:42:44 status half-configured libapparmor1 2.3+1289-0ubuntu4
2009-03-30 06:42:44 status unpacked libapparmor1 2.3+1289-0ubuntu4
2009-03-30 06:42:44 status half-installed libapparmor1 2.3+1289-0ubuntu4
2009-03-30 06:42:44 status half-installed libapparmor1 2.3+1289-0ubuntu4
2009-03-30 06:42:44 status half-installed libapparmor1 2.3+1289-0ubuntu4
2009-03-30 06:42:44 status unpacked libapparmor1 2.3+1289-0ubuntu4.1
2009-03-30 06:42:45 status unpacked libapparmor1 2.3+1289-0ubuntu4.1
2009-03-30 06:42:45 upgrade libapparmor-perl 2.3+1289-0ubuntu4 2.3+1289-0ubuntu4.1
2009-03-30 06:42:45 status half-configured libapparmor-perl 2.3+1289-0ubuntu4
2009-03-30 06:42:45 status unpacked libapparmor-perl 2.3+1289-0ubuntu4
2009-03-30 06:42:45 status half-installed libapparmor-perl 2.3+1289-0ubuntu4
2009-03-30 06:42:45 status half-installed libapparmor-perl 2.3+1289-0ubuntu4
2009-03-30 06:42:45 status unpacked libapparmor-perl 2.3+1289-0ubuntu4.1
2009-03-30 06:42:45 status unpacked libapparmor-perl 2.3+1289-0ubuntu4.1
2009-03-30 06:42:45 upgrade apparmor-utils 2.3+1289-0ubuntu4 2.3+1289-0ubuntu4.1
2009-03-30 06:42:45 status half-configured apparmor-utils 2.3+1289-0ubuntu4
2009-03-30 06:42:45 status unpacked apparmor-utils 2.3+1289-0ubuntu4
2009-03-30 06:42:45 status half-installed apparmor-utils 2.3+1289-0ubuntu4
2009-03-30 06:42:45 status half-installed apparmor-utils 2.3+1289-0ubuntu4
2009-03-30 06:42:45 status half-installed apparmor-utils 2.3+1289-0ubuntu4
2009-03-30 06:42:45 status unpacked apparmor-utils 2.3+1289-0ubuntu4.1
2009-03-30 06:42:45 status unpacked apparmor-utils 2.3+1289-0ubuntu4.1
2009-03-30 06:42:45 upgrade libxml2 2.6.32.dfsg-4ubuntu1 2.6.32.dfsg-4ubuntu1.1
2009-03-30 06:42:45 status half-configured libxml2 2.6.32.dfsg-4ubuntu1
2009-03-30 06:42:45 status unpacked libxml2 2.6.32.dfsg-4ubuntu1
2009-03-30 06:42:45 status half-installed libxml2 2.6.32.dfsg-4ubuntu1
2009-03-30 06:42:45 status half-installed libxml2 2.6.32.dfsg-4ubuntu1
2009-03-30 06:42:45 status unpacked libxml2 2.6.32.dfsg-4ubuntu1.1
2009-03-30 06:42:45 status unpacked libxml2 2.6.32.dfsg-4ubuntu1.1
2009-03-30 06:42:45 upgrade dnsutils 1:9.5.0.dfsg.P2-1ubuntu2 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:45 status half-configured dnsutils 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status unpacked dnsutils 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status half-installed dnsutils 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status half-installed dnsutils 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status half-installed dnsutils 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status unpacked dnsutils 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:45 status unpacked dnsutils 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:45 upgrade bind9-host 1:9.5.0.dfsg.P2-1ubuntu2 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:45 status half-configured bind9-host 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status unpacked bind9-host 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status half-installed bind9-host 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status half-installed bind9-host 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status half-installed bind9-host 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status unpacked bind9-host 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:45 status unpacked bind9-host 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:45 upgrade libbind9-40 1:9.5.0.dfsg.P2-1ubuntu2 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:45 status half-configured libbind9-40 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status unpacked libbind9-40 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status half-installed libbind9-40 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status half-installed libbind9-40 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status unpacked libbind9-40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:45 status unpacked libbind9-40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:45 upgrade libisccfg40 1:9.5.0.dfsg.P2-1ubuntu2 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:45 status half-configured libisccfg40 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status unpacked libisccfg40 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status half-installed libisccfg40 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status half-installed libisccfg40 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status unpacked libisccfg40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:45 status unpacked libisccfg40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:45 upgrade libisccc40 1:9.5.0.dfsg.P2-1ubuntu2 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:45 status half-configured libisccc40 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status unpacked libisccc40 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status half-installed libisccc40 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status half-installed libisccc40 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:45 status unpacked libisccc40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:46 status unpacked libisccc40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:46 upgrade libdns43 1:9.5.0.dfsg.P2-1ubuntu2 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:46 status half-configured libdns43 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:46 status unpacked libdns43 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:46 status half-installed libdns43 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:46 status half-installed libdns43 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:46 status unpacked libdns43 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:46 status unpacked libdns43 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:46 upgrade libisc44 1:9.5.0.dfsg.P2-1ubuntu2 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:46 status half-configured libisc44 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:46 status unpacked libisc44 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:46 status half-installed libisc44 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:46 status half-installed libisc44 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:46 status unpacked libisc44 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:46 status unpacked libisc44 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:46 upgrade liblwres40 1:9.5.0.dfsg.P2-1ubuntu2 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:46 status half-configured liblwres40 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:46 status unpacked liblwres40 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:46 status half-installed liblwres40 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:46 status half-installed liblwres40 1:9.5.0.dfsg.P2-1ubuntu2
2009-03-30 06:42:46 status unpacked liblwres40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:46 status unpacked liblwres40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:46 upgrade command-not-found-data 0.2.26ubuntu1 0.2.26ubuntu1.1
2009-03-30 06:42:46 status half-configured command-not-found-data 0.2.26ubuntu1
2009-03-30 06:42:46 status unpacked command-not-found-data 0.2.26ubuntu1
2009-03-30 06:42:46 status half-installed command-not-found-data 0.2.26ubuntu1
2009-03-30 06:42:46 status half-installed command-not-found-data 0.2.26ubuntu1
2009-03-30 06:42:46 status unpacked command-not-found-data 0.2.26ubuntu1.1
2009-03-30 06:42:46 status unpacked command-not-found-data 0.2.26ubuntu1.1
2009-03-30 06:42:46 upgrade command-not-found 0.2.26ubuntu1 0.2.26ubuntu1.1
2009-03-30 06:42:46 status half-configured command-not-found 0.2.26ubuntu1
2009-03-30 06:42:46 status unpacked command-not-found 0.2.26ubuntu1
2009-03-30 06:42:46 status half-installed command-not-found 0.2.26ubuntu1
2009-03-30 06:42:47 status half-installed command-not-found 0.2.26ubuntu1
2009-03-30 06:42:47 status unpacked command-not-found 0.2.26ubuntu1.1
2009-03-30 06:42:47 status unpacked command-not-found 0.2.26ubuntu1.1
2009-03-30 06:42:47 upgrade libx11-data 2:1.1.5-2ubuntu1 2:1.1.5-2ubuntu1.1
2009-03-30 06:42:47 status half-configured libx11-data 2:1.1.5-2ubuntu1
2009-03-30 06:42:47 status unpacked libx11-data 2:1.1.5-2ubuntu1
2009-03-30 06:42:47 status half-installed libx11-data 2:1.1.5-2ubuntu1
2009-03-30 06:42:47 status half-installed libx11-data 2:1.1.5-2ubuntu1
2009-03-30 06:42:47 status unpacked libx11-data 2:1.1.5-2ubuntu1.1
2009-03-30 06:42:47 status unpacked libx11-data 2:1.1.5-2ubuntu1.1
2009-03-30 06:42:47 upgrade libx11-6 2:1.1.5-2ubuntu1 2:1.1.5-2ubuntu1.1
2009-03-30 06:42:47 status half-configured libx11-6 2:1.1.5-2ubuntu1
2009-03-30 06:42:47 status unpacked libx11-6 2:1.1.5-2ubuntu1
2009-03-30 06:42:47 status half-installed libx11-6 2:1.1.5-2ubuntu1
2009-03-30 06:42:47 status half-installed libx11-6 2:1.1.5-2ubuntu1
2009-03-30 06:42:47 status unpacked libx11-6 2:1.1.5-2ubuntu1.1
2009-03-30 06:42:47 status unpacked libx11-6 2:1.1.5-2ubuntu1.1
2009-03-30 06:42:47 upgrade ufw 0.23.2 0.23.3
2009-03-30 06:42:47 status half-configured ufw 0.23.2
2009-03-30 06:42:47 status unpacked ufw 0.23.2
2009-03-30 06:42:47 status half-installed ufw 0.23.2
2009-03-30 06:42:47 status half-installed ufw 0.23.2
2009-03-30 06:42:47 status half-installed ufw 0.23.2
2009-03-30 06:42:47 status unpacked ufw 0.23.3
2009-03-30 06:42:47 status unpacked ufw 0.23.3
2009-03-30 06:42:47 upgrade update-manager-core 1:0.93.32 1:0.93.34
2009-03-30 06:42:47 status half-configured update-manager-core 1:0.93.32
2009-03-30 06:42:48 status unpacked update-manager-core 1:0.93.32
2009-03-30 06:42:48 status half-installed update-manager-core 1:0.93.32
2009-03-30 06:42:48 status half-installed update-manager-core 1:0.93.32
2009-03-30 06:42:48 status unpacked update-manager-core 1:0.93.34
2009-03-30 06:42:48 status unpacked update-manager-core 1:0.93.34
2009-03-30 06:42:48 upgrade libck-connector0 0.2.10-1ubuntu9 0.2.10-1ubuntu10
2009-03-30 06:42:48 status half-configured libck-connector0 0.2.10-1ubuntu9
2009-03-30 06:42:48 status unpacked libck-connector0 0.2.10-1ubuntu9
2009-03-30 06:42:48 status half-installed libck-connector0 0.2.10-1ubuntu9
2009-03-30 06:42:48 status half-installed libck-connector0 0.2.10-1ubuntu9
2009-03-30 06:42:48 status unpacked libck-connector0 0.2.10-1ubuntu10
2009-03-30 06:42:48 status unpacked libck-connector0 0.2.10-1ubuntu10
2009-03-30 06:42:48 upgrade libglib2.0-0 2.18.2-0ubuntu1 2.18.2-0ubuntu2.1
2009-03-30 06:42:48 status half-configured libglib2.0-0 2.18.2-0ubuntu1
2009-03-30 06:42:48 status unpacked libglib2.0-0 2.18.2-0ubuntu1
2009-03-30 06:42:48 status half-installed libglib2.0-0 2.18.2-0ubuntu1
2009-03-30 06:42:48 status half-installed libglib2.0-0 2.18.2-0ubuntu1
2009-03-30 06:42:48 status unpacked libglib2.0-0 2.18.2-0ubuntu2.1
2009-03-30 06:42:48 status unpacked libglib2.0-0 2.18.2-0ubuntu2.1
2009-03-30 06:42:48 upgrade consolekit 0.2.10-1ubuntu9 0.2.10-1ubuntu10
2009-03-30 06:42:48 status half-configured consolekit 0.2.10-1ubuntu9
2009-03-30 06:42:48 status unpacked consolekit 0.2.10-1ubuntu9
2009-03-30 06:42:48 status half-installed consolekit 0.2.10-1ubuntu9
2009-03-30 06:42:48 status half-installed consolekit 0.2.10-1ubuntu9
2009-03-30 06:42:48 status unpacked consolekit 0.2.10-1ubuntu10
2009-03-30 06:42:48 status unpacked consolekit 0.2.10-1ubuntu10
2009-03-30 06:42:48 upgrade libcups2 1.3.9-2ubuntu7 1.3.9-2ubuntu8
2009-03-30 06:42:48 status half-configured libcups2 1.3.9-2ubuntu7
2009-03-30 06:42:48 status unpacked libcups2 1.3.9-2ubuntu7
2009-03-30 06:42:48 status half-installed libcups2 1.3.9-2ubuntu7
2009-03-30 06:42:48 status half-installed libcups2 1.3.9-2ubuntu7
2009-03-30 06:42:48 status unpacked libcups2 1.3.9-2ubuntu8
2009-03-30 06:42:49 status unpacked libcups2 1.3.9-2ubuntu8
2009-03-30 06:42:49 upgrade libcurl3-gnutls 7.18.2-1ubuntu4 7.18.2-1ubuntu4.3
2009-03-30 06:42:49 status half-configured libcurl3-gnutls 7.18.2-1ubuntu4
2009-03-30 06:42:49 status unpacked libcurl3-gnutls 7.18.2-1ubuntu4
2009-03-30 06:42:49 status half-installed libcurl3-gnutls 7.18.2-1ubuntu4
2009-03-30 06:42:49 status half-installed libcurl3-gnutls 7.18.2-1ubuntu4
2009-03-30 06:42:49 status unpacked libcurl3-gnutls 7.18.2-1ubuntu4.3
2009-03-30 06:42:49 status unpacked libcurl3-gnutls 7.18.2-1ubuntu4.3
2009-03-30 06:42:49 upgrade libglib2.0-data 2.18.2-0ubuntu1 2.18.2-0ubuntu2.1
2009-03-30 06:42:49 status half-configured libglib2.0-data 2.18.2-0ubuntu1
2009-03-30 06:42:49 status unpacked libglib2.0-data 2.18.2-0ubuntu1
2009-03-30 06:42:49 status half-installed libglib2.0-data 2.18.2-0ubuntu1
2009-03-30 06:42:49 status half-installed libglib2.0-data 2.18.2-0ubuntu1
2009-03-30 06:42:49 status unpacked libglib2.0-data 2.18.2-0ubuntu2.1
2009-03-30 06:42:49 status unpacked libglib2.0-data 2.18.2-0ubuntu2.1
2009-03-30 06:42:49 upgrade libpam-ck-connector 0.2.10-1ubuntu9 0.2.10-1ubuntu10
2009-03-30 06:42:49 status half-configured libpam-ck-connector 0.2.10-1ubuntu9
2009-03-30 06:42:49 status unpacked libpam-ck-connector 0.2.10-1ubuntu9
2009-03-30 06:42:49 status half-installed libpam-ck-connector 0.2.10-1ubuntu9
2009-03-30 06:42:49 status half-installed libpam-ck-connector 0.2.10-1ubuntu9
2009-03-30 06:42:49 status half-installed libpam-ck-connector 0.2.10-1ubuntu9
2009-03-30 06:42:49 status unpacked libpam-ck-connector 0.2.10-1ubuntu10
2009-03-30 06:42:49 status unpacked libpam-ck-connector 0.2.10-1ubuntu10
2009-03-30 06:42:49 upgrade libpng12-0 1.2.27-1 1.2.27-1ubuntu0.1
2009-03-30 06:42:49 status half-configured libpng12-0 1.2.27-1
2009-03-30 06:42:49 status unpacked libpng12-0 1.2.27-1
2009-03-30 06:42:49 status half-installed libpng12-0 1.2.27-1
2009-03-30 06:42:49 status half-installed libpng12-0 1.2.27-1
2009-03-30 06:42:49 status unpacked libpng12-0 1.2.27-1ubuntu0.1
2009-03-30 06:42:49 status unpacked libpng12-0 1.2.27-1ubuntu0.1
2009-03-30 06:42:49 upgrade ntpdate 1:4.2.4p4+dfsg-6ubuntu2 1:4.2.4p4+dfsg-6ubuntu2.2
2009-03-30 06:42:49 status half-configured ntpdate 1:4.2.4p4+dfsg-6ubuntu2
2009-03-30 06:42:49 status unpacked ntpdate 1:4.2.4p4+dfsg-6ubuntu2
2009-03-30 06:42:49 status half-installed ntpdate 1:4.2.4p4+dfsg-6ubuntu2
2009-03-30 06:42:49 status half-installed ntpdate 1:4.2.4p4+dfsg-6ubuntu2
2009-03-30 06:42:49 status half-installed ntpdate 1:4.2.4p4+dfsg-6ubuntu2
2009-03-30 06:42:49 status unpacked ntpdate 1:4.2.4p4+dfsg-6ubuntu2.2
2009-03-30 06:42:49 status unpacked ntpdate 1:4.2.4p4+dfsg-6ubuntu2.2
2009-03-30 06:42:49 upgrade sudo 1.6.9p17-1ubuntu2 1.6.9p17-1ubuntu2.1
2009-03-30 06:42:49 status half-configured sudo 1.6.9p17-1ubuntu2
2009-03-30 06:42:49 status unpacked sudo 1.6.9p17-1ubuntu2
2009-03-30 06:42:49 status half-installed sudo 1.6.9p17-1ubuntu2
2009-03-30 06:42:49 status half-installed sudo 1.6.9p17-1ubuntu2
2009-03-30 06:42:49 status half-installed sudo 1.6.9p17-1ubuntu2
2009-03-30 06:42:49 status unpacked sudo 1.6.9p17-1ubuntu2.1
2009-03-30 06:42:49 status unpacked sudo 1.6.9p17-1ubuntu2.1
2009-03-30 06:42:49 trigproc man-db 2.5.2-2 2.5.2-2
2009-03-30 06:42:49 status half-configured man-db 2.5.2-2
2009-03-30 06:42:50 status installed man-db 2.5.2-2
2009-03-30 06:42:51 startup packages configure
2009-03-30 06:42:51 configure libc6-i686 2.8~20080505-0ubuntu9 2.8~20080505-0ubuntu9
2009-03-30 06:42:51 status unpacked libc6-i686 2.8~20080505-0ubuntu9
2009-03-30 06:42:51 status half-configured libc6-i686 2.8~20080505-0ubuntu9
2009-03-30 06:42:51 status installed libc6-i686 2.8~20080505-0ubuntu9
2009-03-30 06:42:51 status triggers-pending libc6 2.8~20080505-0ubuntu9
2009-03-30 06:42:51 configure cpp-4.3 4.3.2-1ubuntu12 4.3.2-1ubuntu12
2009-03-30 06:42:51 status unpacked cpp-4.3 4.3.2-1ubuntu12
2009-03-30 06:42:51 status half-configured cpp-4.3 4.3.2-1ubuntu12
2009-03-30 06:42:51 status installed cpp-4.3 4.3.2-1ubuntu12
2009-03-30 06:42:51 configure busybox-initramfs 1:1.10.2-1ubuntu7 1:1.10.2-1ubuntu7
2009-03-30 06:42:51 status unpacked busybox-initramfs 1:1.10.2-1ubuntu7
2009-03-30 06:42:51 status half-configured busybox-initramfs 1:1.10.2-1ubuntu7
2009-03-30 06:42:51 status installed busybox-initramfs 1:1.10.2-1ubuntu7
2009-03-30 06:42:51 configure libvolume-id0 124-9 124-9
2009-03-30 06:42:51 status unpacked libvolume-id0 124-9
2009-03-30 06:42:51 status half-configured libvolume-id0 124-9
2009-03-30 06:42:51 status installed libvolume-id0 124-9
2009-03-30 06:42:51 configure procps 1:3.2.7-9ubuntu2.1 1:3.2.7-9ubuntu2.1
2009-03-30 06:42:51 status unpacked procps 1:3.2.7-9ubuntu2.1
2009-03-30 06:42:51 status unpacked procps 1:3.2.7-9ubuntu2.1
2009-03-30 06:42:51 status unpacked procps 1:3.2.7-9ubuntu2.1
2009-03-30 06:42:51 status unpacked procps 1:3.2.7-9ubuntu2.1
2009-03-30 06:42:51 status unpacked procps 1:3.2.7-9ubuntu2.1
2009-03-30 06:42:51 status unpacked procps 1:3.2.7-9ubuntu2.1
2009-03-30 06:42:51 status unpacked procps 1:3.2.7-9ubuntu2.1
2009-03-30 06:42:51 status half-configured procps 1:3.2.7-9ubuntu2.1
2009-03-30 06:42:51 status installed procps 1:3.2.7-9ubuntu2.1
2009-03-30 06:42:51 configure libssl0.9.8 0.9.8g-10.1ubuntu2.1 0.9.8g-10.1ubuntu2.1
2009-03-30 06:42:51 status unpacked libssl0.9.8 0.9.8g-10.1ubuntu2.1
2009-03-30 06:42:51 status half-configured libssl0.9.8 0.9.8g-10.1ubuntu2.1
2009-03-30 06:42:51 status installed libssl0.9.8 0.9.8g-10.1ubuntu2.1
2009-03-30 06:42:51 configure openssl 0.9.8g-10.1ubuntu2.1 0.9.8g-10.1ubuntu2.1
2009-03-30 06:42:51 status unpacked openssl 0.9.8g-10.1ubuntu2.1
2009-03-30 06:42:51 status unpacked openssl 0.9.8g-10.1ubuntu2.1
2009-03-30 06:42:51 status half-configured openssl 0.9.8g-10.1ubuntu2.1
2009-03-30 06:42:51 status installed openssl 0.9.8g-10.1ubuntu2.1
2009-03-30 06:42:51 configure ca-certificates 20080514-0ubuntu1.1 20080514-0ubuntu1.1
2009-03-30 06:42:51 status unpacked ca-certificates 20080514-0ubuntu1.1
2009-03-30 06:42:51 status half-configured ca-certificates 20080514-0ubuntu1.1
2009-03-30 06:42:57 status installed ca-certificates 20080514-0ubuntu1.1
2009-03-30 06:42:57 configure libgnutls26 2.4.1-1ubuntu0.2 2.4.1-1ubuntu0.2
2009-03-30 06:42:57 status unpacked libgnutls26 2.4.1-1ubuntu0.2
2009-03-30 06:42:57 status half-configured libgnutls26 2.4.1-1ubuntu0.2
2009-03-30 06:42:57 status installed libgnutls26 2.4.1-1ubuntu0.2
2009-03-30 06:42:57 configure libldap-2.4-2 2.4.11-0ubuntu6.1 2.4.11-0ubuntu6.1
2009-03-30 06:42:57 status unpacked libldap-2.4-2 2.4.11-0ubuntu6.1
2009-03-30 06:42:57 status unpacked libldap-2.4-2 2.4.11-0ubuntu6.1
2009-03-30 06:42:57 status half-configured libldap-2.4-2 2.4.11-0ubuntu6.1
2009-03-30 06:42:57 status installed libldap-2.4-2 2.4.11-0ubuntu6.1
2009-03-30 06:42:57 configure libsqlite3-0 3.5.9-3ubuntu1 3.5.9-3ubuntu1
2009-03-30 06:42:57 status unpacked libsqlite3-0 3.5.9-3ubuntu1
2009-03-30 06:42:57 status half-configured libsqlite3-0 3.5.9-3ubuntu1
2009-03-30 06:42:57 status installed libsqlite3-0 3.5.9-3ubuntu1
2009-03-30 06:42:57 configure vim-common 1:7.1.314-3ubuntu3.1 1:7.1.314-3ubuntu3.1
2009-03-30 06:42:57 status unpacked vim-common 1:7.1.314-3ubuntu3.1
2009-03-30 06:42:57 status unpacked vim-common 1:7.1.314-3ubuntu3.1
2009-03-30 06:42:57 status half-configured vim-common 1:7.1.314-3ubuntu3.1
2009-03-30 06:42:57 status installed vim-common 1:7.1.314-3ubuntu3.1
2009-03-30 06:42:57 configure vim-tiny 1:7.1.314-3ubuntu3.1 1:7.1.314-3ubuntu3.1
2009-03-30 06:42:57 status unpacked vim-tiny 1:7.1.314-3ubuntu3.1
2009-03-30 06:42:57 status unpacked vim-tiny 1:7.1.314-3ubuntu3.1
2009-03-30 06:42:57 status half-configured vim-tiny 1:7.1.314-3ubuntu3.1
2009-03-30 06:42:58 status installed vim-tiny 1:7.1.314-3ubuntu3.1
2009-03-30 06:42:58 configure xkb-data 1.3-2ubuntu4.4 1.3-2ubuntu4.4
2009-03-30 06:42:58 status unpacked xkb-data 1.3-2ubuntu4.4
2009-03-30 06:42:58 status unpacked xkb-data 1.3-2ubuntu4.4
2009-03-30 06:42:58 status half-configured xkb-data 1.3-2ubuntu4.4
2009-03-30 06:42:58 status installed xkb-data 1.3-2ubuntu4.4
2009-03-30 06:42:58 configure apparmor 2.3+1289-0ubuntu4.1 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status half-configured apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status installed apparmor 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 configure libapparmor1 2.3+1289-0ubuntu4.1 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status unpacked libapparmor1 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status half-configured libapparmor1 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 status installed libapparmor1 2.3+1289-0ubuntu4.1
2009-03-30 06:42:58 configure libxml2 2.6.32.dfsg-4ubuntu1.1 2.6.32.dfsg-4ubuntu1.1
2009-03-30 06:42:58 status unpacked libxml2 2.6.32.dfsg-4ubuntu1.1
2009-03-30 06:42:58 status half-configured libxml2 2.6.32.dfsg-4ubuntu1.1
2009-03-30 06:42:58 status installed libxml2 2.6.32.dfsg-4ubuntu1.1
2009-03-30 06:42:58 configure libisc44 1:9.5.0.dfsg.P2-1ubuntu3.1 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status unpacked libisc44 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status half-configured libisc44 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status installed libisc44 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 configure libdns43 1:9.5.0.dfsg.P2-1ubuntu3.1 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status unpacked libdns43 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status half-configured libdns43 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status installed libdns43 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 configure libisccc40 1:9.5.0.dfsg.P2-1ubuntu3.1 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status unpacked libisccc40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status half-configured libisccc40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status installed libisccc40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 configure libisccfg40 1:9.5.0.dfsg.P2-1ubuntu3.1 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status unpacked libisccfg40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status half-configured libisccfg40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status installed libisccfg40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 configure libbind9-40 1:9.5.0.dfsg.P2-1ubuntu3.1 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status unpacked libbind9-40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status half-configured libbind9-40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status installed libbind9-40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 configure liblwres40 1:9.5.0.dfsg.P2-1ubuntu3.1 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status unpacked liblwres40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status half-configured liblwres40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status installed liblwres40 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 configure bind9-host 1:9.5.0.dfsg.P2-1ubuntu3.1 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status unpacked bind9-host 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status half-configured bind9-host 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status installed bind9-host 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 configure dnsutils 1:9.5.0.dfsg.P2-1ubuntu3.1 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status unpacked dnsutils 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status half-configured dnsutils 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 status installed dnsutils 1:9.5.0.dfsg.P2-1ubuntu3.1
2009-03-30 06:42:58 configure command-not-found-data 0.2.26ubuntu1.1 0.2.26ubuntu1.1
2009-03-30 06:42:58 status unpacked command-not-found-data 0.2.26ubuntu1.1
2009-03-30 06:42:58 status half-configured command-not-found-data 0.2.26ubuntu1.1
2009-03-30 06:42:58 status installed command-not-found-data 0.2.26ubuntu1.1
2009-03-30 06:42:58 configure command-not-found 0.2.26ubuntu1.1 0.2.26ubuntu1.1
2009-03-30 06:42:58 status unpacked command-not-found 0.2.26ubuntu1.1
2009-03-30 06:42:59 status unpacked command-not-found 0.2.26ubuntu1.1
2009-03-30 06:42:59 status half-configured command-not-found 0.2.26ubuntu1.1
2009-03-30 06:42:59 status installed command-not-found 0.2.26ubuntu1.1
2009-03-30 06:42:59 configure libx11-data 2:1.1.5-2ubuntu1.1 2:1.1.5-2ubuntu1.1
2009-03-30 06:42:59 status unpacked libx11-data 2:1.1.5-2ubuntu1.1
2009-03-30 06:42:59 status half-configured libx11-data 2:1.1.5-2ubuntu1.1
2009-03-30 06:42:59 status installed libx11-data 2:1.1.5-2ubuntu1.1
2009-03-30 06:42:59 configure libx11-6 2:1.1.5-2ubuntu1.1 2:1.1.5-2ubuntu1.1
2009-03-30 06:42:59 status unpacked libx11-6 2:1.1.5-2ubuntu1.1
2009-03-30 06:42:59 status half-configured libx11-6 2:1.1.5-2ubuntu1.1
2009-03-30 06:42:59 status installed libx11-6 2:1.1.5-2ubuntu1.1
2009-03-30 06:42:59 configure ufw 0.23.3 0.23.3
2009-03-30 06:42:59 status unpacked ufw 0.23.3
2009-03-30 06:42:59 status unpacked ufw 0.23.3
2009-03-30 06:42:59 status unpacked ufw 0.23.3
2009-03-30 06:42:59 status unpacked ufw 0.23.3
2009-03-30 06:42:59 status half-configured ufw 0.23.3
2009-03-30 06:42:59 status installed ufw 0.23.3
2009-03-30 06:42:59 configure update-manager-core 1:0.93.34 1:0.93.34
2009-03-30 06:42:59 status unpacked update-manager-core 1:0.93.34
2009-03-30 06:42:59 status unpacked update-manager-core 1:0.93.34
2009-03-30 06:42:59 status unpacked update-manager-core 1:0.93.34
2009-03-30 06:42:59 status half-configured update-manager-core 1:0.93.34
2009-03-30 06:43:00 status installed update-manager-core 1:0.93.34
2009-03-30 06:43:00 configure libck-connector0 0.2.10-1ubuntu10 0.2.10-1ubuntu10
2009-03-30 06:43:00 status unpacked libck-connector0 0.2.10-1ubuntu10
2009-03-30 06:43:00 status half-configured libck-connector0 0.2.10-1ubuntu10
2009-03-30 06:43:00 status installed libck-connector0 0.2.10-1ubuntu10
2009-03-30 06:43:00 configure libglib2.0-0 2.18.2-0ubuntu2.1 2.18.2-0ubuntu2.1
2009-03-30 06:43:00 status unpacked libglib2.0-0 2.18.2-0ubuntu2.1
2009-03-30 06:43:00 status half-configured libglib2.0-0 2.18.2-0ubuntu2.1
2009-03-30 06:43:00 status installed libglib2.0-0 2.18.2-0ubuntu2.1
2009-03-30 06:43:00 configure consolekit 0.2.10-1ubuntu10 0.2.10-1ubuntu10
2009-03-30 06:43:00 status unpacked consolekit 0.2.10-1ubuntu10
2009-03-30 06:43:00 status unpacked consolekit 0.2.10-1ubuntu10
2009-03-30 06:43:00 status unpacked consolekit 0.2.10-1ubuntu10
2009-03-30 06:43:00 status unpacked consolekit 0.2.10-1ubuntu10
2009-03-30 06:43:00 status half-configured consolekit 0.2.10-1ubuntu10
2009-03-30 06:43:00 status installed consolekit 0.2.10-1ubuntu10
2009-03-30 06:43:00 configure libcups2 1.3.9-2ubuntu8 1.3.9-2ubuntu8
2009-03-30 06:43:00 status unpacked libcups2 1.3.9-2ubuntu8
2009-03-30 06:43:00 status half-configured libcups2 1.3.9-2ubuntu8
2009-03-30 06:43:00 status installed libcups2 1.3.9-2ubuntu8
2009-03-30 06:43:00 configure libcurl3-gnutls 7.18.2-1ubuntu4.3 7.18.2-1ubuntu4.3
2009-03-30 06:43:00 status unpacked libcurl3-gnutls 7.18.2-1ubuntu4.3
2009-03-30 06:43:00 status half-configured libcurl3-gnutls 7.18.2-1ubuntu4.3
2009-03-30 06:43:00 status installed libcurl3-gnutls 7.18.2-1ubuntu4.3
2009-03-30 06:43:00 configure libglib2.0-data 2.18.2-0ubuntu2.1 2.18.2-0ubuntu2.1
2009-03-30 06:43:00 status unpacked libglib2.0-data 2.18.2-0ubuntu2.1
2009-03-30 06:43:00 status half-configured libglib2.0-data 2.18.2-0ubuntu2.1
2009-03-30 06:43:00 status installed libglib2.0-data 2.18.2-0ubuntu2.1
2009-03-30 06:43:00 configure libpam-ck-connector 0.2.10-1ubuntu10 0.2.10-1ubuntu10
2009-03-30 06:43:00 status unpacked libpam-ck-connector 0.2.10-1ubuntu10
2009-03-30 06:43:00 status half-configured libpam-ck-connector 0.2.10-1ubuntu10
2009-03-30 06:43:00 status installed libpam-ck-connector 0.2.10-1ubuntu10
2009-03-30 06:43:00 configure libpng12-0 1.2.27-1ubuntu0.1 1.2.27-1ubuntu0.1
2009-03-30 06:43:00 status unpacked libpng12-0 1.2.27-1ubuntu0.1
2009-03-30 06:43:00 status half-configured libpng12-0 1.2.27-1ubuntu0.1
2009-03-30 06:43:00 status installed libpng12-0 1.2.27-1ubuntu0.1
2009-03-30 06:43:00 configure ntpdate 1:4.2.4p4+dfsg-6ubuntu2.2 1:4.2.4p4+dfsg-6ubuntu2.2
2009-03-30 06:43:00 status unpacked ntpdate 1:4.2.4p4+dfsg-6ubuntu2.2
2009-03-30 06:43:00 status unpacked ntpdate 1:4.2.4p4+dfsg-6ubuntu2.2
2009-03-30 06:43:00 status unpacked ntpdate 1:4.2.4p4+dfsg-6ubuntu2.2
2009-03-30 06:43:00 status unpacked ntpdate 1:4.2.4p4+dfsg-6ubuntu2.2
2009-03-30 06:43:00 status unpacked ntpdate 1:4.2.4p4+dfsg-6ubuntu2.2
2009-03-30 06:43:00 status half-configured ntpdate 1:4.2.4p4+dfsg-6ubuntu2.2
2009-03-30 06:43:00 status installed ntpdate 1:4.2.4p4+dfsg-6ubuntu2.2
2009-03-30 06:43:00 configure sudo 1.6.9p17-1ubuntu2.1 1.6.9p17-1ubuntu2.1
2009-03-30 06:43:00 status unpacked sudo 1.6.9p17-1ubuntu2.1
2009-03-30 06:43:00 status unpacked sudo 1.6.9p17-1ubuntu2.1
2009-03-30 06:43:00 status half-configured sudo 1.6.9p17-1ubuntu2.1
2009-03-30 06:43:00 status installed sudo 1.6.9p17-1ubuntu2.1
2009-03-30 06:43:00 configure perl-modules 5.10.0-11.1ubuntu2.2 5.10.0-11.1ubuntu2.2
2009-03-30 06:43:00 status unpacked perl-modules 5.10.0-11.1ubuntu2.2
2009-03-30 06:43:00 status unpacked perl-modules 5.10.0-11.1ubuntu2.2
2009-03-30 06:43:00 status half-configured perl-modules 5.10.0-11.1ubuntu2.2
2009-03-30 06:43:00 status installed perl-modules 5.10.0-11.1ubuntu2.2
2009-03-30 06:43:00 configure initramfs-tools 0.92bubuntu16 0.92bubuntu16
2009-03-30 06:43:00 status unpacked initramfs-tools 0.92bubuntu16
2009-03-30 06:43:00 status unpacked initramfs-tools 0.92bubuntu16
2009-03-30 06:43:00 status unpacked initramfs-tools 0.92bubuntu16
2009-03-30 06:43:00 status half-configured initramfs-tools 0.92bubuntu16
2009-03-30 06:43:00 status installed initramfs-tools 0.92bubuntu16
2009-03-30 06:43:00 status triggers-pending initramfs-tools 0.92bubuntu16
2009-03-30 06:43:00 configure udev 124-9 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status unpacked udev 124-9
2009-03-30 06:43:00 status half-configured udev 124-9
2009-03-30 06:43:00 status installed udev 124-9
2009-03-30 06:43:00 configure linux-image-2.6.27-7-server 2.6.27-7.16 2.6.27-7.16
2009-03-30 06:43:00 status unpacked linux-image-2.6.27-7-server 2.6.27-7.16
2009-03-30 06:43:00 status half-configured linux-image-2.6.27-7-server 2.6.27-7.16
2009-03-30 06:43:13 status installed linux-image-2.6.27-7-server 2.6.27-7.16
2009-03-30 06:43:13 configure perl 5.10.0-11.1ubuntu2.2 5.10.0-11.1ubuntu2.2
2009-03-30 06:43:13 status unpacked perl 5.10.0-11.1ubuntu2.2
2009-03-30 06:43:13 status half-configured perl 5.10.0-11.1ubuntu2.2
2009-03-30 06:43:13 status installed perl 5.10.0-11.1ubuntu2.2
2009-03-30 06:43:13 configure libapparmor-perl 2.3+1289-0ubuntu4.1 2.3+1289-0ubuntu4.1
2009-03-30 06:43:13 status unpacked libapparmor-perl 2.3+1289-0ubuntu4.1
2009-03-30 06:43:13 status half-configured libapparmor-perl 2.3+1289-0ubuntu4.1
2009-03-30 06:43:13 status installed libapparmor-perl 2.3+1289-0ubuntu4.1
2009-03-30 06:43:13 configure apparmor-utils 2.3+1289-0ubuntu4.1 2.3+1289-0ubuntu4.1
2009-03-30 06:43:13 status unpacked apparmor-utils 2.3+1289-0ubuntu4.1
2009-03-30 06:43:13 status unpacked apparmor-utils 2.3+1289-0ubuntu4.1
2009-03-30 06:43:13 status unpacked apparmor-utils 2.3+1289-0ubuntu4.1
2009-03-30 06:43:13 status half-configured apparmor-utils 2.3+1289-0ubuntu4.1
2009-03-30 06:43:13 status installed apparmor-utils 2.3+1289-0ubuntu4.1
2009-03-30 06:43:13 trigproc libc6 2.8~20080505-0ubuntu9 2.8~20080505-0ubuntu9
2009-03-30 06:43:13 status half-configured libc6 2.8~20080505-0ubuntu9
2009-03-30 06:43:13 status installed libc6 2.8~20080505-0ubuntu9
2009-03-30 06:43:13 trigproc initramfs-tools 0.92bubuntu16 0.92bubuntu16
2009-03-30 06:43:13 status half-configured initramfs-tools 0.92bubuntu16
2009-03-30 06:43:23 status installed initramfs-tools 0.92bubuntu16
2009-04-03 07:47:28 startup archives unpack
2009-04-03 07:47:31 install console-cyrillic <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 0.9-15.1
2009-04-03 07:47:31 status half-installed console-cyrillic 0.9-15.1
2009-04-03 07:47:31 status triggers-pending man-db 2.5.2-2
2009-04-03 07:47:31 status half-installed console-cyrillic 0.9-15.1
2009-04-03 07:47:31 status unpacked console-cyrillic 0.9-15.1
2009-04-03 07:47:31 status unpacked console-cyrillic 0.9-15.1
2009-04-03 07:47:31 trigproc man-db 2.5.2-2 2.5.2-2
2009-04-03 07:47:31 status half-configured man-db 2.5.2-2
2009-04-03 07:47:33 status installed man-db 2.5.2-2
2009-04-03 07:47:34 startup packages configure
2009-04-03 07:47:34 configure console-cyrillic 0.9-15.1 0.9-15.1
2009-04-03 07:47:34 status unpacked console-cyrillic 0.9-15.1
2009-04-03 07:47:34 status unpacked console-cyrillic 0.9-15.1
2009-04-03 07:47:34 status half-configured console-cyrillic 0.9-15.1
2009-04-03 07:47:34 status installed console-cyrillic 0.9-15.1
2009-04-06 07:44:45 startup archives unpack
2009-04-06 07:44:48 install binutils <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.18.93.20081009-0ubuntu1
2009-04-06 07:44:48 status half-installed binutils 2.18.93.20081009-0ubuntu1
2009-04-06 07:44:48 status triggers-pending man-db 2.5.2-2
2009-04-06 07:44:48 status half-installed binutils 2.18.93.20081009-0ubuntu1
2009-04-06 07:44:49 status unpacked binutils 2.18.93.20081009-0ubuntu1
2009-04-06 07:44:49 status unpacked binutils 2.18.93.20081009-0ubuntu1
2009-04-06 07:44:49 install linux-libc-dev <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.6.27-11.27
2009-04-06 07:44:49 status half-installed linux-libc-dev 2.6.27-11.27
2009-04-06 07:44:49 status unpacked linux-libc-dev 2.6.27-11.27
2009-04-06 07:44:49 status unpacked linux-libc-dev 2.6.27-11.27
2009-04-06 07:44:49 install libc6-dev <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.8~20080505-0ubuntu9
2009-04-06 07:44:49 status half-installed libc6-dev 2.8~20080505-0ubuntu9
2009-04-06 07:44:49 status half-installed libc6-dev 2.8~20080505-0ubuntu9
2009-04-06 07:44:50 status unpacked libc6-dev 2.8~20080505-0ubuntu9
2009-04-06 07:44:50 status unpacked libc6-dev 2.8~20080505-0ubuntu9
2009-04-06 07:44:50 install libgomp1 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 4.3.2-1ubuntu12
2009-04-06 07:44:50 status half-installed libgomp1 4.3.2-1ubuntu12
2009-04-06 07:44:50 status unpacked libgomp1 4.3.2-1ubuntu12
2009-04-06 07:44:50 status unpacked libgomp1 4.3.2-1ubuntu12
2009-04-06 07:44:50 install gcc-4.3 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 4.3.2-1ubuntu12
2009-04-06 07:44:50 status half-installed gcc-4.3 4.3.2-1ubuntu12
2009-04-06 07:44:50 status half-installed gcc-4.3 4.3.2-1ubuntu12
2009-04-06 07:44:50 status unpacked gcc-4.3 4.3.2-1ubuntu12
2009-04-06 07:44:50 status unpacked gcc-4.3 4.3.2-1ubuntu12
2009-04-06 07:44:50 install gcc <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 4:4.3.1-1ubuntu2
2009-04-06 07:44:50 status half-installed gcc 4:4.3.1-1ubuntu2
2009-04-06 07:44:50 status half-installed gcc 4:4.3.1-1ubuntu2
2009-04-06 07:44:50 status unpacked gcc 4:4.3.1-1ubuntu2
2009-04-06 07:44:50 status unpacked gcc 4:4.3.1-1ubuntu2
2009-04-06 07:44:50 install libstdc++6-4.3-dev <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 4.3.2-1ubuntu12
2009-04-06 07:44:50 status half-installed libstdc++6-4.3-dev 4.3.2-1ubuntu12
2009-04-06 07:44:51 status unpacked libstdc++6-4.3-dev 4.3.2-1ubuntu12
2009-04-06 07:44:51 status unpacked libstdc++6-4.3-dev 4.3.2-1ubuntu12
2009-04-06 07:44:51 install g++-4.3 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 4.3.2-1ubuntu12
2009-04-06 07:44:51 status half-installed g++-4.3 4.3.2-1ubuntu12
2009-04-06 07:44:51 status half-installed g++-4.3 4.3.2-1ubuntu12
2009-04-06 07:44:51 status unpacked g++-4.3 4.3.2-1ubuntu12
2009-04-06 07:44:51 status unpacked g++-4.3 4.3.2-1ubuntu12
2009-04-06 07:44:51 install g++ <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 4:4.3.1-1ubuntu2
2009-04-06 07:44:51 status half-installed g++ 4:4.3.1-1ubuntu2
2009-04-06 07:44:51 status half-installed g++ 4:4.3.1-1ubuntu2
2009-04-06 07:44:51 status unpacked g++ 4:4.3.1-1ubuntu2
2009-04-06 07:44:51 status unpacked g++ 4:4.3.1-1ubuntu2
2009-04-06 07:44:51 install make <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 3.81-5
2009-04-06 07:44:51 status half-installed make 3.81-5
2009-04-06 07:44:51 status half-installed make 3.81-5
2009-04-06 07:44:51 status unpacked make 3.81-5
2009-04-06 07:44:51 status unpacked make 3.81-5
2009-04-06 07:44:51 install dpkg-dev <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 1.14.20ubuntu6.2
2009-04-06 07:44:51 status half-installed dpkg-dev 1.14.20ubuntu6.2
2009-04-06 07:44:51 status half-installed dpkg-dev 1.14.20ubuntu6.2
2009-04-06 07:44:52 status unpacked dpkg-dev 1.14.20ubuntu6.2
2009-04-06 07:44:52 status unpacked dpkg-dev 1.14.20ubuntu6.2
2009-04-06 07:44:52 install build-essential <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 11.4
2009-04-06 07:44:52 status half-installed build-essential 11.4
2009-04-06 07:44:52 status unpacked build-essential 11.4
2009-04-06 07:44:52 status unpacked build-essential 11.4
2009-04-06 07:44:52 trigproc man-db 2.5.2-2 2.5.2-2
2009-04-06 07:44:52 status half-configured man-db 2.5.2-2
2009-04-06 07:44:54 status installed man-db 2.5.2-2
2009-04-06 07:44:54 startup packages configure
2009-04-06 07:44:54 configure binutils 2.18.93.20081009-0ubuntu1 2.18.93.20081009-0ubuntu1
2009-04-06 07:44:54 status unpacked binutils 2.18.93.20081009-0ubuntu1
2009-04-06 07:44:55 status half-configured binutils 2.18.93.20081009-0ubuntu1
2009-04-06 07:44:55 status installed binutils 2.18.93.20081009-0ubuntu1
2009-04-06 07:44:55 status triggers-pending libc6 2.8~20080505-0ubuntu9
2009-04-06 07:44:55 configure linux-libc-dev 2.6.27-11.27 2.6.27-11.27
2009-04-06 07:44:55 status unpacked linux-libc-dev 2.6.27-11.27
2009-04-06 07:44:55 status half-configured linux-libc-dev 2.6.27-11.27
2009-04-06 07:44:55 status installed linux-libc-dev 2.6.27-11.27
2009-04-06 07:44:55 configure libc6-dev 2.8~20080505-0ubuntu9 2.8~20080505-0ubuntu9
2009-04-06 07:44:55 status unpacked libc6-dev 2.8~20080505-0ubuntu9
2009-04-06 07:44:55 status half-configured libc6-dev 2.8~20080505-0ubuntu9
2009-04-06 07:44:55 status installed libc6-dev 2.8~20080505-0ubuntu9
2009-04-06 07:44:55 configure libgomp1 4.3.2-1ubuntu12 4.3.2-1ubuntu12
2009-04-06 07:44:55 status unpacked libgomp1 4.3.2-1ubuntu12
2009-04-06 07:44:55 status half-configured libgomp1 4.3.2-1ubuntu12
2009-04-06 07:44:55 status installed libgomp1 4.3.2-1ubuntu12
2009-04-06 07:44:55 configure gcc-4.3 4.3.2-1ubuntu12 4.3.2-1ubuntu12
2009-04-06 07:44:55 status unpacked gcc-4.3 4.3.2-1ubuntu12
2009-04-06 07:44:55 status half-configured gcc-4.3 4.3.2-1ubuntu12
2009-04-06 07:44:55 status installed gcc-4.3 4.3.2-1ubuntu12
2009-04-06 07:44:55 configure gcc 4:4.3.1-1ubuntu2 4:4.3.1-1ubuntu2
2009-04-06 07:44:55 status unpacked gcc 4:4.3.1-1ubuntu2
2009-04-06 07:44:55 status half-configured gcc 4:4.3.1-1ubuntu2
2009-04-06 07:44:55 status installed gcc 4:4.3.1-1ubuntu2
2009-04-06 07:44:55 configure make 3.81-5 3.81-5
2009-04-06 07:44:55 status unpacked make 3.81-5
2009-04-06 07:44:55 status half-configured make 3.81-5
2009-04-06 07:44:55 status installed make 3.81-5
2009-04-06 07:44:55 configure dpkg-dev 1.14.20ubuntu6.2 1.14.20ubuntu6.2
2009-04-06 07:44:55 status unpacked dpkg-dev 1.14.20ubuntu6.2
2009-04-06 07:44:55 status unpacked dpkg-dev 1.14.20ubuntu6.2
2009-04-06 07:44:55 status unpacked dpkg-dev 1.14.20ubuntu6.2
2009-04-06 07:44:55 status half-configured dpkg-dev 1.14.20ubuntu6.2
2009-04-06 07:44:55 status installed dpkg-dev 1.14.20ubuntu6.2
2009-04-06 07:44:55 configure libstdc++6-4.3-dev 4.3.2-1ubuntu12 4.3.2-1ubuntu12
2009-04-06 07:44:55 status unpacked libstdc++6-4.3-dev 4.3.2-1ubuntu12
2009-04-06 07:44:55 status half-configured libstdc++6-4.3-dev 4.3.2-1ubuntu12
2009-04-06 07:44:55 status installed libstdc++6-4.3-dev 4.3.2-1ubuntu12
2009-04-06 07:44:55 configure g++-4.3 4.3.2-1ubuntu12 4.3.2-1ubuntu12
2009-04-06 07:44:55 status unpacked g++-4.3 4.3.2-1ubuntu12
2009-04-06 07:44:55 status half-configured g++-4.3 4.3.2-1ubuntu12
2009-04-06 07:44:55 status installed g++-4.3 4.3.2-1ubuntu12
2009-04-06 07:44:55 configure g++ 4:4.3.1-1ubuntu2 4:4.3.1-1ubuntu2
2009-04-06 07:44:55 status unpacked g++ 4:4.3.1-1ubuntu2
2009-04-06 07:44:55 status half-configured g++ 4:4.3.1-1ubuntu2
2009-04-06 07:44:55 status installed g++ 4:4.3.1-1ubuntu2
2009-04-06 07:44:55 configure build-essential 11.4 11.4
2009-04-06 07:44:55 status unpacked build-essential 11.4
2009-04-06 07:44:55 status half-configured build-essential 11.4
2009-04-06 07:44:55 status installed build-essential 11.4
2009-04-06 07:44:55 trigproc libc6 2.8~20080505-0ubuntu9 2.8~20080505-0ubuntu9
2009-04-06 07:44:55 status half-configured libc6 2.8~20080505-0ubuntu9
2009-04-06 07:44:55 status installed libc6 2.8~20080505-0ubuntu9
2009-04-08 07:35:12 startup archives unpack
2009-04-08 07:35:16 install linux-headers-2.6.27-7 <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.6.27-7.16
2009-04-08 07:35:16 status half-installed linux-headers-2.6.27-7 2.6.27-7.16
2009-04-08 07:35:25 status unpacked linux-headers-2.6.27-7 2.6.27-7.16
2009-04-08 07:35:25 status unpacked linux-headers-2.6.27-7 2.6.27-7.16
2009-04-08 07:35:25 install linux-headers-2.6.27-7-server <&#1072;&#1053;&#1072;&#1045;&#1073;&#65533;> 2.6.27-7.16
2009-04-08 07:35:25 status half-installed linux-headers-2.6.27-7-server 2.6.27-7.16
2009-04-08 07:35:26 status unpacked linux-headers-2.6.27-7-server 2.6.27-7.16
2009-04-08 07:35:26 status unpacked linux-headers-2.6.27-7-server 2.6.27-7.16
2009-04-08 07:35:27 startup packages configure
2009-04-08 07:35:27 configure linux-headers-2.6.27-7 2.6.27-7.16 2.6.27-7.16
2009-04-08 07:35:27 status unpacked linux-headers-2.6.27-7 2.6.27-7.16
2009-04-08 07:35:27 status half-configured linux-headers-2.6.27-7 2.6.27-7.16
2009-04-08 07:35:27 status installed linux-headers-2.6.27-7 2.6.27-7.16
2009-04-08 07:35:27 configure linux-headers-2.6.27-7-server 2.6.27-7.16 2.6.27-7.16
2009-04-08 07:35:27 status unpacked linux-headers-2.6.27-7-server 2.6.27-7.16
2009-04-08 07:35:27 status half-configured linux-headers-2.6.27-7-server 2.6.27-7.16
2009-04-08 07:35:27 status installed linux-headers-2.6.27-7-server 2.6.27-7.16
2009-04-14 07:43:51 startup archives unpack
2009-04-14 07:43:54 upgrade dpkg 1.14.20ubuntu6.1 1.14.20ubuntu6.2
2009-04-14 07:43:54 status half-configured dpkg 1.14.20ubuntu6.1
2009-04-14 07:43:54 status unpacked dpkg 1.14.20ubuntu6.1
2009-04-14 07:43:54 status half-installed dpkg 1.14.20ubuntu6.1
2009-04-14 07:43:54 status triggers-pending man-db 2.5.2-2
2009-04-14 07:43:55 status half-installed dpkg 1.14.20ubuntu6.1
2009-04-14 07:43:55 status half-installed dpkg 1.14.20ubuntu6.1
2009-04-14 07:43:55 status unpacked dpkg 1.14.20ubuntu6.2
2009-04-14 07:43:55 status unpacked dpkg 1.14.20ubuntu6.2
2009-04-14 07:43:55 trigproc man-db 2.5.2-2 2.5.2-2
2009-04-14 07:43:55 status half-configured man-db 2.5.2-2
2009-04-14 07:43:56 status installed man-db 2.5.2-2
2009-04-14 07:43:57 startup packages configure
2009-04-14 07:43:57 configure dpkg 1.14.20ubuntu6.2 1.14.20ubuntu6.2
2009-04-14 07:43:57 status unpacked dpkg 1.14.20ubuntu6.2
2009-04-14 07:43:57 status unpacked dpkg 1.14.20ubuntu6.2
2009-04-14 07:43:57 status unpacked dpkg 1.14.20ubuntu6.2
2009-04-14 07:43:57 status unpacked dpkg 1.14.20ubuntu6.2
2009-04-14 07:43:57 status unpacked dpkg 1.14.20ubuntu6.2
2009-04-14 07:43:57 status half-configured dpkg 1.14.20ubuntu6.2
2009-04-14 07:43:57 status installed dpkg 1.14.20ubuntu6.2
2009-04-14 07:43:57 startup archives unpack
2009-04-14 07:43:57 upgrade tzdata 2009b-0ubuntu0.8.10 2009d-0ubuntu0.8.10
2009-04-14 07:43:57 status half-configured tzdata 2009b-0ubuntu0.8.10
2009-04-14 07:43:57 status unpacked tzdata 2009b-0ubuntu0.8.10
2009-04-14 07:43:57 status half-installed tzdata 2009b-0ubuntu0.8.10
2009-04-14 07:43:58 status half-installed tzdata 2009b-0ubuntu0.8.10
2009-04-14 07:43:58 status unpacked tzdata 2009d-0ubuntu0.8.10
2009-04-14 07:43:58 status unpacked tzdata 2009d-0ubuntu0.8.10
2009-04-14 07:43:59 startup packages configure
2009-04-14 07:43:59 configure tzdata 2009d-0ubuntu0.8.10 2009d-0ubuntu0.8.10
2009-04-14 07:43:59 status unpacked tzdata 2009d-0ubuntu0.8.10
2009-04-14 07:43:59 status half-configured tzdata 2009d-0ubuntu0.8.10
2009-04-14 07:43:59 status installed tzdata 2009d-0ubuntu0.8.10
2009-04-14 07:44:00 startup archives unpack
2009-04-14 07:44:00 upgrade libssl0.9.8 0.9.8g-10.1ubuntu2.1 0.9.8g-10.1ubuntu2.2
2009-04-14 07:44:00 status half-configured libssl0.9.8 0.9.8g-10.1ubuntu2.1
2009-04-14 07:44:00 status unpacked libssl0.9.8 0.9.8g-10.1ubuntu2.1
2009-04-14 07:44:00 status half-installed libssl0.9.8 0.9.8g-10.1ubuntu2.1
2009-04-14 07:44:00 status half-installed libssl0.9.8 0.9.8g-10.1ubuntu2.1
2009-04-14 07:44:01 status unpacked libssl0.9.8 0.9.8g-10.1ubuntu2.2
2009-04-14 07:44:01 status unpacked libssl0.9.8 0.9.8g-10.1ubuntu2.2
2009-04-14 07:44:01 upgrade libkrb53 1.6.dfsg.4~beta1-3 1.6.dfsg.4~beta1-3ubuntu0.1
2009-04-14 07:44:01 status half-configured libkrb53 1.6.dfsg.4~beta1-3
2009-04-14 07:44:01 status unpacked libkrb53 1.6.dfsg.4~beta1-3
2009-04-14 07:44:01 status half-installed libkrb53 1.6.dfsg.4~beta1-3
2009-04-14 07:44:01 status half-installed libkrb53 1.6.dfsg.4~beta1-3
2009-04-14 07:44:01 status unpacked libkrb53 1.6.dfsg.4~beta1-3ubuntu0.1
2009-04-14 07:44:01 status unpacked libkrb53 1.6.dfsg.4~beta1-3ubuntu0.1
2009-04-14 07:44:01 upgrade libcups2 1.3.9-2ubuntu8 1.3.9-2ubuntu9
2009-04-14 07:44:01 status half-configured libcups2 1.3.9-2ubuntu8
2009-04-14 07:44:01 status unpacked libcups2 1.3.9-2ubuntu8
2009-04-14 07:44:01 status half-installed libcups2 1.3.9-2ubuntu8
2009-04-14 07:44:01 status half-installed libcups2 1.3.9-2ubuntu8
2009-04-14 07:44:01 status unpacked libcups2 1.3.9-2ubuntu9
2009-04-14 07:44:01 status unpacked libcups2 1.3.9-2ubuntu9
2009-04-14 07:44:01 upgrade linux-libc-dev 2.6.27-11.27 2.6.27-11.31
2009-04-14 07:44:01 status half-configured linux-libc-dev 2.6.27-11.27
2009-04-14 07:44:01 status unpacked linux-libc-dev 2.6.27-11.27
2009-04-14 07:44:01 status half-installed linux-libc-dev 2.6.27-11.27
2009-04-14 07:44:02 status half-installed linux-libc-dev 2.6.27-11.27
2009-04-14 07:44:02 status unpacked linux-libc-dev 2.6.27-11.31
2009-04-14 07:44:02 status unpacked linux-libc-dev 2.6.27-11.31
2009-04-14 07:44:02 upgrade openssl 0.9.8g-10.1ubuntu2.1 0.9.8g-10.1ubuntu2.2
2009-04-14 07:44:02 status half-configured openssl 0.9.8g-10.1ubuntu2.1
2009-04-14 07:44:02 status unpacked openssl 0.9.8g-10.1ubuntu2.1
2009-04-14 07:44:02 status half-installed openssl 0.9.8g-10.1ubuntu2.1
2009-04-14 07:44:02 status triggers-pending man-db 2.5.2-2
2009-04-14 07:44:02 status half-installed openssl 0.9.8g-10.1ubuntu2.1
2009-04-14 07:44:02 status half-installed openssl 0.9.8g-10.1ubuntu2.1
2009-04-14 07:44:02 status unpacked openssl 0.9.8g-10.1ubuntu2.2
2009-04-14 07:44:02 status unpacked openssl 0.9.8g-10.1ubuntu2.2
2009-04-14 07:44:02 trigproc man-db 2.5.2-2 2.5.2-2
2009-04-14 07:44:02 status half-configured man-db 2.5.2-2
2009-04-14 07:44:02 status installed man-db 2.5.2-2
2009-04-14 07:44:03 startup packages configure
2009-04-14 07:44:03 configure libssl0.9.8 0.9.8g-10.1ubuntu2.2 0.9.8g-10.1ubuntu2.2
2009-04-14 07:44:03 status unpacked libssl0.9.8 0.9.8g-10.1ubuntu2.2
2009-04-14 07:44:03 status half-configured libssl0.9.8 0.9.8g-10.1ubuntu2.2
2009-04-14 07:44:03 status installed libssl0.9.8 0.9.8g-10.1ubuntu2.2
2009-04-14 07:44:03 status triggers-pending libc6 2.8~20080505-0ubuntu9
2009-04-14 07:44:03 configure libkrb53 1.6.dfsg.4~beta1-3ubuntu0.1 1.6.dfsg.4~beta1-3ubuntu0.1
2009-04-14 07:44:03 status unpacked libkrb53 1.6.dfsg.4~beta1-3ubuntu0.1
2009-04-14 07:44:03 status half-configured libkrb53 1.6.dfsg.4~beta1-3ubuntu0.1
2009-04-14 07:44:03 status installed libkrb53 1.6.dfsg.4~beta1-3ubuntu0.1
2009-04-14 07:44:03 configure libcups2 1.3.9-2ubuntu9 1.3.9-2ubuntu9
2009-04-14 07:44:03 status unpacked libcups2 1.3.9-2ubuntu9
2009-04-14 07:44:03 status half-configured libcups2 1.3.9-2ubuntu9
2009-04-14 07:44:03 status installed libcups2 1.3.9-2ubuntu9
2009-04-14 07:44:03 configure linux-libc-dev 2.6.27-11.31 2.6.27-11.31
2009-04-14 07:44:03 status unpacked linux-libc-dev 2.6.27-11.31
2009-04-14 07:44:03 status half-configured linux-libc-dev 2.6.27-11.31
2009-04-14 07:44:03 status installed linux-libc-dev 2.6.27-11.31
2009-04-14 07:44:03 configure openssl 0.9.8g-10.1ubuntu2.2 0.9.8g-10.1ubuntu2.2
2009-04-14 07:44:03 status unpacked openssl 0.9.8g-10.1ubuntu2.2
2009-04-14 07:44:03 status unpacked openssl 0.9.8g-10.1ubuntu2.2
2009-04-14 07:44:03 status half-configured openssl 0.9.8g-10.1ubuntu2.2
2009-04-14 07:44:03 status installed openssl 0.9.8g-10.1ubuntu2.2
2009-04-14 07:44:03 trigproc libc6 2.8~20080505-0ubuntu9 2.8~20080505-0ubuntu9
2009-04-14 07:44:03 status half-configured libc6 2.8~20080505-0ubuntu9
2009-04-14 07:44:05 status installed libc6 2.8~20080505-0ubuntu9

```

---

### Post by Romala on 2009-05-06
Meantime, i've made a mistake -  installing a packet for ```
gedit
``` (an editor in non-server Ubuntu). Should i have to delete it, and how is it made better? Thank you :-({|=

---

### Post by Romala on 2009-05-06
*daemon.log*

```
May  5 07:29:46 user dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  5 07:29:46 user dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  5 07:29:46 user dhcpd: All rights reserved.
May  5 07:29:46 user dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  5 07:29:46 user ntpdate[3993]: no server suitable for synchronization found
May  5 07:29:51 user ntpdate[4540]: no server suitable for synchronization found
May  5 07:33:19 user pptpd[4823]: MGR: connections limit (100) reached, extra IP addresses ignored
May  5 07:33:19 user pptpd[4824]: MGR: Manager process started
May  5 07:33:19 user pptpd[4824]: MGR: Maximum of 100 connections available
May  5 07:39:56 user init: tty4 main process (4276) killed by TERM signal
May  5 07:39:56 user init: tty5 main process (4277) killed by TERM signal
May  5 07:39:56 user init: tty2 main process (4285) killed by TERM signal
May  5 07:39:56 user init: tty3 main process (4287) killed by TERM signal
May  5 07:39:56 user init: tty6 main process (4288) killed by TERM signal
May  5 07:39:56 user init: tty1 main process (4589) killed by TERM signal
May  5 07:39:56 user console-kit-daemon[4392]: WARNING: Unable to activate console: No such device or address 
May  5 07:41:00 user pptpd[4405]: MGR: connections limit (100) reached, extra IP addresses ignored
May  5 07:41:00 user pptpd[4406]: MGR: Manager process started
May  5 07:41:00 user pptpd[4406]: MGR: Maximum of 100 connections available
May  5 07:41:02 user dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  5 07:41:02 user dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  5 07:41:02 user dhcpd: All rights reserved.
May  5 07:41:02 user dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  5 07:41:02 user ntpdate[4010]: no server suitable for synchronization found
May  5 07:41:06 user ntpdate[4573]: no server suitable for synchronization found
May  5 07:42:16 user pptpd[4704]: MGR: connections limit (100) reached, extra IP addresses ignored
May  5 07:42:16 user pptpd[4705]: MGR: Manager process started
May  5 07:42:16 user pptpd[4705]: MGR: Maximum of 100 connections available
May  5 07:42:56 user init: tty4 main process (4309) killed by TERM signal
May  5 07:42:56 user init: tty5 main process (4310) killed by TERM signal
May  5 07:42:56 user init: tty2 main process (4319) killed by TERM signal
May  5 07:42:56 user init: tty3 main process (4321) killed by TERM signal
May  5 07:42:56 user init: tty6 main process (4323) killed by TERM signal
May  5 07:42:56 user init: tty1 main process (4622) killed by TERM signal
May  5 07:42:56 user console-kit-daemon[4425]: WARNING: Unable to activate console: No such device or address 
May  6 07:31:19 user pptpd[4372]: MGR: connections limit (100) reached, extra IP addresses ignored
May  6 07:31:19 user pptpd[4373]: MGR: Manager process started
May  6 07:31:19 user pptpd[4373]: MGR: Maximum of 100 connections available
May  6 07:31:21 user dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  6 07:31:21 user dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  6 07:31:21 user dhcpd: All rights reserved.
May  6 07:31:21 user dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  6 07:31:21 user ntpdate[3974]: no server suitable for synchronization found
May  6 07:31:25 user ntpdate[4540]: no server suitable for synchronization found

```

---

### Post by Romala on 2009-05-06
Thank you for your attention! 
and waiting for your suggestion

---

### Post by Romala on 2009-05-07
I've deleted gedit by
```
sudo apt-get remove gedit
      sudo apt-get clean   
```
Also
```
sudo apt-get update
      sudo apt-get upgrade
```
What else can I do?


Dear **Administrators**, could you change my thread name from "PPTP Server" to "Could not build PPTP Server in Linux Ubuntu Server 8.10" - I hope it could help to solve me this problem. Thank you!

---

### Post by Romala on 2009-05-07
May be someone could give me a picture of working route table? I would try to add a tunnel by *route* command.
:confused:

---

### Post by Romala on 2009-05-12
Is any body here, who have installed PPTP Server before? 
Maybe, someone knows what does it mean:
```
May  5 07:42:56 user init: tty4 main process (4309) killed by TERM signal
May  5 07:42:56 user init: tty5 main process (4310) killed by TERM signal
May  5 07:42:56 user init: tty2 main process (4319) killed by TERM signal
May  5 07:42:56 user init: tty3 main process (4321) killed by TERM signal
May  5 07:42:56 user init: tty6 main process (4323) killed by TERM signal
May  5 07:42:56 user init: tty1 main process (4622) killed by TERM signal
May  5 07:42:56 user console-kit-daemon[4425]: WARNING: Unable to activate console: No such device or address 
May  5 07:42:58 user exiting on signal 15
```

---

### Post by Romala on 2009-06-07
Thanks for koenn (the tunnel is occured ppp) and Rusty Russell for his 
[https://help.ubuntu.com/community/IptablesHowTo]("https://help.ubuntu.com/community/IptablesHowTo")
, it's very helpful and in good writing.

---

