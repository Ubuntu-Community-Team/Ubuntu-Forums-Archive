---
title: "Can't access some sites since I upgraded to 9.04"
date: 2009-04-28
forum: General Help
---

### Post by Gojippo on 2009-04-28
Hi all.

2 days ago, I upgraded from 8.10 to 9.04 and since then, I can't seem to access sites I was using without any problem before (on 8.10). I know these sites work because I can access them from other places.

In Firefox, they just don't seem to load. I don't even get a timeout error. Other sites (like this one) work w/o problems.

I asked support on the japanese ubuntu support forum, where they asked me to dig and ping the sites that don't work, but from the results they don't know the cause.

```
dig www.nicovideo.jp | grep A;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 62166
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2
;www.nicovideo.jp.        IN    A
;; ANSWER SECTION:
www.nicovideo.jp.    109    IN    A    202.248.110.243
;; AUTHORITY SECTION:
;; ADDITIONAL SECTION:
ns101.dwango.co.jp.    165    IN    A    61.204.150.137
ns102.dwango.co.jp.    214    IN    A    202.219.104.21
;; WHEN: Tue Apr 28 19:38:29 2009
```

```
$ dig fc2.com | grep A
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 20877
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 0
;fc2.com.            IN    A
;; ANSWER SECTION:
fc2.com.        901    IN    A    208.71.106.124
;; AUTHORITY SECTION:
;; WHEN: Tue Apr 28 19:21:22 2009
```

```
$ for i in 1400 1454 1500 ; do ping -c 4 -s $i www.nicovideo.jp; done
PING www.nicovideo.jp (202.248.110.243) 1400(1428) bytes of data.

--- www.nicovideo.jp ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2998ms

PING www.nicovideo.jp (202.248.110.243) 1454(1482) bytes of data.

--- www.nicovideo.jp ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3024ms

PING www.nicovideo.jp (202.248.110.243) 1500(1528) bytes of data.

--- www.nicovideo.jp ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3023ms
```

```
$ for i in 1400 1454 1500 ; do ping -c 4 -s $i fc2.com; done
PING fc2.com (208.71.106.124) 1400(1428) bytes of data.
1408 bytes from sata4.fc2.com (208.71.106.124): icmp_seq=1 ttl=52 time=108 ms
1408 bytes from sata4.fc2.com (208.71.106.124): icmp_seq=2 ttl=52 time=124 ms
1408 bytes from sata4.fc2.com (208.71.106.124): icmp_seq=3 ttl=52 time=110 ms
1408 bytes from sata4.fc2.com (208.71.106.124): icmp_seq=4 ttl=52 time=108 ms

--- fc2.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 108.755/112.957/124.012/6.411 ms
PING fc2.com (208.71.106.124) 1454(1482) bytes of data.
1462 bytes from sata4.fc2.com (208.71.106.124): icmp_seq=1 ttl=52 time=111 ms
1462 bytes from sata4.fc2.com (208.71.106.124): icmp_seq=2 ttl=52 time=121 ms
1462 bytes from sata4.fc2.com (208.71.106.124): icmp_seq=3 ttl=52 time=121 ms
1462 bytes from sata4.fc2.com (208.71.106.124): icmp_seq=4 ttl=52 time=120 ms

--- fc2.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 111.028/118.872/121.926/4.546 ms
PING fc2.com (208.71.106.124) 1500(1528) bytes of data.
1508 bytes from sata4.fc2.com (208.71.106.124): icmp_seq=1 ttl=52 time=123 ms
1508 bytes from sata4.fc2.com (208.71.106.124): icmp_seq=2 ttl=52 time=123 ms
1508 bytes from sata4.fc2.com (208.71.106.124): icmp_seq=3 ttl=52 time=109 ms
1508 bytes from sata4.fc2.com (208.71.106.124): icmp_seq=4 ttl=52 time=121 ms

--- fc2.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 109.109/119.570/123.842/6.097 ms
```

I don't get ping response for one site but still from dig, and the other site gets responses for both. But I can't still access them. Any idea ?

---

### Post by BKonkle on 2009-04-28
Are there any entries in your /etc/hosts file that would interfere with these sites?

---

