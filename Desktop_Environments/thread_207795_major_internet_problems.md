---
title: "major internet problems"
date: 2006-07-02
forum: Desktop Environments
---

### Post by vulcan123 on 2006-07-02
i love ubuntu. It is just so ausome. But one major problem i am having it that the internet just isn't working. Only a few of the major websites work, like ubuntu.com(thankfuly) and a few others. The most common error message is:

"The connection has timed out"

It isn't like this on Windows at all and i am using firefox there too. I have DSL if that might help solve the problem. But only a small collection of websites accually work. Please help!

---

### Post by DJ Scribblinni on 2006-07-02
I would take a look at the DNS servers list and make sure there are some there.  This would be accomplished in the Network Settings dialog.  That would be guess number 1.

---

### Post by vulcan123 on 2006-07-02
yah, i have 2 DNS servers in the list. I have no idea what the problem is... :cry:

---

### Post by kripkenstein on 2006-07-02
Ok, to start finding out what the problem is, run these commands, and tell us what you get:

```

ping 66.102.9.104

host google.com

```

---

### Post by vulcan123 on 2006-07-02
ok, i assume you wanted me to enter that code into the terminal.
for ping 66.102.9.104 i got:




PING 66.102.9.104 (66.102.9.104) 56(84) bytes of data.
64 bytes from 66.102.9.104: icmp_seq=1 ttl=236 time=213 ms
64 bytes from 66.102.9.104: icmp_seq=2 ttl=236 time=213 ms
64 bytes from 66.102.9.104: icmp_seq=3 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=4 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=5 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=6 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=7 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=8 ttl=236 time=211 ms
64 bytes from 66.102.9.104: icmp_seq=9 ttl=236 time=211 ms
64 bytes from 66.102.9.104: icmp_seq=10 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=11 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=12 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=13 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=14 ttl=236 time=211 ms
64 bytes from 66.102.9.104: icmp_seq=15 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=16 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=17 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=18 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=19 ttl=236 time=213 ms
64 bytes from 66.102.9.104: icmp_seq=20 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=21 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=22 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=23 ttl=236 time=224 ms
64 bytes from 66.102.9.104: icmp_seq=24 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=25 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=26 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=27 ttl=236 time=213 ms
64 bytes from 66.102.9.104: icmp_seq=28 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=29 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=30 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=31 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=32 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=33 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=34 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=35 ttl=236 time=213 ms
64 bytes from 66.102.9.104: icmp_seq=36 ttl=236 time=211 ms
64 bytes from 66.102.9.104: icmp_seq=37 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=38 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=39 ttl=236 time=211 ms
64 bytes from 66.102.9.104: icmp_seq=40 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=41 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=42 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=43 ttl=236 time=211 ms
64 bytes from 66.102.9.104: icmp_seq=44 ttl=236 time=213 ms
64 bytes from 66.102.9.104: icmp_seq=45 ttl=236 time=211 ms
64 bytes from 66.102.9.104: icmp_seq=46 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=47 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=48 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=49 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=50 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=51 ttl=236 time=213 ms
64 bytes from 66.102.9.104: icmp_seq=52 ttl=236 time=216 ms
64 bytes from 66.102.9.104: icmp_seq=53 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=54 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=55 ttl=236 time=213 ms
64 bytes from 66.102.9.104: icmp_seq=56 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=57 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=58 ttl=236 time=211 ms
64 bytes from 66.102.9.104: icmp_seq=59 ttl=236 time=213 ms
64 bytes from 66.102.9.104: icmp_seq=60 ttl=236 time=211 ms
64 bytes from 66.102.9.104: icmp_seq=61 ttl=236 time=213 ms
64 bytes from 66.102.9.104: icmp_seq=62 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=63 ttl=236 time=213 ms
64 bytes from 66.102.9.104: icmp_seq=64 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=65 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=66 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=67 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=68 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=69 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=70 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=71 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=72 ttl=236 time=213 ms
64 bytes from 66.102.9.104: icmp_seq=73 ttl=236 time=211 ms
64 bytes from 66.102.9.104: icmp_seq=74 ttl=236 time=211 ms
64 bytes from 66.102.9.104: icmp_seq=75 ttl=236 time=211 ms
64 bytes from 66.102.9.104: icmp_seq=76 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=77 ttl=236 time=211 ms
64 bytes from 66.102.9.104: icmp_seq=78 ttl=236 time=211 ms
64 bytes from 66.102.9.104: icmp_seq=79 ttl=236 time=213 ms
64 bytes from 66.102.9.104: icmp_seq=80 ttl=236 time=211 ms
64 bytes from 66.102.9.104: icmp_seq=81 ttl=236 time=210 ms
64 bytes from 66.102.9.104: icmp_seq=82 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=83 ttl=236 time=213 ms
64 bytes from 66.102.9.104: icmp_seq=84 ttl=236 time=211 ms
64 bytes from 66.102.9.104: icmp_seq=85 ttl=236 time=213 ms
64 bytes from 66.102.9.104: icmp_seq=86 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=87 ttl=236 time=211 ms
64 bytes from 66.102.9.104: icmp_seq=88 ttl=236 time=211 ms
64 bytes from 66.102.9.104: icmp_seq=89 ttl=236 time=211 ms
64 bytes from 66.102.9.104: icmp_seq=90 ttl=236 time=212 ms
64 bytes from 66.102.9.104: icmp_seq=91 ttl=236 time=210 ms

