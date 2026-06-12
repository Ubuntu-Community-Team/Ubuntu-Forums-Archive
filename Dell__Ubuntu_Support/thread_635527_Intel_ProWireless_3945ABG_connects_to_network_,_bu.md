---
title: "Intel Pro/Wireless 3945ABG connects to network , but will not connect to internet"
date: 2007-12-08
forum: Dell  Ubuntu Support
---

### Post by mcauley on 2007-12-08
I have a Dell Inspiron 1520 with an Intel Pro/Wireless 3945ABG wireless card that will not allow any internet traffic. The card is recognized and the driver installed with no problem. The card will scan and connect to any open networks, but if I try to srf the net or check email there is no traffic. This is a dual boot machine and the card works fine in XP. The wired connection works perfect with both Ubuntu and XP. Any help appreciated.

Scott.

---

### Post by p_quarles on 2007-12-08
I use the same card (on a Compaq) with no problems, so this is most likely a configuration issue. Could you post the output of the following two commands?:
```
cat /etc/network/interfaces
```
and
```
ifconfig -a
```
That will give me (and anyone else who wants to help) a better idea of where to go from here.

---

### Post by mcauley on 2007-12-08
OK,

I get:

auto lo
iface lo inet loopback

and:

bash: itconfig: command not found

Scott.

---

### Post by p_quarles on 2007-12-08
"ifconfig" not "itconfig." "i" then "**f**" :)

That said, I can guess from the results of the first command what the output will be. Go ahead and post it still, though.

Were you able to get this card working on the live CD?

---

### Post by mcauley on 2007-12-08
Here it is.

eth0      Link encap:Ethernet  HWaddr 00:1D:09:A7:1C:E7  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fea7:1ce7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23849 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5055 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15446129 (14.7 MB)  TX bytes:1068618 (1.0 MB)
          Interrupt:17 

eth2      Link encap:Ethernet  HWaddr 00:19:D2:72:5F:5E  
          inet6 addr: fe80::219:d2ff:fe72:5f5e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:9344 overruns:0 frame:0
          TX packets:3 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21815 (21.3 KB)  TX bytes:19306 (18.8 KB)
          Interrupt:17 Base address:0xa000 Memory:fe8ff000-fe8fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:484 (484.0 b)  TX bytes:484 (484.0 b)

---

### Post by p_quarles on 2007-12-08
You didn't answer my other question . . . did your wireless card work with the live CD?

Anyway, this *might* fix things (that's far from a promise, though): open up your network configuration file:
```
sudo nano /etc/network/interfaces
```
and add these lines to the end:
```
auto eth2
iface eth2 inet dhcp
```
Then, restart networking by typing:
```
sudo /etc/init.d/networking restart
```
Like I said, not sure if this will work, but worth a try.

---

### Post by mcauley on 2007-12-09
Too tired.
Will try again tomorrow.
Thanks,
Scott.

---

### Post by mcauley on 2007-12-09
I finally have the wireless working now. When I did the initial install of Ubuntu, I still had the original broadcom card installed. I never was able to get the Broadcom card to connect so I installed the Intel card. The intel card would connect, but would not allow any traffic. Since this was a new install, I didn't have any data to lose, so I just did a clean install and now everything works as it should.

Thanks and best regards,

Scott.

---

### Post by GraemeStevsen on 2008-04-04
> **p_quarles said:**
> "ifconfig" not "itconfig." "i" then "**f**" :)


Were you able to get this card working on the live CD? 

Hi

I have a similar problem with an Intel 3945abg and in answer to your question mine works fine on the live CD but not on an install.

I'm hoping that as you asked the question you have a nice simple fix. :)

---

### Post by p_quarles on 2008-04-04
> **GraemeStevsen said:**
> Hi

I have a similar problem with an Intel 3945abg and in answer to your question mine works fine on the live CD but not on an install.

I'm hoping that as you asked the question you have a nice simple fix. :)
What's the output of this command?:
```
uname -r
```

---

### Post by GraemeStevsen on 2008-04-04
> **p_quarles said:**
> What's the output of this command?:
```
uname -r
```

2.6.22-14-generic

Since posting the wireless has started working intermittently. When it works in Network Tools under the Devices tab it shows IPv4 under protocol as well as IPv6. Only IPv6 shows when it is not working.

Also when it works there are three network devices on the drop down; loopback interface (lo), ethernet interface (eth0) and ethernet interface (eth1). When it doesn't work there is a 4th network device ethernet interface. It's all working at the moment and I can't remember exactly what it said but it is, very roughly, ethernet interface (eth1:somestuff here)

Thanks

---

### Post by GraemeStevsen on 2008-04-16
I have finally solved this problem, for me at least.

I tried the suggestions on this and various other sites with no success. I tried Hardy and, even allowing that it's a beta, the problem doesn't seem to be fixed.

Then I installed OpenGEU and it worked out of the box. Not just on the live cd but actually when it was fully installed as well.

> **GraemeStevsen said:**
> 2.6.22-14-generic

Since posting the wireless has started working intermittently. When it works in Network Tools under the Devices tab it shows IPv4 under protocol as well as IPv6. Only IPv6 shows when it is not working.

Also when it works there are three network devices on the drop down; loopback interface (lo), ethernet interface (eth0) and ethernet interface (eth1). When it doesn't work there is a 4th network device ethernet interface. It's all working at the moment and I can't remember exactly what it said but it is, very roughly, ethernet interface (eth1:somestuff here)

Thanks

---

