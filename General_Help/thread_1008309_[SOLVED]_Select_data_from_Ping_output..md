---
title: "[SOLVED] Select data from Ping output."
date: 2008-12-11
forum: General Help
---

### Post by ajcham on 2008-12-11
Hi guys.

I was wondering what would be the best way to extract selected data from a Ping output?  I'm trying to extract just the average response time from the final line:

```
6 packets transmitted, 6 received, 0% packet loss, time 5021ms
rtt min/avg/max/mdev = 30.655/31.406/32.115/0.499 ms

```

At present, I am using the head and tail commands to pull '31.4' from the above output.  The downside to this solution is that it is only useful while pings remain under 100ms.

---

### Post by meindian523 on 2008-12-11
```
easwarh@linuxr0cks:~$ ping -c5 127.0.0.1|grep 5
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.010 ms
5 packets transmitted, 5 received, 0% packet loss, time 3997ms
easwarh@linuxr0cks:~$ 

```But this would work when you define how many packets you want to ping with.

or in general
```

easwarh@linuxr0cks:~$ ping -c5 127.0.0.1|grep rtt
rtt min/avg/max/mdev = 0.016/0.034/0.045/0.012 ms
easwarh@linuxr0cks:~$ 

```

:)

---

### Post by meindian523 on 2008-12-11
Maybe a longer pipe would be better.But I'm out of ideas as to what you would grep for.

---

### Post by ajcham on 2008-12-11
> But I'm out of ideas as to what you would grep for.
Yeah, that's what's puzzling me too.

As I said, at the moment I'm using a combination of head and tail:
```
$ ping -c 6 ubuntuforums.org | tail -c 23 | head -c 4
28.9
```

The problem being this only works if the character count of the final line is exactly right, which it would not be if I get a ping above 100ms.

---

### Post by Wayne_V on 2008-12-11
You want *just* the average rtt?  

$ ping -c5 127.0.0.1 | grep rtt | cut -d"/" -f5
0.031

---

### Post by meindian523 on 2008-12-11
Beautiful.

---

### Post by ajcham on 2008-12-11
That's fantastic Wayne_V, thanks.

---

