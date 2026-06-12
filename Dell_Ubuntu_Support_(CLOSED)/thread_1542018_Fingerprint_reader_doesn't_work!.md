---
title: "Fingerprint reader doesn't work!"
date: 2010-07-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by becatron on 2010-07-29
Hi everyone,

I have a dell studio 1737, and I've never been able to find the drivers for the fingerprint reader, and I'd like to get it working. Currently running 10.04.

Any help would be awesome.

Thanks

---

### Post by P4man on 2010-07-30
Have a look here:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_Z61m#Setup_Fingerprint_Reader](http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_Z61m#Setup_Fingerprint_Reader)

Although that may not work with your particular finger scanner. Can you post outputs of lsusb and lspci?

---

### Post by becatron on 2010-07-31
I've run through that, but it doesn't recognise my device.

i'm not sure how to post outputs of lsusb and lspci...

---

### Post by ronnielsen1 on 2010-07-31
Go to terminal and type in lsusb. It will display text like in the window below. Hit the icon above that looks like [IMG]http://ubuntuforums.org/images/editor/quote.gif[/IMG] and copy your text in terminal and paste in the middle of quote and /quote 

Here's mine
> lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2015 SGS Thomson Microelectronics TouchChip&#65533; Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05dc:a793 Lexar Media, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                      I've been trying to get mine working following the directions at this page but I haven't been successful yet

[http://www.ubuntu-unleashed.com/2008/04/get-your-fingerprint-reader-to-work-in.html](http://www.ubuntu-unleashed.com/2008/04/get-your-fingerprint-reader-to-work-in.html)

This page shows supported devices

[http://www.reactivated.net/fprint/wiki/Supported_devices](http://www.reactivated.net/fprint/wiki/Supported_devices)

---

### Post by becatron on 2010-07-31
I had no luck with that one either. I don't think my device is supported :(

Here is my lsusb:
> Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 08ff:2810 AuthenTec, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 05ca:18a1 Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by P4man on 2010-07-31
> Bus 005 Device 002: ID 08ff:2810 **AuthenTec**, Inc. 

Looks like you can forget about the authentec one:
[http://reactivated.net/fprint/wiki/Unsupported_devices#AuthenTec_AES2550_.26_AES2810](http://reactivated.net/fprint/wiki/Unsupported_devices#AuthenTec_AES2550_.26_AES2810)

No data on those fingerprint scanners and suspected encrypted protocol. Dont hold your breath for that one.

---

