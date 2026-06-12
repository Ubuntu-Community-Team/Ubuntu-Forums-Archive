---
title: "Internet Connection Problems"
date: 2006-07-02
forum: Desktop Environments
---

### Post by craz on 2006-07-02
Hi, I have a question about internet connectivity on Ubuntu 6.06.  I have a broadband connection that plugs into my computer through the ethernet port.  When I run the Ubuntu Live CD, the internet works fine without even requireing any settings to be changed.  The problem is with Ubuntu when I run it off the hard drive.  When I load up Ubuntu, the internet works fine for about 30 seconds, then it will not work any more.  No matter what settings I adjust, it will not work.  It will only start working for about 30 seconds if my computer is off for a while.  When I put the Live CD in again, it works fine - and the settings for the Live CD and the installed version are the same!  Does anybody know what is going on here?  I am very greatful for any help.

P.S. - Internet connection is DHCP.

---

### Post by craz on 2006-07-03
Does anybody know what I could do?

---

### Post by craz on 2006-07-03
Please, could somebody help me?

---

### Post by moffa on 2006-07-03
Is your broadband connection dsl or cable? If its dsl you probably need to setup the PPPoE.
Try manually entering the DNS information under System > Administration > Networking and on the DNS tab.
Also if you could type ifconfig in the terminal and c&p the output it might help as well.

---

### Post by craz on 2006-07-03
Hi, thanks for replying.  I have a DSL connection.  I have tried manual settings but no luck.  When I try to set up PPPoE with the live cd, it works fine.  But once I am actually setting it up the installed Ubuntu, it recognizes the connection but will not work after that.  I will try those config setting in the morning, as it is past 11:00 at night here.  In the mean time, does anybody know why the connection would work on the live cd but not the installed ubuntu, even with the same settings?  It works for just a few seconds then cuts out.  Weird!

---

### Post by craz on 2006-07-04
I am posting this now from the Live CD.

I cannot post the ifconfig from the installed version because I cannot acces the drive with the file on it because I cant get internet access on it...but here is what I have noticed.

This is the ifconfig from the live cd:

eth0      Link encap:Ethernet  HWaddr 00:80:AD:76:D4:FA
          inet addr:192.168.1.46  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::280:adff:fe76:d4fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1010 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1035 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:802734 (783.9 KiB)  TX bytes:150937 (147.3 KiB)
          Interrupt:185 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

With the installed ubuntu ifconfig, after just abuout 6 minutes, there are over 130 errors for each type of packet.  That version is using the same settings as this live cd version.  

Does anybody know what is going on here?  I am very eager to get the internet working on my Linux desktop.  :(

---

### Post by craz on 2006-07-05
Has anybody else had this problem that may know how to fix it?

---

### Post by craz on 2006-07-05
Please?

---

### Post by craz on 2006-07-06
*bump*

---

### Post by craigi on 2006-07-06
Don't have any good ideas at the moment, but have you tried disabling IPv6?  I know there's been some issues with it and people who have disabled it have reproted generally better success with their networking issues.  Maybe it'll help yours?

There's a HOWTO or two out there on these forums.  Good luck to you.

---

### Post by zenboomerang on 2006-07-07
> **craz said:**
> *bump*

Hi,

I had a similar problem with the dsl line dropping out after a short time and found that my problem was in my modems settings.

I changed my PPPoE to PPPoA LLC and fixed the problem instantly.

As you are getting a line and then dropping out, it sounds like a similar problem.

hth
Andy

---

