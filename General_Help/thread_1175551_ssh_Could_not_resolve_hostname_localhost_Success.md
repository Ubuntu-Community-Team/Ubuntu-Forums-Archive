---
title: "ssh: Could not resolve hostname localhost: Success"
date: 2009-06-01
forum: General Help
---

### Post by flopin on 2009-06-01
Hello,
i have a problem with Kubuntu 9.04. When i try to run

ssh localhost
or
ssh mymachinename

i get an error

ssh: Could not resolve hostname localhost: Success

My /etc/hosts file has both records

127.0.0.1 localhost
127.0.0.1 mymachinename

In /etc/nsswitch.conf i have (default configuration)
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

When i run ssh 127.0.0.1, everything goes well, unfortunately i am using aplication which needs to run "ssh mymachinename" and i am unable to change it.

Also running ping localhost/mymachinename or resolveip localhost/mymachinename runs exactly as it should be, it seems that only application having this problem is ssh.

---

### Post by flopin on 2009-06-01
Update on my investigation :

it seems that "ssh localhost" tries to connect to localhost via IPv6

adding

AddressFamily inet

in vim /etc/ssh/ssh_config forces ssh client to use IPv4 and both ssh localhost and ssh mymachinename starts to work. My /etc/hosts also contains lines

::1 ip6-mymachinename
::1 ip6-localhost

but, what exactly the "ip6-" prefix means a how does it work, and why it does not work for ssh?

---

### Post by Iowan on 2009-06-01
Although it may work that way, "standard" configuration is to leave 127.0.0.1 as localhost, and make 127.0.1.1 mymachinename.

---

### Post by capscrew on 2009-06-01
fopin,

Out of curiosity: are you trying to ssh to another machine, or to yourself?  If you are trying to ssh to the host you are on, then 2 questions come to mind.  First, why would you use a remote login routine (ssh) to log in when you can just open a terminal?  Second, what do you get when you to this?```
ping localhost
```

If you are trying to ssh to another machine then local host is not the name you want to use.  The name localhost always refers to the host you are at.  But I bet you knew that already.  :-)

As far as using 127.0.1.1 or 127.0.0.1; it doesn't matter as in always refers to the loopback interface (internal).  All 127.0.0.0 is loopback.

---

### Post by flopin on 2009-06-02
Yes, strange, i am trying to ssh the host i am on. The thing is, that i have to use another application - mpirun, which connects to multiple hosts (including localhost) via ssh and runs applications in parallel on them and i am unable to configure mpirun to run "ssh 127.0.0.1" instead of "ssh localhost". But, anyway, i think that ssh localhost (although it seems useless and for nothing) should work.

ping localhost:

PING mymachinename (127.0.0.1) 56(84) bytes of data.
64 bytes from mymachinename (127.0.0.1): icmp_seq=1 ttl=64 time=0.044 ms
64 bytes from mymachinename (127.0.0.1): icmp_seq=2 ttl=64 time=0.041 ms

---

### Post by capscrew on 2009-06-02
I think you have misunderstood instructions for configuring mpirun.  The application wants to be able to communicate with the other hosts in the network.  It therefore needs an Ethernet interface that is in the LAN.  You need to configure it to use the LAN address.  Typically this will be 192.168.n.n on eth0.

Post your results of```
ifconfig
```

---

### Post by flopin on 2009-06-02
ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:1c:23:56:1e:07
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe56:1e07/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:1288000 (1.2 MB)  TX bytes:301890 (301.8 KB)
          Memory:febe0000-fec00000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1344 (1.3 KB)  TX bytes:1344 (1.3 KB)

```

Yes, that is probably right i misunderstood mpirun configuration (i do not use it regulary, it is just for my school project :( ). Nevertheless, the problem is not in the mpirun itself. The main problem is, that if i run JUST command "ssh localhost", it ends up with

ssh: Could not resolve hostname localhost: Success

---

### Post by capscrew on 2009-06-02
> Yes, that is probably right i misunderstood mpirun configuration (i do not use it regulary, it is just for my school project ). Nevertheless, the problem is not in the mpirun itself. The main problem is, that if i run JUST command "ssh localhost", it ends up with

ssh: Could not resolve hostname localhost: Success

So at least we agree that mpirun should use 192.168.1.100.

Do you have a host named mymachinename?  My host is named malibu (as in the beach).

Without seeing your /etc/hosts file and not really understanding  what you have setup, I appears the hosts file does work.  So lets try this in the /etc/hosts file```
127.0.0.1 localhost 
192.168.1. 100 mymachinename
```

Now we have named the loopback: localhost (and indeed it is an appropriate name) and the eth0 interface mymachinename.

Now try the ```
ssh localhost
``` and ```
ping mymachinename.
```

You should be successful on both.

---

### Post by orrie on 2009-12-08
Sorry for the bump.

I just had this problem also.

It took a while before I found the problem.
My problem was that I've been tampering with /etc/nsswitch.conf to stop Audacious to crash (I think it was Audacious).

The old file had this:
```

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```

And the new (the "solution" for the crash-problem):
```

hosts:          wins files dns mdns

```

Now I have changed back to the old file and now I can ssh to an host without any problems again.
Just run an *sudo /etc/init.d/networking restart* to restart the network.

---

