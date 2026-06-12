---
title: "ubuntu 8.10, internet, eth1, ath0, lo, and me."
date: 2008-12-10
forum: General Help
---

### Post by DestroyerOfTheSeas on 2008-12-10
Hello my friends! How very nice to meet you. A pitty the circumstances aren't a little more light-hearted. Please take a minute to comprehend my situation. I'm black, gay, hermaphrodite republican. My life is unlivable. No, I'm just kidding, my problems are much less severe (no offense to those whose problems are more severe).

I'm got a sony vaio, my hard drive is partitioned every which way; I'm running Ubuntu Hardy on one part, XP on another, and UbuntuStudio 8.10 on another. Everything is fine and dandy, except one little thing: I'm just having a little trouble getting my internet up in UbuntuStudio.

When I hover my mouse over the NetworkManager in the toolbar it says "Network Connection: lo". In my Connection Properties, under "name:", "lo" is my only option.

this is my iwconfig readout: 

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

wifi0     no wireless extensions.

ath0      no wireless extensions.


As you can see, lo has no wireless extensions. eth1 however does. How do I connect through eth1 instead of lo?

I am so embarrassed, will someone not reply out of courtesy just so I am forced to figure it out myself? Again, I am just kidding. Please respond. I am dumb and I need help.

Thank you my friends. 

P.S.

If nobody does reply, I will unleash a doomsday device.

---

### Post by DestroyerOfTheSeas on 2008-12-10
Please guys, does anybody have any word of advice? 

This is my ifconfig readout:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10316 (10.3 KB)  TX bytes:10316 (10.3 KB)



Cmon guys PLLLLEEEEEAAAAAASSSSSEEEEE make some magic

---

### Post by mali2297 on 2008-12-11
Here is an howto that might help:
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

If you still can't get it working, give us some more information about your wireless card; see
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

