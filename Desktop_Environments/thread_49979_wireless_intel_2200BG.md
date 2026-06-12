---
title: "wireless intel 2200BG"
date: 2005-07-18
forum: Desktop Environments
---

### Post by sabin on 2005-07-18
hi guys I'm trying to establish a wlan connection running hoary..

seems my wlancard has been detected on install (I'm using the intel wireless pro 2200BG with a centrino laptop) my problem is that it seems like everything works fine. I can list the ap's with "iwlist eth1 scan" I can configure the interface I even seem to get a connection to the ap by entering the right essid, enc, etc... though I cannot ping any ip nor host in the lan. here some outputs:

[PHP]root@lappy:~ # ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0E:35:6D:58:CD
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe6d:58cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:869 errors:0 dropped:44 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:348 (348.0 b)
          Interrupt:18 Base address:0x2000 Memory:e0206000-e0206fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:600 (600.0 b)  TX bytes:600 (600.0 b)



root@lappy:~ # iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Linuxp-G"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:12:17:CC:E9:82
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:0118-B29F-my-secret-839C-key-here   Security mode:open
          Power Management:off
          Link Quality=100/100  Signal level=-34 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:44   Missed beacon:0

sit0      no wireless extensions.

root@lappy:~ # iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:12:17:CC:E9:82
                    ESSID:"Linuxp-G"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Extra: RSSI: -33  dBm
                    Extra: Last beacon: 7ms ago[/PHP]

see what I mean? The gateway was set in the control center... but it doesn't work! anyone an idea what could be wrong here?

greets!

---

### Post by roblubbers on 2005-07-18
did you set the card to use the correct channel?

---

### Post by luca_linux on 2005-07-18
Have you set the gateway and DNS?

---

### Post by sabin on 2005-07-18
well hope so.. dns was set by adding my ns servers into /etc/resolv.conf 
channel was set correct... gateway was set in the controlcenter.. though I wonder what the file is where I can set the gateway...

here the output when I try to ping the ap:

[PHP]root@lappy:~ # ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1)
56(84) bytes of data.
From 192.168.1.2 icmp_seq=1 Destination Host Unreachable
From 192.168.1.2 icmp_seq=2 Destination Host Unreachable
[/PHP] 

I wonder why I get a reply from 192.168.1.2 (which is $wlan interface) even if I ping 192.168.1.1...

it's so strange!

greets!

---

### Post by sabin on 2005-07-18
does anyone have an idea here? I was trying for 2 hours already but it still doesn't work.. 

:(

---

### Post by brim4brim on 2005-07-18
Did you install the latest Intel drivers?  The ones in Hoary don't seem to work that well.  My connection to the internet was dropping until I got the new drivers then it worked perfectly.

---

### Post by sabin on 2005-07-18
no I didn't.. I thought I'm done since it was detected quite fine during installation.

---

### Post by matthew on 2005-07-18
Take a look at [this thread](http://ubuntuforums.org/showthread.php?t=26623&page=1&pp=10) to find out how to install the latest drivers. Once you have done so things should work well for you.

---

### Post by ghoshe on 2005-07-19
I see that you use encryption, i tried too but I couldn't make it work, try to connect without encryption.
I could connect with a public wlan via dhcp (with dhclient).

---

