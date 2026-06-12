---
title: "Huawei 226 + networkmanager 0.7(ppp) = no go"
date: 2009-02-21
forum: General Help
---

### Post by pablosanchezuy on 2009-02-21
Intrepid, amd64 on a Compaq 6820s .

I have a huawei 226 modem, which is recognized as a usb modem on /dev/ttyUSB0 correctly.
I made a 3G connection, named "xxxx" with the "Ancel" ISP (uruguay), and after a lot of google, ubuntuforums.org and launchpad somehow i got it running 5 or 6 times. After that i got no connection and system freezes .
I managed to strip off the PIN number of the SIM card.
Here's the log of what is happening (i replaced the username with "myuser").

Feb 21 20:03:16 pablos NetworkManager: <info>  Activation (ttyUSB0) starting connection 'xxxx' 
Feb 21 20:03:16 pablos NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 
Feb 21 20:03:16 pablos NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb 21 20:03:16 pablos NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Feb 21 20:03:16 pablos NetworkManager: <debug> [1235253796.008930] nm_serial_device_open(): (ttyUSB0) opening device... 
Feb 21 20:03:16 pablos NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Feb 21 20:03:16 pablos NetworkManager: <info>  (ttyUSB0): powering up... 
Feb 21 20:03:16 pablos NetworkManager: <info>  Registered on Home network 
Feb 21 20:03:16 pablos NetworkManager: <info>  Associated with network: +COPS: 0,2,"74801",2 
Feb 21 20:03:16 pablos NetworkManager: <info>  Connected, Woo! 
Feb 21 20:03:16 pablos NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled... 
Feb 21 20:03:16 pablos NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting... 
Feb 21 20:03:16 pablos NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5 
Feb 21 20:03:16 pablos NetworkManager: <info>  Starting pppd connection 
Feb 21 20:03:16 pablos NetworkManager: <debug> [1235253796.318988] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute user myuser ttyUSB0 noipdefault usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/0 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so 
Feb 21 20:03:16 pablos NetworkManager: <debug> [1235253796.334255] nm_ppp_manager_start(): ppp started with pid 6304 
Feb 21 20:03:16 pablos NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete. 
Feb 21 20:03:16 pablos pppd[6304]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Feb 21 20:03:16 pablos pppd[6304]: pppd 2.4.4 started by root, uid 0
Feb 21 20:03:16 pablos kernel: [   79.165890] PPP generic driver version 2.4.2
Feb 21 20:03:16 pablos pppd[6304]: using channel 1
Feb 21 20:03:16 pablos pppd[6304]: Using interface ppp0
Feb 21 20:03:16 pablos pppd[6304]: Connect: ppp0 <--> /dev/ttyUSB0
Feb 21 20:03:16 pablos pppd[6304]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MD5> <magic 0x41b57a61> <pcomp> <accomp>]
Feb 21 20:03:16 pablos pppd[6304]: rcvd [LCP ConfReq id=0x0 <asyncmap 0x0> <auth chap MD5> <magic 0xd31c70> <pcomp> <accomp>]
Feb 21 20:03:16 pablos pppd[6304]: sent [LCP ConfAck id=0x0 <asyncmap 0x0> <auth chap MD5> <magic 0xd31c70> <pcomp> <accomp>]
Feb 21 20:03:16 pablos pppd[6304]: rcvd [LCP ConfRej id=0x1 <auth chap MD5>]
Feb 21 20:03:16 pablos pppd[6304]: sent [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0x41b57a61> <pcomp> <accomp>]
Feb 21 20:03:16 pablos pppd[6304]: rcvd [LCP ConfAck id=0x2 <asyncmap 0x0> <magic 0x41b57a61> <pcomp> <accomp>]
Feb 21 20:03:16 pablos pppd[6304]: peer refused to authenticate: terminating link
Feb 21 20:03:16 pablos pppd[6304]: sent [LCP TermReq id=0x3 "peer refused to authenticate"]
Feb 21 20:03:16 pablos pppd[6304]: rcvd [LCP DiscReq id=0x1 magic=0xd31c70]
Feb 21 20:03:16 pablos pppd[6304]: rcvd [CHAP Challenge id=0x1 <7224cfcbe620628c0a245e7e564d9056>, name = "UMTS_CHAP_SRVR"]
Feb 21 20:03:16 pablos pppd[6304]: Discarded non-LCP packet when LCP not open
Feb 21 20:03:16 pablos pppd[6304]: rcvd [LCP TermAck id=0x3]
Feb 21 20:03:16 pablos pppd[6304]: Connection terminated.
Feb 21 20:03:16 pablos NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 9 
Feb 21 20:03:16 pablos NetworkManager: <debug> [1235253796.566518] nm_serial_device_close(): Closing device 'ttyUSB0' 
Feb 21 20:03:16 pablos NetworkManager: <info>  Marking connection 'xxxx' invalid. 
Feb 21 20:03:16 pablos NetworkManager: <info>  Activation (ttyUSB0) failed. 
Feb 21 20:03:16 pablos NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 
Feb 21 20:03:16 pablos NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0). 
Feb 21 20:03:16 pablos NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Feb 21 20:03:16 pablos NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Feb 21 20:03:17 pablos pppd[6304]: Exit.
Feb 21 20:03:18 pablos NetworkManager: <debug> [1235253798.571370] ensure_killed(): waiting for ppp pid 6304 to exit 
Feb 21 20:03:18 pablos NetworkManager: <debug> [1235253798.571563] ensure_killed(): ppp pid 6304 cleaned up

If anyone can lend a hand, i'll be very grateful.
This modem works 100% on an XP PC .

Regards.

pablo.

---

### Post by pablosanchezuy on 2009-02-25
just uninstall ppp, network-manager and the plugins, with their configs.

reinstall all that, edit  /etc/ppp/options and added the line

"ipcp-max-failure 30" again ( the fix for the dns problem) and go.



sorry for the waste of bandwidth .

pablo .

---

