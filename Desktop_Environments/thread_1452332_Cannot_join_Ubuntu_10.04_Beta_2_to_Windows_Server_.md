---
title: "Cannot join Ubuntu 10.04 Beta 2 to Windows Server 2003 Domain via Likewise-Open 5.4"
date: 2010-04-11
forum: Desktop Environments
---

### Post by rusivi on 2010-04-11
PROBLEM:

With Ubuntu 9.10 host, cannot join Virtualbox guests Ubuntu 10.04 Beta 2 to Windows Server 2003 domain via Likewise Open 5.4
_______________________________________________________________

ERROR:

With Ubuntu 10.04 Beta 2 guest:

name@name-laptop:~/Desktop/id$ sudo domainjoin-cli join dnsname.local Administrator
Joining to AD Domain:   dnsname.local
With Computer DNS Name: name-laptop.dnsname.local

Administrator@DNSNAME.LOCAL's password:

Error: Lsass Error [code 0x00080047]

40286 (0x9D5E) LW_ERROR_LDAP_SERVER_DOWN - Unknown error

SYNOPSIS:

Using Virtualbox 3.1.6, with Ubuntu 9.10 as the host, there are 2 virtual machines (Ubuntu 10.04 Beta 2 & Server 2003) both with 1 internal network NIC. All OSes fully updated.

+ Server 2003:
    + firewall is completely off
    + DNS Server at 10.10.0.1
    + Active Directory Integrated
    + Setup NTP Server using “How to configure an authoritative time server in Windows Server”, “Configuring the Windows Time service to use an internal hardware clock” via: http://support.microsoft.com/kb/816042
    + Statically assigned IP Address 10.10.0.1

HOST DETAILS (Ubuntu 9.10)

name@name-laptop:~$ lsb_release -rd
Description:    Ubuntu 9.10
Release:    9.10

name@name-laptop:~$ apt-cache policy virtualbox-3.1
virtualbox-3.1:
  Installed: 3.1.6-59338_Ubuntu_karmic
  Candidate: 3.1.6-59338_Ubuntu_karmic
  Version table:
 *** 3.1.6-59338_Ubuntu_karmic 0
        100 /var/lib/dpkg/status

GUEST DETAILS (Ubuntu 10.04 Alpha 2)

name@name-laptop:~$ lsb_release -rd
Description:    Ubuntu lucid (development branch)
Release:    10.04

name@name-laptop:~$ apt-cache policy likewise-open
likewise-open:
  Installed: 5.4.0.42111-2
  Candidate: 5.4.0.42111-2
  Version table:
 *** 5.4.0.42111-2 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status

name@name-laptop:~$ apt-cache policy likewise-open-gui
likewise-open-gui:
  Installed: 5.4.0.42111-2
  Candidate: 5.4.0.42111-2
  Version table:
 *** 5.4.0.42111-2 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/universe Packages
        100 /var/lib/dpkg/status

name@name-laptop:~$ ifconfig
eth0    Link encap:Ethernet  HWaddr 08:00:27:c6:3a:91 
          inet addr:10.10.0.5  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::a00:27ff:fec6:3a91/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5893 (5.8 KB)  TX bytes:7671 (7.6 KB)
          Interrupt:10 Base address:0xd020

GUEST DETAILS (Windows Server 2003)

C:\Documents and Settings\Administrator\Desktop\id>ipconfig /all
Windows IP Configuration
 
   Host Name . . . . . . . . . . . . : name
   Primary Dns Suffix  . . . . . . . : dnsname.local
   Node Type . . . . . . . . . . . . : Unknown
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : dnsname.local
                                        
 
Ethernet adapter Local Area Connection:
 
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : AMD PCNET Family PCI Ethernet Adapter
   Physical Address. . . . . . . . . : 08-00-27-27-3F-B1
   DHCP Enabled. . . . . . . . . . . : No
   IP Address. . . . . . . . . . . . : 10.10.0.1
   Subnet Mask . . . . . . . . . . . : 255.0.0.0
   Default Gateway . . . . . . . . . : 
   DNS Servers . . . . . . . . . . . : 10.10.0.1

