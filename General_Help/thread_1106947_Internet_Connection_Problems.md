---
title: "Internet Connection Problems"
date: 2009-03-26
forum: General Help
---

### Post by perliff on 2009-03-26
Hi all, 

I am running a ubuntu server 8.04 hardy heron. here's my list of troubles... 

1. last week, the server got hacked. some guys installed some programs in a users directory. it seemed to me to be connecting to some undernet servers in netherlands. after getting alerted by our network guys, all passwords were changed. also i located the installation in this users folder and deleted it as some processes were being launched from here. i think i also killed all procesess of this user as well. a firewall was installed (firestarter)

2. however, as soon as the malware was deleted, the internet connection stopped working as well. i am still able to ping other servers, eg. 

ping [www.google.com](www.google.com) 

work, and gives me a reply (including an IP address). But if I take this IP address and put in the firefox address bar, it says connection error.

3. the internet connection was working fine with DHCP before. no problems at all. now it doesnt work.

4. here i my /etc/network/interfaces file

auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth0

5. the other source of trouble is the gnome-nettools. when i want to configure my eth0 using this tool, it gives me the error "interface does not exist"


6. some details are below..

output of ifconfig eth0

eth0      Link encap:Ethernet  HWaddr 00:1a:92:8c:4d:bc  
          inet addr:xxx.xxx.xxx.xxx  Bcast:xxx.xxx.xxx.xxx  Mask:xxx.xxx.xxx.xxx
          inet6 addr: fe80::21a:92ff:fe8c:4dbc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1027 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:96577 (94.3 KB)  TX bytes:21004 (20.5 KB)
          Base address:0x2000 Memory:c8200000-c8220000 

output of ifconfig lo
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:394386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:394386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16573116 (15.8 MB)  TX bytes:16573116 (15.8 MB)


output from /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                                                                                                        * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
There is already a pid file /var/run/dhclient.eth0.pid with pid 14390
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1a:92:8c:4d:bc
Sending on   LPF/eth0/00:1a:92:8c:4d:bc
Sending on   Socket/fallback

DHCPRELEASE on eth0 to xxx.xxx.xxx.xxx port 67
send_packet: Operation not permitted
Updating databases ...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/databases...
Updating Makefile ...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/Makefile...
Updating sendmail.cf ...
WARNING: Antispam rules not available in deferred delivery mode.
Updating auth ...
sasl2-bin not installed, not configuring sendmail support.

To enable sendmail SASL2 support at a later date, invoke "/usr/share/sendmail/update_auth"

Creating /etc/mail/relay-domains
# Optional file...
The following file(s) have changed:
  /etc/mail/sendmail.cf
** ** You should issue `/etc/init.d/sendmail reload` ** **
 * Reloading Mail Transport Agent (MTA) sendmail
   ...done.
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1a:92:8c:4d:bc
Sending on   LPF/eth0/00:1a:92:8c:4d:bc
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPOFFER of xxx.xxx.xxx.xxx from zzz.zzz.zzz.zzz
DHCPREQUEST of xxx.xxx.xxx.xxx on eth0 to 255.255.255.255 port 67
DHCPACK of xxx.xxx.xxx.xxx from zzz.zzz.zzz.zzz
addr=xxx.xxx.xxx.xxx,		 name=hostname
Updating databases ...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/databases...
Updating Makefile ...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/Makefile...
Updating sendmail.cf ...
Updating auth ...
sasl2-bin not installed, not configuring sendmail support.

To enable sendmail SASL2 support at a later date, invoke "/usr/share/sendmail/update_auth"

Creating /etc/mail/relay-domains
# Optional file...
The following file(s) have changed:
  /etc/mail/sendmail.cf
** ** You should issue `/etc/init.d/sendmail reload` ** **
 * Reloading Mail Transport Agent (MTA) sendmail
   ...done.
bound to xxx.xxx.xxx.xxx -- renewal in 12417 seconds.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
Updating sendmail.cf ...
Updating auth ...
sasl2-bin not installed, not configuring sendmail support.

To enable sendmail SASL2 support at a later date, invoke "/usr/share/sendmail/update_auth"

Creating /etc/mail/relay-domains
# Optional file...
The following file(s) have changed:
  /etc/mail/sendmail.cf
** ** You should issue `/etc/init.d/sendmail reload` ** **
 * Reloading Mail Transport Agent (MTA) sendmail
   ...done.

I have been trawling all forums without success... and this seems to be the last hope...

:confused:

---

### Post by perliff on 2009-03-26
ok.. i have managed to sort the problem... the problem was that the firestarter firewall was blocking everything. removed it and everything went fine. now will try to install firewall again and configure it better...

:P

---

