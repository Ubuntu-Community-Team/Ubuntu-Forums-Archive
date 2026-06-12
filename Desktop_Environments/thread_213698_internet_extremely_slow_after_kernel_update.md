---
title: "internet extremely slow after kernel update"
date: 2006-07-11
forum: Desktop Environments
---

### Post by Thorndeux on 2006-07-11
hello everybody,

i'm running ubuntu 6.06 on my desktop. since today's kernel update (to 2.6.15-26-386) 'the internet' is extremely slow. i didn't have any problems before the update.
i'm using firefox 1.5.0.3. it seems to me that it takes long to connect to the site ('connecting to www.taz.de...' and 'waiting for www.taz.de...'), but once that is done the page loads relatively quickly (but a little bit slower than before). right now i'm donwloading the openoffice update via the update manager and that runs on normal speed (125kB/s), so it's not the connection. i checked the dns servers (read in another thread that they sometimes get deleted after reboot) but they are fine.

ideas?

cheerio, thorn

---

### Post by GFBurke on 2006-07-11
Commenting out IPV6 really helped out for me.

---

### Post by Thorndeux on 2006-07-11
Sounds good - where and how do i do that again?

---

### Post by Thorndeux on 2006-07-11
ok, this is where i found how to disable ipv6:
[http://doc.gwos.org/index.php/DisableIPV6]("http://doc.gwos.org/index.php/DisableIPV6")

unfortunately it didn't seem to have any effect (i did reboot). so if anyone has another idea i would be very grateful.

---

### Post by Thorndeux on 2006-07-12
Still no luck.

right now my hosts file lists:
192.168.1.1
217.237.149.225
217.237.151.97

ping times are fine for all three of them:

```
thorn@ubunthorn:~$ ping -c 3 217.237.149.225
PING 217.237.149.225 (217.237.149.225) 56(84) bytes of data.
64 bytes from 217.237.149.225: icmp_seq=1 ttl=249 time=52.4 ms
64 bytes from 217.237.149.225: icmp_seq=2 ttl=249 time=52.4 ms
64 bytes from 217.237.149.225: icmp_seq=3 ttl=249 time=52.6 ms

--- 217.237.149.225 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2006ms
rtt min/avg/max/mdev = 52.429/52.514/52.633/0.086 ms

thorn@ubunthorn:~$ ping -c 3 217.237.151.97
PING 217.237.151.97 (217.237.151.97) 56(84) bytes of data.
64 bytes from 217.237.151.97: icmp_seq=1 ttl=250 time=49.9 ms
64 bytes from 217.237.151.97: icmp_seq=2 ttl=250 time=51.5 ms
64 bytes from 217.237.151.97: icmp_seq=3 ttl=250 time=51.6 ms

--- 217.237.151.97 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2007ms
rtt min/avg/max/mdev = 49.969/51.054/51.659/0.768 ms

thorn@ubunthorn:~$ ping -c 3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=0.322 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=0.305 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=0.307 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.305/0.311/0.322/0.016 ms
```

however, when i ping a url, it's much slower:
```

thorn@ubunthorn:~$ ping -c 3 www.taz.de
PING www.taz.de (212.91.251.182) 56(84) bytes of data.
64 bytes from www.taz.eu (212.91.251.182): icmp_seq=1 ttl=58 time=466 ms
64 bytes from www.taz.de (212.91.251.182): icmp_seq=2 ttl=58 time=57.0 ms
64 bytes from www.taz.de (212.91.251.182): icmp_seq=3 ttl=58 time=783 ms

--- www.taz.de ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10990ms
rtt min/avg/max/mdev = 57.025/435.548/783.042/297.206 ms

```

note the total time of over 10 seconds. i had between 15 and 25 seconds for many pages - even some timeouts.
it always takes longest the first time i access a page, e.g. the new york times homepage. if i want to read an article then, it loads quickly. that's why i thought it might be connected to the dns servers.

i'm puzzled.

---

### Post by philippe_carlo on 2006-07-12
From your postings below, it seems like the problem could be with [www.taz.de](www.taz.de). Here is what I get from pinging google.com (a good reference):

PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from 64.233.187.99: icmp_seq=1 ttl=237 time=103 ms
64 bytes from 64.233.187.99: icmp_seq=2 ttl=237 time=104 ms
64 bytes from 64.233.187.99: icmp_seq=3 ttl=237 time=103 ms

Do you get slower replies?

---

### Post by Thorndeux on 2006-07-12
> **philippe_carlo said:**
> From your postings below, it seems like the problem could be with [www.taz.de](www.taz.de). Here is what I get from pinging google.com (a good reference):

PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from 64.233.187.99: icmp_seq=1 ttl=237 time=103 ms
64 bytes from 64.233.187.99: icmp_seq=2 ttl=237 time=104 ms
64 bytes from 64.233.187.99: icmp_seq=3 ttl=237 time=103 ms

Do you get slower replies?

no, right now i even get quicker replies, but that's only because i visited the site already. after reboot it takes ages to load google for the first time. i've encountered the problem for all web pages, [www.taz.de](www.taz.de) was only an example.

---

### Post by philippe_carlo on 2006-07-12
But then it _does_ sound like a DNS lookup problem to me.

---

### Post by Thorndeux on 2006-07-12
> **philippe_carlo said:**
> But then it _does_ sound like a DNS lookup problem to me.

i now rebooted and the speed is fine. i might BE a dns problem, because now my hosts file doesn't list the router's ip anymore.

i keep my fingers crossed that it stays like that now.

thanks for your help, though :p

---

