---
title: "Ndiswrapper works, but i can't access my network!"
date: 2006-01-05
forum: General Help
---

### Post by shroom on 2006-01-05
Thanks for checking the thread out.

My ndiswrapper works propertly, it finds the driver and the device is working.
*driver present, hardware present.*

The device wlan0 have both recieved and transmitted data and it's possible to scan for networks and it finds my network. That means the device is working!

BUT, it seems like I don't obtain any IP from the DHCP. What could possible be the problem? This driving me nuts! 


output for iwconfig;

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     Auto  ESSID:"Belkin_Pre-N_587192"
          Mode:Managed  Channel:0  Access Point: 00:11:50:29:09:FB
          Bit Rate:108 Mb/s
          Power Management:off
          Link Quality:100/100  Signal level:-58 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



output for ifconfig;

eth0      Link encap:Ethernet  HWaddr 00:09:6B:30:00:1D
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::209:6bff:fe30:1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1068215 (1.0 MiB)  TX bytes:164962 (161.0 KiB)

lo        Link encap:Local Loopback
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4324 (4.2 KiB)  TX bytes:4324 (4.2 KiB)

sit0      Link encap:IPv6-in-IPv4
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:5 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:2C:FE:90
          inet6 addr: fe80::211:50ff:fe2c:fe90/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2142 (2.0 KiB)  TX bytes:11358 (11.0 KiB)
          Memory:10800000-1087ffff


Thanks in advance!

---

### Post by Mattj on 2006-01-05
Once you are connected to the access point, have you tried running 'dhclient wlan0'?

or even set an IP in your wifi's IP range manually to test the connection??

-Matt

---

### Post by Zelut on 2006-01-05
After you installed the ndiswrapper drivers and got the *hardware present, driver present* did you also include the '*sudo modprobe ndiswrapper*' and '*sudo ndiswrapper -m*' commands?  Also, (assuming you're using gnome) have you activated your card in network-admin? (Sys > Admin > Networking)

Also, assuming you've set your ESSID in network-admin (Sys > Admin > Networking) do you still not get a connection?

---

### Post by Mattj on 2006-01-05
> wlan0 Auto ESSID:"Belkin_Pre-N_587192"
Mode:Managed Channel:0 Access Point: 00:11:50:29:09:FB
Bit Rate:108 Mb/s
Power Managementff
Link Quality:100/100 Signal level:-58 dBm Noise level:-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

wlan0 Link encap:Ethernet HWaddr 00:11:50:2C:FE:90
inet6 addr: fe80::211:50ff:fe2c:fe90/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:30 errors:0 dropped:0 overruns:0 frame:0
TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2142 (2.0 KiB) TX bytes:11358 (11.0 KiB)
Memory:10800000-1087ffff



He us connected to an access point, which has sent and received (a little bit of) data.

I think its probably just the need for a DHCP Client, Or just to manaually set an IP for testing.

Just my 10p

-matt

---

### Post by shroom on 2006-01-06
Hi folks, thanks for replying!

Yeah yeah. I've tried to manually set up an IP and I've done "dhclient wlan0" several times without sucess.

Something I'm worried about is that it says it's connected to Belkin_Pre_N_xxx on * channel 0 * even if my router is configured for channel 10.

*man iwconfig* tells me that I should be able to change channel with *sudo iwconfig channel X* but it doesn't change anyway.


This makes me to pull my hair off!

---

### Post by Titus A Duxass on 2006-01-06
Are you using a wired connection on the machine as well as the wireless connection.

If you are then you have to disable the wired (eth0) connection first.

Try doing this in a terminal:

sudo ifdown eth0
passwd
sudo ifup wlan0

---

### Post by shroom on 2006-01-07
Hi people,

During the time I was fighting with this I've tried everything. The previous message told me to disconnect the eth0-device and I've already tried that many times without sucess.

I have now made a fresh install of Ubuntu and installed Kubuntu on top of that. I saw that some wireless-packages was included and I hope that this time it will work. I will start off to install ndiswrapper and then hope for the best.

Thanks for checking, I'll reply with further info how it's going...

---

