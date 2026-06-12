---
title: "Debian 9 - Networking issues"
date: 2018-06-18
forum: Debian
---

### Post by skyluke.1987 on 2018-06-18
[COLOR=#000000]Dear all, I would need some advice on the following: [/COLOR]

[COLOR=#000000]1. SELKS 4.0 desktop.[/COLOR]
[COLOR=#000000]2. Installed on physical server.[/COLOR]
[COLOR=#000000]3. /etc/network/interface (File settings)[/COLOR]
[COLOR=#000000]> auto lo[/COLOR]
[COLOR=#000000]iface lo inet loopback[/COLOR]

[COLOR=#000000]iface eno1 inet static [/COLOR]
[COLOR=#000000]address 10.0.106.61[/COLOR]
[COLOR=#000000]netmask 255.255.255.0[/COLOR]
[COLOR=#000000]network 10.0.106.0[/COLOR]
[COLOR=#000000]broadcast 10.0.106.255[/COLOR]
[COLOR=#000000]gateway 10.0.106.1[/COLOR]
[COLOR=#000000]4. sudo vim /etc/resolv.conf (Settings with nameservers)[/COLOR]

[COLOR=#000000]When I run ifup eno1, RTNETLINK answers: File exists, ifup: failed to bring up eno1.[/COLOR]
[COLOR=#000000]"Network not configured" error displayed. [/COLOR]
[COLOR=#000000]Run "ifconfig" only displaying one network which is "lo"[/COLOR]

[COLOR=#000000]Run "cd /etc/network >> ls"[/COLOR]
[COLOR=#000000]- eno1[/COLOR]
[COLOR=#000000]- eno2[/COLOR]
[COLOR=#000000]- eno3 [/COLOR]
[COLOR=#000000]- eno4[/COLOR]
[COLOR=#000000]- lo[/COLOR]

[COLOR=#000000]Run "cd /etc/network >> ls"[/COLOR]
[COLOR=#000000]- if-down.d[/COLOR]
[COLOR=#000000]- if-post-down.d[/COLOR]
[COLOR=#000000]- if-pre-up.d[/COLOR]
[COLOR=#000000]- if-up.d[/COLOR]
[COLOR=#000000]- interfaces[/COLOR]
[COLOR=#000000]- interfaces.d[/COLOR]

[COLOR=#000000]Restarted network settings: service networking restart[/COLOR]

[COLOR=#000000]..... After performing all the above, including a system reboot, there is still no network on the machine. Kindly advise.[/COLOR]

---

### Post by oldfred on 2018-06-18
Did you manually retype or use cat to display data?
As this has an extra space.
[COLOR=#000000]broadcast 10.0. 106.255[/COLOR]

---

### Post by skyluke.1987 on 2018-06-19
Its typo/. please ignore that.

Updates: 
ifconfig result: lo, inet 127.0.0.1 / netmask 255.0.0.0
SSH from other server: timeout, cannot connect - port 22
Route -n: no result 
[COLOR=#242729][FONT=Arial]ifup eno1: RTNETLINK answer: File exist, failed to bring up eno1.[/FONT][/COLOR]

---

### Post by oldos2er on 2018-06-19
Moved to Debian.

---

### Post by skyluke.1987 on 2018-06-19
Have anyone faced Debian network issue like this? Understand that its a based OS and Ubuntu is based on this Debian, in certain ways it is smarted compared to Debian, and certain processes are automated. I have also came across this link, [https://packages.debian.org/stretch/network-manager](https://packages.debian.org/stretch/network-manager), is it something I missed out to install this network manager manually?

---

