---
title: "Debian 8.1 Bind9 DNS Configuration. First time Linux user."
date: 2015-08-06
forum: Debian
---

### Post by Scrapps on 2015-08-06
Hello,
I'm trying to set up a home LAN Debian Server, just because. I've managed to setup eth0 interface & SSH, I'm now trying to configure the DNS in bind9. I've been through A LOT of tutorials but I'm not having a win. Any help would be appreciated I thought I was getting the hang of it but it seems not :icon_frown:.
This is the error I'm getting:

```
root@server1:/etc/bind# nslookup pc.home.lan
Server:         127.0.0.1
Address:        127.0.0.1#53

** server can't find pc.home.lan: SERVFAIL

```
This is what I have so far:
```

/etc/bind/home.lan

;
; BIND Direct
;

$TTL    604800
@       IN      SOA     home.lan. root.home.lan. (
                        201508061       ; Serial
                        604800          ; Refresh
                        86400           ; Retry
                        2419200         ; Expire
                        604800 )        ; Negative Cache TTL
;

@       IN      NS      home.lan.
www     IN      A       192.168.2.100
pc      IN      A       192.168.2.2
_________________________________________________________________________
/etc/bind/home.lan.loopback

;
;  BIND Loopback
;

$TTL    604800
@       IN      SOA      home.lan.  root.home.lan. (
                         201508061      ;serial
                         604800         ;refresh
                         86400          ;retry
                         2419200        ;expires
                         604800 )       ;Negative Cache TTL
;

@       IN      NS       home.lan.
1       IN      PTR      www.home.lan.
2       IN      PTR      pc.home.lan.
_________________________________________________________________________
/etc/bind/named.conf.local

zone "home.lan" {
        type master;
        file "/etc/bind/home.lan";
};

zone "2.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/home.lan.loopback";
};
_________________________________________________________________________
/etc/resolv.conf

domain home.lan
search home.lan
nameserver 127.0.0.1
_________________________________________________________________________
/etc/bind/named.conf.options

options {
        directory "/var/cache/bind";

        forwarders {
        // OpenDNS servers
        208.67.222.222;
        208.67.220.220;
        // ADSL router
        192.168.1.1;
        };

        // Security options
        listen-on port 53 { 127.0.0.1; 192.168.1.100; };
        allow-query { 127.0.0.1; 192.168.1.0/24; };
        allow-recursion { 127.0.0.1; 192.168.1.0/24; };
        allow-transfer { none; };

        dnssec-validation auto;
        auth-nxdomain no;    # conform to RFC1035
};

```

---

### Post by Scrapps on 2015-08-07
Fixed. Had wrong IP addresses in the security settings.

---

