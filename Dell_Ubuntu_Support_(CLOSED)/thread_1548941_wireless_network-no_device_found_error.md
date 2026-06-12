---
title: "wireless network-no device found error"
date: 2010-08-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mad25 on 2010-08-09
Hello evryone
         I hav just installed ubuntu 10.04 on ma Dell inspiron 1525 laptop ,without partitioning inside windows. Though my wireless network is perfectly working on ma Windows Xp ,its not connecting in Ubuntu:( 
for followin commands its me followin info:
   [FONT=&quot]mad@ubuntu:~$ ping 192.168.1.2
connect: Network is unreachable
mad@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:ae:19:6a:30  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26320 (26.3 KB)  TX bytes:26320 (26.3 KB)

mad@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.[/FONT]


    [FONT=&quot]mad@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/FONT]




[FONT=&quot]plz help me out in getting connection
[/FONT]
  [FONT=&quot]
[/FONT]

---

### Post by xdunlapx on 2010-08-10
In a terminal type "lspci" do you see 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

I've got a Dell Inspiron 1750 and had to hook the laptop up to ethernet, update apt-get and then install bcmwl-kernel-source and its few requirements to get my wifi to be detected and work.

---

