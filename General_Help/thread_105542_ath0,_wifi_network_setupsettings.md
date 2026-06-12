---
title: "ath0, wifi network setup/settings"
date: 2005-12-18
forum: General Help
---

### Post by transkinetic on 2005-12-18
I just intalled breezy (had used hoary previusly with no trouble) and am having trouble getting my network settings right.
I did all the steps in [(link)]("https://wiki.ubuntu.com/WiFiHowto?highlight=%28ath0%29") up until pinging my router failed. It claims connectivity at 80% strength but I can't ping anything other than localhost. I've tried setting up both static ip and DHCP.

---

### Post by Lambert on 2005-12-18
Post the output of these commands with the interface up.

iwconfig

ifconfig

route

What kind of network configuration do you have? open signal? wep? etc...

---

### Post by TrinitronX on 2005-12-18
Are you using the madwifi driver?  What type of encryption do you have set up on your router?

---

### Post by transkinetic on 2005-12-20
spacepopeye@spacerig:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"ACTIONTEC"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0F:B3:1B:56:4F
          Bit Rate:12 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=32/94  Signal level=-63 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:1   Missed beacon:0

sit0      no wireless extensions.

spacepopeye@spacerig:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:90:96:8B:06:37
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:96ff:fe8b:637/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1070 errors:378 dropped:0 overruns:0 frame:378
          TX packets:1188 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:913146 (891.7 KiB)  TX bytes:149840 (146.3 KiB)
          Interrupt:22 Memory:dfc00000-dfc10000

eth0      Link encap:Ethernet  HWaddr 00:08:0D:8D:76:F3
          inet6 addr: fe80::208:dff:fe8d:76f3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1867 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1867 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:168810 (164.8 KiB)  TX bytes:168810 (164.8 KiB)

spacepopeye@spacerig:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 ath0
default         dslmodem.domain 0.0.0.0         UG    0      0        0 ath0

Encryption is off and I don't know about madwifi. I can ping most ips but it takes a long time of no activity before firefox will load a page. My windows partition isn't even delivered DHCP settings. Oddly the other win box here (also wireless) can connect with no trouble. This router (ACTIONTEC) has lots of other problems associated with it such as not being able to save setting and taking up to an hour to turn on if turned off or if a restart/save is initiated via web interface. I've connected to other wireless gateways via this ubuntu installation without trouble.

I appreciate the help.

Edit: Just booted into windows and am now everything works fine. Will try it again in ubuntu.
Edit2: Windows works sparodically and ubuntu hasn't changed. In ubuntu, GAIM dosn't work but Skype does.

---

### Post by akniss on 2005-12-20
Your ESSID is ACTIONTEC... do you happen to have the GT701 provided by Qwest?  If so you might want to check the links below.  Any questions, post again.

 
[http://www.ubuntuforums.org/showthread.php?t=95460](http://www.ubuntuforums.org/showthread.php?t=95460)
[http://www.linuxquestions.org/questions/showthread.php?p=1970137#post1970137](http://www.linuxquestions.org/questions/showthread.php?p=1970137#post1970137)

---

