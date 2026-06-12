---
title: "Message in ubuntu (don´t know what means)"
date: 2009-01-31
forum: General Help
---

### Post by demlasjr on 2009-01-31
When I checked dmesg on my ubuntu I receive this messages, I don´t know what means and how to resolve. Everything look to be ok and I don´t have problems, but I hate this "spams". This are the messages:
[320998.334830] cdrom: This disc doesn't have any tracks I recognize!
[320998.729692] end_request: I/O error, dev sr0, sector 0
[320998.729712] Buffer I/O error on device sr0, logical block 0
[320998.737656] end_request: I/O error, dev sr0, sector 0
[320998.737673] Buffer I/O error on device sr0, logical block 0
[321662.429517] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[321662.429540] ata2.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[321662.429542]          cdb 1b 00 00 00 02 00 00 00  00 00 00 00 00 00 00 00
[321662.429544]          res 40/00:02:00:08:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[321662.429549] ata2.01: status: { DRDY }
[321663.140050] ata2: soft resetting link
[321663.551009] ata2.01: configured for UDMA/33
[321663.551081] ata2: EH complete
[321663.926214] Buffer I/O error on device sr0, logical block 1135904
[321663.943115] Buffer I/O error on device sr0, logical block 1135904
[321663.943507] Buffer I/O error on device sr0, logical block 12
[321663.943516] Buffer I/O error on device sr0, logical block 13
[321663.943520] Buffer I/O error on device sr0, logical block 14
[321663.943525] Buffer I/O error on device sr0, logical block 15
[321663.943529] Buffer I/O error on device sr0, logical block 16
[321663.943533] Buffer I/O error on device sr0, logical block 17
[321663.943538] Buffer I/O error on device sr0, logical block 18
[321663.943542] Buffer I/O error on device sr0, logical block 19
[324039.499687] __ratelimit: 11 callbacks suppressed
[324039.499698] type=1503 audit(1233351648.608:98): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[325964.358903] cdrom: This disc doesn't have any tracks I recognize!
[325964.673466] end_request: I/O error, dev sr0, sector 0
[325964.673484] Buffer I/O error on device sr0, logical block 0
[325964.680318] end_request: I/O error, dev sr0, sector 0
[325964.680340] Buffer I/O error on device sr0, logical block 0
[327549.650103] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[327549.650131] ata2.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[327549.650134]          cdb 1b 00 00 00 02 00 00 00  00 00 00 00 00 00 00 00
[327549.650136]          res 40/00:02:00:08:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[327549.650141] ata2.01: status: { DRDY }
[327550.370067] ata2: soft resetting link
[327550.780316] ata2.01: configured for UDMA/33
[327550.780369] ata2: EH complete
[327551.652556] Buffer I/O error on device sr0, logical block 1142904
[327551.672320] Buffer I/O error on device sr0, logical block 1142904
[327551.672541] Buffer I/O error on device sr0, logical block 1142934
[327551.672565] Buffer I/O error on device sr0, logical block 1142934
[327551.672602] Buffer I/O error on device sr0, logical block 1142935
[327551.672621] Buffer I/O error on device sr0, logical block 1142935
[327551.672648] Buffer I/O error on device sr0, logical block 1142935
[327551.672728] Buffer I/O error on device sr0, logical block 0
[327551.672761] Buffer I/O error on device sr0, logical block 0
[327551.672787] Buffer I/O error on device sr0, logical block 0
[327639.499699] __ratelimit: 7 callbacks suppressed
[327639.499709] type=1503 audit(1233355248.608:99): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[329443.142033] ppdev0: registered pardevice
[329443.142689] ppdev0: unregistered pardevice
[329445.780967] ppdev0: registered pardevice
[329445.822150] ppdev0: unregistered pardevice
[331239.499787] type=1503 audit(1233358848.608:100): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[334839.499754] type=1503 audit(1233362448.608:101): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[338439.500076] type=1503 audit(1233366048.618:102): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[342039.499831] type=1503 audit(1233369648.608:103): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[345639.499851] type=1503 audit(1233373248.608:104): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[349239.499908] type=1503 audit(1233376848.608:105): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[352839.499932] type=1503 audit(1233380448.608:106): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[356439.500060] type=1503 audit(1233384048.618:107): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[360039.500330] type=1503 audit(1233387648.618:108): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[363639.500323] type=1503 audit(1233391248.618:109): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[363942.173807] i801_smbus 0000:00:1f.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[363944.679537] i2c /dev entries driver
[366059.760788] ppdev0: registered pardevice
[366059.800649] ppdev0: unregistered pardevice
[366061.250459] ppdev0: registered pardevice
[366061.290063] ppdev0: unregistered pardevice
[366061.424147] ppdev0: registered pardevice
[366061.460650] ppdev0: unregistered pardevice
[367239.500139] type=1503 audit(1233394848.618:110): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[370839.500134] type=1503 audit(1233398448.618:111): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[374439.500177] type=1503 audit(1233402048.618:112): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[378039.500304] type=1503 audit(1233405648.618:113): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[381639.500274] type=1503 audit(1233409248.618:114): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[385239.500324] type=1503 audit(1233412848.618:115): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[388839.500409] type=1503 audit(1233416448.618:116): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[392439.500383] type=1503 audit(1233420048.618:117): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"
[396039.500376] type=1503 audit(1233423648.618:118): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"



How to resolve this problem. thanks in advance.

---

### Post by cariboo on 2009-01-31
It looks like you've got a bad cdrom, or cdrom drive. You aslo got something on your paralell port that is trying  to use ipv6 to connect.

Jim

---

### Post by demlasjr on 2009-01-31
interesting. I have a dvd-rw connected and is working perfect. I have a sata hdd connected with a sata-to-usb cable. This can be the problem ? Also I don't have any port with need to be connected at ipv6. I have only a network card. Is strange. If nothings happening after this messages I will leave them. I wanna be sure everythings is fine.
thanks for informations.

---

### Post by lavinog on 2009-04-03
> **demlasjr said:**
> 
[392439.500383] type=1503 audit(1233420048.618:117): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4630/net/if_inet6" pid=4631 profile="/usr/sbin/named"

I don't see anything about a parallel port.
I am getting the same message though on my server...It is repeated every hour.

---

### Post by demlasjr on 2009-04-03
I resolved the problem: Change my server with debian. If you check in problem section I write about other problems and nobody answer for it. So....I was sick using the Ubuntu 8.xx and I changed with Debian Lenny. I never get this errors, I don't have any problem and I have the same things like in ubuntu. Sometimes Ubuntu show me blackscreen if I used startx, now I don't have this problem and also my resolution is more biggest than in ubuntu. The desavantage is the apt-get function because can't give you suggest when you type a package wrong. The last cup in ubuntu was when I received a message with impossibility to connect to universe main server (cannot find the package, but the package was there, when using apt-get update command). I found other people with this error in this forum. I changed the server but nothing, so...i changed the OS :) Now the use of system's rams and processors is more low like with ubuntu

---

### Post by semenzato on 2009-06-08
Apparently this is caused by a bug in the apparmor configuration:

[https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/289060/+activity](https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/289060/+activity)

The suggested fix is to edit /etc/apparmor.d/usr.sbin.named and change the line

  /proc/net/if_inet6 r,

to

  /proc/**/net/if_inet6 r,

then restart apparmor and bind9.

---