--- 66.102.9.104 ping statistics ---
91 packets transmitted, 91 received, 0% packet loss, time 90345ms
rtt min/avg/max/mdev = 210.133/211.924/224.792/1.798 ms






and for host google.com i got:





google.com has address 72.14.207.99
google.com has address 64.233.167.99
google.com has address 64.233.187.99
;; Warning: Message parser reports malformed message packet.
google.com mail is handled by 10 smtp1.google.com.
google.com mail is handled by 10 smtp2.google.com.
google.com mail is handled by 10 smtp3.google.com.
google.com mail is handled by 10 smtp4.google.com.

---

### Post by FLeiXiuS on 2006-07-02
Post the output of 

```
$ sudo ifconfig
```

---

### Post by vulcan123 on 2006-07-02
when i entered $ sudo ifconfig i got:

bash: $: command not found

---

### Post by Thund3rstruck on 2006-07-02
The $ symbol indicates a non-admin account. just enter
```

sudo ifconfig

```

---

### Post by vulcan123 on 2006-07-02
when i entered  the code it asked for my password and what i got when i entered it was this:


eth0      Link encap:Ethernet  HWaddr 00:12:3F:D4:B1:A4
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fed4:b1a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:602889 (588.7 KiB)  TX bytes:135871 (132.6 KiB)
          Interrupt:169

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

---

### Post by FLeiXiuS on 2006-07-03
On windows could you open a command prompt and enter *ping 66.102.9.104*.   I want to verify that linux is infact the problem.  

Afterwards on linux could you do the same.  *ping -c 4 66.102.9.104 *

---

### Post by vulcan123 on 2006-07-15
I got this when i entered 66.102.9.104 in ms-dos




Pinging 66.102.9.104 with 32 bytes of data:

Reply from 66.102.9.104: bytes=32 time=238ms TTL=234
Reply from 66.102.9.104: bytes=32 time=232ms TTL=234
Reply from 66.102.9.104: bytes=32 time=233ms TTL=234
Reply from 66.102.9.104: bytes=32 time=232ms TTL=234

Ping statistics for 66.102.9.104:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 232ms, Maximum = 238ms, Average = 233ms

---

### Post by blitzd on 2006-07-15
Disabling IPV6 may help if you don't require it for anything, there is a How-To thread regarding that here:

[http://www.ubuntuforums.org/showthread.php?t=87798&page=&highlight=disable+ipv6](http://www.ubuntuforums.org/showthread.php?t=87798&page=&highlight=disable+ipv6)

If you are using Dapper then this particular post is what did the trick for me:

[http://www.ubuntuforums.org/showpost.php?p=1112537&postcount=50](http://www.ubuntuforums.org/showpost.php?p=1112537&postcount=50)

I found with IPv6 enabled the initial DNS lookups in many applications (Firefox especially) seemed to take a long time. After disabling it everything was much more responsive.

If you're connected through a home gateway/router then it's unlikely that you need IPv6.

---

