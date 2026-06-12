---
title: "Unable to download any updates please help"
date: 2006-09-02
forum: Desktop Environments
---

### Post by sketchone on 2006-09-02
I recently installed ubuntu after switching from mandrake, im a noob when it comes to linux so i know some basics.

I managed to install and get the pc on the network to see the internet, (direct connection through a router) but i cant seem to download any updates/software, can anyone help me out - it just hangs - here is a what im getting in the terminal

sketchone@sketchone-desktop:~$ sudo gedit /etc/apt/sources.list
Password:
sketchone@sketchone-desktop:~$ wget [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
--12:38:55-- [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
=> `automatix-installer'
Resolving [www.getautomatix.com](www.getautomatix.com)... 1.0.0.0
Connecting to www.getautomatix.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.

--12:42:05-- [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
(try: 2) => `automatix-installer'
Connecting to www.getautomatix.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.

--12:45:16-- [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
(try: 3) => `automatix-installer'
Connecting to www.getautomatix.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.

--12:48:28-- [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
(try: 4) => `automatix-installer'
Connecting to www.getautomatix.com|1.0.0.0|:80...

here is some info on my network ect 

eth0 Link encap:Ethernet HWaddr 00:04:E2:00:EC:CE
inet addr:192.168.1.4 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::204:e2ff:fe00:ecce/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:7438 errors:0 dropped:0 overruns:0 frame:0
TX packets:7050 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:5196822 (4.9 MiB) TX bytes:903703 (882.5 KiB)
Interrupt:11 Base address:0x2000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:23 errors:0 dropped:0 overruns:0 frame:0
TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1172 (1.1 KiB) TX bytes:1172 (1.1 KiB)


any help will be greatly appreciated as im really stuck and i dont know what to do

sketch

---

### Post by Uncle Spellbinder on 2006-09-02
Automatix seems to have been down for days now. I've not even been able to get to the Automatix Forums [http://www.getautomatix.com/forum/](http://www.getautomatix.com/forum/) to try and find out what the problem might be. They're just down. And with the Automatix forums in Ubuntu gone, I guess we're in Automatix limbo for the time being.

---

### Post by ashenrose on 2006-09-02
Hey there, I am having the same problems. Its not just when I try to get/install Automatix either. I can't apt-get update or anything. It just times out. 

# apt-get update
Errhttp://gb.archive.ubuntu.com dapper Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out

I am running behind a router and cannot connect to Gaim or IRC(Xchat) either. Evolution mail says it cannot connect aswell. Yet Firefox works almost perfectly (aside from my java issue in another thread). 

(I hope you don't mind me jumping in here, I was going to start a new topic, but this appears to be the same kind of thing)

---

### Post by sketchone on 2006-09-02
> **ashenrose said:**
> Hey there, I am having the same problems. Its not just when I try to get/install Automatix either. I can't apt-get update or anything. It just times out. 

# apt-get update
Errhttp://gb.archive.ubuntu.com dapper Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out

I am running behind a router and cannot connect to Gaim or IRC(Xchat) either. Evolution mail says it cannot connect aswell. Yet Firefox works almost perfectly (aside from my java issue in another thread). 

(I hope you don't mind me jumping in here, I was going to start a new topic, but this appears to be the same kind of thing)

no not at all, this is exactly my trouble so it seems we both need the same answer!

Anyone got any ideas - thanks in advance

---

