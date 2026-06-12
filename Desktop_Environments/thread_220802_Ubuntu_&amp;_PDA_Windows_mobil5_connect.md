---
title: "Ubuntu &amp; PDA: Windows mobil5 connect"
date: 2006-07-22
forum: Desktop Environments
---

### Post by Mendiaco on 2006-07-22
Hi,
I'm a 6 months ubuntu user. I like a lot ubuntu.
But now I have just buy a Fujitsu-Siemens N560 PDA. with windows mobile 5.

I connect my PDA via USB, and I like to syncronize with multysinc, I want to exchange files, and install aplications in my pda.

Is it possible? how can I do?

I try:
tail -f /var/log/syslog

but the result is:

josep@josep-domicili:~$ tail -f /var/log/syslog
Jul 22 10:28:01 josep-domicili -- MARK --
Jul 22 10:38:01 josep-domicili kernel: [17181400.200000] usb 1-1: new full speed  USB device using uhci_hcd and address 3
Jul 22 10:38:01 josep-domicili usbmgr[4475]: vendor:0xbf8 product:0x1011
Jul 22 10:38:01 josep-domicili usbmgr[4475]: class:0xa subclass:0x0 protocol:0x0
Jul 22 10:38:01 josep-domicili usbmgr[4475]: USB device isn't matched the config uration
Jul 22 10:38:30 josep-domicili kernel: [17181429.192000] usb 1-1: USB disconnect , address 3
Jul 22 10:38:36 josep-domicili kernel: [17181435.984000] usb 1-1: new full speed  USB device using uhci_hcd and address 4
Jul 22 10:38:37 josep-domicili usbmgr[4475]: vendor:0xbf8 product:0x1011
Jul 22 10:38:37 josep-domicili usbmgr[4475]: class:0xa subclass:0x0 protocol:0x0
Jul 22 10:38:37 josep-domicili usbmgr[4475]: USB device isn't matched the config uration
Jul 22 10:43:35 josep-domicili kernel: [17181734.868000] usb 1-1: USB disconnect, address 4


Is it Fujitsu-Siemens compatible, or windows mobile 5 with ubuntu Dapper Drake? Thanks.

---

