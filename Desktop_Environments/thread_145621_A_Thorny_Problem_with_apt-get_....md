---
title: "A Thorny Problem with apt-get ..."
date: 2006-03-16
forum: Desktop Environments
---

### Post by bakert on 2006-03-16
If you can work this one out I will give you a special award.

Problem:

apt-get resolves all hostnames like security.ubuntu.com to 1.0.0.0 and thus doesn't work.

Other Factors:

0. It used to work fine pre D-Link router so I think it is probably to do with that.
1. The router does not support ipv6.
2. Firefox doesn't work unless I go into about:config and disable ipv6.  After that it is fine.
3. I have gone into /etc/modprobe.d/aliases and tried every combination of commenting out and replacing the ipv6 line.  And rebooting (over and over).  apt-get is still unhappy.
4. ping and Automatix and loads of other things are perfectly happy.  I don't /think/ anything except apt-get is broken.
5. This is on more than one machine (Ubuntu and Kubuntu).

PLEASE help me if you have any suggestions at all!  I can't bear all the entries in my /etc/hosts file to keep apt (kind of) working.

Thanks!

**EDIT: If I put my ISPs DNS details in /etc/resolv.conf then it works until resolv.conf is overwritten (every 5 mins or so).**

---

### Post by Ramses de Norre on 2006-03-16
what's the output of ifconfig?

---

### Post by nalmeth on 2006-03-16
ifconfig eth0 :)
> 
Not all ethernet cards are eth0 by default, like mine is ath0 by default (refering to the chipset).
True enough, be ifconfig on its own won't tell you anything

---

### Post by Ramses de Norre on 2006-03-16
Not all ethernet cards are eth0 by default, like mine is ath0 by default (refering to the chipset).

---

### Post by bakert on 2006-03-16
Output of ifconfig as requested.  eth1 is the wireless card.  Works fine, apart form as detailed above.  I also had this problem on my old laptop (since getting the new router, worked fine before that).

bakert@haskell:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:C6:E2:E8:31
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16

eth1      Link encap:Ethernet  HWaddr 00:13:CE:9A:74:56
          inet addr:192.168.1.17  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:18308141 (17.4 MiB)  TX bytes:643010 (627.9 KiB)
          Interrupt:21 Base address:0x2000 Memory:a8401000-a8401fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11501 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11501 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1043292 (1018.8 KiB)  TX bytes:1043292 (1018.8 KiB)

bakert@haskell:~$

---

### Post by bakert on 2006-03-16
Should also have said that if I put my ISPs DNS server in /etc/resolv.conf then everything works fine, until that file is overwritten with the router address again (about every 5 mins).

---

### Post by Ramses de Norre on 2006-03-16
Does it help when you turn off the ethernet card you're not using to browse the internet?
To do so: sudo ifdown eth* (get the right number for * ;))

For the DNS problem: try to add a line for your DNS servers to /etc/network/interfaces

---

### Post by bakert on 2006-03-16
Disabling eth0 (wired LAN) has no effect.

What do I need to put in /etc/network/interfaces ?  All the docs I can find say DNS goes in /etc/resolv.conf

Thanks for looking at this,

Tom

---

### Post by Azrael on 2006-03-16
[quote=bakert]
What do I need to put in /etc/network/interfaces ?  All the docs I can find say DNS goes in /etc/resolv.conf
[/quote]
I think you can edit /etc/dhcp3/dhclient.conf to have a manually designated nameserver overrule the one you get with your dhcp lease (see "man dhcp.conf" for mor info).

If that doesn't work you could try to put your ISP's nameserver in /etc/resolv.conf and then "sudo chmod -w /etc/resolv.conf" to make it non-writeable. Yeah, really ugly, but hell, maybe it does the job.

In any case it would be best if you could find out what's giving you the 10.0.0.0 address. Maybe some sniffing with ethereal will give you a hint?

Good luck.

---

### Post by bakert on 2006-03-17
Thanks I'll definitely try that as a workaround.

The address apt tries to use (for everything) 1.0.0.0 which I think just represents a total failure to find the address.  Because it is trying to use ipv6, I think.

Also, on boot my "bringing up the network interface" takes a long time (10 seconds+).  And people who disable ipv6 report that this then happens a lot faster.

So I definitely think the problem is that apt is using ipv6.  However, I've followed all the instructions I can find for disabling ipv6 and it still does the same.  Is there any way to check if I have successfully disabled ipv6?

Thanks,

Tom

---

### Post by bakert on 2006-04-02
I think I was mixing up two problems here.  I did have a problem with ipv6 not working with my router.  But the reason apt could not resolve domain names was to do with the nameserver being set by DHCP to be the router's address.

I found a fairly workable answer here (elithrar's post):

[http://ubuntuforums.org/showthread.php?t=141728&page=2](http://ubuntuforums.org/showthread.php?t=141728&page=2)

---

