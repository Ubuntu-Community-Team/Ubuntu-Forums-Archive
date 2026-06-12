---
title: "cant print to Brother MFC 640CW"
date: 2010-06-26
forum: Desktop Environments
---

### Post by pdc124 on 2010-06-26
I've downloaded the lpd file and cups wrapper from the Brother site. The  network printing is failing, regardless of the protocol I set up 

D [26/Jun/2010:15:59:17 +0100] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [26/Jun/2010:15:59:17 +0100] cupsdSetBusyState: Dirty files
D [26/Jun/2010:15:59:17 +0100] cupsdAcceptClient: 15 from localhost (Domain)
D [26/Jun/2010:15:59:17 +0100] cupsdReadClient: 15 GET /admin/log/error_log HTTP/1.1
D [26/Jun/2010:15:59:17 +0100] cupsdSetBusyState: Active clients and dirty files
D [26/Jun/2010:15:59:17 +0100] cupsdAuthorize: No authentication data provided.

its the same  configured as 
lpd://192.168.0.198
lpd://192.168.0.198/queue
socket ://192.168.0.198:9100

im in lpdadmin group 

post scanning the printer 
Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-06-26 16:06 BST
Interesting ports on TRIBBLE.home.nw (192.168.0.198):
Not shown: 996 closed ports

PORT     STATE SERVICE
21/tcp   open  ftp
23/tcp   open  telnet
515/tcp  open  printer
9100/tcp open  jetdirect
MAC Address: 00:16:CF:01:DF:19 (Hon Hai Precision Ind. Co.)

so where is the authentication problem ?

---

