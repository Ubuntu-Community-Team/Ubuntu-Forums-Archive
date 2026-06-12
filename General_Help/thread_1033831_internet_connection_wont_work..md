---
title: "internet connection wont work."
date: 2009-01-07
forum: General Help
---

### Post by marie-p on 2009-01-07
Hi,

I installed ubuntu 8.10 on my brand new desktop and it did not recognize my internet connection. 

I *think* that my connection is a pppoe (I know at least that it works with an ethernet cable and my isp is a cable company). 

I tried the pppoeconf function and it saw an ethernet card (eth0) and another type of card (I don't remember what it was) but then did not see any connection. 

I know my internet connection works fine (it's working on my laptop). What can I do?

---

### Post by sPiN1 on 2009-01-07
Linux is notorious for being a huge pain in the *** to get wireless to work I would suggest just using an ethernet cable

---

### Post by Snow986 on 2009-01-07
I'm a little rusty on this but try 
ifconfig -a

in the terminal and post the results

and are you trying to get your ethernet card to work or a wireless card?

---

### Post by marie-p on 2009-01-11
(sorry for taking so long to reply)

I did the ifconfig -a and got this:

> 
eth0      Link encap:Ethernet  HWaddr 00:1f:e2:09:c2:91  
          inet6 addr: fe80::21f:e2ff:fe09:c291/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:528 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33592 (33.5 KB)  TX bytes:2178 (2.1 KB)
          Interrupt:222 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

pan0      Link encap:Ethernet  HWaddr 12:bb:52:c3:5b:30  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



My connection is not wireless, I am connecting with the wire.

---

### Post by ajcham on 2009-01-11
You're computer hasn't been assigned an IP address by the router - your IP address would usually appear between these two lines:
```
eth0 Link encap:Ethernet HWaddr 00:1f:e2:09:c2:91
inet6 addr: fe80::21f:e2ff:fe09:c291/64 Scope:Link
```

Are you able to access your router's configuration dialog? (try [http://192.168.0.1](http://192.168.0.1) or [http://192.168.1.1](http://192.168.1.1) from a browser - you may have to use another connected computer, but I don't think so)
Make sure the router is set up as a DHCP server.

---

### Post by marie-p on 2009-01-11
> **ajcham said:**
> You're computer hasn't been assigned an IP address by the router - your IP address would usually appear between these two lines:
```
eth0 Link encap:Ethernet HWaddr 00:1f:e2:09:c2:91
inet6 addr: fe80::21f:e2ff:fe09:c291/64 Scope:Link
```

Are you able to access your router's configuration dialog? (try [http://192.168.0.1](http://192.168.0.1) or [http://192.168.1.1](http://192.168.1.1) from a browser - you may have to use another connected computer, but I don't think so)
Make sure the router is set up as a DHCP server.

I tried on both my desktop and my laptop (my laptop has a working internet connection&#65289;and neither worked. :confused:

The network connection on my desktop is set to DHCP.
There is room to enter a "DHCP Client ID" Do I need one?

---

### Post by ajcham on 2009-01-11
> **marie-p said:**
> The network connection on my desktop is set to DHCP.
There is room to enter a "DHCP Client ID" Do I need one?

You shouldn't need one, no.  However, is the checkbox to 'Connect automatically' ticked?

Also, what make/model of router do you have? Is there a manual?

---

### Post by marie-p on 2009-01-11
> **ajcham said:**
> You shouldn't need one, no.  However, is the checkbox to 'Connect automatically' ticked?

yes, it is. (and the computer does try to connect when I boot)
the 'system setting' is also ticked. 


> 
Also, what make/model of router do you have? Is there a manual?

I connect directly to the modem that was provided by my isp. (for now... I have a wireless router but I haven't set it up) The manual I have here says very little (it shows how to connect the wires and then asks you to put in the cd rom - which of course doesn't work with linux). I can see if there was any more documentation.

---

### Post by ajcham on 2009-01-11
Are you in the US? From what I've read, some US Cable companies set up the router in such a way as to only allow the computer you set up with access (stupid, I know). Presumably, they use MAC filtering for this.

You could try the config dialog again - some cable modems use the address [http://192.168.100.1](http://192.168.100.1) rather than either of the two I posted earlier.

---

### Post by marie-p on 2009-01-11
> **ajcham said:**
> Are you in the US? From what I've read, some US Cable companies set up the router in such a way as to only allow the computer you set up with access (stupid, I know). Presumably, they use MAC filtering for this.



I'm in Canada. I've been using the same modem for years and I changed computers a few times and I always managed to connect to the net. 

There is a MAC address on my network connection. Is it normal?

> 
You could try the config dialog again - some cable modems use the address [http://192.168.100.1](http://192.168.100.1) rather than either of the two I posted earlier.

It's not working either. 
On my desktop it says that it can't browse the web while offline, and the address wont load on my laptop either.

---

### Post by ajcham on 2009-01-11
> **marie-p said:**
> There is a MAC address on my network connection. Is it normal?

The MAC address is a unique identifier for your computer - if a modem uses MAC address filtering it means that it will only let specific addresses connect to it.

Does the laptop run Linux? Or any of the previous machines you connected with?

Also, were you able to find out more about the modem?  The make and model may be written on the underside.  Or, at the very least, a serial number.

---

### Post by Yellow Pasque on 2009-01-11
Is eth0 set to use dhcp?
```
cat /etc/network/interfaces
```
should show this somewhere:
```
auto eth0
iface eth0 inet dhcp
```
If not, you can edit the file:
```
gksudo gedit /etc/network/interfaces
```

---

### Post by marie-p on 2009-01-11
I got it working!! 

It was as simple as resetting the modem. Why didn't I think of that before?? I think I'll go hide in shame now. :redface: ](*,)

Thank you all for your help.

---

### Post by ajcham on 2009-01-11
> **marie-p said:**
> I got it working!! 

It was as simple as resetting the modem. Why didn't I think of that before?? I think I'll go hide in shame now. :redface: ](*,)

Thank you all for your help.

Well done! Don't be ashamed that you didn't think to reset the modem - after all, no-one thought to suggest it to you either.

---

