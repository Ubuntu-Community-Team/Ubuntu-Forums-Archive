---
title: "IP changes every time I restart my system"
date: 2009-01-19
forum: General Help
---

### Post by naseemkkd on 2009-01-19
Hi guys,

When I restart my computer IP address of my debian system changes to another. Also the number with my network card name is incremented by one (ie, eth(n+1))

Now my ifconfig command gives the following output

eth205    Link encap:Ethernet  HWaddr 00:00:6C:CE:B8:29
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:6cff:fece:b829/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18095 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10591 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10487091 (10.0 MiB)  TX bytes:2722992 (2.5 MiB)
          Interrupt:217 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1093965 (1.0 MiB)  TX bytes:1093965 (1.0 MiB)


Please anyone help me. I want a static IP address

thanks in advance
Naseem

---

### Post by eatberrys on 2009-01-19
Here is two threads that had similar problems and seemed to of solved it (i didnt read it all)

[http://ubuntuforums.org/showthread.php?t=745293](http://ubuntuforums.org/showthread.php?t=745293)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153727](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153727)

As for setting a static ip right click network manger then click edit settings then click the inteface and then edit.

---

### Post by doas777 on 2009-01-19
well the simple way is in your interfaces file. open it with:
```

gksu gedit /etc/network/interfaces

```

here is an redacted example of an interfaces file that uses static addressing on eth0:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.XXX.YYY
netmask 255.255.255.0
gateway 192.168.XXX.YYY
dns-servers 192.168.XXX.YYY

auto wlan0
iface wlan0 inet dhcp


```

When I used this file with Intrepid/Gnomes new network manager though, gnome-network-manager will not load, because all the interfaces are unmanaged. when i needed it for wifi, i had to delete my config and use NM to do it. 

good luck,
franklin

---

### Post by blazemore on 2009-01-19
If you're using Ubuntu and/or Network Manager, you can do it through the nm-applet Gnome Panel tool.

Alternatively, your router may have a tool to automatically assign the same IP address to a particular MAC.

---

### Post by doas777 on 2009-01-20
> **blazemore said:**
> If you're using Ubuntu and/or Network Manager, you can do it through the nm-applet Gnome Panel tool.

Alternatively, your router may have a tool to automatically assign the same IP address to a particular MAC.

quite true on both points. In order to get NM running static IPs correctly, I had to delete the "Auth0" profile that the installer created for me and create a new one.

---

### Post by naseemkkd on 2009-01-20
Thanks for all,

I solved my problem by replacing content of /etc/udev/rules.d/z25_persistent-net.rules with following

SUBSYSTEM=="net", DRIVERS=="forcedeth", NAME="eth0"

---

