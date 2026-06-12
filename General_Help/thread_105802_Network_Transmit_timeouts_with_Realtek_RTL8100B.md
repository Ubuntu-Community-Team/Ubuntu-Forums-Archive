---
title: "Network Transmit timeouts with Realtek RTL8100B"
date: 2005-12-19
forum: General Help
---

### Post by gaston_123 on 2005-12-19
I have a problem with my RealTek RTL8100B card. When I do more than one thing at the same time, eg. download something and start pinging a host, it completely stops responding and stays like that for some time.  The output of ping for example then usually sooks like that:

> PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=9389 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=8389 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=255 time=7389 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=255 time=6390 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=255 time=5390 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=255 time=4391 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=255 time=3391 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=255 time=2391 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=255 time=1392 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=255 time=392 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=255 time=3.90 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=255 time=0.371 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=255 time=0.353 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=255 time=0.351 ms
...


After a using the (painfully slow) network card for a while, dmesg is full of entries like this one:

> [4294787.125000] NETDEV WATCHDOG: eth0: transmit timed out
[4294787.125000] eth0: Transmit timeout, status 01 0000 0000 media 10.
[4294787.125000] eth0: Tx queue start entry 13  dirty entry 9.
[4294787.125000] eth0:  Tx descriptor 0 is 00002000.
[4294787.125000] eth0:  Tx descriptor 1 is 00002000. (queue head)
[4294787.125000] eth0:  Tx descriptor 2 is 00002000.
[4294787.125000] eth0:  Tx descriptor 3 is 00002000.
[4294787.125000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4295123.125000] NETDEV WATCHDOG: eth0: transmit timed out


The interesting thing is, that these problems only appear with Ubuntu Breezy 5.10. With both Ubuntu Hoary 5.04 (I unfortunately deleted it...) and OpenBSD  I never experienced that problem. 

I of course searched the forum and tried out a couple of things. nothing really helped:
- unloaded (rmmod) the modules 8139cp and 8139too and loaded (modprobe) 8139too only.
- changed in "/1tc/modprobe.d/aliases" "alias net-pf-10 ipv6" to "alias net-pf-10 off"  
- turned acpi off in BIOS
- booted with "acpi=off"

Can someone help me? :confused:

---

### Post by arx-lupus on 2005-12-19
I know this isn't going to help fix it but... I had exactly the same errors in dmesg from an Nforce3 onboard Gigabit NIC.

Although mine generally worked for a couple of minutes before going pear-shaped. Mine was on Slackware 10 and Warty and on Hoary when it was released - only way around it was to use a different NIC.

---

### Post by gaston_123 on 2005-12-20
Thank you for your quick reply!

Using a different NIC does not work for me. The Mainboard (a mini-itx) I use does not have any expansion slots. So either I get that card working or I have to buy a new mainboard.

---

### Post by ewoox on 2006-06-12
try booting kernel with parameters: acpi=force pci=noacpi

---

