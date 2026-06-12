---
title: "Setting up an Ubuntu gateway (8.10 x86_64)"
date: 2009-04-06
forum: General Help
---

### Post by sanemanmad on 2009-04-06
Hi All, 

I know this guide is incomplete, however that is why I am posting it here so hopefully others will provide feedback. I am still considered a *noob* after all, I still spend alot of my time on these forums.

Here it is: I have also attached the .doc version (Preserves the original format)

```

Setting up an Ubuntu gateway (8.10 x86_64) Kernel 2.6.27-11-server. This setup assumes all of the most recent updates and patches are available and installed up until this document was created.

Where I live, my mother&#8217;s home is within wireless distance (~ 20-30 meters), enabling her to use my internet connection for her network also. She has a laptop and a network printer (Wireless also) that she uses and connects to my network with. I also have my Sister and her fiancé who live almost same distance maybe a bit further in the opposite direction. They use their IPOD and desktop to connect to my network over their own connection for FTP and e-mail etc.. Big Deal! Right? Well for my setup I have (including my roommate) 2 laptops, 1 Server, 1 X360, 1 PS3 and Sometimes my work laptop. As you can see, I would and DO benefit from a small home lan gateway. This Server also functions as my File, backup, FTP, WEB, NFS and Mediatomb server along with a few other neat apps, so the need for dual LAN NIC can be justified.

At first this document may seem convoluted and eventually will be updated to be precise and to the point (with as much help).

1.	IPtables
2.	Bind9
3.	Denyhosts
4.	ifenslave
5.	DHCP3-server
6.	Squid3
7.	SSHd
8.	TC (traffic control)

Modem 
&#8226;	Motorola cable modem provided by ISP
Switch
&#8226;	5 port Linksys SD205
WAP 
&#8226;	Linksys WAP54g v2
Gateway:
&#8226;	AMD Phenom(tm) 8450 Triple-Core Processor
NIC  
&#8226;	eth0 - onboard
&#8226;	eth1 - pci
&#8226;	eth2 &#8211; pci
HDD 
&#8226;	ATA Hitachi HDT72101 (Direct-Access) &#8211; 1Tb
&#8226;	ATA Maxtor 2B020H1 (Direct-Access) &#8211; / 20Gb
&#8226;	ATA ST3320613AS (Direct-Access) &#8211; Backups 320Gb
&#8226;	ATA WDC WD5000AAKS-0 (Direct-Access) &#8211; MEDIA 500Gb
&#8226;	HL-DT-ST DVD-RAM GH22NS30 (CD-ROM) &#8211; *
Memory 
&#8226;	2x2 = 3.62 Gb Useable  (Dual Channel)

Basic Topology
modem &#8211; gateway &#8211; switch - wap
   eth0    	eth1  	eth2 
                                 |
		     bond0

Using this document:
All items BOLDED are meant to be comments 
All items ITALICIZED are meant to be commands
All other REGULAR text is meant to be the actual configuration.

First thing is to install the necessary software.

sudo aptitude install openssh-server bind9 squid3 dhcp3-server denyhosts ifenslave apache2 phpsysinfo phpmyadmin mysql-server-5.0  mii-tool &&  sudo aptitude remove apparmor  && sudo aptitude safe-upgrade

Become root &#8211; sudo bash

vi /etc/hostname
Alice

SECURE SHELL
edit ssh server to allow for remote administration (this should be a headless setup). I learned using vi, however many users find it easier to use nano

cp /etc/ssh/sshd_config /etc/ssh/sshd_config.original

vi /etc/ssh/sshd_config

# SSH Config
AddressFamily inet # IPv4 only
Port 22		# Listen on Port 22
Protocol 2 	# Only use 2, 1 is less secure
HostKey /etc/ssh/ssh_host_rsa_key
UsePrivilegeSeparation yes
KeyRegenerationInterval 3600
ServerKeyBits 768
SyslogFacility AUTH
LogLevel INFO 
AllowUsers michael 	# Only allow users listed here [space space]
LoginGraceTime 20	 # Users have 20 seconds to enter login information
PermitRootLogin no	 # No reason to change this &#8211; you can always ssh as less priviledged user (who has sudo rights) and sudo
StrictModes yes
MaxAuthTries 3		 # Disconnect after 3 failed tries
RSAAuthentication yes	 # Allows for ssh key login
PubkeyAuthentication yes	 # Allows for ssh key login
IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no
PasswordAuthentication yes
PermitEmptyPasswords no # Be sure this is set to &#8220;no&#8221;
ChallengeResponseAuthentication no
X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
UseLogin yes		 # Allow for client to enter login credentials
MaxStartups 10:30:60
AcceptEnv LANG LC_*
Subsystem sftp /usr/lib/openssh/sftp-server	 # A secure FTP server (sftp) 
UsePAM yes

INTERFACES
Next edit the interface file

vi /etc/network/interfaces

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto bond0 iface bond0 inet static address 192.168.51.10 netmask 255.255.255.0 network 192.168.51.0 post-up ifenslave bond0 eth1 eth2 pre-down ifenslave -d bond0 eth1 eth2 
check for daemon netstat -nl|grep 22  (on the gateway itself)
 netstat -nl|grep 22
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN 

vi /etc/modprobe.d/arch/x86_64 * Different on a 32bit system

Add this to bottom of the file

alias bond0 bonding options bond0 mode=0 miimon=100 downdelay=200 updelay=200 

* Note this will only work if you have 3 NICs on the gateway itself. I use this for  load-balancing amongst my LAN. You will need to verify with  the mii-tool that your network cards are supported.

DHCP SERVER

Edit 2 files in the directory. 
1.	dhclient.conf
2.	dhcpd.conf
Why am I changing my dhclient.conf?
I have found that unless this is changed, the eth0 asks my ISP for the nameservers (no matter what I try).

1.	dhclient.conf

One easy way of re-creating file:

mv /etc/dhcp/dhclient.conf  /etc/dhcp.dhclient.original
vi /etc/dhcp/dhclient.conf <--- I removed all other interfaces from this file.

interface "eth0" { 
request subnet-mask, broadcast-address, time-offset, routers,
interface-mtu;
}

2.	dhcpd.conf

vi /etc/init.d/dhcpd.conf

ddns-update-style interim;
ddns-updates on;
ddns-domainname	"home.lan.";
ddns-rev-domainname	"in-addr.arpa.";
ignore client-updates;
server-identifier	192.168.51.10;
authoritative;
log-facility local7;
include                 "/etc/bind/rndc.key";
zone home.lan {
	primary 127.0.0.1;
	key "rndc-key";
	}
zone in-addr.arpa {
        primary 127.0.0.1;
        key "rndc-key";
        }
# Basic Config 
default-lease-time 21600;
max-lease-time 43200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.51.31;
option routers 192.168.51.10;
option domain-name-servers 192.168.51.10; 
option domain-name "home.lan";
option ntp-servers 192.168.51.10;
# subnet configuration
subnet 192.168.51.0 netmask 255.255.255.0 {
range 192.168.51.12 192.168.51.20;
}
host printer {
hardware ethernet xx:xx:xx:xx:xx;
option host-name "printer";
option domain-name "home.lan";
ddns-hostname "printer";
}
host lara-croft {
hardware ethernet xx:xx:xx:xx:xx; 
fixed-address 192.168.51.11;
}
host elektra {
hardware ethernet xx:xx:xx:xx:xx
}


Configure default dhcp server interface

vi /etc/default/dhcp

INTERFACES="bond0" <-- This tells your DHCP server only to serve requests on the bonded interface (in my case eth1+eth2)

DNS SERVER


vi  /etc/bind/db.192.168.51

$ORIGIN .
$TTL 21600	; 6 hours
in-addr.arpa		IN SOA	Alice.home.lan. admin.home.lan. (  <----  needs to be exact syntax
				364        ; serial
				10800      ; refresh (3 hours)
				3600       ; retry (1 hour)
				604800     ; expire (1 week)
				86400      ; minimum (1 day)
				)
			NS	Alice.home.lan. <----- Nameserver for network, same as gateway
$ORIGIN 51.168.192.in-addr.arpa.
10			PTR	Alice.home.lan. <---- static devices, non-DHCP
11			PTR	Lara-Croft.home.lan.  <---- static devices, non-DHCP


vi  /etc/bind/db.home.lan

$ORIGIN .
$TTL 21600	; 6 hours
home.lan		IN SOA	Alice.home.lan. admin.home.lan. ( 
				581        ; serial
				10800      ; refresh (3 hours)
				3600       ; retry (1 hour)
				604800     ; expire (1 week)
				86400      ; minimum (1 day)
				)
			NS	Alice.home.lan.
$ORIGIN home.lan.
$TTL 86400	; 1 day
Alice			A	192.168.51.10 <---- static devices, non-DHCP

vi /etc/bind/named.conf

Append this to the end of file

acl lan {
        192.168.51.0/24;  <--- this should be the network of your LAN and the loopback of the gateway
        127.0.0.1;
        };
include "/etc/bind/named.conf.local"; 

vi /etc/bind/named.conf.local

zone "home.lan" IN { <---- I chose this for a simple domain; does not resolve outside my network
        type master;
        file "/etc/bind/db.home.lan";
	allow-update { key "rndc-key"; };
	notify yes;
};
zone "in-addr.arpa" IN {
        type master;
        file "/etc/bind/db.192.168.51";
	allow-update { key "rndc-key"; };
	notify yes;
}; 
 
include "/etc/bind/rndc.key";  <--- Make sure this file exists, if not you will need to locate it.

vi /etc/bind/named.conf.options

options { 	
directory "/var/cache/bind"; 	
forward first; 	
forwarders { 	 
208.67.220.220; 208.67.222.222;  <---- This is where you place your forwarding DNS  (non-internal)
	};
	auth-nxdomain yes;    # conform to RFC1035
        listen-on { 127.0.0.1; 192.168.51.10; }; <---- I only allow my gateway to serve DNS requests to the LAN or itself.
        allow-query { lan; };          allow-recursion { lan; }; }; // allow localhost to perform updates controls {         inet 127.0.0.1 allow { localhost; } keys { "rndc-key"; }; }; 
	
DISABLE IPV6

vi /etc/modprobe.d/aliases

alias net-pf-10 ipv6 # make the following line look like below
alias net-pf-10 off ipv6 
IPtables

A script I put together over the last few months (with the help of various resources)
There are many ways to accomplish this, however I have saved this a firewall.sh under /etc/init.d, then created a symlink to /etc/rcS.d/S39firewall. Each time my server is reboot the file is read into the startup script. Should you ever need to disable this, just remove the symlink to /etc/rcS.d/S39firewall

#!/bin/bash
IPT="/sbin/iptables"
INT="eth0"
$IPT -F
$IPT -F INPUT
$IPT -F OUTPUT
$IPT -F FORWARD
$IPT -F -t mangle
$IPT -F -t nat
$IPT -X
$IPT -P INPUT DROP
$IPT -P OUTPUT ACCEPT
$IPT -P FORWARD ACCEPT
#  Lan - Proxy setup
$IPT -A INPUT -i bond0 -s 192.168.51.0/24 -d 192.168.51.0/24 -p all -j ACCEPT
$IPT -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
# This allows for all clients on my LAN to access my WEB server without hitting the proxy.
$IPT -t nat -A PREROUTING -i bond0 -p tcp --dport 80 -d ! 192.168.51.10 -j DNAT --to 192.168.51.10:3128
# Logging
$IPT -N firewall
$IPT -A firewall -m limit --limit 15/minute -j LOG --log-prefix Firewall:
$IPT -A firewall -j DROP
$IPT -N dropwall
$IPT -A dropwall -m limit --limit 15/minute -j LOG --log-prefix Dropwall:
$IPT -A dropwall -j DROP
$IPT -N badflags
$IPT -A badflags -m limit --limit 15/minute -j LOG --log-prefix Badflags:
$IPT -A badflags -j DROP
$IPT -N silent
$IPT -A silent -j DROP
# Accept all on loopback
$IPT -A INPUT -i lo -j ACCEPT
# Bad packets get dropped
$IPT -A INPUT -p tcp --tcp-flags ALL FIN,URG,PSH -j badflags
$IPT -A INPUT -p tcp --tcp-flags ALL ALL -j badflags
$IPT -A INPUT -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j badflags
$IPT -A INPUT -p tcp --tcp-flags ALL NONE -j badflags
$IPT -A INPUT -p tcp --tcp-flags SYN,RST SYN,RST -j badflags
$IPT -A INPUT -p tcp --tcp-flags SYN,FIN SYN,FIN -j badflags
# Block Ping
$IPT -A INPUT -i $INT -p icmp --icmp-type 0 -j DROP
$IPT -A INPUT -i $INT -p icmp --icmp-type 3 -j DROP
$IPT -A INPUT -i $INT -p icmp --icmp-type 8 -j DROP
$IPT -A INPUT -i $INT -p icmp --icmp-type 11 -j DROP
$IPT -A INPUT -i $INT -p icmp --icmp-type address-mask-request -j DROP
$IPT -A INPUT -i $INT -p icmp --icmp-type timestamp-request -j DROP
$IPT -A INPUT -p icmp -j firewall
# Limit connections to Sensitive ports by dropping incoming connections @ a rate-limit of 2/60s
$IPT -A INPUT -i $INT -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
$IPT -A INPUT -i $INT -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 2 --rttl --name SSH -j DROP
$IPT -A INPUT -i $INT -p tcp --dport 20:21 -m state --state NEW -m recent --set --name FTP
$IPT -A INPUT -i $INT -p tcp --dport 20:21 -m state --state NEW -m recent --update --seconds 60 --hitcount 2 --rttl --name FTP -j DROP
$IPT -A INPUT -i $INT -p tcp --dport 5900:5913 -m state --state NEW -m recent --set --name VNC
$IPT -A INPUT -i $INT -p tcp --dport 5900:5913 -m state --state NEW -m recent --update --seconds 60 --hitcount 2 --rttl --name VNC -j DROP
# Accept incoming connections for SSH and FTP
$IPT -A INPUT -i $INT -s 0/0 -d 0/0 -p tcp --dport 22 -j ACCEPT
$IPT -A INPUT -i $INT -s 0/0 -d 0/0 -p tcp --dport 21 -j ACCEPT
$IPT -A INPUT -i $INT -s 0/0 -d 0/0 -p tcp --dport 20 -j ACCEPT
# Stateful packet monitoring for HTTP/FTP
modprobe ip_conntrack
modprobe ip_conntrack_ftp
# Enable IP forwarding - NAT
echo 1 > /proc/sys/net/ipv4/ip_forward
echo 1 > /proc/sys/net/ipv4/tcp_syncookies
$IPT -t nat -A POSTROUTING -o $INT -j MASQUERADE
# Redirect to Proxy
$IPT -t nat -A PREROUTING -i $INT -p tcp --dport 80 -j REDIRECT --to-port 3128
# Used to forward port to a client on network
$IPT -t nat -A PREROUTING -i $INT -p tcp --dport 5912 -j DNAT --to 192.168.51.12:5912

Squid3 Proxy

vi /etc/squid3/squid.conf 

http_port 192.168.51.10:3128 transparent
hierarchy_stoplist cgi-bin ?
acl QUERY urlpath_regex cgi-bin \?
refresh_pattern ^ftp: 1440 20% 10080
refresh_pattern ^gopher: 1440 0% 1440
refresh_pattern -i \.(gif|png|jpg|jpeg|ico)$ 10080 90% 43200 override-expire ignore-no-cache ignore-no-store ignore-private
refresh_pattern -i \.(iso|avi|wav|mp3|mp4|mpeg|swf|flv|x-flv)$ 43200 90% 432000 override-expire ignore-no-cache ignore-no-store ignore-private
refresh_pattern -i \.(deb|rpm|exe|zip|tar|tgz|ram|rar|bin|ppt|doc|tiff)$ 10080 90% 43200 override-expire ignore-no-cache ignore-no-store ignore-private
refresh_pattern -i \.index.(html|htm)$ 0 40% 10080
refresh_pattern -i \.(html|htm|css|js)$ 1440 40% 40320
refresh_pattern . 0 40% 40320
acl lan src 192.168.51.0/24
acl SSL_ports port 443          # https
acl SSL_ports port 873          # rsync
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 1025-65535  # unregistered ports
acl purge method PURGE
acl CONNECT method CONNECT
cache_mem 256 MB
logfile_rotate 3
maximum_object_size 50000 KB
http_access allow purge
http_access allow lan
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access deny all
visible_hostname Alice.home.lan
cache_access_log /var/log/squid3/access.log
logformat squid %>a %<A %{format}tl %Hs %Ss
cache_dir ufs /var/spool/squid3 256 16 256
log_fqdn off
negative_ttl 2

Change Permissions on paths
chown -R proxy:proxy /var/log/squid3/
chown proxy:proxy /etc/squid3/squid.conf

Restart squid and verify it starts correctly. look for any error/messages on terminal.

/etc/init.d/squid restart
tail -30 /var/log/dmesg|grep squid
tail -30 /var/log/squid3/cache.log

Example output from dmesg
2009/01/22 15:53:38| Loaded Icons.
2009/01/22 15:53:38| Accepting transparently proxied HTTP connections at 192.168.51.10, port 3128, FD 13.
-----------------	SNIP   -----------------
2009/01/22 15:53:38|   Completed Validation Procedure

TC (Traffic Shapping)


COMING SOON &#61663; Already complete, I just need to go over my configuration before submitting it to this How-To.


References:
http://www.linux.com/feature/153221 
http://brunogirin.blogspot.com/2007/11/dhcp-and-dynamic-dns-on-ubuntu-server.html
http://pupa.da.ru/tc/
http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/
http://www.squid-cache.org/
http://www.iptablesrocks.org/
http://www.howtoforge.org/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server
http://debianclusters.cs.uni.edu/index.php/Testing_and_Troubleshooting_BIND
https://help.ubuntu.com/community/dhcp3-server
http://www.linuxselfhelp.com/HOWTO/Adv-Routing-HOWTO-9.html
http://www.ubuntugeek.com
http://ubuntuforums.org/


```

---

