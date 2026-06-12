---
title: "Eth0 network problem."
date: 2005-02-08
forum: Desktop Environments
---

### Post by ibs on 2005-02-08
Yesterday i decided to update all the packages using Synaptic. And this morning i was unable to connect to the internet. I tried to set up the ethernet interface again but nothing worked. I think this may be because of the update i did on the system. I don't know what package could be causing it.  What can i do?

---

### Post by anomie on 2005-02-08
What output does the ```
ifconfig
``` command give you?

---

### Post by drasko on 2005-02-08
Hi. 
I had a simmilar problem, an I suspected on proxy firewall i have on my work place, though I wrote the http proxy port in Synaptic. Anyway, when I tried it at home on Progeny Debian 2.0, it also didn't work (and I'm not firewalled there). I tried a lot of things, like removing Synaptic and installing some older version, suspecting a bug in release. Finnaly I found the solution - you have to build it from the source. So, write in console:

#apt-get source Synptic

and after that

#apt-get build-dep Synaptic

which will install all packages needed for compiling and buildin Synaptic from the source. After that compile the source and install it. Now it should be ok.

(Btw, it may not apear on the lounch bar, and you'll have to add it manually, but the binnary will  be installed, so run synaptic from the root console).

Drasko

---

### Post by ibs on 2005-02-09
hmm, i can't even use apt-get or any other program that needs an internet connection.

I will try to execute ifconfig next time i boot into Ubuntu.

---

### Post by alastair on 2005-02-09
This is what you should report - output of :

sudo ifconfig -a
route -n

and a short description of what your internet connection is (network layout).

---

### Post by ibs on 2005-02-10
Here is my output of sudo ifconfig -a and route -n:

```

ibs@ubuntu:~ $ sudo ifconfig -a
Password:
eth0      Link encap:Ethernet  HWaddr 00:08:A1:25:9F:C7
          inet6 addr: fe80::208:a1ff:fe25:9fc7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1889 (1.8 KiB)  TX bytes:2088 (2.0 KiB)
          Interrupt:11 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8640 (8.4 KiB)  TX bytes:8640 (8.4 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ibs@ubuntu:~ $

```

```

ibs@ubuntu:~ $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
ibs@ubuntu:~ $

```

I connect to the internet through an Alcatel SpeedTouch 570 router that is connected to my computer, it works as it should when i boot into my ugly windows system so there is something in Ubuntu that is causing the problem. As you can see from the output of ifconfig i have no IP address assigned, very strange.

---

### Post by krojc on 2005-02-10
Oh, goody... I'm not the only one.
Using Hoary + universe, did an upgrade which went OK, at next boot (five minutes later, since I also updated linux-image) no network.

Tray netmonitor reports a lot of activity from the net, but no net visible. Settings in network stayed the same. I have no idea which packages were installed, but there were quite a few.

---

### Post by drasko on 2005-02-10
ok, what happens when you try to configure net manually, using ifconfig command. Or what is written in /etc/network/interfaces - that should be resad at the boottime, and writen to you after ifconfig command...

---

### Post by alastair on 2005-02-10
OK - so the Alcatel SpeedTouch 570 is a router connected via ethernet/LAN - not a speedtouch USB modem? That should be good.

For some reason, no IP address and route is getting set up for you - the file that details these settings is :

/etc/network/interfaces

What is in there?

If you know your "network" (or what your IP used to be and the IP of your router) we can set this manually.

Assuming your computer has eth0 IP 192.168.0.10 (say) and your DSL router is 192.168.0.1, try :

sudo ifconfig eth0 192.168.0.10 netmask 255.255.255.0

Check : ifconfig eth0

sudo route add default gw 192.168.0.1

Check : route -n

Anything? Anything printed out in /var/log/syslog?

It is sometimes a good idea to have another shell open and "tail" the log file as you do things. You can see any errors or messages as they appear i.e. in another shell :

sudo tail -f /var/log/syslog

---

### Post by krojc on 2005-02-10
Before reading your mail I reinstalled linux image. This time network works. I have no idea what happened, but all the settings on my box looked OK and ifconfig and route -n gave correct settings. 

Thanks.

---

### Post by ibs on 2005-02-18
OK i could not fix it when i was in Warty.
Now I decided to download the new Hoary ISO image. I installed it and everything went fine. But now i can't connect to the Internet either. This is an completely fresh installation and i can't figure out what's going on.  What can i do?

Here is how my /etc/network/interfaces looks like:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

auto eth0

```

---

