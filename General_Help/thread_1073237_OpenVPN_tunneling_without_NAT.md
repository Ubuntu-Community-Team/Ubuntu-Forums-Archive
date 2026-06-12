---
title: "OpenVPN tunneling without NAT"
date: 2009-02-18
forum: General Help
---

### Post by moep on 2009-02-18
Hello everyone,

I've just now installed OpenVPN on my "do everything" VPS so I can tunnel connections through it in a secure manner while traveling and using unencrypted hotspots.

The guide I've found for this worked well so far:

[http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu](http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu)

Even though that article has different intentions (bypassing Hulu's location check), the basic outcome should be the same.

OpenVPN is now set up on both my client and my server and I can ping and interact between them in the VPN just fine. The only major problem now is internet access.

The guide lists this command to set up NAT and allow the client to use the servers internet connection:

```
sudo iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
```


The problem here is that my VPS has no NAT chain. I am 99% sure that the kernel was compiled without the iptables NAT module and there's no way to get them to recompile it as all virtual machines on that server share the same kernel. #-o
Is there any way to get around this to allow the client to access the internet via the server?


Iptables chains that are available are:

```
INPUT, FORWARD, OUTPUT, VZ_FORWARD, VZ_INPUT, VZ_OUTPUT
```

and as for interfaces:

```
tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:1948 (1.9 KB)  TX bytes:0 (0.0 B)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:127.0.0.1  P-t-P:127.0.0.1  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:27725 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19483 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9050071 (8.6 MB)  TX bytes:2580852 (2.4 MB)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:87.xxx.xxx.xxx  P-t-P:87.xxx.xxx.xxx  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1

```

I’d like to do a modprobe for more information but it fails:

```
modprobe -l
modprobe: Can't open dependencies file /lib/modules/2.6.9-023stab048.4-enterprise/modules.dep (No such file or directory)

```

All the other settings, configs, etc. are exactly as shown in the article linked above.

thanks!

---

### Post by moep on 2009-02-19
no ideas on this? :(

---

### Post by jgombos on 2009-07-04
Bump

OP - what did you end up doing?

---

### Post by moep on 2009-07-04
> **jgombos said:**
> Bump

OP - what did you end up doing?

I gave up on the whole project and went with ssh tunneling instead. 8-[

---

### Post by jgombos on 2009-07-04
I hear the iproute2 package may be a better tool for the job than iptables.. and apparently it doesn't require kernel mods.

---

