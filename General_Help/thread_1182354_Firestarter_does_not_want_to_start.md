---
title: "Firestarter does not want to start"
date: 2009-06-08
forum: General Help
---

### Post by Bigtime_Scrub on 2009-06-08
I just installed Firestarter.

```
sudo apt-get install firestarter
```

I went through the run wizard where it asks for my connection and it recognized eth1. Everything was going fine until I clicked save at the end and I got this error message:

"Firestarter rejects to start reporting that eth1 interface is not ready." Really? This interface is ready and working very well. 

It won't work from the command line either as I tried:

```
sudo firestarter start
External network device eth1 is not ready. Aborting..
```
and
```
 sudo firestarter show 
External network device eth1 is not ready. Aborting..
```

I know damn well eth1 is working because I am using wireless right now to make this post. 

Just for giggles though I ran 
```
gary@gary-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:b0:91:e6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:23:4d:4d:bc:47  
          inet addr:192.168.1.82  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4dff:fe4d:bc47/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54761 errors:0 dropped:0 overruns:0 frame:57134
          TX packets:38153 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45723772 (45.7 MB)  TX bytes:4566979 (4.5 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:442 errors:0 dropped:0 overruns:0 frame:0
          TX packets:442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27396 (27.3 KB)  TX bytes:27396 (27.3 KB)

gary@gary-laptop:~$ 

```

I have no idea why firestarter is not cooperating.

---

### Post by 123456789123456789123456 on 2009-06-08
try going through add/remove, remove firestarter, and then install it thorugh add/remove.  It is possible that apt installer did not configure the program correctly, though I doubt it.  If that does not work, the only thing I can think of, is possible the firestarter program may be 32bit and is not fully compatable with the 64bit OS version of Ubuntu.

---

### Post by lovinglinux on 2009-06-08
Don't bother with Firestarter. Install gufw instead, which is the frontend for UFW (Uncomplicated Firewall).

```
sudo apt-get install gufw
```

Firestarter is not recommended anymore.

**Quick links to similar threads:** [Google Site Search](http://www.google.com/search?q=ufw firestarter gufw+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0) | [Forum Search](http://ubuntuforums.org/search.php?do=process&query=ufw firestarter gufw)

---

### Post by Bigtime_Scrub on 2009-06-08
I tried it with add/remove. I did
```
sudo apt-get purge firestarter
```
and then to make sure
```
sudo apt-get autoremove
```

I installed firestarter with add/remove. This time the error message did not show up but eth1 on Firestarter shows no activity and under Events there is no log. There should be lots of hits in that log. Which tells me it still isn't working.

So, after a little more research I am inclined to think either it is a bug
[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/230166](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/230166)

OR

You are right, and it does not support 64-bit.


So....I still would like a firewall. Any suggestions?

---

### Post by Bigtime_Scrub on 2009-06-08
> **lovinglinux said:**
> Don't bother with Firestarter. Install gufw instead, which is the frontend for UFW (Uncomplicated Firewall).

```
sudo apt-get install gufw
```

Firestarter is not recommended anymore.

**Quick links to similar threads:** [Google Site Search](http://www.google.com/search?q=ufw firestarter gufw+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0) | [Forum Search](http://ubuntuforums.org/search.php?do=process&query=ufw firestarter gufw)

Cool! Thanks.

---