C:\Documents and Settings\Administrator\Desktop\id>systeminfo
Host Name:                 NAME
OS Name:                   Microsoft(R) Windows(R) Server 2003, Enterprise Edition
OS Version:                5.2.3790 Service Pack 2 Build 3790
OS Manufacturer:           Microsoft Corporation
OS Configuration:          Primary Domain Controller
OS Build Type:             Uniprocessor Free
Registered Owner:          name
Registered Organization:   name
Product ID:                69763-024-5476123-43990
Original Install Date:     2/2/2010, 5:26:46 PM
System Up Time:            0 Days, 12 Hours, 27 Minutes, 34 Seconds
System Manufacturer:       innotek GmbH
System Model:              VirtualBox
System Type:               X86-based PC
Processor(s):              1 Processor(s) Installed.
                           [01]: x86 Family 17 Model 3 Stepping 1 AuthenticAMD ~1973 Mhz
BIOS Version:              VBOX   - 1
Windows Directory:         C:\WINDOWS
System Directory:          C:\WINDOWS\system32
Boot Device:               \Device\HarddiskVolume1
System Locale:             en-us;English (United States)
Input Locale:              en-us;English (United States)
Time Zone:                 (GMT-05:00) Eastern Time (US & Canada)
Total Physical Memory:     511 MB
Available Physical Memory: 298 MB
Page File: Max Size:       1,254 MB
Page File: Available:      1,049 MB
Page File: In Use:         205 MB
Page File Location(s):     C:\pagefile.sys
Domain:                    dnsname.local
Logon Server:              \\NAME
Hotfix(s):                 221 Hotfix(s) Installed.
                           [01]: File 1
                           [02]: File 1
                           [03]: File 1
                           [04]: File 1
                           [05]: File 1
                           [06]: File 1
                           [07]: File 1
                           [08]: File 1
                           [09]: File 1
                           [10]: File 1
                           [11]: File 1
                           [12]: File 1
                           [13]: File 1
                           [14]: File 1
                           [15]: File 1
                           [16]: File 1
                           [17]: File 1
                           [18]: File 1
                           [19]: File 1
                           [20]: File 1
                           [21]: File 1
                           [22]: File 1
                           [23]: File 1
                           [24]: File 1
                           [25]: File 1
                           [26]: File 1
                           [27]: File 1
                           [28]: File 1
                           [29]: File 1
                           [30]: File 1
                           [31]: File 1
                           [32]: File 1
                           [33]: File 1
                           [34]: File 1
                           [35]: File 1
                           [36]: File 1
                           [37]: File 1
                           [38]: File 1
                           [39]: File 1
                           [40]: File 1
                           [41]: File 1
                           [42]: File 1
                           [43]: File 1
                           [44]: File 1
                           [45]: File 1
                           [46]: File 1
                           [47]: File 1
                           [48]: File 1
                           [49]: File 1
                           [50]: File 1
                           [51]: File 1
                           [52]: File 1
                           [53]: File 1
                           [54]: File 1
                           [55]: File 1
                           [56]: File 1
                           [57]: File 1
                           [58]: File 1
                           [59]: File 1
                           [60]: File 1
                           [61]: File 1
                           [62]: File 1
                           [63]: File 1
                           [64]: File 1
                           [65]: File 1
                           [66]: File 1
                           [67]: File 1
                           [68]: File 1
                           [69]: File 1
                           [70]: File 1
                           [71]: File 1
                           [72]: File 1
                           [73]: File 1
                           [74]: File 1
                           [75]: File 1
                           [76]: File 1
                           [77]: File 1
                           [78]: File 1
                           [79]: File 1
                           [80]: File 1
                           [81]: File 1
                           [82]: File 1
                           [83]: File 1
                           [84]: File 1
                           [85]: File 1
                           [86]: File 1
                           [87]: File 1
                           [88]: File 1
                           [89]: File 1
                           [90]: File 1
                           [91]: File 1
                           [92]: File 1
                           [93]: File 1
                           [94]: File 1
                           [95]: File 1
                           [96]: File 1
                           [97]: File 1
                           [98]: File 1
                           [99]: File 1
                           [100]: File 1
                           [101]: File 1
                           [102]: File 1
                           [103]: File 1
                           [104]: File 1
                           [105]: File 1
                           [106]: File 1
                           [107]: Q147222
                           [108]: KB933854 - QFE
                           [109]: KB953298 - QFE
                           [110]: SP1 - SP
                           [111]: Q954430
                           [112]: Q973688
                           [113]: IDNMitigationAPIs - Update
                           [114]: NLSDownlevelMapping - Update
                           [115]: KB925398_WMP64
                           [116]: KB938127-IE7 - Update
                           [117]: KB976325-IE7 - Update
                           [118]: KB978207-IE7 - Update
                           [119]: KB980182-IE7 - Update
                           [120]: KB971513 - Update
                           [121]: KB914961 - Service Pack
                           [122]: KB926139-v2
                           [123]: KB915800-v9 - Update
                           [124]: KB923561 - Update
                           [125]: KB924667-v2 - Update
                           [126]: KB925876 - Update
                           [127]: KB925902-v2 - Update
                           [128]: KB926122 - Update
                           [129]: KB927891 - Update
                           [130]: KB929123 - Update
                           [131]: KB930178 - Update
                           [132]: KB932168 - Update
                           [133]: KB933729 - Update
                           [134]: KB933854 - Update
                           [135]: KB936782 - Update
                           [136]: KB938464-v2 - Update
                           [137]: KB938759-v4 - Update
                           [138]: KB941569 - Update
                           [139]: KB942830 - Update
                           [140]: KB942831 - Update
                           [141]: KB943055 - Update
                           [142]: KB943460 - Update
                           [143]: KB944338-v2 - Update
                           [144]: KB944653 - Update
                           [145]: KB945553 - Update
                           [146]: KB946026 - Update
                           [147]: KB948496 - Update
                           [148]: KB950760 - Update
                           [149]: KB950762 - Update
                           [150]: KB950974 - Update
                           [151]: KB951066 - Update
                           [152]: KB951748 - Update
                           [153]: KB952004 - Update
                           [154]: KB952069 - Update
                           [155]: KB952954 - Update
                           [156]: KB953298 - Update
                           [157]: KB954155 - Update
                           [158]: KB954600 - Update
                           [159]: KB955069 - Update
                           [160]: KB955759 - Update
                           [161]: KB955839 - Update
                           [162]: KB956572 - Update
                           [163]: KB956744 - Update
                           [164]: KB956802 - Update
                           [165]: KB956803 - Update
                           [166]: KB956844 - Update
                           [167]: KB957097 - Update
                           [168]: KB958469 - Update
                           [169]: KB958644 - Update
                           [170]: KB958687 - Update
                           [171]: KB958690 - Update
                           [172]: KB958869 - Update
                           [173]: KB959426 - Update
                           [174]: KB960225 - Update
                           [175]: KB960803 - Update
                           [176]: KB960859 - Update
                           [177]: KB961063 - Update
                           [178]: KB961118 - Update
                           [179]: KB961373 - Update
                           [180]: KB961501 - Update
                           [181]: KB967715 - Update
                           [182]: KB967723 - Update
                           [183]: KB968389 - Update
                           [184]: KB968816 - Update
                           [185]: KB969059 - Update
                           [186]: KB969947 - Update
                           [187]: KB970238 - Update
                           [188]: KB970430 - Update
                           [189]: KB970483 - Update
                           [190]: KB971032 - Update
                           [191]: KB971468 - Update
                           [192]: KB971657 - Update
                           [193]: KB971737 - Update
                           [194]: KB971961 - Update
                           [195]: KB972270 - Update
                           [196]: KB973037 - Update
                           [197]: KB973354 - Update
                           [198]: KB973507 - Update
                           [199]: KB973540 - Update
                           [200]: KB973687 - Update
                           [201]: KB973815 - Update
                           [202]: KB973869 - Update
                           [203]: KB973904 - Update
                           [204]: KB973917-v2 - Update
                           [205]: KB974112 - Update
                           [206]: KB974318 - Update
                           [207]: KB974392 - Update
                           [208]: KB974571 - Update
                           [209]: KB975025 - Update
                           [210]: KB975467 - Update
                           [211]: KB975560 - Update
                           [212]: KB975713 - Update
                           [213]: KB977165-v2 - Updat
