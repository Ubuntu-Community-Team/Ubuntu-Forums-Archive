---
title: "Web browsers won't connect to the internet"
date: 2023-07-12
forum: Desktop Environments
---

### Post by John_Carver on 2023-07-12
[SIZE=3]Ubuntu Jammy 22.04.2 LTS will not connect to the internet with either Chromium or Firefox
1000mps current speed
Has worked without a problem but not now
Gmail connects without a problem--not true scratch it
[/SIZE]

---

### Post by #&amp;thj^% on 2023-07-12
Can you show us this:
```
ls -al /etc/resolv.conf
```
Also have you tried to "ping 8.8.8.8"
```
ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=115 time=55.9 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=115 time=59.6 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=115 time=52.0 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=115 time=56.7 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=115 time=54.6 ms
64 bytes from 8.8.8.8: icmp_seq=6 ttl=115 time=64.6 ms
^C
--- 8.8.8.8 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5009ms
rtt min/avg/max/mdev = 51.950/57.226/64.647/4.036 ms

```

---

### Post by John_Carver on 2023-07-12
I get no feedback on the resolve command except it repeats part of it.  Can't copy it to my Mac
The 8.8.8.8 produces zero

---

### Post by John_Carver on 2023-07-12
A side bar to this  this cannot find the scanner
Brother MFC 7460 DN 
Never had that before on other versions 
I replaced the scanner file from Brother but didn't work either

---

### Post by yancek on 2023-07-13
If the network worked before, did you make any changes just prior to this problem?  If so, what changes or updates?

You should get some output with the ping command.  If you are not connected to the internet it would show 100% packet loss.  Did you run the exact command shown in post 2?  Can you try to ping your router?  What happens when you do?

---

### Post by ActionParsnip on 2023-07-13
Do applications like apt run OK? Non-web browser applications. Do you use a proxy for web access? Are you connected to a VPN when the issue occurs?

---

### Post by John_Carver on 2023-07-13
[SIZE=3]running apt works
no proxy
ping router works
I have a VPN 
Shut it down and makes no difference
I also have Ubuntu 18.04.6 LTS where everything works
[/SIZE][SIZE=3][/SIZE]

---

