---
title: "conky wireless_* parameters do not have any values"
date: 2009-03-01
forum: General Help
---

### Post by rvbhute on 2009-03-01
The wireless_* family of variables in conky are returning zero values.

wireless_essid
wireless_mode - works, returns 'Auto'.
wireless_bitrate
wireless_link_qual
wireless_link_qual_max

Rest of the values are returning zero or empty.

The wireless interface is managed by Network Manager and listed as eth1. It is detected by other variables of conky - downspeedf, upspeedf, etc. Most of the conkyrc files in threads on this forum and on the net refer to wireless interfaces as ath0 or wlan0. Is this the problem?

The wireless interface is :
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01).

It is using the Restricted Broadcom STA wireless driver.

Output of ipconfig, iwconfig and 'cat /proc/net/wireless'

```
rohit@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:ae:07:9f:4b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:23:4e:93:0b:67  
          inet addr:192.168.5.82  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4eff:fe93:b67/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:24
          TX packets:21 errors:5 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:852 (852.0 B)  TX bytes:3737 (3.7 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1356 (1.3 KB)  TX bytes:1356 (1.3 KB)

rohit@ubuntu:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:229  Noise level:167
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.

rohit@ubuntu:~$ cat /proc/net/wireless 
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
rohit@ubuntu:~$
```

As per this link [http://mydellmini.com/forum/conky-configuration--t1627.html#p31697](http://mydellmini.com/forum/conky-configuration--t1627.html#p31697) it seems to be an issue with the Broadcom driver. But I still have access to Link Quality, Signal Level and Noise Level. 

If someone can point out  a way to represent signal strength in 'human-readable' format using these three values, maybe I could churn up a simple bash script for it.

---

### Post by rvbhute on 2009-03-05
Is this issue related to the Broadcom STA proprietary drivers? 'iwconfig eth1' needs to be run with sudo to get any practical information. Output of '/proc/net/wireless' is like in post above.

```
rohit@ubuntu:~$ iwconfig eth1
eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:2  Signal level:183  Noise level:168
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

rohit@ubuntu:~$ sudo iw
iwconfig  iwevent   iwgetid   iwlist    iwpriv    iwspy     
rohit@ubuntu:~$ sudo iwconfig eth1
eth1      IEEE 802.11bg  ESSID:"olympus-ai-5"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:6B:92:2D:D9   
          Bit Rate=36 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=2/5  Signal level=-74 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:0   Missed beacon:0

```

---

### Post by marranzano on 2009-03-24
any luck so far??

the problem seems to be permissions, I have the same driver and wireless is on eth1...

if I run conky with sudo permission wireless data shows correctly, otherwise situation is as you mentioned...

could we solve it changing some permission?

---

### Post by ViMMeD on 2009-03-27
Did you install conky with the wlan flag?  Also it doesn't matter if the interfaces are named eth or wlan; mine are named eth0 and eth1.  I don't think conky comes defaulted with the wlan variables (wireless_*) but I know when i tried it, the terminal wouldn't run it, saying unknown variable.  Try reinstalling conky with:

```
./configure --enable-wlan
make
make install
```

---

### Post by marranzano on 2009-03-27
> **ViMMeD said:**
> Did you install conky with the wlan flag?  Also it doesn't matter if the interfaces are named eth or wlan; mine are named eth0 and eth1.  I don't think conky comes defaulted with the wlan variables (wireless_*) but I know when i tried it, the terminal wouldn't run it, saying unknown variable.  Try reinstalling conky with:
```
./configure --enable-wlan
make
make install
```
the default ubuntu package seems to be compiled with --enable-wlan
```
~$ conky -v
Conky 1.6.1 compiled Fri Oct 10 23:13:54 UTC 2008 for Linux 2.6.24-16-server (x86_64)

Compiled in features:

System config file: /etc/conky/conky.conf

 X11:
  * Xdamage extension
  * Xdbe extension (double buffer)
  * xft

 Music detection:
  * mpd

 General features:
  * math
  * hddtemp
  * portmon
  * rss
  * wireless
```
I'll try compiling it and see if it makes a difference... although i suspect it to be a permission problem seeing as i need sudo to get vars from iwconfig...

**EDIT:**
compiled conky-1.7.0_rc with "./configure --enable-wlan" and wireless_* variables give me the exact results as running iwconfig as normal user... if i run "sudo conky" i get the expected variables (essid..etc)

Do I need to give my user special networking permissions??

---

### Post by rvbhute on 2009-04-05
> **marranzano said:**
> the problem seems to be permissions, I have the same driver and wireless is on eth1...

Please note that the following is probably a bad idea.

I have added the iwconfig command to the sudoers file so that 'sudo iwconfig eth1' can be called by my username without a password. Then I used some bash scripting to fetch the various parameters from the output and call the script from conky.

---

### Post by ljungkvist on 2009-05-01
I'm also getting the same problem here: If I install conky from the repo, and run it, the wireless_* commands doesn't return what they should:

```
${color grey}${wireless_essid eth1}${color} - ${wireless_ap eth1} - ${wireless_mode eth1} - ${wireless_bitrate eth1}
```

yields:

*- Not-Associated - Auto - *

Whereas if I run it with sudo in a terminal, I get:

*MyNetwork - 00:23:71:82:22:90 - Managed - 54 Mb/s*

Did you find any solution to this (except customizing sudoers)?

---

### Post by Mechaphoenix25 on 2010-04-07
I can confirm this issue, also with the STA drivers.  However, I would seriously caution anyone who gives the Conky process itself root access.  Conky has the $exec variable, meaning it can execute an arbitrary file, assumably with its own privelege (root in this case).  It can also be directed to run a config that can be from anywhere, written by any user.  Meaning that anyone with access to your machine and Conky can write a script to run a file with root privileges.

I could be completely wrong, but that's what I'd worry about.  Does anyone know how to give Conky access to the STA driver info without giving it full root access to the machine?

---

### Post by bengaltiger on 2010-05-10
so it normal?

with out sudo how it can be done?

any solutions?

thanks,
BT

---

### Post by skew on 2010-06-06
I'm having the same problem. Has a solution been found yet?

---

### Post by stevepoppers on 2010-06-17
Hate to bump without being useful, but
[SIZE="7"]HELP![/SIZE]

---

### Post by marranzano on 2010-06-19
i'm only interested in getting my external ip... this is my workaround using the following script:
```
#!/bin/bash
wget http://checkip.dyndns.org/ -q -O - |
grep -Eo '\<[[:digit:]]{1,3}(\.[[:digit:]]{1,3}){3}\>'

```

marranzano

---

### Post by stevepoppers on 2010-06-19
I got this off the crunchbang forums.
```
${execi 3600 wget -O - www.whatismyip.com/automation/n09230945.asp | tail}
```
It's basically the same but looks a little neater. That url is recommended by whatismyip.com for just this sort of purpose. Don't set the time interval to less than 300. They'll block you.

---

