---
title: "Wireshark doesn't detect interface"
date: 2011-11-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by luckysanj on 2011-11-09
Wireshark does not detect my any interface but interface card is working properly..

With each reboot I got all my laptop interface  are in block state.

root@jupiter:~# rfkill ist
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: yesI need your suggestion.
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

So i have to do manually unblock all interface every time & it is  irritating me &  I want to know what happen with my system why the  interface are automatically block in each reboot & because of this my wireshark or EtherApe also doesn't show the interface

Suggest will be highly appreciated...

Thanks

---

### Post by Khaledbaqer on 2011-11-09
Are you giving Wireshark root priviledges? Wireshark needs root privilege to access network interfaces. Run it from the terminal with sudo and see if that works.

This is my first post, hope it's helpful :)

---

### Post by luckysanj on 2011-11-10
Thank you so much [Khaledbaqer]("http://ubuntuforums.org/member.php?u=1490630") it works perfectly...

---

### Post by rocklobster217 on 2011-11-27
[FONT=Tahoma]## WARNING ## Wireshark does not require  root   privileges to capture packets and should not be run this way; only   dumpcap requires root  privileges [[1]]("http://wiki.wireshark.org/Security").

The documented method [[2]]("http://wiki.wireshark.org/CaptureSetup/CapturePrivileges") is summarized below and can be run via command line:[/FONT]
```
[FONT=Courier New]sudo chgrp wireshark /usr/bin/dumpcap  
sudo chmod 754 /usr/bin/dumpcap
sudo setcap 'CAP_NET_RAW+eip CAP_NET_ADMIN+eip' /usr/bin/dumpcap[/FONT]
```[FONT=Tahoma]
This command is extra but required; adds your username to the wireshark group.[/FONT][FONT=Courier New][FONT=Tahoma]
[/FONT]```
sudo usermod -a -G wireshark *<your-username-here>*
```[/FONT][FONT=Tahoma]
Log Out or Reboot for changes to take affect. 

Please ensure Wireshark works only from root and from a user in the "wireshark" group.[/FONT]
[FONT=Tahoma]
Regards, David Chute.
[U]
Sources:[/U]
[I][[1]]("http://wiki.wireshark.org/Security") [http://wiki.wireshark.org/Security](http://wiki.wireshark.org/Security)
[[2]]("http://wiki.wireshark.org/CaptureSetup/CapturePrivileges") [http://wiki.wireshark.org/CaptureSetup/CapturePrivileges](http://wiki.wireshark.org/CaptureSetup/CapturePrivileges)[/I][/FONT]

---

