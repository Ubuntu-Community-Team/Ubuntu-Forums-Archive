---
title: "Command line for new router, nameservers?"
date: 2006-04-25
forum: Desktop Environments
---

### Post by dgermann on 2006-04-25
Hi--

Just installed a router (never had one before), so the gateway and the nameservers have changed from what I had before. Got it all set up and working (but slow) in three Ubuntu 5.10 boxes running gnome.

The problem: I have a headless box not running gnome. What files do I need to change to be able to get Internet access on this machine?

I have edited /etc/resolv.conf and /etc/network/interfaces to include the new gateway and nameservers. But still apt-get update can connect to only some but not all servers it is looking for.

Any ideas what else I need to change?

Thanks!

---

### Post by jazzmuzik on 2006-04-25
/etc/hosts ?

Is a firewall blocking anything?

---

### Post by dgermann on 2006-04-25
jazzmuzik--

Thanks for the quick reply!

I don't see anything in /etc/hosts that relates to these nameservers or gateways.

I have not changed the firewall on this machine since the last time I ran apt-get update, so I doubt that is the issue. I have firestarter on it, and don't know enough about iptables to change anything manually, and would have to lug a monitor to it in another building to change it or check it out. ;) 

And the other machines are getting through to the Internet OK, so I doubt it is the firewall in the router.

I tried running apt-get update from the machine I am on now, and it ran without problems. The headless box on the other hand, has a lot of these errors:
```

Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz  Could not connect to us.archive.ubuntu.com:80 (85.133.25.8). - connect (101 Network is unreachable) [IP: 85.133.25.8 80]

```

Any other ideas?

Thanks, jazzmuzik!

---

### Post by jazzmuzik on 2006-04-25
It seems you have dns working because it resolved the ubuntu repository address.

Maybe the route is not right? 

netstat -r

ifconfig

tracepath (which seems to be a replacement for traceroute)

dig is a good tool for checking dns but that seems to be working. 

Try to log into your router and/or modem via Firefox and look around there for clues.

Sorry, I'm out of ideas.

---

### Post by jazzmuzik on 2006-04-26
How about Firestarter... look at the Policy tab. Something there might need to be set.

---

### Post by dgermann on 2006-04-26
jazzmuzik--

Thank you for your help.

Here's netstat -r:
```

root@bak:~ # netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
localnet        *               255.255.255.0   U         0 0          0 eth0
default         samba1          0.0.0.0         UG        0 0          0 eth0
root@bak:~ #

```

Should samba1 (the server) be all zeroes? If not, how/where do I change that?

```

root@bak:~ # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:11:C7:C4:A5
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: [[blanked]] Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:190859803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131811037 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1233473099 (1.1 GiB)  TX bytes:3967005489 (3.6 GiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8805 (8.5 KiB)  TX bytes:8805 (8.5 KiB)

root@bak:~ #

```

Not sure what I am reading here....

I doubt it's firestarter, since I ran an apt-get update a few weeks ago, with no problems, and no changes on that machine since.

Ahh, now maybe this is a clue:

```

root@bak:~ # tracepath 85.133.25.8:80
gethostbyname: Unknown host
root@bak:~ # tracepath 85.133.25.8
 1:  bak (192.168.0.106)                                    0.236ms pmtu 1500
 1:  samba1 (192.168.0.200)                                 0.738ms !N
     Resume: pmtu 1500
root@bak:~ #

```

Well, maybe not. The ipaddress for the server, samba1, is 192.168.0.200; it just is no longer the gateway (which is now 192.168.0.1). But why did this stop at the sever and not go out from there? And why did it go to the server first anyway? Shouldn't it have gone to the gateway instead? Is that a clue?

But look at this. From my desktop machine, I get this:
```

doug@doug2:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
localnet        *               255.255.255.0   U         0 0          0 eth0
YPBINDPROC_DOMAIN: Domain not bound
YPBINDPROC_DOMAIN: Domain not bound
default         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
doug@doug2:~$

```

(Someday I gotta get that YP stuff outta there!) but note that it goes for the gateway ip ...0.1, not the server ...0.200. So where do I fix that?

Maybe you are getting me somewhere on this!

Thanks for your help, jazzmuzik!

---

### Post by dgermann on 2006-04-28
Just a report.

I lugged the machine from building 1 to building A, hooked up a monitor and keyboard, etc., and ran X and update manager. All went relatively smoothly, if slowly, and even tracepath works now.

So what's it all mean? Just one of those things, I suspect.

Thanks for your help folks!

---

