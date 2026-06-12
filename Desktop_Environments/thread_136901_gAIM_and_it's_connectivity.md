---
title: "gAIM and it's connectivity"
date: 2006-02-26
forum: Desktop Environments
---

### Post by aqualad on 2006-02-26
Okay, so I know this is a little much to ask, but I was really hoping I would be able to some how actually make gAIM's file sharing and direct connect features work.  I'm behind a D-Link 514 router and I have a firewall:

```
 #!/bin/sh
 #
 # a simple iptables ruleset
 #
 
 iptables="/sbin/iptables"
 
 # flush any existing chains and set default policies
 $iptables -F INPUT
 $iptables -F OUTPUT
 $iptables -F FORWARD
 
 # set default parameters
 $iptables -P INPUT DROP
 $iptables -P OUTPUT ACCEPT
 $iptables -P FORWARD DROP
 
 # this is our main rule, to allow established connections in
 $iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
 $iptables -A INPUT -p tcp --dport 22 -j ACCEPT
 $iptables -A INPUT -p udp --dport 22 -j ACCEPT 
 $iptables -A INPUT -p tcp --dport 4662 -j ACCEPT
 $iptables -A INPUT -p udp --dport 4672 -j ACCEPT

 # allow all packets on the loopback interface (so that gnome can function)
 $iptables -A INPUT -i lo -j ACCEPT
 $iptables -A OUTPUT -o lo -j ACCEPT

```

What ports and what protocol do I need to open to get gAIM working fully?  I assume I just need to add some lines in my firewall and configure some stuff in my router.  Any help is appreciated, thank you

---

