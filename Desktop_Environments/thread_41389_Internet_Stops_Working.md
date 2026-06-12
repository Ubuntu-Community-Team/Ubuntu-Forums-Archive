---
title: "Internet Stops Working"
date: 2005-06-13
forum: Desktop Environments
---

### Post by taddy_porter on 2005-06-13
Ok, I've been trying to figure this out on my own for several weeks now, but I just can't get it working. I have my Ubuntu Hoary machine set up through a Sonicwall SOHO router on a cable internet connection. The networks fine, runs fine but anytime I run usenet downloads it will stop working. Basically the network just becomes unavailable. It sit trying to resolve the DNS for several minutes. This is across the board, just not PAN or Newsbin or whatever I'm using, there's no access to the network at all. Running /etc/init.d/newtork restart or anything does nothing. If I try connecting directly via the IP address I get a rejection error. I can't connect to my router either. Only way I can get the network back is to reboot. I originally thought this was a PAN error and even upgraded to the CVS upgraded version of PAN, but same problem. Running Newsbin through WINE also duplicates the problem. I have not duplicated the problem with HTTP or FTP downloads, but I don't really download things through either much. Any ideas where to start to troubleshoot this? I'm clueless. Thanks.

---

### Post by GrammatonCleric on 2005-06-13
Are you doing this via a wireless connection?  I had an issue like this went I was using a linksys wireless card on my laptop.  It seemed realted to the amount of bandwith that i was using through the card.  If I kept things below 150k everything was fine.  When the linksys card exceeded the 150k my connection dropped and I had to restart my laptop to get it to see the wireless network again.  Sorry to day that the way I resolved the issue was to puchase a Proxim a/b/g Gold card.


-G

---

### Post by taddy_porter on 2005-06-13
Nope. Hard-wired.

---

### Post by taddy_porter on 2005-06-13
bump

---

### Post by Joeb on 2005-06-13
[QUOTE=taddy_porter]Ok, I've been trying to figure this out on my own for several weeks now, but I just can't get it working. I have my Ubuntu Hoary machine set up through a Sonicwall SOHO router on a cable internet connection. The networks fine, runs fine but anytime I run usenet downloads it will stop working. Basically the network just becomes unavailable. It sit trying to resolve the DNS for several minutes. This is across the board, just not PAN or Newsbin or whatever I'm using, there's no access to the network at all. Running /etc/init.d/newtork restart or anything does nothing. If I try connecting directly via the IP address I get a rejection error. I can't connect to my router either. Only way I can get the network back is to reboot. I originally thought this was a PAN error and even upgraded to the CVS upgraded version of PAN, but same problem. Running Newsbin through WINE also duplicates the problem. I have not duplicated the problem with HTTP or FTP downloads, but I don't really download things through either much. Any ideas where to start to troubleshoot this? I'm clueless. Thanks.[/QUOTE]


I wonder if you are actually having a problem with your router instead of your install?  Is it possible to bypass the router and connect directly to the cable modem to test if it is a router configuration problem?

---

### Post by taddy_porter on 2005-06-14
I doubt it's the router. I have 3 computers hooked up to it and only the ubuntu box has this problem. I can connect to the internet with the other 2 even when the ubuntu box stops working. I can give it a shot tonight though and see.

---

### Post by taddy_porter on 2005-06-14
Nope. Not the router. I duplicated the problem connected directly to the internet.

---

### Post by Joeb on 2005-06-14
[QUOTE=taddy_porter]Nope. Not the router. I duplicated the problem connected directly to the internet.[/QUOTE]

Well, I was figuring it wasn't particularly after you last post about other computers not having the problem.  When it quits working, are you able to ping any of the other computers on the local network?  Also, are you using the stock kernels or did you compile your own?

Does this computer happen to dual boot?  If so, does the problem exist under Windows or is it Linux specific?  If Linux specific, or if it doesn't dual boot, do you know if the network adapter is sharing a interrupt with something else? (I ask, because I once had a sound card and the ethernet card sharing an interrupt.  All work well until a sound was played during a download.  It broke the connection, but didn't require a reboot).

