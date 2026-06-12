---
title: "xsession-errors"
date: 2006-02-14
forum: Desktop Environments
---

### Post by roe on 2006-02-14
Hi 

I keep getting this error message "** (gnome-session:12140): WARNING **: Host name lookup failure on localhost." Is there anyone who knows how to resolve tihs problem.

Thanks Roe

---

### Post by mattheweast on 2006-02-14
[QUOTE=roe]Host name lookup failure on localhost[/QUOTE]

What is your hostname set to? You can look by opening a terminal and typing "hostname". Try changing it to something else, with the command "sudo hostname newname".

Matt

---

### Post by roe on 2006-02-14
Hi Matt 
I tried changing my hostname , but unfortunately it did not help , but thanks for your reply.

Roe

---

### Post by mattheweast on 2006-02-14
Can you see if your loopback device is working?

Type "ifconfig" in a terminal, and post the result here. We're looking for a device called "lo".

M

---

### Post by roe on 2006-02-14
Hi 

My ifconfig looks like this :

eth0      Link encap:Ethernet  HWaddr 00:10:B5:4C:EC:DC
          inet addr:80.199.145.59  Bcast:80.199.145.255  Mask:255.255.255.0
          inet6 addr: fe80::210:b5ff:fe4c:ecdc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1884 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1851 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2283593 (2.1 MiB)  TX bytes:163978 (160.1 KiB)
          Interrupt:11 Base address:0x1000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20073 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20073 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5682783 (5.4 MiB)  TX bytes:5682783 (5.4 MiB)

roe

---

### Post by mattheweast on 2006-02-14
That looks fine. Sorry, I've run out of ideas :/ Hopefully someone else can help.

Matt

---

### Post by roe on 2006-02-15
Thanks Matt.

My computer is running ok, only this error message is irritating ,but I can live with that.Any help is appreciated.

Roe

---