### Post by naked on 2006-02-27
You might have better luck contacting someone at Gaim.  [http://gaim.sourceforge.net/]("http://gaim.sourceforge.net/")

Check the contact page.  They have always been helpful to me.  

(Gaim 2.0 is amazing!)

---

### Post by RAOF on 2006-02-27
Why are you even running that ipchains firewall setup?  It seems that you're only disallowing traffic to ports which aren't being listened on anyway.

Just try just disabling your firewall, and see if GAIM works then.

---

### Post by aqualad on 2006-02-28
Hm, got a connection with one person, but no one else is online to test it out.  Maybe it's just a problem connecting to people with routers but who doesn't have a router these days :-/  I'll give it a shot again tomorrow

---

### Post by anthro398 on 2006-02-28
I respectfully submit that advising people not to use firewalls is an asanine idea.  Anyway...

It depends on how much security you want.  On my desktop I allow all outgoing traffic and allow incoming for traffic in state established or related.
```
# Inbound Internet Packet Rules

# Accept Established Connections
$IPTABLES -A INPUT -p ALL -i $INET_IFACE -m state --state ESTABLISHED,RELATED \
     -j ACCEPT

```
With this first rule of my inbound chain it means I don't have to specify ports and ip address for gaim, which was a pain since services like aol use multiple ip addresses.  

However, under more secure configurations you'll have to specify the ports and ip ranges.  I did this, but can't find the firewall rules that I used.  I gathered the information using google.com/linux, I'm sure you could too.

For what it's worth, here are my rules:
```

#!/bin/sh
#
#    may want to append the command to execute this script to rc.local.
#    rc.local is typically located in /etc and /etc/rc.d and is usually
#    the last thing executed on startup.  Simply add /path/to/script/script_name
#    on its own line in the rc.local file.
###############################################################################
# 
# Local Settings
#

# sysctl location.  If set, it will use sysctl to adjust the kernel parameters.
# If this is set to the empty string (or is unset), the use of sysctl
# is disabled.

SYSCTL="/sbin/sysctl -w" 

# To echo the value directly to the /proc file instead
# SYSCTL=""

# IPTables Location - adjust if needed

IPTABLES="/sbin/iptables"
IPTS="/sbin/iptables-save"
IPTR="/sbin/iptables-restore"

# Internet Interface
INET_IFACE="eth0"

# Localhost Interface

LO_IFACE="lo"
LO_IP="127.0.0.1"

# Save and Restore arguments handled here
if [ "$1" = "save" ]
then
	echo -n "Saving firewall to /etc/sysconfig/iptables ... "
	$IPTS > /etc/sysconfig/iptables
	echo "done"
	exit 0
elif [ "$1" = "restore" ]
then
	echo -n "Restoring firewall from /etc/sysconfig/iptables ... "
	$IPTR < /etc/sysconfig/iptables
	echo "done"
	exit 0
fi

# Traceroute ports.  Usually uses -S 32769:65535 -D 33434:33523
TRACEROUTE_SRC_PORTS="32769:65535"
TRACEROUTE_DEST_PORTS="33434:33523"

# Port ranges
P_PORTS="0:1023" 
UP_PORTS="1024:65535" 

###############################################################################
#
# Load Modules
#

echo "Loading kernel modules ..."

# You should uncomment the line below and run it the first time just to
# ensure all kernel module dependencies are OK.  There is no need to run
# every time, however.

# /sbin/depmod -a

# Unless you have kernel module auto-loading disabled, you should not
# need to manually load each of these modules.  Other than ip_tables,
# ip_conntrack, and some of the optional modules, I've left these
# commented by default.  Uncomment if you have any problems or if
# you have disabled module autoload.  Note that some modules must
# be loaded by another kernel module.

# core netfilter module
/sbin/modprobe ip_tables

# the stateful connection tracking module
/sbin/modprobe ip_conntrack

# filter table module
# /sbin/modprobe iptable_filter

# mangle table module
# /sbin/modprobe iptable_mangle

# nat table module
# /sbin/modprobe iptable_nat

# LOG target module
# /sbin/modprobe ipt_LOG

# This is used to limit the number of packets per sec/min/hr
# /sbin/modprobe ipt_limit

# masquerade target module
# /sbin/modprobe ipt_MASQUERADE

# filter using owner as part of the match
# /sbin/modprobe ipt_owner

# REJECT target drops the packet and returns an ICMP response.
# The response is configurable.  By default, connection refused.
# /sbin/modprobe ipt_REJECT

# This target allows packets to be marked in the mangle table
# /sbin/modprobe ipt_mark

# This target affects the tcp MSS
# /sbin/modprobe ipt_tcpmss

# This match allows multiple ports instead of a single port or range
# /sbin/modprobe multiport

# This match checks against the tcp flags
# /sbin/modprobe ipt_state

# This match catches packets with invalid flags
# /sbin/modprobe ipt_unclean

# The ftp nat module is required for non-PASV ftp support
/sbin/modprobe ip_nat_ftp

# the module for full ftp connection tracking
/sbin/modprobe ip_conntrack_ftp

# the module for full irc connection tracking
/sbin/modprobe ip_conntrack_irc


###############################################################################
#
# Kernel Parameter Configuration
#
# See http://ipsysctl-tutorial.frozentux.net/chunkyhtml/index.html
# for a detailed tutorial on sysctl and the various settings
# available.

# Required to enable IPv4 forwarding.
# Redhat users can try setting FORWARD_IPV4 in /etc/sysconfig/network to true
# Alternatively, it can be set in /etc/sysctl.conf
#if [ "$SYSCTL" = "" ]
#then
#    echo "1" > /proc/sys/net/ipv4/ip_forward
#else
#    $SYSCTL net.ipv4.ip_forward="1"
#fi

# This enables dynamic address hacking.
# This may help if you have a dynamic IP address \(e.g. slip, ppp, dhcp\).
#if [ "$SYSCTL" = "" ]
#then
#    echo "1" > /proc/sys/net/ipv4/ip_dynaddr
#else
#    $SYSCTL net.ipv4.ip_dynaddr="1"
#fi

# This enables SYN flood protection.
# The SYN cookies activation allows your system to accept an unlimited
# number of tcp connections while still trying to give reasonable
# service during a denial of service attack.
if [ "$SYSCTL" = "" ]
then
    echo "1" > /proc/sys/net/ipv4/tcp_syncookies
else
    $SYSCTL net.ipv4.tcp_syncookies="1"
fi

# This enables source validation by reversed path according to RFC1812.
# In other words, did the response packet originate from the same interface
# through which the source packet was sent?  It's recommended for single-homed
# systems and routers on stub networks.  Since those are the configurations
# this firewall is designed to support, I turn it on by default.
# Turn it off if you use multiple NICs connected to the same network.
if [ "$SYSCTL" = "" ]
then
    echo "1" > /proc/sys/net/ipv4/conf/all/rp_filter
else
    $SYSCTL net.ipv4.conf.all.rp_filter="1"
fi

# This option allows a subnet to be firewalled with a single IP address.
# It's used to build a DMZ.  Since that's not a focus of this firewall
# script, it's not enabled by default, but is included for reference.
# See: http://www.sjdjweis.com/linux/proxyarp/ 
#if [ "$SYSCTL" = "" ]
#then
#    echo "1" > /proc/sys/net/ipv4/conf/all/proxy_arp
#else
#    $SYSCTL net.ipv4.conf.all.proxy_arp="1"
#fi

# The following kernel settings were suggested by Alex Weeks. Thanks!

# This kernel parameter instructs the kernel to ignore all ICMP
# echo requests sent to the broadcast address.  This prevents
# a number of smurfs and similar DoS nasty attacks.
if [ "$SYSCTL" = "" ]
then
    echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
else
    $SYSCTL net.ipv4.icmp_echo_ignore_broadcasts="1"
fi

# This option can be used to accept or refuse source routed
# packets.  It is usually on by default, but is generally
# considered a security risk.  This option turns it off.
if [ "$SYSCTL" = "" ]
then
    echo "0" > /proc/sys/net/ipv4/conf/all/accept_source_route
else
    $SYSCTL net.ipv4.conf.all.accept_source_route="0"
fi

# This option can disable ICMP redirects.  ICMP redirects
# are generally considered a security risk and shouldn't be
# needed by most systems using this generator.
#if [ "$SYSCTL" = "" ]
#then
#    echo "0" > /proc/sys/net/ipv4/conf/all/accept_redirects
#else
#    $SYSCTL net.ipv4.conf.all.accept_redirects="0"
#fi

# However, we'll ensure the secure_redirects option is on instead.
# This option accepts only from gateways in the default gateways list.
if [ "$SYSCTL" = "" ]
then
    echo "1" > /proc/sys/net/ipv4/conf/all/secure_redirects
else
    $SYSCTL net.ipv4.conf.all.secure_redirects="1"
fi

# This option logs packets from impossible addresses.
if [ "$SYSCTL" = "" ]
then
    echo "1" > /proc/sys/net/ipv4/conf/all/log_martians
else
    $SYSCTL net.ipv4.conf.all.log_martians="1"
fi


###############################################################################
#
# Flush Any Existing Rules or Chains
#

echo "Flushing Tables ..."

# Reset Default Policies
$IPTABLES -P INPUT ACCEPT
$IPTABLES -P FORWARD ACCEPT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -t nat -P PREROUTING ACCEPT
$IPTABLES -t nat -P POSTROUTING ACCEPT
$IPTABLES -t nat -P OUTPUT ACCEPT
$IPTABLES -t mangle -P PREROUTING ACCEPT
$IPTABLES -t mangle -P OUTPUT ACCEPT

# Flush all rules
$IPTABLES -F
$IPTABLES -t nat -F
$IPTABLES -t mangle -F

# Erase all non-default chains
$IPTABLES -X
$IPTABLES -t nat -X
$IPTABLES -t mangle -X

if [ "$1" = "stop" ]
then
	echo "Firewall completely flushed!  Now running with no firewall."
	exit 0
fi

###############################################################################
# IP Address Definitions

# Self
LOOPBACK="127.0.0.1"
THISMACHINE="xxx.xxx.xxx.xxx"  # <----- Set this to your IP address!

# DNS Servers
PRIMARYDNS="xxx.xxx.xxx.xxx"
SECONDARYDNS="xxx.xxx.xxx.xxx"
#HOMEDNS="192.168.0.1"

# Time Server
TIMESERVER="xxx.xxx.xxx.xxx"
TIMESERVER_UBUNTU="ntp.ubuntulinux.org"

## Removed the rest for privacy

###############################################################################
#
# Rules Configuration
#

###############################################################################
#
# Filter Table
#
###############################################################################

# Set Policies

$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT DROP
$IPTABLES -P FORWARD DROP

###############################################################################
#
# User-Specified Chains
#
# Create user chains to reduce the number of rules each packet
# must traverse.

echo "Create and populate custom rule chains ..."

# Create a chain to filter INVALID packets

$IPTABLES -N bad_packets

# Create another chain to filter bad tcp packets

$IPTABLES -N bad_tcp_packets

# Create separate chains for icmp, tcp (incoming and outgoing),
# and incoming udp packets.

$IPTABLES -N icmp_packets

# Used for udp packets inbound from the Internet
$IPTABLES -N udp_inbound

# Used to block outbound udp services from internal network
# Default to allow all
$IPTABLES -N udp_outbound

# Used to allow inbound services if desired
# Default fail except for established sessions
$IPTABLES -N tcp_inbound

# Used to block outbound services from internal network
# Default to allow all
$IPTABLES -N tcp_outbound

###############################################################################
#
# Populate User Chains
#
echo "bad_packets chain ..."
# bad_packets chain
#

# Drop INVALID packets immediately
$IPTABLES -A bad_packets -p ALL -m state --state INVALID -m limit --limit 6/h --limit-burst 5 -j LOG \
    --log-prefix "IPT=bad_packets:1 a=DROP "

$IPTABLES -A bad_packets -p ALL -m state --state INVALID -j DROP

# Then check the tcp packets for additional problems
$IPTABLES -A bad_packets -p tcp -j bad_tcp_packets

# All good, so return
$IPTABLES -A bad_packets -p ALL -j RETURN

# bad_tcp_packets chain
#
# All tcp packets will traverse this chain.
# Every new connection attempt should begin with
# a syn packet.  If it doesn't, it is likely a
# port scan.  This drops packets in state
# NEW that are not flagged as syn packets.


$IPTABLES -A bad_tcp_packets -p tcp ! --syn -m state --state NEW -m limit --limit 6/h --limit-burst 5 -j LOG \
    --log-prefix "IPT=bad_tcp_packets:1 a=DROP "
$IPTABLES -A bad_tcp_packets -p tcp ! --syn -m state --state NEW -j DROP

$IPTABLES -A bad_tcp_packets -p tcp --tcp-flags ALL NONE -m limit --limit 6/h --limit-burst 5 -j LOG \
    --log-prefix "IPT=bad_tcp_packets:2 a=DROP "
$IPTABLES -A bad_tcp_packets -p tcp --tcp-flags ALL NONE -j DROP

$IPTABLES -A bad_tcp_packets -p tcp --tcp-flags ALL ALL -m limit --limit 6/h --limit-burst 5 -j LOG \
    --log-prefix "IPT=bad_tcp_packets:3 a=DROP "
$IPTABLES -A bad_tcp_packets -p tcp --tcp-flags ALL ALL -j DROP

$IPTABLES -A bad_tcp_packets -p tcp --tcp-flags ALL FIN,URG,PSH -m limit --limit 6/h --limit-burst 5 -j LOG \
    --log-prefix "IPT=bad_tcp_packets:4 a=DROP "
$IPTABLES -A bad_tcp_packets -p tcp --tcp-flags ALL FIN,URG,PSH -j DROP

$IPTABLES -A bad_tcp_packets -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -m limit --limit 6/h --limit-burst 5 -j LOG \
    --log-prefix "IPT=bad_tcp_packets:5 a=DROP "
$IPTABLES -A bad_tcp_packets -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j DROP

$IPTABLES -A bad_tcp_packets -p tcp --tcp-flags SYN,RST SYN,RST -m limit --limit 6/h --limit-burst 5 -j LOG \
    --log-prefix "IPT=bad_tcp_packets:6 a=DROP "
$IPTABLES -A bad_tcp_packets -p tcp --tcp-flags SYN,RST SYN,RST -j DROP

$IPTABLES -A bad_tcp_packets -p tcp --tcp-flags SYN,FIN SYN,FIN -m limit --limit 6/h --limit-burst 5 -j LOG \
    --log-prefix "IPT=bad_tcp_packets:7 a=DROP "
$IPTABLES -A bad_tcp_packets -p tcp --tcp-flags SYN,FIN SYN,FIN -j DROP

# All good, so return
$IPTABLES -A bad_tcp_packets -p tcp -j RETURN

# icmp_packets chain
#
echo "icmp_packets chain ..."
# This chain is for inbound (from the Internet) icmp packets only.
# Type 8 (Echo Request) is not accepted by default
# Enable it if you want remote hosts to be able to reach you.
# 11 (Time Exceeded) is the only one accepted
# that would not already be covered by the established
# connection rule.  Applied to INPUT on the external interface.
# 
# See: http://www.ee.siue.edu/~rwalden/networking/icmp.html
# for more info on ICMP types.
#
# Note that the stateful settings allow replies to ICMP packets.
# These rules allow new packets of the specified types.

# ICMP packets should fit in a Layer 2 frame, thus they should
# never be fragmented.  Fragmented ICMP packets are a typical sign
# of a denial of service attack.
$IPTABLES -A icmp_packets --fragment -p ICMP -m limit --limit 6/h --limit-burst 5 -j LOG \
    --log-prefix "IPT=icmp_packets:1 a=DROP "
$IPTABLES -A icmp_packets --fragment -p ICMP -j DROP

# Echo - uncomment to allow your system to be pinged.
# Uncomment the LOG command if you also want to log PING attempts
# 
# $IPTABLES -A icmp_packets -p ICMP -s 0/0 --icmp-type 8 -m limit --limit 6/h --limit-burst 5 -j LOG \
#    --log-prefix "IPT=icmp_packets:2 a=ACCEPT "
# $IPTABLES -A icmp_packets -p ICMP -s 0/0 --icmp-type 8 -j ACCEPT

# By default, however, drop pings without logging. Blaster
# and other worms have infected systems blasting pings.
# Comment the line below if you want pings logged, but it
# will likely fill your logs.
$IPTABLES -A icmp_packets -p ICMP -s 0/0 --icmp-type 8 -j DROP

# Time Exceeded
$IPTABLES -A icmp_packets -p ICMP -s 0/0 --icmp-type 11 -j ACCEPT

# Not matched, so return so it will be logged
$IPTABLES -A icmp_packets -p ICMP -j RETURN

# tcp & udp
# Identify ports at:
#    http://www.chebucto.ns.ca/~rakerman/port-table.html
#    http://www.iana.org/assignments/port-numbers

##################################################################
# udp_inbound chain
echo "udp_inbound chain"
#
# This chain describes the inbound udp packets it will accept.
# It's applied to INPUT on the external or Internet interface.
# Note that the stateful settings allow replies.
# These rules are for new requests.

# Ident requests (Port 113) must have a REJECT rule rather than the
# default DROP rule.  This is the minimum requirement to avoid
# long delays while connecting.  Also see the tcp_inbound rule.
$IPTABLES -A udp_inbound -p udp -s 0/0 --destination-port 113 -j DROP				# ident

# A more sophisticated configuration could accept the ident requests.
# $IPTABLES -A udp_inbound -p udp -s 0/0 --destination-port 113 -j ACCEPT

# Dynamic Address
# If DHCP, the initial request is a broadcast. The response
# doesn't exactly match the outbound packet.  This explicitly
# allow the DHCP ports to alleviate this problem.
# If you receive your dynamic address by a different means, you
# can probably comment this line.
$IPTABLES -A udp_inbound -p udp -s 0/0 --source-port 67 --destination-port 68 \
     -j ACCEPT

### This is organized badly.  udp and tcp are seperated so operations that require both are not list together.  Dumb.  Should move this next statement.


# Not matched, so return for logging
#$IPTABLES -A udp_inbound -p udp -j RETURN

# udp_outbound chain
#
# This chain is used with a private network to prevent forwarding for
# udp requests on specific protocols.  Applied to the FORWARD rule from
# the internal network.  Ends with an ACCEPT


# No match, so ACCEPT
$IPTABLES -A udp_outbound -p udp -s 0/0 -j ACCEPT

# ---------------------------------------------------------------------------------------------
# TCP_INBOUND CHAIN
echo "tcp_inbound chain"
#
# This chain is used to allow inbound connections to the
# system/gateway.  Use with care.  It defaults to none.
# It's applied on INPUT from the external or Internet interface.

# Ident requests (Port 113) must have a REJECT rule rather than the
# default DROP rule.  This is the minimum requirement to avoid
# long delays while connecting.  Also see the tcp_inbound rule.
$IPTABLES -A tcp_inbound -p tcp -s 0/0 --destination-port 113 -j DROP



# Web Server

# HTTP
#$IPTABLES -A tcp_inbound -p tcp -s 0/0 --destination-port 80 -j ACCEPT

# HTTPS (Secure Web Server)
#$IPTABLES -A tcp_inbound -p tcp -s 0/0 --destination-port 443 -j ACCEPT

# -------------------------------------------------------------------------------
# NTP

# Accept connections to/from RFC 868 time-server on port 37
# This allows the system time to be from a time-server using the command:
#    /usr/bin/ntp -s $TIMESERVER

#$IPTABLES -A tcp_inbound -s $TIMESERVER -p tcp --sport 37 -j ACCEPT
#$IPTABLES -A tcp_inbound -s $TIMESERVER_UBUNTU -p tcp --sport 37 -j ACCEPT


# -------------------------------------------------------------------------------
# SSH

# Accept SSH requests from specific hosts on port 22
# These hosts need to be specified in /etc/hosts.allow, too!

# unity.
$IPTABLES -A tcp_inbound -s $UNITY1 -p tcp --dport 22 -j ACCEPT
$IPTABLES -A tcp_inbound -s $UNITY2 -p tcp --dport 22 -j ACCEPT
$IPTABLES -A tcp_inbound -s $UNITY3 -p tcp --dport 22 -j ACCEPT
$IPTABLES -A tcp_inbound -s $UNITY4 -p tcp --dport 22 -j ACCEPT
$IPTABLES -A tcp_inbound -s $UNITY5 -p tcp --dport 22 -j ACCEPT
$IPTABLES -A tcp_inbound -s $UNITY6 -p tcp --dport 22 -j ACCEPT

# pnet
$IPTABLES -A tcp_inbound -s $PNET -p tcp --dport 22 -j ACCEPT

# laptop
$IPTABLES -A tcp_inbound -s $LAPTOP -p tcp --dport 22 -j ACCEPT

# desktop
$IPTABLES -A tcp_inbound -s $DESK -p tcp --dport 22 -j ACCEPT

# DMZ
$IPTABLES -A tcp_inbound -s $DMZ -p tcp --dport 22 -j ACCEPT

# desktop at home kailua
$IPTABLES -A tcp_inbound -s $KAILUA -p tcp --dport 22 -j ACCEPT

# desktop on RR
$IPTABLES -A tcp_inbound -s $HOME -p tcp --dport 22 -j ACCEPT

# Log and drop all remaining ssh requests not explicitly specified 
$IPTABLES -A tcp_inbound -s 0/0 -p tcp --destination-port 22 -m limit --limit 6/h --limit-burst 5 -j LOG --log-prefix "IPT=SSH a=DROP "
$IPTABLES -A tcp_inbound -s 0/0 -p tcp --destination-port 22 -j DROP

# -------------------------------------------------------------------------------
# SAMBA

# Allow outgoing Samba connections to local network
$IPTABLES -A udp_inbound -s $LOCAL_LAN -p udp --sport 139 -j ACCEPT
$IPTABLES -A tcp_inbound -s $LOCAL_LAN -p tcp --sport 139 -j ACCEPT
$IPTABLES -A udp_inbound -s $LOCAL_LAN -p udp --sport 445 -j ACCEPT
$IPTABLES -A tcp_inbound -s $LOCAL_LAN -p tcp --sport 445 -j ACCEPT

# Drop all remaining without logging
$IPTABLES -A udp_inbound -p udp -s 0/0 --destination-port 137 -j DROP
$IPTABLES -A udp_inbound -p udp -s 0/0 --destination-port 138 -j DROP
$IPTABLES -A udp_inbound -p udp -s 0/0 --destination-port 445 -j DROP
$IPTABLES -A tcp_inbound  -p tcp -s 0/0 --destination-port 137 -j DROP
$IPTABLES -A tcp_inbound  -p tcp -s 0/0 --destination-port 138 -j DROP
$IPTABLES -A tcp_inbound  -p tcp -s 0/0 --destination-port 445 -j DROP


# -------------------------------------------------------------------------------
# LDAP

# Accept LDAP requests from/to the local machine to/from xxx on port 389
$IPTABLES -A tcp_inbound -s $LDAP -p tcp --sport 389 -j ACCEPT
$IPTABLES -A udp_inbound -s $LDAP -p udp --sport 389 -j ACCEPT

# -------------------------------------------------------------------------------
# IMAP

# Accept IMAP requests to the local machine from your IMAP server on port 143
# and the encrypted IMAP port (993)
$IPTABLES -A tcp_inbound -s $IMAP -p tcp --sport 143 -j ACCEPT
$IPTABLES -A tcp_inbound -s $IMAP -p tcp --sport 993 -j ACCEPT
$IPTABLES -A tcp_inbound -s $PNETIMAP -p tcp --sport 143 -j ACCEPT
$IPTABLES -A tcp_inbound -s $PNETIMAP -p tcp --sport 993 -j ACCEPT


# -------------------------------------------------------------------------------
# SMTP

$IPTABLES -A tcp_inbound -s $SMTP -p tcp --sport 25 -j ACCEPT

# -------------------------------------------------------------------------------
# Azureus

$IPTABLES -A tcp_inbound -p tcp --dport 6881 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT 

# -------------------------------------------------------------------------------
# iTunes	

$IPTABLES -A tcp_inbound -s $LOCAL_LAN -p tcp --dport 3689 -j ACCEPT
$IPTABLES -A udp_inbound -s $LOCAL_LAN -p udp --dport 5385 -j ACCEPT
$IPTABLES -A udp_inbound -s $LOCAL_LAN -p udp --dport 5353 -j ACCEPT


# Not matched, so return so it will be logged
$IPTABLES -A tcp_inbound -p tcp -j RETURN

# Moved udp_inbound default drop to allow for tcp/udp combinations in tcp_inbound chain
# Not matched, so return for logging
$IPTABLES -A udp_inbound -p udp -j RETURN


# -----------------------------------------------------------------------
# tcp_outbound chain
#
echo "tcp_outbound chain"
# This chain is used with a private network to prevent forwarding for
# requests on specific protocols.  Applied to the FORWARD rule from
# the internal network.  Ends with an ACCEPT

# No match, so ACCEPT
$IPTABLES -A tcp_outbound -p tcp -s 0/0 -j ACCEPT


###############################################################################
#
# INPUT Chain
#

echo "Process INPUT chain ..."

# Allow all on localhost interface
$IPTABLES -A INPUT -p ALL -i $LO_IFACE -j ACCEPT

# -------------------------------------------------------------------------------
# DNS LOOKUPS

# Accept DNS requests from the local machine to the NCSU DNS servers on port 53
$IPTABLES -A OUTPUT -s $THISMACHINE -d $PRIMARYDNS -p udp --dport 53 -j ACCEPT
$IPTABLES -A INPUT -d $THISMACHINE -s $PRIMARYDNS -p udp --sport 53 -j ACCEPT

$IPTABLES -A OUTPUT -s $THISMACHINE -d $SECONDARYDNS -p udp --dport 53 -j ACCEPT
$IPTABLES -A INPUT -d $THISMACHINE -s $SECONDARYDNS -p udp --sport 53 -j ACCEPT

$IPTABLES -A OUTPUT -s $THISMACHINE -d $PRIMARYDNS -p tcp --dport 53 -j ACCEPT
$IPTABLES -A INPUT -d $THISMACHINE -s $PRIMARYDNS -p tcp --sport 53 -j ACCEPT

$IPTABLES -A OUTPUT -s $THISMACHINE -d $SECONDARYDNS -p tcp --dport 53 -j ACCEPT
$IPTABLES -A INPUT -d $THISMACHINE -s $SECONDARYDNS -p tcp --sport 53 -j ACCEPT

# Drop bad packets
$IPTABLES -A INPUT -p ALL -j bad_packets

# DOCSIS compliant cable modems
# Some DOCSIS compliant cable modems send IGMP multicasts to find
# connected PCs.  The multicast packets have the destination address
# 224.0.0.1.  You can accept them.  If you choose to do so,
# Uncomment the rule to ACCEPT them and comment the rule to DROP
# them  The firewall will drop them here by default to avoid
# cluttering the log.  The firewall will drop all multicasts
# to the entire subnet (224.0.0.1) by default.  To only affect
# IGMP multicasts, change '-p ALL' to '-p 2'.  Of course,
# if they aren't accepted elsewhere, it will only ensure that
# multicasts on other protocols are logged.
# Drop them without logging.
$IPTABLES -A INPUT -p ALL -d 224.0.0.1 -j DROP
# The rule to accept the packets.
# $IPTABLES -A INPUT -p ALL -d 224.0.0.1 -j ACCEPT


# Inbound Internet Packet Rules

# Accept Established Connections
$IPTABLES -A INPUT -p ALL -i $INET_IFACE -m state --state ESTABLISHED,RELATED \
     -j ACCEPT

# Route the rest to the appropriate user chain
$IPTABLES -A INPUT -p tcp -i $INET_IFACE -j tcp_inbound
$IPTABLES -A INPUT -p udp -i $INET_IFACE -j udp_inbound
$IPTABLES -A INPUT -p ICMP -i $INET_IFACE -j icmp_packets

# Drop without logging broadcasts that get this far.
# Cuts down on log clutter.
# Comment this line if testing new rules that impact
# broadcast protocols.
$IPTABLES -A INPUT -m pkttype --pkt-type broadcast -j DROP

# Log packets that still don't match
$IPTABLES -A INPUT -m limit --limit 6/h --limit-burst 5 -j LOG --log-prefix "IPT=INPUT:99 a=DROP "

###############################################################################
#
# FORWARD Chain
#

echo "Process FORWARD chain ..."

# Used if forwarding for a private network


###############################################################################
#
# OUTPUT Chain
#

echo "Process OUTPUT chain ..."

# Generally trust the firewall on output

# However, invalid icmp packets need to be dropped
# to prevent a possible exploit.
$IPTABLES -A OUTPUT -m state -p icmp --state INVALID -j DROP

# Localhost
$IPTABLES -A OUTPUT -p ALL -s $LO_IP -j ACCEPT
$IPTABLES -A OUTPUT -p ALL -o $LO_IFACE -j ACCEPT

# To internet
$IPTABLES -A OUTPUT -p ALL -o $INET_IFACE -j ACCEPT

# Log packets that still don't match
$IPTABLES -A OUTPUT -m limit --limit 6/h --limit-burst 5 -j LOG --log-prefix "IPT=OUTPUT:99 a=DROP "

###############################################################################
#
# nat table
#
###############################################################################

# The nat table is where network address translation occurs if there
# is a private network.  If the gateway is connected to the Internet
# with a static IP, snat is used.  If the gateway has a dynamic address,
# masquerade must be used instead.  There is more overhead associated
# with masquerade, so snat is better when it can be used.
# The nat table has a builtin chain, PREROUTING, for dnat and redirects.
# Another, POSTROUTING, handles snat and masquerade.

echo "Load rules for nat table ..."

###############################################################################
#
# PREROUTING chain
#


###############################################################################
#
# POSTROUTING chain
#


###############################################################################
#
# mangle table
#
###############################################################################

# The mangle table is used to alter packets.  It can alter or mangle them in
# several ways.  For the purposes of this generator, we only use its ability
# to alter the TTL in packets.  However, it can be used to set netfilter
# mark values on specific packets.  Those marks could then be used in another
# table like filter, to limit activities associated with a specific host, for
# instance.  The TOS target can be used to set the Type of Service field in
# the IP header.  Note that the TTL target might not be included in the
# distribution on your system.  If it is not and you require it, you will
# have to add it.  That may require that you build from source.

echo "Load rules for mangle table ..."

echo "Firewall loaded."

#$IPTABLES -L -n --line-numbers

```

My machine is invisible to nmap except to machines that I specify.  I run several servers that are available to the machines I specify.  I also use hosts.allow and hosts.deny in case of firewall failure.  I have granular control over who can and can't communicate with my machine.  The posters who don't use firewalls can't say the same.

---

### Post by RAOF on 2006-02-28
[QUOTE=anthro398]...
My machine is invisible to nmap except to machines that I specify.  I run several servers that are available to the machines I specify.  I also use hosts.allow and hosts.deny in case of firewall failure.  I have granular control over who can and can't communicate with my machine.  The posters who don't use firewalls can't say the same.[/QUOTE]
Most of the posters who don't use firewalls don't have any internet visible services, anyway.  And while your setup is more secure (at least if you're actually running some servers), it's also less convenient.  If security is **very** important to you, then it might be worth it.  But the majority of Ubuntu users **do not need** a firewall - it is not possible to remotely attack a default Ubuntu setup.

---

### Post by anthro398 on 2006-03-01
Foolish, foolish.  Is the 'average user' aware of every application that listens on a network port?  Are you?  Do you really want to be pingable?  Other than the couple of hours it took me to learn about iptables to write the rules I've posted here, I have no idea what you could possibly be referring to when you speak of inconvenience.  I find it exceptionally convenient that I can run Apache on my system to test webpages, but that all remote users are denied access to it.  I find it highly convenient that I can ssh to my machine, but that you can't.  Etc. 

I'm done talking about this, but I wanted there to be another perspective here.  Use or don't use a firewall, it is certainly up to each user, but ,were I you, I'd carefully weigh the pros and cons of a firewall rather than take the knee-jerk "not possible to remotely attack a default Ubuntu setup" opinion that is so rampant here.

---

