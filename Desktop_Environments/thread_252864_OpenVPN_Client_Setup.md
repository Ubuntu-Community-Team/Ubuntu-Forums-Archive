---
title: "OpenVPN Client Setup"
date: 2006-09-07
forum: Desktop Environments
---

### Post by kw1502 on 2006-09-07
I’m a new Dapper Drake user. I’m trying to setup an OpenVPN client on Ubuntu using certificates. I’ve installed the OpenVPN package but have not changed any other system configuration files and/or parameters. My OpenVPN server and client configuration files are the same ones that work under Windows XP.  Is there sometime else I need to do to make this work under Dapper?  I’ve attached the terminal output from an attempt to establish the VPN. Any suggestions would be greatly appreciated.

ken@ubuntu:~$ cd /etc/openvpn
ken@ubuntu:/etc/openvpn$ sudo openvpn --config ipcop.ovpn
Wed Sep  6 23:14:01 2006 OpenVPN 2.0.6 i486-pc-linux-gnu [SSL] [LZO] [EPOLL] bui lt on Apr 10 2006
Wed Sep  6 23:14:01 2006 IMPORTANT: OpenVPN's default port number is now 1194, b ased on an official port number assignment by IANA.  OpenVPN 2.0-beta16 and earl ier used 5000 as the default port.
Enter Private Key Password:
Wed Sep  6 23:14:08 2006 LZO compression initialized
Wed Sep  6 23:14:08 2006 WARNING: normally if you use --mssfix and/or --fragment , you should also set --tun-mtu 1500 (currently it is 1400)
Wed Sep  6 23:14:08 2006 Control Channel MTU parms [ L:1442 D:138 EF:38 EB:0 ET: 0 EL:0 ]
Wed Sep  6 23:14:08 2006 Data Channel MTU parms [ L:1442 D:1442 EF:42 EB:135 ET: 0 EL:0 AF:3/1 ]
Wed Sep  6 23:14:08 2006 Local Options hash (VER=V4): 'a6ae7d69'
Wed Sep  6 23:14:08 2006 Expected Remote Options hash (VER=V4): '006a55ce'
Wed Sep  6 23:14:08 2006 UDPv4 link local (bound): [undef]:1194
Wed Sep  6 23:14:08 2006 UDPv4 link remote: 192.168.1.1:1194
Wed Sep  6 23:15:08 2006 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Wed Sep  6 23:15:08 2006 TLS Error: TLS handshake failed
Wed Sep  6 23:15:08 2006 TCP/UDP: Closing socket
Wed Sep  6 23:15:08 2006 SIGUSR1[soft,tls-error] received, process restarting
Wed Sep  6 23:15:08 2006 Restart pause, 2 second(s)
Wed Sep  6 23:15:10 2006 IMPORTANT: OpenVPN's default port number is now 1194, based on an official port number assignment by IANA.  OpenVPN 2.0-beta16 and earlier used 5000 as the default port.
Wed Sep  6 23:15:10 2006 LZO compression initialized
Wed Sep  6 23:15:10 2006 WARNING: normally if you use --mssfix and/or --fragment, you should also set --tun-mtu 1500 (currently it is 1400)
Wed Sep  6 23:15:10 2006 Control Channel MTU parms [ L:1442 D:138 EF:38 EB:0 ET:0 EL:0 ]
Wed Sep  6 23:15:10 2006 Data Channel MTU parms [ L:1442 D:1442 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Wed Sep  6 23:15:10 2006 Local Options hash (VER=V4): 'a6ae7d69'
Wed Sep  6 23:15:10 2006 Expected Remote Options hash (VER=V4): '006a55ce'
Wed Sep  6 23:15:10 2006 UDPv4 link local (bound): [undef]:1194
Wed Sep  6 23:15:10 2006 UDPv4 link remote: 192.168.1.1:1194
Wed Sep  6 23:16:10 2006 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Wed Sep  6 23:16:10 2006 TLS Error: TLS handshake failed
Wed Sep  6 23:16:10 2006 TCP/UDP: Closing socket
Wed Sep  6 23:16:10 2006 SIGUSR1[soft,tls-error] received, process restarting
Wed Sep  6 23:16:10 2006 Restart pause, 2 second(s)

---

### Post by secure bit on 2007-12-15
still need help, mate ?

---

