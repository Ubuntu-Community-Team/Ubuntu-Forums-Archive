---
title: "DHCP release IP adres"
date: 2005-06-10
forum: Desktop Environments
---

### Post by cotcot on 2005-06-10
Last week I installed Kubuntu to compare to Suse 9.2. First impression is fine.
As I switch sometimes between 2 computers (1 with XP and 1 with Win98 - Suse 9.2 and Kubuntu). In XP the IP release is done with 'ipconfig /release' in the command mode.
I am currently searching how to release the IP adres form a DHCP internet connection in Kubuntu when I go from Kubuntu to XP. For Suse it worked perfect with the command 'dhcpcd -k' in the console. For Kubuntu I guess it is 'dhclient -r -pf ... '.  Can anybody tell me more ?
Thanks

---

### Post by defkewl on 2005-06-10
So you want to get Dynamic IP for your Kubuntu client? Does your ISP support DHCP?

---

### Post by cotcot on 2005-06-10
[QUOTE=defkewl]So you want to get Dynamic IP for your Kubuntu client? Does your ISP support DHCP?[/QUOTE]

I have a cable connection (Telenet Belgium). It supports DHCP. It is no problem to get an IP in Kubuntu, XP or Suse. I released quite often the IP with the commands mentioned last year in Suse and XP. Earlier also with Mandrake 10.0 with /sbin/dhclient -r -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp/dhclient-eth0.leases eth0. But I do not know whether these options are OK for Kubuntu.

Thanks

---

### Post by cotcot on 2005-06-12
[QUOTE=cotcot]I have a cable connection (Telenet Belgium). It supports DHCP. It is no problem to get an IP in Kubuntu, XP or Suse. I released quite often the IP with the commands mentioned last year in Suse and XP. Earlier also with Mandrake 10.0 with /sbin/dhclient -r -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp/dhclient-eth0.leases eth0. But I do not know whether these options are OK for Kubuntu.

Thanks[/QUOTE]
Problem is solved by installing DHCPCD and uninstalling DHCLIENT. The command in DHCPCD is '/sbin/dhcpcd -k eth0'.

---

