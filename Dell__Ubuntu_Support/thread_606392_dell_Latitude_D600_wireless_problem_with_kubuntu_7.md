---
title: "dell Latitude D600 wireless problem with kubuntu 7.10"
date: 2007-11-07
forum: Dell  Ubuntu Support
---

### Post by abrazafi on 2007-11-07
Hi All,

I have a Dell latitude D600 laptop and the wireless connection is working fine with kubuntu 6.06 LTS. I upgraded to kubuntu 7.04 then the wireless connection is working for while  then , somehow, it is dropped down for some reason  .. I have no clue. Then I tried to install  kubuntu 7.10 (Feisty - Gibbon). The wiless is not working at all.
Note that the dhcp parametrs are set correctly: SSID, WEP, etc...
And, I'm getting some strange connection (see the output for ifconfig command).
My router is a Dlink and my network IP address is 192.168.0.*

Any help on how to make this Pro/wireless 2200BG working ?

Thanks.
Abdon.

------------ actual output on the Dell

abdon@dell:~$ lspci | grep -i network
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

abdon@dell:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:35:21:27:49
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0x4000 Memory:fafff000-faffffff

eth0:avah Link encap:Ethernet  HWaddr 00:0E:35:21:27:49
          inet addr:169.254.2.229  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:5 Base address:0x4000 Memory:fafff000-faffffff
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1744 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1744 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:140000 (136.7 KB)  TX bytes:140000 (136.7 KB)

abdon@dell:~$ uname -a
Linux dell 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

---

### Post by dacap06 on 2007-11-08
Of more interest would be the hosts's response to "iwconfig eth0".  If you haven't already, you'll need to install the wirelesstools package.

DaCAP

---

### Post by abrazafi on 2007-11-08
Thanks DaCap ...

abdon@dell:~$ iwconfig eth0
eth0      radio off  ESSID:"mahefa"
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

> If you haven't already, you'll need to install the wirelesstools package.

Which one ? Could you more specific, please ? 
Are talking the wrapper used for windows driver (ndiswrapper from sourceforge) ?

Anyway, I removed the Knetworkmanager application to avoid any conflict.

Many thanks,
Abdon.

---

### Post by dacap06 on 2007-11-09
I apologize for not being clearer.  The wireless tool I had i mind is iwconfig.  You already have wireless tools installed or you would not be able to run it.

The answer lies in the response to iwconfig.  I'm sure you noted that your transmitter is turned off (Tx-Power=off).  You will not be able to connect to anything until you turn it on!  Here's what I get when I run the command on my atheros-based wireless client:

ath0   IEEE 802.11g  ESSID:"<my WAP's ESSID>"  Nickname:"<my WAP's ESSID>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: <my WAP's MAC>
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=24/70  Signal level=-67 dBm  Noise level=-91 dBm
          Rx invalid nwid:370207  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


The CLI command to turn the transmitter on is:
[INDENT]iwconfig eth0 txpower on[/INDENT]
[INDENT][INDENT]or[/INDENT][/INDENT]
[INDENT]iwconfig eth0 txpower auto[/INDENT]
You can use man iwconfig to see what else you can do with the command.

The question in my mind is what turned off the radio in the first place.  How do you have your ACPI and laptop power-saving set up?  Sometimes the setup to save maximum power while running on battery can do this kind of thing.  I've worked on this in other distributions (including Kubuntu), but not in Ubuntu - so bear with me if I seem a little vague about where to go and what to check.

DaCAP

---

### Post by abrazafi on 2007-11-09
Hi DaCap,

My issue is solved .. how ?:

You suggested to do the command:

abdon@dell:~$ sudo iwconfig eth0 txpower on
[sudo] password for abdon:
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth0 ; Input/output error.

Means that my wireless card is hardset to OFF.

I just turn it on with the keybord:
<Fn> + <F2> which is equivalent to the wireless blue sign.
And this key is a switch Turn ON/OFF of the wireless card.

And that's it ... everything works smouthly.

Many thanks,
Abdon.

---