Network Card(s):           2 NIC(s) Installed.
                           [01]: AMD PCNET Family PCI Ethernet Adapter
                                 Connection Name: Local Area Connection
                                 DHCP Enabled:    No
                                 IP address(es)
                                 [01]: 10.10.0.1
                           [02]: AMD PCNET Family PCI Ethernet Adapter
                                 Connection Name: Local Area Connection 2
                                 Status:          Media disconnected

TESTS PERFORMED (Ubuntu 10.04 Beta 2)

name@name-laptop:~$ ping 10.10.0.1
PING 10.10.0.1 (10.10.0.1) 56(84) bytes of data.
64 bytes from 10.10.0.1: icmp_seq=1 ttl=128 time=44.9 ms
64 bytes from 10.10.0.1: icmp_seq=2 ttl=128 time=1.97 ms
64 bytes from 10.10.0.1: icmp_seq=3 ttl=128 time=2.13 ms
64 bytes from 10.10.0.1: icmp_seq=4 ttl=128 time=3.97 ms
^C
--- 10.10.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3016ms
rtt min/avg/max/mdev = 1.970/13.263/44.977/18.327 ms

name@name-laptop:~$ telnet 10.10.0.1 389
Trying 10.10.0.1...
Connected to 10.10.0.1.
Escape character is '^]'.

