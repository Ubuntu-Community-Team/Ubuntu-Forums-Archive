---
title: "wireless keeps disconnetcs every 60 sec"
date: 2005-12-26
forum: General Help
---

### Post by smb2004 on 2005-12-26
i just installed ubuntu on my compaq v2000 laptop.  on windows my wireless works great and doesnt disconnect or loose signal when in my house. 
i installed ndiswrapper and installed the drivers and it the wireless works (kind of).  after i do 'sudo dhclient' it connects to my wireless router but the internet wil only work for around 60 seconds, after that i have to do another 'sudo dhclient' and it will work for another 60 seconds or so (even when right next to router, so its not loseing signal).  
does anyone know what could be cause this or how to correct it.  thanks.

---

### Post by brainkilla on 2005-12-26
Try commenting out this line in /etc/dhcp3/dhclient.conf

#timeout 60

---

### Post by smb2004 on 2005-12-26
it is commeted out.  here is my dhclient.conf :

```


# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}


```


i've also disabled wep/wpa untill i get it all setup and running smooth.

---

### Post by smb2004 on 2005-12-26
UPDATE:

the same thing just happened when i went to a wired connection.  so it seems to be all networking i get this situation.

---

