---
title: "MySQL + hostname = access denied"
date: 2009-02-07
forum: General Help
---

### Post by annunaki2k2 on 2009-02-07
Summary: MySQL, on Ubuntu (Ibex here), seems to be pulling a hostname from nowhere, and so amarok is being denied access to my MySQL server.

Note: Other clients work perfectly and have done for years.

Set-up: I have a domain of annunaki2k2.co.uk, with a mysql server of starbug. My client ubuntu PC, called lister, is set to DHCP, and pulls back all relevant host/domain information, and for the most part just works:
```
russell@lister:~$ hostname
lister
russell@lister:~$ hostname -f
lister.annunaki2k2.co.uk
russell@lister:~$ dnsdomainname 
annunaki2k2.co.uk
russell@lister:~$ cat /etc/hosts
127.0.0.1	lister.annunaki2k2.co.uk lister localhost.localdomain localhost 
127.0.1.1	lister.annunaki2k2.co.uk lister localhost.localdomain localhost

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
russell@lister:~$ 

```

As you can see, the hostname+dhcp works fine. The server has a correctly working dhcpd + dynamic dns system, and so my dns setup also works fine. This is from my client machine:
```
russell@lister:~$ ping -c 1 starbug
PING starbug.annunaki2k2.co.uk (192.168.0.10) 56(84) bytes of data.
64 bytes from starbug.annunaki2k2.co.uk (192.168.0.10): icmp_seq=1 ttl=64 time=0.228 ms

--- starbug.annunaki2k2.co.uk ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.228/0.228/0.228/0.000 ms
russell@lister:~$ ping -c 1 lister
PING lister.annunaki2k2.co.uk (127.0.0.1) 56(84) bytes of data.
64 bytes from lister.annunaki2k2.co.uk (127.0.0.1): icmp_seq=1 ttl=64 time=0.045 ms

--- lister.annunaki2k2.co.uk ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.045/0.045/0.045/0.000 ms
russell@lister:~$ 

```

...and this is on the actual mysql server:
```
starbug ~ # ping -c1 starbug
PING starbug.annunaki2k2.co.uk (192.168.0.10) 56(84) bytes of data.
64 bytes from starbug.annunaki2k2.co.uk (192.168.0.10): icmp_seq=1 ttl=64 time=0.042 ms

--- starbug.annunaki2k2.co.uk ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.042/0.042/0.042/0.000 ms
starbug ~ # ping -c1 lister
PING lister.annunaki2k2.co.uk (192.168.0.26) 56(84) bytes of data.
64 bytes from lister.annunaki2k2.co.uk (192.168.0.26): icmp_seq=1 ttl=64 time=0.259 ms

--- lister.annunaki2k2.co.uk ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.259/0.259/0.259/0.000 ms
starbug ~ # 

```

Everything is well on the name resolution front, and in mysql I have the system set-up to allow access to the amarok database from client "lister.annunaki2k2.co.uk". Other clients are set-up the same way and work well.

However, MySQL insists on trying to connect using the hostname of "ubuntu.annunaki2k2.co.uk":
```
russell@lister:~$ mysql -uamarok -p -hstarbug
Enter password: 
ERROR 1130 (00000): Host 'ubuntu.annunaki2k2.co.uk' is not allowed to connect to this MySQL server

```

I have tried everything I can think of, but what should I do next? I seriously can't believe how dumb mysql is being with it's name resolution - where on earth is "ubuntu" set to a default hostname?

I appreciate ANYONES help or suggestions on this...

---

