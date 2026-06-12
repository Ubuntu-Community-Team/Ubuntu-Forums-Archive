---
title: "USB pendrive not mounting after upgrade to 11.10 DELL XPS 15"
date: 2011-11-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by antonioclopesmd on 2011-11-10
USB pendrives and my HP printer used to automount once plugged, in Ubuntu 11.04. Ever since I uograded Ubuntu to 11.10, pendrives and printers don't mount in different USB ports. The only way to access my USB pendrive is by booting the computer with the pendrive plugged in. 
Can anyone help me please?

lsusb lists:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0408:2fb1 Quanta Computer, Inc. 
Bus 002 Device 003: ID 8086:0189 Intel Corp. 
Bus 003 Device 002: ID 05dc:a764 Lexar Media, Inc. 

and dmesg | tail:
[ 1307.271643] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = f4:ec:38:cd:92:bc tid = 6
[ 3539.435431] [UFW AUDIT] IN= OUT=lo SRC=0000:0000:0000:0000:0000:0000:0000:0001 DST=0000:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=TCP SPT=59299 DPT=631 WINDOW=16376 RES=0x00 SYN URGP=0 
[ 3539.435445] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0001 DST=0000:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=TCP SPT=59299 DPT=631 WINDOW=16376 RES=0x00 SYN URGP=0 
[ 5865.798125] usb 3-1: new high speed USB device number 2 using xhci_hcd
[ 5865.817762] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
[ 5865.818547] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
[ 5865.819297] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
[ 5865.820297] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
[ 7038.314077] [UFW AUDIT] IN= OUT=lo SRC=0000:0000:0000:0000:0000:0000:0000:0001 DST=0000:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=TCP SPT=59540 DPT=631 WINDOW=16376 RES=0x00 SYN URGP=0 
[ 7038.314091] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0001 DST=0000:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=TCP SPT=59540 DPT=631 WINDOW=16376 RES=0x00 SYN URGP=0 


(Lexar is my pendrive)

---