Connection closed by foreign host.

name@name-laptop:~$ nslookup name.dnsname.local
Server:        10.10.0.1
Address:    10.10.0.1#53

Name:    name.dnsname.local
Address: 10.10.0.1

name@name-laptop:~/Desktop/id$ nslookup -q=srv _ldap._tcp.dnsname.local
Server:        10.10.0.1
Address:    10.10.0.1#53

_ldap._tcp.dnsname.local    service = 0 100 389 name.dnsname.local.

name@name-laptop:~/Desktop/id$ nslookup -q=srv _ldap._tcp.gc._msdcs.dnsname.local
Server:        10.10.0.1
Address:    10.10.0.1#53

_ldap._tcp.gc._msdcs.dnsname.local    service = 0 100 3268 name.dnsname.local.

name@name-laptop:~/Desktop/id$ sudo domainjoin-cli --loglevel info --log . join dnsname.local Administrator
20100411163246:INFO:Domainjoin invoked with the join command (remaining arguments will be printed later):
20100411163246:INFO:    [domainjoin-cli]
20100411163246:INFO:    [--loglevel]
20100411163246:INFO:    [info]
20100411163246:INFO:    [--log]
20100411163246:INFO:    [.]
20100411163246:INFO:    [join]
20100411163246:INFO:Checking status of daemon [/etc/init.d/lwsmd]
20100411163246:INFO:Daemon [/etc/init.d/lwsmd]: status [0]
20100411163247:INFO:Checking status of daemon [/etc/init.d/lwsmd]
20100411163247:INFO:Daemon [/etc/init.d/lwsmd]: status [0]
20100411163247:INFO:Checking status of daemon [/etc/init.d/lwregd]
20100411163248:INFO:Daemon [/etc/init.d/lwregd]: status [0]
20100411163248:INFO:Checking status of daemon [/etc/init.d/lwregd]
20100411163248:INFO:Daemon [/etc/init.d/lwregd]: status [0]
20100411163248:INFO:Checking status of daemon [/etc/init.d/netlogond]
20100411163248:INFO:Daemon [/etc/init.d/netlogond]: status [0]
20100411163249:INFO:Checking status of daemon [/etc/init.d/netlogond]
20100411163249:INFO:Daemon [/etc/init.d/netlogond]: status [0]
20100411163249:INFO:Checking status of daemon [/etc/init.d/lwiod]
20100411163249:INFO:Daemon [/etc/init.d/lwiod]: status [0]
20100411163249:INFO:Checking status of daemon [/etc/init.d/lwiod]
20100411163249:INFO:Daemon [/etc/init.d/lwiod]: status [0]
20100411163249:INFO:Checking status of daemon [/etc/init.d/dcerpcd]
20100411163250:INFO:Daemon [/etc/init.d/dcerpcd]: status [0]
20100411163250:INFO:Checking status of daemon [/etc/init.d/dcerpcd]
20100411163250:INFO:Daemon [/etc/init.d/dcerpcd]: status [0]
20100411163250:INFO:Checking status of daemon [/etc/init.d/eventlogd]
20100411163250:INFO:Daemon [/etc/init.d/eventlogd]: status [0]
20100411163251:INFO:Checking status of daemon [/etc/init.d/eventlogd]
20100411163251:INFO:Daemon [/etc/init.d/eventlogd]: status [0]
20100411163251:INFO:Checking status of daemon [/etc/init.d/lsassd]
20100411163251:INFO:Daemon [/etc/init.d/lsassd]: status [0]
20100411163251:INFO:Checking status of daemon [/etc/init.d/lsassd]
20100411163252:INFO:Daemon [/etc/init.d/lsassd]: status [0]
20100411163252:INFO:Domainjoin invoked with 2 arg(s) to the join command:
20100411163252:INFO:    [dnsname.local]
20100411163252:INFO:    [Administrator]
20100411163252:INFO:Adding name-laptop (fqdn name-laptop.dnsname.local) to /etc/hosts ip 127.0.1.1, removing name-laptop, name-laptop.dnsname.local, name-laptop, name-laptop.dnsname.local
20100411163252:INFO:Reading krb5 file /tmp/likewisetmpYBkEEA/etc/krb5.conf
20100411163252:INFO:Reading nsswitch file /etc/nsswitch.conf
20100411163252:INFO:Reading krb5 file /tmp/likewisetmpG4kuyN/etc/krb5.conf
20100411163252:INFO:Found config file /etc/ssh/ssh_config
20100411163252:INFO:Found binary /usr/bin/ssh
20100411163252:INFO:Reading ssh file /etc/ssh/ssh_config
20100411163252:INFO:Testing option GSSAPIAuthentication
20100411163252:INFO:Testing option GSSAPIDelegateCredentials
20100411163252:INFO:Option GSSAPIDelegateCredentials supported
Joining to AD Domain:   dnsname.local
With Computer DNS Name: name-laptop.dnsname.local

