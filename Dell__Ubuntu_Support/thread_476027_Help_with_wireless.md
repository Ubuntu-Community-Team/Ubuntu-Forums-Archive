---
title: "Help with wireless"
date: 2007-06-16
forum: Dell  Ubuntu Support
---

### Post by BigNeek on 2007-06-16
Hello All,

I'm having an issue with my wireless.  Basically, I have a Dell Latitude D600 w/a TrueMobile 1300 wireless NIC.  I installed NDISWrapper and installed the drivers.  I can get the wireless to work if I run the following commands:

  sudo modprobe ndiswrapper
  dhclient eth01

I'm a noob and I'm not even sure what those commands do.  I just know that they work.  The problem is that I have to run them each time that I reboot.  Is there a way to enable the NIC and DHCP automatically on reboot?

Thanks,

Big Neek

---

### Post by neptho on 2007-06-16
eth01?  Is that right?

Do an 'ifconfig -a' and post the results here just to make sure.

If you edit  /etc/modules, and add 'ndiswrapper', it will automatically setup the ndiswrapper drivers for your machine.

Then, edit /etc/network/interfaces, and add the following:

```
auto ethX
iface ethX inet dhcp
```

where the 'X' is the number of your ethernet interface.  That'll tell it to automatically connect via DHCP.

---

### Post by BigNeek on 2007-06-17
jniko@JNiko-L:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0D:56:DE:E1:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:90:4B:6D:7D:D3  
          inet addr:192.168.50.100  Bcast:192.168.50.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe6d:7dd3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:304850 errors:0 dropped:0 overruns:0 frame:0
          TX packets:199140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:408470595 (389.5 MiB)  TX bytes:20138962 (19.2 MiB)
          Interrupt:5 Memory:fafee000-faff0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:498 (498.0 b)  TX bytes:498 (498.0 b)

---

### Post by neptho on 2007-06-17
Looks to be eth1; use eth1 in place of the ethX notation above.

---

### Post by kgr132 on 2007-06-18
You can also try this thread:

[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

I followed it to the letter, including the linked driver files, after a clean install of Fiesty on my Dell Latitiude D600 and my wireless was up and running (including WPA encryption) in under 30 minutes. BTW, the Broadcom How-To works because your Dell TrueMobile 13xx is really just a Broadcom 43xx in disguise.

Good Luck
-K-

---