You might also try turning off the plug and play detection in your bios and/or from the kernel when it boots and see if that makes a difference (noapic setting)

---

### Post by FLeiXiuS on 2005-06-14
[QUOTE=taddy_porter]Ok, I've been trying to figure this out on my own for several weeks now, but I just can't get it working. I have my Ubuntu Hoary machine set up through a Sonicwall SOHO router on a cable internet connection. The networks fine, runs fine but anytime I run usenet downloads it will stop working. Basically the network just becomes unavailable. It sit trying to resolve the DNS for several minutes. This is across the board, just not PAN or Newsbin or whatever I'm using, there's no access to the network at all. Running /etc/init.d/newtork restart or anything does nothing. If I try connecting directly via the IP address I get a rejection error. I can't connect to my router either. Only way I can get the network back is to reboot. I originally thought this was a PAN error and even upgraded to the CVS upgraded version of PAN, but same problem. Running Newsbin through WINE also duplicates the problem. I have not duplicated the problem with HTTP or FTP downloads, but I don't really download things through either much. Any ideas where to start to troubleshoot this? I'm clueless. Thanks.[/QUOTE]

Why don't you try bumping down to the physical layer.  This sounds like symptoms I had when my cable was bad.

---

### Post by taddy_porter on 2005-06-15
Once it stops working I can't get anywhere. Opening Firefox gives errors about not being able to lookup the DNS. Ping or other net operations gives an error about network being unavailable. 

The machine does dual-boot. I don't really use the Windows anymore, but the problem is linux specific. Never had the problem in Windows before. I ran newsbin for 2 hours to check it in Windows and no problems. 5 minutes in Ubuntu-no network.

To my knowledge the LAN card is not sharing an interrupt with anything else.

---

### Post by taddy_porter on 2005-06-15
I played around with a bit tonight. I figured out I can actually ping the Ubuntu box from another computer. It doesn't seem to have any problems receiving connections, but outgoing packets error out. Not sure what that means, however.

---

### Post by desdinova on 2005-06-15
what does "ifconfig" return?

---

### Post by Joeb on 2005-06-15
[QUOTE=taddy_porter]I played around with a bit tonight. I figured out I can actually ping the Ubuntu box from another computer. It doesn't seem to have any problems receiving connections, but outgoing packets error out. Not sure what that means, however.[/QUOTE]

How many network adapters are in your computer?  I'm wondering if somehow the default route is getting messed up and your outgoing packets are going to neverland (this could happen even with only one adapter).

---

### Post by taddy_porter on 2005-06-16
**bump**

---

### Post by Joeb on 2005-06-16
Hmm, why did you bump without responding to the last question?

---

### Post by taddy_porter on 2005-06-16
Sorry, I didn't notice anyone had replied. My bad. I just have the one NIC card. It's a PCI card, Realtek if I remember correctly. 


Here's my ifconfig with the net working. I'll get it locked up and see if it shows anything different:

root@mshome:/home/taddy # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:29:33:0C:05
          inet addr:192.168.168.2  Bcast:192.168.168.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:29ff:fe33:c05/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:568 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:2 txqueuelen:1000
          RX bytes:605681 (591.4 KiB)  TX bytes:47495 (46.3 KiB)
          Interrupt:19 Base address:0xb000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1833 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:508252 (496.3 KiB)  TX bytes:508252 (496.3 KiB)

root@mshome:/home/taddy #

---

### Post by taddy_porter on 2005-06-16
and the output after the net goes down:

root@mshome:/home/taddy # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:29:33:0C:05
          inet addr:192.168.168.2  Bcast:192.168.168.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:29ff:fe33:c05/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1262 errors:49 dropped:0 overruns:0 carrier:0
          collisions:109 txqueuelen:1000
          RX bytes:1655960 (1.5 MiB)  TX bytes:122624 (119.7 KiB)
          Interrupt:19 Base address:0xb000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3960 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3960 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1106146 (1.0 MiB)  TX bytes:1106146 (1.0 MiB)

root@mshome:/home/taddy #

---

