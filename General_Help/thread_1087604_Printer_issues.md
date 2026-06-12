---
title: "Printer issues"
date: 2009-03-05
forum: General Help
---

### Post by cezarica on 2009-03-05
Hi.

I'm on Ubuntu 8.10 and just installed HPLip version 3.9.2 on CUPS version 1.3.9. My printer HP LaserJet P30005 prints a file (or a 'job') then connection between the PC and the printer is lost. Haven't touched the USB cable nor stoped the printer or anything like this.

Upon doing a 'dmesg |tail' i see:

[ 4761.848170] usb 1-2.1: new high speed USB device using ehci_hcd and address 12
[ 4761.952016] usb 1-2.1: configuration #1 chosen from 1 choice
[ 4761.960680] usblp0: USB Bidirectional printer dev 12 if 0 alt 1 proto 2 vid 0x03F0 pid 0x7317
[ 4763.753310] usblp0: removed

If I'd unplug the cable and then replug the printer back, the printer will then print another file (or job) then the connection dies again. What should I do to make this damn thing work? :(

---

### Post by cezarica on 2009-03-06
I even installed a new firmware for the printer, nothing changed. :( What else should I try, anyone please?

---

### Post by albandy on 2009-03-06
this printer have an ethernet port?

---

### Post by cezarica on 2009-03-06
Just noticed I typed the wrong version of the printer, it's P3005. No, it doesn't have one.
 
Has 1 x parallel - IEEE 1284 (EPP/ECP) and 1 x Hi-Speed USB. I'm using the USB one. The Ethernet port 'HP JetDirect 620n' costs 350$. :(

---

### Post by cezarica on 2009-03-09
bump..

anyone? :S

---

### Post by albandy on 2009-03-09
ok, so do this:
first open a terminal and type
tail -f /var/log/messages
now without closing the terminal open a program and print something
paste here what appears in terminal

---

### Post by cezarica on 2009-03-10
I figured out by myself. Removed completely the HPLIP version 3.9.2 ([How to uninstall HPLIP]("http://hplipopensource.com/node/188")) then installed HPLIP from Synaptic Package Manager. Re-pluged the printer and was detected and installed. So far it's working fine. :)

I've found [&#8220;hplip&#8221; source package in Ubuntu]("https://launchpad.net/ubuntu/+source/hplip") and noticed there that version 3.9.2 is for Jaunty build while I have Intrepid thus needed to install 2.8.7 in order to make it work. Must be a bug or something in the HPLIP, either way I'm finally happy my printer it's working again.\\:D/

thanks anyway for helping out albandy.

---

