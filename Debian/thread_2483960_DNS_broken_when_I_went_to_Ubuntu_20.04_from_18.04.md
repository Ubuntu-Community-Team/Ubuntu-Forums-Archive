---
title: "DNS broken when I went to Ubuntu 20.04 from 18.04"
date: 2023-02-14
forum: Debian
---

### Post by ski-brimson on 2023-02-14
So Debian Sarge, using dig and my comcast DNS server:

```
dig @100.115.92.193 google.com 

; <<>> DiG 9.16.37-Debian <<>> @100.115.92.193 google.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 16157
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             143     IN      A       142.250.191.174

;; Query time: 16 msec
;; SERVER: 100.115.92.193#53(100.115.92.193)
;; WHEN: Tue Feb 14 00:44:32 CST 2023
;; MSG SIZE  rcvd: 55
```

Now the response on 20.04 from the same subnet on the same router:

```
dig  @100.115.92.193 google.com

; <<>> DiG 9.16.1-Ubuntu <<>> @100.115.92.193 google.com
; (1 server found)
;; global options: +cmd
;; connection timed out; no servers could be reached

```


Now 20.04 with 8.8.8.8
```
; <<>> DiG 9.16.1-Ubuntu <<>> @8.8.8.8 google.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 9884
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             15      IN      A       172.217.0.174

;; Query time: 28 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Tue Feb 14 00:45:23 CST 2023
;; MSG SIZE  rcvd: 55

```

So just use google for everything?

---

### Post by slickymaster on 2023-02-14
*Thread moved to **Debian**.*

---

### Post by SeijiSensei on 2023-02-14
First, is the system using systemd-resolved? Check with "ps ax | grep resolved". If so, your /etc/resolv.conf should have a "nameserver" entry that points to 127.0.0.53.

With systemd, you need to manage DNS via edits to /etc/systemd/resolv.conf. You can specify custom nameservers in the "DNS=" line.

---

### Post by ski-brimson on 2023-02-14
Not sure why this thread was moved to Debian, when my problem was Ubuntu upgrade, though maybe the packages are common to both.

I was originally using the address of my router as the name server, as it has DNS.  I think what happened is some kind of feature/security enhancement that broke my router's DNS server.

I had another Ubuntu 20.04 system, and looked at the IP addresses of the name server which were generated in /etc/systemd/resolv.conf.

```
nameserver 75.75.75.75
nameserver 75.75.76.76
```

So I updated /etc/netplan configuration of the interface to use those two addresses on my new Ubuntu 20 system, and it worked.

By the way, 
```
dig @[dns server ip v.4] hostname
```

has nothing to do with systemd or any other user-space server.  It is merely testing the target DNS server, the kernel, the C library, and any firewalls.

I now realize that my Debian system was not on the same subnet, so I suspect 100.115.92.193
Is not a valid address on my Ubuntu systems.

---

### Post by ski-brimson on 2023-02-14
I should have looked in /etc/systemd/resolv.conf on working systems to get the nameservers on the public internet.  Thanks.

---

### Post by SeijiSensei on 2023-02-15
Those are Comcast's name servers. They'll work if you're a Comcast subscriber but not if you aren't. I cannot query the server at 75.75.75.75 from my Verizon connection; it hangs and does not reply. It also does not reply to queries from my virtual servers at Linode.

---

### Post by #&amp;thj^% on 2023-02-15
I get mixed results, and I'm not a Comcast customer:
```
ping 75.75.75.75
PING 75.75.75.75 (75.75.75.75) 56(84) bytes of data.
64 bytes from 75.75.75.75: icmp_seq=1 ttl=52 time=45.1 ms
64 bytes from 75.75.75.75: icmp_seq=2 ttl=52 time=45.9 ms
64 bytes from 75.75.75.75: icmp_seq=3 ttl=52 time=45.5 ms
64 bytes from 75.75.75.75: icmp_seq=4 ttl=52 time=44.8 ms
64 bytes from 75.75.75.75: icmp_seq=6 ttl=52 time=44.5 ms
64 bytes from 75.75.75.75: icmp_seq=7 ttl=52 time=45.1 ms
64 bytes from 75.75.75.75: icmp_seq=8 ttl=52 time=45.8 ms
64 bytes from 75.75.75.75: icmp_seq=9 ttl=52 time=44.6 ms
^C
--- 75.75.75.75 ping statistics ---
9 packets transmitted, 8 received, 11.1111% packet loss, time 8027ms
rtt min/avg/max/mdev = 44.455/45.165/45.891/0.507 ms

```
 ```
 ping 75.75.75.76
PING 75.75.75.76 (75.75.75.76) 56(84) bytes of data.

^C
--- 75.75.75.76 ping statistics ---
14 packets transmitted, 0 received, 100% packet loss, time 13290ms


```

---

### Post by SeijiSensei on 2023-02-16
PIngs aren't the correct test. Try doing a DNS query like
```
host www.google.com 75.75.75.75
```

---

