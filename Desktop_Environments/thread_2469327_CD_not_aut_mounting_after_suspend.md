---
title: "CD not aut mounting after suspend"
date: 2021-11-26
forum: Desktop Environments
---

### Post by lister171254 on 2021-11-26
I have upgraded to Ubuntu 21.10 (64bit) and noticed that if I load a CD, the cd is auto mounted (expected)

This doesn't happen when I restart after suspending.

---

### Post by ActionParsnip on 2021-11-26
Can you manually mount it OK?

---

### Post by lister171254 on 2021-11-26
yep, manual mount works.
I'd just like to know why it wouldn't after the suspend

---

### Post by ActionParsnip on 2021-11-27
OK. Next time you put a CD in and it doesn't mount, press CTRL + ALT + T and run
```

dmesg -T | tail

```
What is the output please?

---

### Post by lister171254 on 2021-11-27
sudo dmesg -THw

shows 

```
[  +0.000410] sd 0:0:0:0: [sda] Starting disk
[  +0.000001] sd 1:0:0:0: [sdb] Starting disk
[  +0.000000] sd 2:0:0:0: [sdc] Starting disk
[  +0.000001] sd 3:0:0:0: [sdd] Starting disk
[  +0.022129] usb usb3: root hub lost power or was reset
[  +0.000002] usb usb4: root hub lost power or was reset
[  +0.112666] r8169 0000:04:00.0 enp4s0: Link is Down
[  +0.178915] ata6: SATA link down (SStatus 0 SControl 330)
[  +0.113668] usb 1-8: reset full-speed USB device number 4 using xhci_hcd
[  +0.047768] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  +0.000024] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  +0.001620] ata4.00: configured for UDMA/133
[  +0.015964] ata5.00: configured for UDMA/133
[  +0.295149] usb 1-3: reset full-speed USB device number 3 using xhci_hcd
[  +0.492016] usb 1-2: reset high-speed USB device number 2 using xhci_hcd
[  +0.371091] OOM killer enabled.
[  +0.000002] Restarting tasks ... done.
[  +0.000882] PM: suspend exit
[  +2.091283] r8169 0000:04:00.0 enp4s0: Link is Up - 1Gbps/Full - flow control rx/tx
[  +5.316082] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  +0.000030] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  +0.055967] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  +0.044699] ata1.00: configured for UDMA/133
[  +0.017331] ata3.00: configured for UDMA/133
[  +0.048414] ata2.00: configured for UDMA/133
[  +0.253729] rfkill: input handler disabled
[  +1.043839] audit: type=1400 audit(1638055536.041:45): apparmor="DENIED" operation="capable" profile="/usr/sbin/cupsd" pid=34644 comm="cupsd" capability=12  capname="net_admin"
[  +0.120724] audit: type=1400 audit(1638055536.161:46): apparmor="DENIED" operation="capable" profile="/usr/sbin/cups-browsed" pid=34702 comm="cups-browsed" capability=23  capname="sys_nice"
[ +16.712229] [UFW BLOCK] IN=enp4s0 OUT= MAC=01:00:5e:00:00:01:34:e8:94:7b:10:c0:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[Nov28 10:27] [UFW BLOCK] IN=enp4s0 OUT= MAC=01:00:5e:00:00:01:34:e8:94:7b:10:c0:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[Nov28 10:30] [UFW BLOCK] IN=enp4s0 OUT= MAC=01:00:5e:00:00:01:34:e8:94:7b:10:c0:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[Nov28 10:32] [UFW BLOCK] IN=enp4s0 OUT= MAC=01:00:5e:00:00:01:34:e8:94:7b:10:c0:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 

```

when I load the CD

---

