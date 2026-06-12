---
title: "strange DNS rsolutions"
date: 2006-03-11
forum: Desktop Environments
---

### Post by stevea1210 on 2006-03-11
I'm having a strange issue with DNS name resolution from all of my ubuntu boxes.  The below is true for all three ubuntu boxes on my network.  None of the windows boxes have this issue.

Network: multiple XP and Ubuntu workstations
             servers: ms server 2k3 and ubuntu
            DNS and DHCP are handled by the MS 2k3 server

When I ping a workstation from one of the linux boxes, I get multiple name resolutions.  Please see below.
```
steve@mmm-fs:~$ ping big-daddy
PING big-daddy.SNPP.BURNS (192.168.0.101) 56(84) bytes of data.
64 bytes from big-daddy-xp.snpp.burns (192.168.0.101): icmp_seq=1 ttl=64 time=0.211 ms
64 bytes from laptop-emily.snpp.burns (192.168.0.101): icmp_seq=2 ttl=64 time=0.183 ms
64 bytes from laptop-ubuntu.snpp.burns (192.168.0.101): icmp_seq=3 ttl=64 time=0.160 ms
64 bytes from big-daddy.snpp.burns (192.168.0.101): icmp_seq=4 ttl=64 time=0.171 ms
64 bytes from big-daddy-xp.snpp.burns (192.168.0.101): icmp_seq=5 ttl=64 time=0.170 ms
64 bytes from laptop-emily.snpp.burns (192.168.0.101): icmp_seq=6 ttl=64 time=0.160 ms
64 bytes from laptop-ubuntu.snpp.burns (192.168.0.101): icmp_seq=7 ttl=64 time=0.205 ms
64 bytes from big-daddy.snpp.burns (192.168.0.101): icmp_seq=8 ttl=64 time=0.169 ms
64 bytes from big-daddy-xp.snpp.burns (192.168.0.101): icmp_seq=9 ttl=64 time=0.164 ms
64 bytes from laptop-emily.snpp.burns (192.168.0.101): icmp_seq=10 ttl=64 time=0.171 ms
64 bytes from laptop-ubuntu.snpp.burns (192.168.0.101): icmp_seq=11 ttl=64 time=0.176 ms
64 bytes from big-daddy.snpp.burns (192.168.0.101): icmp_seq=12 ttl=64 time=0.176 ms
64 bytes from big-daddy-xp.snpp.burns (192.168.0.101): icmp_seq=13 ttl=64 time=0.164 ms
64 bytes from laptop-emily.snpp.burns (192.168.0.101): icmp_seq=14 ttl=64 time=0.166 ms
64 bytes from laptop-ubuntu.snpp.burns (192.168.0.101): icmp_seq=15 ttl=64 time=0.174 ms
64 bytes from big-daddy.snpp.burns (192.168.0.101): icmp_seq=16 ttl=64 time=0.172 ms
64 bytes from big-daddy-xp.snpp.burns (192.168.0.101): icmp_seq=17 ttl=64 time=0.169 ms
64 bytes from laptop-emily.snpp.burns (192.168.0.101): icmp_seq=18 ttl=64 time=0.166 ms
64 bytes from laptop-ubuntu.snpp.burns (192.168.0.101): icmp_seq=19 ttl=64 time=0.159 ms
64 bytes from big-daddy.snpp.burns (192.168.0.101): icmp_seq=20 ttl=64 time=0.185 ms
64 bytes from big-daddy-xp.snpp.burns (192.168.0.101): icmp_seq=21 ttl=64 time=0.176 ms
64 bytes from laptop-emily.snpp.burns (192.168.0.101): icmp_seq=22 ttl=64 time=0.170 ms

--- big-daddy.SNPP.BURNS ping statistics ---
22 packets transmitted, 22 received, 0% packet loss, time 21017ms
rtt min/avg/max/mdev = 0.159/0.173/0.211/0.018 ms
steve@mmm-fs:~$

```

As you see, the IP 192.168.0.101 is returning 4 different pc names.  From windows, if I ping each of those pc's, they return the correct ip for that box.  At one time or another, I'm sure each of those pc's had that IP, but they don't anymore.  Where is that coming from, and how can I change it?  Another strange thins is that it doesn't effect ssh, or file browsing.  I always ssh into the correct box via unc name.  SInce this is only happening on the linux boxes, and the windows boxes aren't affected, I don't beleive there is any issue with my DNS server.

More info:I tried swapping the hosts line in the nsswitch.conf from {files dns} to {dns files}, but after restarting networking, it didn't change anything.  Here is my nsswitch.conf
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat winbind
group:          compat winbind
shadow:         compat

#hosts:          files dns
hosts:          dns files
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

and my resolv.conf
```
steve@laptop-ubuntu:~$ cat /etc/resolv.conf
search snpp.burns
nameserver 192.168.0.80

```


Any help would be appreciated :)

---

### Post by dcstar on 2006-03-12
[QUOTE=stevea1210]
......
and my resolv.conf
```
steve@laptop-ubuntu:~$ cat /etc/resolv.conf
search snpp.burns
nameserver 192.168.0.80

```


Any help would be appreciated :)[/QUOTE]
And exactly what is set in that DNS server for each of those systems?

Also do an ```
arp -a
``` on you Ubuntu systems

---

