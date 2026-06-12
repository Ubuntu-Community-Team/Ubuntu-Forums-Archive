---
title: "Network connection help."
date: 2006-01-01
forum: General Help
---

### Post by HIGHLIFE on 2006-01-01
Ok so I just installed ubuntu 5.10 and am very new to linux, but when i try to use firefox it cant find the connection.  I went into System> Administation> Networking and played around with the settings in there but i still can't get it to work.  The Computer is connected by ethernet cable to a wireless router and I know that both the ethernet card and the router work but I'm confused as to why this is not working?!?

someone please help:confused:

---

### Post by qferret on 2006-01-01
router handing out DHCP?

What does typing "ip address" in a terminal window give you?

---

### Post by HIGHLIFE on 2006-01-01
1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:e0:4c:e5:72:5a brd ff:ff:ff:ff:ff:ff
    inet6 fe80::2e0:4cff:fee5:725a/64 scope link
       valid_lft forever preferred_lft forever
3: sit0: <NOARP> mtu 1480 qdisc noop
    link/sit 0.0.0.0 brd 0.0.0.0

ok heres what it gave me

---

### Post by harisund on 2006-01-01
I would give
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0
and then check for connectivity with 
sudo ifconfig
and ping -c 2 [www.yahoo.com](www.yahoo.com)

---

### Post by harisund on 2006-01-01
I would give the following a try: 
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0
and then check for connectivity with 
sudo ifconfig
and ping -c 2 [www.yahoo.com](www.yahoo.com)

---

### Post by HIGHLIFE on 2006-01-01
ok so when i type in 

sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0

it comes up with this:

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:e0:4c:e5:72:5a
Sending on   LPF/eth0/00:e0:4c:e5:72:5a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.

I then did sudo ifconfig and it came up with this:

eth0      Link encap:Ethernet  HWaddr 00:E0:4C:E5:72:5A
          inet6 addr: fe80::2e0:4cff:fee5:725a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:22 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:68896 (67.2 KiB)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6813 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:388595 (379.4 KiB)  TX bytes:388595 (379.4 KiB)

---

### Post by qferret on 2006-01-01
[QUOTE=HIGHLIFE]
No DHCPOFFERS received.
[/QUOTE]

Are you sure DHCP is enabled on your router?
Try power cycling that thing once & see if you get an address after that.
Otherwise you may have to hardcode an IP address at least long enough to get into the router and check the config.

(192.168.0.* is usually the default addressing scheme)

---

### Post by HIGHLIFE on 2006-01-01
yeah its enabled.

---

### Post by mendieta on 2006-01-01
I am having the same problem. My main distro (mandriva) autoconnects perfectly to the DHCP connection served by the dsl modem. Even kubuntu live connected to the internet with no problems. But kubuntu (install version) could not connect, both during and after install :-( And playing from the control center with network settings did not help.

---

### Post by HIGHLIFE on 2006-01-01
What do you mean by power cycling and hardcoding?

---

### Post by qferret on 2006-01-01
Power cycle = turn off/on

Turn your router off for a few seconds, then turn it back on. After it initializes, it may hand out IP addresses normally again.

If not, you may need to "hardcode" a static IP address on your PC.

System -> Administration -> Networking
Click on Eth0 and select Properties

---

### Post by qferret on 2006-01-01
[QUOTE=mendieta]I am having the same problem. My main distro (mandriva) autoconnects perfectly to the DHCP connection served by the dsl modem. Even kubuntu live connected to the internet with no problems. But kubuntu (install version) could not connect, both during and after install :-( And playing from the control center with network settings did not help.[/QUOTE]

Can you connect if you use a static IP? 
(Just trying to narrow the problem a bit)

I have an issue with mine where the DNS server list always ends up containing my router address every time DHCP hands out a new lease, resulting in me being able to talk on my LAN but not on the internet. I had to switch to a static IP, as changing permissions on resolv.conf didn't do the trick....

---

### Post by mendieta on 2006-01-01
[QUOTE=qferret]Can you connect if you use a static IP? 
(Just trying to narrow the problem a bit)

I have an issue with mine where the DNS server list always ends up containing my router address every time DHCP hands out a new lease, resulting in me being able to talk on my LAN but not on the internet. I had to switch to a static IP, as changing permissions on resolv.conf didn't do the trick....[/QUOTE]

Haven't tried that. I'll try next time I reboot. I did try booting with the live CD, then copying all the **/etc/network** files and directories recursively to the harddrive partition where kubuntu is installed, then rebooting on kubuntu, still no luck. But in the liveCD I get to the internet just perfect, so most likely it's not a problem of the router itself. I think that kubuntu should **install to the HD from the live CD**, just use the live CD as a graphical installer. Anyways, thanks a lot !

---

### Post by HIGHLIFE on 2006-01-01
No I'll try one more time but I'm pretty sure I can't.

---

### Post by HIGHLIFE on 2006-01-01
Nope doesnt work with the static IP.

---

### Post by qferret on 2006-01-01
what does "ip address" give for output with the static IP?

---

### Post by mendieta on 2006-01-02
Guys

Is there any good ubuntu/kubuntu package for **network configuration** that is not included in the CD ? I could try downloading it in Mandriva and putting it in the Kubuntu partition, installing there and trying ...

Thanks!

---

### Post by mendieta on 2006-01-02
Allright, at this point we should file a bug report. The problem persists in latest dapper. I'm heading there, let's fix this for good :cool:

---

### Post by HIGHLIFE on 2006-01-11
Mendieta what is your chipset?
jw

---

### Post by cvmostert on 2006-01-12
[QUOTE=qferret]Power cycle = turn off/on

Turn your router off for a few seconds, then turn it back on. After it initializes, it may hand out IP addresses normally again.

If not, you may need to "hardcode" a static IP address on your PC.

System -> Administration -> Networking
Click on Eth0 and select Properties[/QUOTE]

hi, thanx for the help ... powering my router down and up fixed the problem that was made by
sudo dhconfig eth0

now i still have the sound problem... my pc hangs with the sound card plugged in.. but without it, works fine... just no sound!

---