Administrator@DNSNAME.LOCAL's password:
20100411163256:INFO:Running module join
20100411163256:INFO:Starting krb5.conf configuration (enabling)
20100411163256:INFO:Reading krb5 file /tmp/likewisetmpzXfYHa/etc/krb5.conf
20100411163256:WARNING:Short domain name not specified. Defaulting to 'dnsname'
20100411163256:INFO:Creating krb5 stanza 'appdefaults'
20100411163256:INFO:Writing krb5 file /tmp/likewisetmpzXfYHa/etc/krb5.conf
20100411163256:INFO:File /tmp/likewisetmpzXfYHa/etc/krb5.conf modified
20100411163256:INFO:Finishing krb5.conf configuration

Error: Lsass Error [code 0x00080047]

40286 (0x9D5E) LW_ERROR_LDAP_SERVER_DOWN - Unknown error
20100411163307:ERROR:Lsass Error [CENTERROR_DOMAINJOIN_LSASS_ERROR]

40286 (0x9D5E) LW_ERROR_LDAP_SERVER_DOWN - Unknown error

Stack Trace:
main.c:938
main.c:479
djmodule.c:323
djauthinfo.c:843
djauthinfo.c:1187

---

### Post by rusivi on 2010-04-12
Submitted Ubuntu bug:

https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/561878

---

### Post by rusivi on 2010-04-12
Problem solved as per bug: 

[https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/561878](https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/561878)

---

