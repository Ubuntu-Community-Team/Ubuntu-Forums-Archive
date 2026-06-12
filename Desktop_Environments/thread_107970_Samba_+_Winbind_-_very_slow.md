---
title: "Samba + Winbind - very slow"
date: 2005-12-24
forum: Desktop Environments
---

### Post by hornett on 2005-12-24
Hello!

I'm running Breezy on two machines on my network (named d600 and hive). I need to be able to reference them by hostname, so I use WinBind (as per [this thread]("http://ubuntuforums.org/showthread.php?t=88206")). 

The problem is that pinging the machines by their hostnames is incredibly slow. 

[FONT="Courier New"]retro@hive:~$ time ping d600 -c 1
PING d600 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=64 time=0.164 ms

--- d600 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.164/0.164/0.164/0.000 ms

**real    0m20.322s**
user    0m0.044s
sys     0m0.006s
[/FONT]

If I ping the machines by their IP address, all is well.

Also, nmblookup returns the IP address from the given name immediately, as does the wbinfo -n command.

Anybody have any idea what could be causing this huge delay? 

Thanks :)

---

