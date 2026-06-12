---
title: "Amule connection woes"
date: 2006-08-14
forum: Desktop Environments
---

### Post by zrothe on 2006-08-14
This is a fresh install of Amule. My problem is I am unable to connect to most servers and the ones that I can connect to say I have lowid. I setup port forwarding (and ultimately, put my ip in dmz) and ran the web based test and it shows:

> Success The TCP port 9552 is available. You should be able to use the ED2K P2P service without any problems.

I have tried higher ports and lower ports also. Here is what I get when I open amule.

> 2006-08-13 23:11:53: Connecting
2006-08-13 23:11:53: Servers: Trying to connect
2006-08-13 23:11:53: Connecting to Wild (82.80.248.24 - 82.80.248.24:4232)
2006-08-13 23:11:53: Kad network cannot be used if UDP port is disabled on preferences, not starting.
2006-08-13 23:11:54: Credit file loaded, 0 clients are known

2006-08-13 23:11:54:  - This is aMule 2.1.0 using wxGTK2 v2.6.1 (Unicoded) based on eMule.
2006-08-13 23:11:54:    Running on Linux 2.6.15-26-386 i686
2006-08-13 23:11:54:  - Visit [http://www.amule.org](http://www.amule.org) to check if a new version is available.

2006-08-13 23:11:54: Loading ipfilter.dat files.
2006-08-13 23:11:54: Loaded 0 IP-ranges from 'ipfilter.dat'. 0 malformed lines were discarded.
2006-08-13 23:11:54: Loaded 0 IP-ranges from 'ipfilter_static.dat'. 0 malformed lines were discarded.
2006-08-13 23:11:54: Loading server.met file: /home/knapp/.aMule/server.met
2006-08-13 23:11:54: 95 servers in server.met found
2006-08-13 23:11:54: No file parts found
2006-08-13 23:11:54: External connections disabled in config file
2006-08-13 23:11:54: MuleUDPSocket: Created Server UDP-Socket at port 9555
2006-08-13 23:11:54: Found 0 known shared files
2006-08-13 23:11:54: AICH Thread: Syncronization thread started.
2006-08-13 23:11:54: AICH Thread: Masterhashes of known files have been loaded.
2006-08-13 23:11:54: AICH Thread: No new files found.
2006-08-13 23:11:54: AICH Thread: Terminated.
2006-08-13 23:11:54: Servers: Trying to connect
2006-08-13 23:11:54: Connecting to Breizh Punisher's (213.251.133.129 - 213.251.133.129:6567)
2006-08-13 23:11:54: Connected to Wild (82.80.248.24:4232)
2006-08-13 23:11:54: Connected to Breizh Punisher's (213.251.133.129:6567)
2006-08-13 23:12:12: Lost connection to Wild (82.80.248.24:4232)
2006-08-13 23:12:12: Connection lost
2006-08-13 23:12:14: Lost connection to Breizh Punisher's (213.251.133.129:6567)
2006-08-13 23:12:14: Connection lost
2006-08-13 23:12:17: Connection attempt to Wild (82.80.248.24:4232) timed out.
2006-08-13 23:12:17: Servers: Trying to connect
2006-08-13 23:12:17: Connecting to !-= [www.FreeOsex.com](www.FreeOsex.com) =-! (83.149.123.188 - 83.149.123.188:80)
2006-08-13 23:12:18: Connected to !-= [www.FreeOsex.com](www.FreeOsex.com) =-! (83.149.123.188:4321)
2006-08-13 23:12:20: Connection attempt to Breizh Punisher's (213.251.133.129:6567) timed out.
2006-08-13 23:12:20: Servers: Trying to connect
2006-08-13 23:12:20: Connecting to [www.Sofortige-Downloads.de](www.Sofortige-Downloads.de) (85.17.35.2 - 85.17.35.2:1661)
2006-08-13 23:12:20: Connected to [www.Sofortige-Downloads.de](www.Sofortige-Downloads.de) (85.17.35.2:1661)
2006-08-13 23:12:32: Warning: !-= [www.FreeOsex.com](www.FreeOsex.com) =-! (83.149.123.188:4321) - NG : You have a lowid. Please review your network config and/or your settings.
2006-08-13 23:12:33: Servers: Connected
2006-08-13 23:12:33: Connection established with: !-= [www.FreeOsex.com](www.FreeOsex.com) =-!
2006-08-13 23:12:33: WARNING: You have recieved Low-ID!
2006-08-13 23:12:33: 	Most likely this is because you're behind a firewall or router.
2006-08-13 23:12:33: 	For more information, please refer to [http://wiki.amule.org](http://wiki.amule.org)
2006-08-13 23:12:33: New client ID is 8215195


I am at a complete loss. Only thing I can come up with is my ISP is doing something?

---

### Post by zrothe on 2006-08-14
Well, I unplugged my router and ran the line directly from my modem into my computer. Still getting lowid.

> 2006-08-14 08:54:34: Connection established with: Bidonkey 2k
2006-08-14 08:54:34: WARNING: You have recieved Low-ID!

---

### Post by zrothe on 2006-08-14
Anyone? Please.

---

