---
title: "Ubuntu 8.10 VPN connection failed"
date: 2009-03-22
forum: Desktop Environments
---

### Post by daboroe on 2009-03-22
I have followed instructions listed here at this site:

[http://www.splatdot.com/2008/11/19/ubuntu-810-how-connect-microsoft-vpn](http://www.splatdot.com/2008/11/19/ubuntu-810-how-connect-microsoft-vpn)


Below is what is in my syslog file from when i start the vpn to when it fails

```

Mar 22 11:34:10 ubuntu NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Mar 22 11:34:10 ubuntu NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 16558 
Mar 22 11:34:10 ubuntu NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Mar 22 11:34:10 ubuntu NetworkManager: <info>  VPN plugin state changed: 1 
Mar 22 11:34:15 ubuntu NetworkManager: <info>  VPN plugin state changed: 3 
Mar 22 11:34:15 ubuntu pppd[16562]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Mar 22 11:34:15 ubuntu NetworkManager: <info>  VPN connection 'PCT' (Connect) reply received. 
Mar 22 11:34:15 ubuntu pppd[16562]: pppd 2.4.4 started by root, uid 0
Mar 22 11:34:15 ubuntu pptp[16564]: nm-pptp-service-16558 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Mar 22 11:34:15 ubuntu pppd[16562]: Using interface ppp0
Mar 22 11:34:15 ubuntu pppd[16562]: Connect: ppp0 <--> /dev/pts/1
Mar 22 11:34:15 ubuntu pptp[16571]: nm-pptp-service-16558 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Mar 22 11:34:15 ubuntu pptp[16571]: nm-pptp-service-16558 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Mar 22 11:34:15 ubuntu pptp[16571]: nm-pptp-service-16558 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Mar 22 11:34:16 ubuntu pptp[16571]: nm-pptp-service-16558 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Mar 22 11:34:16 ubuntu pptp[16571]: nm-pptp-service-16558 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Mar 22 11:34:16 ubuntu pptp[16571]: nm-pptp-service-16558 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 37612). 
Mar 22 11:34:16 ubuntu pppd[16562]: CHAP authentication succeeded
Mar 22 11:34:16 ubuntu pppd[16562]: Refusing MPPE stateful mode offered by peer
Mar 22 11:34:16 ubuntu pppd[16562]: MPPE required but peer negotiation failed
Mar 22 11:34:16 ubuntu pppd[16562]: Connection terminated.
Mar 22 11:34:16 ubuntu NetworkManager: <info>  VPN plugin failed: 1 
Mar 22 11:34:16 ubuntu pptp[16564]: nm-pptp-service-16558 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Mar 22 11:34:16 ubuntu pptp[16564]: nm-pptp-service-16558 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Mar 22 11:34:16 ubuntu pptp[16571]: nm-pptp-service-16558 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Mar 22 11:34:16 ubuntu pppd[16562]: Exit.
Mar 22 11:34:16 ubuntu NetworkManager: <info>  VPN plugin failed: 1 
Mar 22 11:34:16 ubuntu pptp[16571]: nm-pptp-service-16558 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Mar 22 11:34:16 ubuntu pptp[16571]: nm-pptp-service-16558 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Mar 22 11:34:16 ubuntu NetworkManager: <info>  VPN plugin state changed: 6 
Mar 22 11:34:16 ubuntu NetworkManager: <info>  VPN plugin state change reason: 0 
Mar 22 11:34:16 ubuntu NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Mar 22 11:34:16 ubuntu NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Mar 22 11:34:28 ubuntu NetworkManager: <debug> [1237736068.889706] ensure_killed(): waiting for vpn service pid 16558 to exit 
Mar 22 11:34:28 ubuntu NetworkManager: <debug> [1237736068.889857] ensure_killed(): vpn service pid 16558 cleaned up 

```

---

