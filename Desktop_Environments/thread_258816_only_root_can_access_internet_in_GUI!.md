---
title: "only root can access internet in GUI?!"
date: 2006-09-16
forum: Desktop Environments
---

### Post by mojoman on 2006-09-16
Hi,

I have a really weird problem. I recently installed Dapper on a new computer.

As root, I can get on the web, no problems at all, but on my regular account I can't connect with the browser or mailclient. I can, however, ping google from the terminal so there is some connection. It seem to be connected to privilige since, as far as I know, I have no firewall up and running. :confused: 

Does anyone out there hav a solution?

Thanks in advance :D ,
Mojoman

---

### Post by aysiu on 2006-09-16
What groups does your user belong to? Can you post the output of this command? ```
groups
```

---

### Post by mojoman on 2006-09-16
> **aysiu said:**
> What groups does your user belong to? Can you post the output of this command? ```
groups
```


```
mojoman adm dialout fax cdrom floppy tape audio dip video plugdev lpadmin scanner admin
```

I've pinpointed the problem somewhat. If I'm connected to a server (I have a server at home and since I've just installed the desktop I connect through "Places>Connect to server" on the menu) and when I'm connected to this I can't use Internet through other programs, or so it seems (but I can ping other sites). As if the network connection can only handle on thing ... ?

ifconfig gives the following:
```
eth1      Link encap:Ethernet  HWaddr 00:16:17:70:16:61
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe70:1661/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:787576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:409156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1186885932 (1.1 GiB)  TX bytes:27733332 (26.4 MiB)
          Interrupt:50 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0eth1      Link encap:Ethernet  HWaddr 00:16:17:70:16:61
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe70:1661/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:787576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:409156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1186885932 (1.1 GiB)  TX bytes:27733332 (26.4 MiB)
          Interrupt:50 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:872 (872.0 b)  TX bytes:872 (872.0 b)
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:872 (872.0 b)  TX bytes:872 (872.0 b)
```

Any ideas on this?

Thanks for the help!
/mojoman

---

### Post by aysiu on 2006-09-16
Well, you appear to be in the right groups. Unfortunately, internet troubleshooting isn't my strong suit (Ubuntu has always autodetected my connection).

One thing you could try, though, is to create a new user with the same groups and see if that new test user can connect or not.

If the new test user can, something's wrong with your original user's configuration files.

If the new test user cannot, something may be wrong with the permissions on whatever program's trying to connect to the internet.

---

### Post by mojoman on 2006-09-16
> **aysiu said:**
> Well, you appear to be in the right groups. Unfortunately, internet troubleshooting isn't my strong suit (Ubuntu has always autodetected my connection).

One thing you could try, though, is to create a new user with the same groups and see if that new test user can connect or not.

If the new test user can, something's wrong with your original user's configuration files.

If the new test user cannot, something may be wrong with the permissions on whatever program's trying to connect to the internet.

Thanks for the tip. I'll give it a go but I think it's be something else because the connection seem to come and go for no apperent reason at all. However, I can always ping so even when I can't use the browser I do have some form of connection.

btw, I had some good help from your site on the dual boot issue, keep up the good work. :D 

/mojoman

---

### Post by whizbaby on 2006-09-16
Have you tried browsing in terminal?
**w3m *[www.google.com](www.google.com)***
If you can browse with that your problem is a browser (firefox?) problem.

---

