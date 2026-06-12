---
title: "CUPS problem, microphone doesn't work in 6.06 &amp; DNS problem"
date: 2006-06-09
forum: Desktop Environments
---

### Post by JeyKey on 2006-06-09
Hi, I've got 3 problems I'd like some help solving, which I've haven't been able to fix. 

First of all, after i installed 6.06, I've been unable to install my printer. It worked fine in 5.10, but this happens in Dapper:
[IMG]http://80.203.31.175/ubuntuforums/english/cups.png[/IMG]
I can't select a printer port, which worked fine in breezy. Any ideas on how to solve this?

My second problem is about my microphone, which hasn't worked since I converted to Ubuntu from XP. It's a Logitech USB microphone. I've been searching for a solution to this for a long time, but haven't found anything.
```
hakon@dapper:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 004: ID 046d:c509 Logitech, Inc.
Bus 002 Device 003: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 002 Device 001: ID 0000:0000

```
That's my microphone, the AK5370. It doesn't show up in Audacity, the only record source i can choose is /dev/dsp. It shows up in GNOME Volume Control, but it doesn't capture any sound.

My third issue is about using local domain names on the network, which doesn't work in Dapper. When I log into my router (3Com 3CRWE554G72), this is the list of DHCP clients:
[IMG]http://80.203.31.175/ubuntuforums/english/utklipp.png[/IMG]
The router's IP: 192.168.1.1
My IP adress: 192.168.1.247
My sister's IP: 192.168.1.167

My sister runs XP, and has a DNS name which is working across the network. I've been trying to set up my IP with a domain name, but I'm obviously doing something wrong:
[IMG]http://80.203.31.175/ubuntuforums/english/network_general.png[/IMG][IMG]http://80.203.31.175/ubuntuforums/english/network_dns.png[/IMG][IMG]http://80.203.31.175/ubuntuforums/english/network_hosts.png[/IMG]
I've no idea how to configure this, so the problem is probably rather apparent. Any ideas?

Thanks in advance!

---

### Post by not_yet on 2006-06-09
ok, only 1 out of 3 :-| 

for your printer problem try this from the terminal

sudo foomatic-cleanupdrivers

---

### Post by JeyKey on 2006-06-10
Didn't work, still unable to select printer port.

---

