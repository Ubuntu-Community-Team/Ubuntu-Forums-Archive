---
title: "Router help"
date: 2009-04-16
forum: General Help
---

### Post by Anders B on 2009-04-16
This may not be the correct forums for this, but there's so many helpful people her :D

Im having some trouble with my ftp-server.
My router is blocking something. I can connect to my server if i put it in the Demilitarized Zone in the router setup, so im thinking I need to open up some ports, but I dont know which ones.

Im getting this error from the ftp-client, when trying to connect:

```
STATUS:>  	Getting listing ""...
STATUS:>  	Resolving host name xxxxx.servegame.org...
STATUS:>  	Host name xxxx.servegame.org resolved: ip = xx.xx.xx.xx.
STATUS:>  	Connecting to FTP server... xxxx.servegame.org:21 (ip = xx.xx.xx.xx)...
STATUS:>  	Socket connected. Waiting for welcome message...
		220 Welcome to Anders' FTP service.
STATUS:>  	Connected. Authenticating...
COMMAND:>	USER anders
		331 Please specify the password.
COMMAND:>	PASS *****
		230 Login successful.
STATUS:>  	Login successful.
COMMAND:>	PWD
		257 "/"
STATUS:>  	Home directory: /
COMMAND:>	FEAT
		Informational Message Only:
		211-Features:
		 EPRT
		 EPSV
		 MDTM
		 PASV
		 REST STREAM
		 SIZE
		 TVFS
		 UTF8
		211 End
STATUS:>  	This site supports features.
STATUS:>  	This site supports SIZE.
STATUS:>  	This site can resume broken downloads.
COMMAND:>	REST 0
		350 Restart position accepted (0).
COMMAND:>	PASV
		227 Entering Passive Mode (192,168,0,100,53,149)
STATUS:>  	Substituting received PASV address 192.168.0.100 to server address xx.xx.xx.xx.
COMMAND:>	LIST
STATUS:>  	Connecting FTP data socket... xx.xx.xx.xx:13717...
ERROR:>   	The connection failed due to an error or timeout.
		1) Verify that the destination IP address is correct.
		2) Increase the connection timeout threshold under Global Settings | Connection.
		3) Switch to the opposite data connection type (PASV or PORT) under Site Settings | Type tab.
		4) Verify that the problem is not local by trying to connect to an alternate server.
		5) If a server name was used, verify it resolves to the correct address.
		6) If using a local server table for server name resolution, check to see that it doesn't resolve to an obsolete address.
		7) Try pinging the address.
		8) If you are using a router, verify the router is up and running (check by pinging it and then ping an address outside of the router).
		9) Do a traceroute to the destination to verify all routers along the connection path are operational.
		10) Verify that your subnet mask is setup properly.
		11) Verify that your local software or hardware firewall is not blocking outbound connections originating from CuteFTP.
		12) Verify that your anti-virus software is not at fault (try disabling it).
ERROR:>   	PASV failed, trying PORT.
STATUS:>  	Waiting 0 seconds...
STATUS:>  	Getting listing "/"...
STATUS:>  	Resolving host name xxxx.servegame.org...
STATUS:>  	Host name xxxxx.servegame.org resolved: ip = xx.xx.xx.xx.
STATUS:>  	Connecting to FTP server... xxxx.servegame.org:21 (ip = xx.xx.xx.xx)...
STATUS:>  	Socket connected. Waiting for welcome message...
		220 Welcome to Anders' FTP service.
STATUS:>  	Connected. Authenticating...
COMMAND:>	USER anders
		331 Please specify the password.
COMMAND:>	PASS *****
		230 Login successful.
STATUS:>  	Login successful.
COMMAND:>	PWD
		257 "/"
STATUS:>  	Home directory: /
STATUS:>  	This site supports features.
STATUS:>  	This site supports SIZE.
STATUS:>  	This site can resume broken downloads.
COMMAND:>	REST 0
		350 Restart position accepted (0).
COMMAND:>	PORT 192,168,0,101,217,125
		500 Illegal PORT command.
ERROR:>   	Syntax error: command unrecognized.
ERROR:>   	Failed to establish data socket.

```

---

