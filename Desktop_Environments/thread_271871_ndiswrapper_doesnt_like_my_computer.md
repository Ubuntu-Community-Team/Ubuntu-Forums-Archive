---
title: "ndiswrapper doesnt like my computer"
date: 2006-10-05
forum: Desktop Environments
---

### Post by shortflip on 2006-10-05
hey all, im new to ubuntu and very excited about it. I'm having trouble getting my wireless to work on my Compaq V2000 laptop with the IPW2200 wifi card in it. 

I installed ndiswrapper, and I downloaded the latest driver on my friends windows machine, extracted the INF, sent it to my linux box (I'm connected via 10/100), 

but when I use the sudo ndiswrapper -i w22n51 command, it installs but then says I have an invalid driver when I use the ndiswrapper -l command. Any thoughts?

I got the driver link from the ndiswrapper wiki.

---

### Post by wieman01 on 2006-10-05
You don't need "ndiswrapper" as IPW2200 is recognized by default. Please run these commands from a terminal window and post the ouput here:
> ifconfig
> iwconfig
> iwlist eth1 scan
Also tell us a bit more about your network: wireless security (WEP, WPA), DHCP vs. static leases, etc. As said, there is a good chance that your card has been installed.

---

### Post by shortflip on 2006-10-05
andrew@andrew-laptop:~/Desktop$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:4C:4E:D7
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe4c:4ed7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:47749572 (45.5 MiB)  TX bytes:3200772 (3.0 MiB)
          Interrupt:193 Base address:0x800

eth1      Link encap:Ethernet  HWaddr 00:0E:35:59:03:1B
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0x4000 Memory:e0206000-e0206fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1229 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1229 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:111458 (108.8 KiB)  TX bytes:111458 (108.8 KiB)





andrew@andrew-laptop:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.




andrew@andrew-laptop:~/Desktop$ iwlist eth1 scan
eth1      No scan results



The wireless network is an 802.11b/g that is WPA protected with a passphrase. IP addresses are assigned by DHCP. It works absolutely fine with a 10/100 cable plugged in from the router.

Thanks!!! :-D

---

### Post by hegenious on 2006-10-05
perhaps this info is not acurate anymore (breezy), but I remember that I needed wpasupplicant to enter the wpa passphrase and send it to the router for comparison against the key that is stored there.

---

### Post by wieman01 on 2006-10-05
WPA_SUPPLICANT is still required for WPA. But what worries me more at this stage is that the scan ("iwlist eth1 scan") delivers no results. The network adapter seems to be working ("iwconfig") but I don't see any networks around you.

Can you run "dmesg" please?
> dmesg
Have you enabled wireless in your router? Please make sure you have turned it on.

---

