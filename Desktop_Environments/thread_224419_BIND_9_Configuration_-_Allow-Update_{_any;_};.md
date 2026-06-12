---
title: "BIND 9 Configuration - Allow-Update { any; };"
date: 2006-07-27
forum: Desktop Environments
---

### Post by SuperJason on 2006-07-27
I'm trying to set up BIND 9.3.2 for my local network.  It's working great, except that I'm trying to get anonymous dynamic updates working.  According to everything I could find (not much), I have correctly set it up to allow anyone to make updates.

I would apreciate any help that you could provide!


Here are my configuration files.  If anything, they might help someone else get as far as I got:

named.conf.local
--------------------------------------------
zone "ytech.private" {
        type master;
        file "/etc/bind/zone.private.ytech";
	allow-update { any; };
};

zone "0.168.192.in-addr.arpa" {
	type master;
	file "/etc/bind/revp.192.168.0";
	allow-update { any; };
};
---------------------------------------------

zone.private.ytech
---------------------------------------------
$ttl 38400
$ORIGIN ytech.private.
@	IN      SOA     NetSrv hostmaster (
          200607262
          1200       
          900    
          1209600  
          1200 )   
	IN	NS	NetSrv

NetSrv			IN	A	192.168.0.4
test			IN	A	192.168.0.99
---------------------------------------------

revp.192.168.0
---------------------------------------------
$ORIGIN 0.168.192.in-addr.arpa.
$TTL 1D
@     IN SOA  NetSrv.ytech.private. hostmaster.ytech.private. (
              200607261  ; serial
              28800      ; refresh (8 hours)
              14400      ; retry (4 hours)
              2419200    ; expire (4 weeks)
              86400      ; minimum (1 day)
              )
; define the authoritative name server
              NS      NetSrv.ytech.private.

4		PTR	NetSrv.ytech.private.

---

### Post by genesis[OFT] on 2006-12-13
I know that this is an old thread, but I'm having the same problem.  I have BIND9 installed on a Ubuntu Linux 6.06 LTS Dapper Drake box and I am trying to configure dynamic updates for some Windows XP clients.  Was there ever a solution to this thread or does anyone have any ideas on how to fix this issue.  My named.conf.local\named.conf.options\named.conf and zone files are the same as the OT, of course with different domains though.

---

