---
title: "Fedora 10 name resolution issues"
date: 2008-12-07
forum: Fedora/RedHat and derivatives
---

### Post by michaelkahl on 2008-12-07
I'm wanting to switch to Fedora as I prepare for my RHCE.  I'm having a bit of an issue, that I'm kinda embarrassed to admit, but I can't learn unless I ask.
I boot up Fedora 10 live and my network connection is fine, I get a DHCP address.  I check /etc/resolv.conf and it has the proper DNS server listed.  I type the command
```
ping www.purdue.edu
```
I get good results from this, but when I try to use Firefox it is unable to resolve [www.purdue.edu](www.purdue.edu).  So I type the IP address in Firefox for purdue.edu and the page loads, but not fully.  I basically get the text and links of the website, none of the images or multimedia load.  I don't expect flash objects since it's not installed on the live CD, but a white background with only text and links in a column?  
Any idea?  BTW this is the i686 live CD not 64 bit.

---

### Post by jmoorse on 2008-12-07
Media may not load because they are referenced by full dns name.  e.g.: [www.purdue.edu/img.photo.jpg](www.purdue.edu/img.photo.jpg)

Check connection settings in Firefox are correct.  Please post ifconfig -a output

---

### Post by michaelkahl on 2008-12-08
I'll see what I can get next time I run the live cd.  I'm not going to consider installing it until I can get this resolved.  
Good point on the images.
I did check firefox settings and everything looked ok, but who knows.

---

### Post by michaelkahl on 2008-12-08
Here is the output from ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:50:8D:9C:55:EA  
          inet addr:192.168.2.113  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe9c:55ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16637 (16.2 KiB)  TX bytes:10591 (10.3 KiB)
          Interrupt:23 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:800 (800.0 b)  TX bytes:800 (800.0 b)

pan0      Link encap:Ethernet  HWaddr 96:8E:25:7F:92:4F  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by spacemooseprime on 2008-12-30
Hi.  

Your problem sounds identical to one I had to resolve, caused by a known bug.  You can perform the workaround on this page: [http://www.fedorafaq.org/f10/#dns-slow](http://www.fedorafaq.org/f10/#dns-slow)
Which worked fine for me.

Good Luck.

---