### Post by Joeb on 2005-06-16
This is a long shot, but are you using DHCP or manual IP address on all of your computers.  In otherwords, is it possible that you have a duplicate IP address and the nic is shutting down, but when you ping it from another location, some one else is responding?  I ask, because your address ends in ".2" which is a pretty low address if you are regularly having to reboot the computer.  It's possible that it could just be retaining it's lease on the address, but it would be something to check out.

If you are using DHCP, all addresses should be DHCP, if manual, all should be manual (there are ways to mix DHCP and manual, though, but for testing, it's easier if they are all the same).

---

### Post by taddy_porter on 2005-06-17
It's DHCP. It shouldn't be duplicating the address. I have it on auto on all the machines. Checking IP address on all machines now shows Ubuntu as *.2, and my other 2 computers as *.1 & *.3. The router is *.200.

---

### Post by taddy_porter on 2005-06-18
bump

---

### Post by desdinova on 2005-06-18
try these five pings in order - which fails

ping 127.0.0.1
ping (your own ip address)
ping router ip address
ping 194.168.4.100
ping [www.yahoo.co.uk](www.yahoo.co.uk)

---

### Post by taddy_porter on 2005-06-18
1st two work, rest don't. Once it locks up I can't get anything outside my machine. I have no idea why. I figured it had to be firewall issue but stopping firestarter does nothing.

---

### Post by taddy_porter on 2005-06-19
I played around a bit with it this weekend. Still no success in fixing it, however I did notice that when it locked up all the IP addresses are being routed to 127.0.0.1 including DNS etc. Anyone have any idea why this would happen?

---

### Post by Joeb on 2005-06-20
[QUOTE=taddy_porter]I played around a bit with it this weekend. Still no success in fixing it, however I did notice that when it locked up all the IP addresses are being routed to 127.0.0.1 including DNS etc. Anyone have any idea why this would happen?[/QUOTE]

I'm not sure why this is occuring, but there is a good chance it is related to firestarter (iptables).  When you said stopping it doesn't fix the problem, is that stopping it after the problem occurs?  In which case, it won't fix it, since the default route has already been reset.  What happens if you don't run it at all?  Does the problem still exist?

One solution, thought not ideal, but will work in a small network, is not to use dhcp (at least on your Ubunut computer).  That way, the ip address and default gateway are hard coded and shouldn't change.  If they do, it's definately an iptables problem (maybe a bad filter).  Of course, if you go this route (no pun intended), you will also need to hard code your dns server, but probably can just enter the router address.

---

### Post by FLeiXiuS on 2005-06-20
I don't think microsoft has solved their issue with Domain / Hostname names conflicting with eachother.  Since everything is working and there seems to be no issues at all..I can only reccommend one solution.

Avoid using hostnames which match Domains/Hostnames already inuse.

Change your hostname then reply if all else fails..

$ sudo hostname [NEWHOSTNAME]

Replace [NEWHOSTNAME] with another hostname of course.

---

### Post by taddy_porter on 2005-06-20
I thought of the host name thing, tried that and it didn't work. Still locked up. I'll try removing firestarter and see if it works then. If it doesn't, then I'll hard code the DNS, IP address etc in. Thanks for the help, I'll let you know if it works.

---

### Post by taddy_porter on 2005-07-04
Still having problems with this. Removed firestarter, flused iptables, setic a static IP address, still lose my connectin. I even tried all the window managers I have and I still get the errors. I have been able to duplicate the problem with ftp services so it seems to be all large binary downloads that cause the probem. anyone have any other troubleshooting ideas?

---

### Post by taddy_porter on 2005-07-04
I'm getting a few errors in my dmesg log, could this be the problem?  

Log file attached

---

### Post by boterbram on 2008-02-07
I am sorry but I don't think i will be of any help, but i do think i have got the same problem.

When I use my network/internet and do not move my mouse, the connection dies and reboot is needed to start it up again (as far as i know). another symptom is that my mouse acts like the computer is very busy, so it jumps across the screen, while the cpu is not nearly fully used

my thread: [http://forum.ubuntu-nl.org/message/205868#p205868](http://forum.ubuntu-nl.org/message/205868#p205868)

gr Bram

---

