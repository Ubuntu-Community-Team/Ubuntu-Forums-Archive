---
title: "Name resolution"
date: 2006-01-17
forum: Desktop Environments
---

### Post by qferret on 2006-01-17
When I try to access anything on my LAN by name it fails. How do I turn on NetBIOS resolution? I don't have THAT many devices, but it still gets interesting sometimes with DHCP...

---

### Post by Azion on 2006-01-17
How do you mean "LAN by name"?

---

### Post by qferret on 2006-01-17
user@ubuntu:~$ ping computerB
ping: unknown host computerB

user@ubuntu:~$ ping 192.168.0.1
PING 192.168.0.4 (192.168.0.4) 56(84) bytes of data.
64 bytes from 192.168.0.4: icmp_seq=1 ttl=255 time=0.947 ms
64 bytes from 192.168.0.4: icmp_seq=2 ttl=255 time=0.846 ms

user@ubuntu:~$ ping [www.ubuntuforums.org](www.ubuntuforums.org)
PING [www.ubuntuforums.org](www.ubuntuforums.org) (64.21.33.9) 56(84) bytes of data.
64 bytes from wailuku.xlogicgroup.com (64.21.33.9): icmp_seq=1 ttl=52 time=105 ms
64 bytes from wailuku.xlogicgroup.com (64.21.33.9): icmp_seq=2 ttl=52 time=79.9 ms

DNS takes care of name resolution on WAN, but as it is my ISP's DNS server, it doesn't know what the machines in my house are called.....

---

### Post by dcstar on 2006-01-17
[QUOTE=qferret]user@ubuntu:~$ ping computerB
ping: unknown host computerB

user@ubuntu:~$ ping 192.168.0.1
PING 192.168.0.4 (192.168.0.4) 56(84) bytes of data.
64 bytes from 192.168.0.4: icmp_seq=1 ttl=255 time=0.947 ms
64 bytes from 192.168.0.4: icmp_seq=2 ttl=255 time=0.846 ms

user@ubuntu:~$ ping [www.ubuntuforums.org](www.ubuntuforums.org)
PING [www.ubuntuforums.org](www.ubuntuforums.org) (64.21.33.9) 56(84) bytes of data.
64 bytes from wailuku.xlogicgroup.com (64.21.33.9): icmp_seq=1 ttl=52 time=105 ms
64 bytes from wailuku.xlogicgroup.com (64.21.33.9): icmp_seq=2 ttl=52 time=79.9 ms

DNS takes care of name resolution on WAN, but as it is my ISP's DNS server, it doesn't know what the machines in my house are called.....[/QUOTE]
Then manually put those entries into your /etc/hosts file.

---

### Post by qferret on 2006-01-18
That'll work until the DHCP leases expire....  :)

---

### Post by nickmcg on 2006-01-18
I have the same problem:

Mainly Windoze machines, Netgear router.

I can browse the network from Ubuntu, and the computers appear by name, but there's no ip name resolution.

Additionally, the Ubuntu host name is not resolved on the netgear router, although the Win machines (and the wireless HP printer) are recognised. Ubuntu host is listed as 'UNKNOWN'

Editing the hosts file is only good as long as the DHCP addresses don't change!

Are these two oddities linked?

---

### Post by qferret on 2006-02-19
OK...what gives?

```

user@ubuntu:~$ net lookup pcxp
192.168.0.2

```

```

ubuntu:~$ ping pcxp
ping: unknown host pcxp

```

If I specifically tell Ubuntu to look up the address it can, but if I try to access the machine by name, it can't.....

Makes it kinda out of the question for implementation in anything but a home user environment unless it can "shout" to other nodes on the same subnet...

---

### Post by dcstar on 2006-02-20
[QUOTE=qferret]OK...what gives?

```

user@ubuntu:~$ net lookup pcxp
192.168.0.2

```

```

ubuntu:~$ ping pcxp
ping: unknown host pcxp

```

If I specifically tell Ubuntu to look up the address it can, but if I try to access the machine by name, it can't.....

Makes it kinda out of the question for implementation in anything but a home user environment unless it can "shout" to other nodes on the same subnet...[/QUOTE]
"net" uses whatever you have set in your smb.conf file:

[http://optics.ph.unimelb.edu.au/help/samba/smb.conf.5.html#nameresolveorder](http://optics.ph.unimelb.edu.au/help/samba/smb.conf.5.html#nameresolveorder)

These will only work for smb (Windows networking) connections, not DNS ones.

---

### Post by nickmcg on 2006-02-27
In the thread [http://www.ubuntuforums.org/showthread.php?t=135323](http://www.ubuntuforums.org/showthread.php?t=135323) 

dcstar pointed me to:

[http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

This fixed these problems for me.

Cheers

Nick

---

### Post by qferret on 2006-03-13
Thanks Much nickmcg :)

---

