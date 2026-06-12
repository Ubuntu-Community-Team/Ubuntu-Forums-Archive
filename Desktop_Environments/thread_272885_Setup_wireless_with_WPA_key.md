---
title: "Setup wireless with WPA key"
date: 2006-10-07
forum: Desktop Environments
---

### Post by GotenSSj on 2006-10-07
Hi, I just switched to Ubuntu (well not really, i'm actually trying to switch to Ubuntu)

Now my question is:
I need to connect to a wireless with WPA key and fixed IP, DNS...

Searching I found a lot of information about this network manager, but after the install he do not shows anything :\

Do not matter if the configuartion need to be manual or with tools :P

I just need to get working.
Tnk for any help :D

---

### Post by strabes on 2006-10-07
sudo apt-get install network-manager

Then restart X (ctrl + alt + backspace) and there should be an obvious icon in your notification area with a pretty simple interface. This is my favorite wireless program

---

### Post by GotenSSj on 2006-10-08
Maybe I'm not been clear :(

I already tryed to install this nework manager

The icon is appeared (after fixing a bug for the gtk resources), but no wireless or cable connection was found :\

---

### Post by kngcrntrd on 2006-10-08
What kind of wireless card are you using?  You need more than just the network manager.  You also need to make sure you have the correct drivers, modules, etc..  Type this: [COLOR="Red"]iwconfig[/COLOR] in a command prompt and post the output, along with the wireless card you're using.

---

### Post by GotenSSj on 2006-10-10
Sorry for the long time between the posts, but I had very long days :\

Here are all the hardware data

The pc is a vaio FS315H (a really bad choice after all :\)

The network controller should be quite standard

from lspci:
```

Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ/ - PRO/100
                             VE (LOM) Ethernet Controller Mobile (rev 03)

```


from lsmod
```

ipw2200
ieee80211  (needed by ipw2200)

```


Tnks for the patience.

---

### Post by GotenSSj on 2006-10-10
Here the missing information #-o

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:01:4A:C4:AA:ED  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:13:CE:72:CD:39  
          inet addr:10.0.0.180  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe72:cd39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6570 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1191 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0x2000 Memory:b0006000-b0006fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3432 (3.3 KiB)  TX bytes:3432 (3.3 KiB)
```


iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

