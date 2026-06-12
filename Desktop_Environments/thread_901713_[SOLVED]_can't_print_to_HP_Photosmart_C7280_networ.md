---
title: "[SOLVED] can't print to HP Photosmart C7280 network printer"
date: 2008-08-26
forum: Desktop Environments
---

### Post by r.stiltskin on 2008-08-26
Since upgrading to hardy, I'm unable to print to my Photosmart C7280 over the network.  It worked under feisty, it works from Windows XP and from MacOSX.  I can ping it. It responds to snmpwalk; for example:
```
~$ snmpwalk -Os -c public -v 1 [local ip address of printer] 1.3.6.1.4.1.11.2.3.9.1.1.7.0
enterprises.11.2.3.9.1.1.7.0 = STRING: "MFG:HP;MDL:Photosmart C7200 series;CMD:MLC,PCL,PML,DW-PCL,DESKJET,DYN;1284.4DL:4d,4e,1;CLS:PRINTER;DES:CC567A;SN:MY78MG32N004YG;S:038088C4840F10210978cb0000041b8003f46b8006447b8006444b8006448b8006445b80064;Z:0102,05000009016a81013241013241013241013241013241,0600,070000000000000000000000000000,0b000000000000000097c997db000097c997db000097c797db000097c997db000097c897db000097c997db,0c0;"

```
I have installed hplip, hplip-data, hpijs and hpijs-ppds.  According to info on hplip.sourceforge.net, this printer is supported by the HPLIP version included in ubuntu 8.04.  I have tried installing the printer using both gnome system/administration/printing and directly in cups via browser (localhost:631).  I've tried the "HP Photosmart C7200 Foomatic/hpijs (recommended)" driver as well as an HP-Photosmart-C7200-hpijs.ppd that I downloaded.   When I install it with uri [http://[local](http://[local) ip address of printer], nothing is sent to the printer and cups constantly shows ```
recoverable: Network host '[ip address]' is busy; will retry in 30 seconds..."
```  When I install it with uri [http://[local](http://[local) ip address]:9100, it prints garbage.

After restarting cups and sending a test page, /var/log/cups/error_log shows ```
D [26/Aug/2008:17:23:16 -0400] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [26/Aug/2008:17:23:16 -0400] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [26/Aug/2008:17:23:16 -0400] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [26/Aug/2008:17:23:16 -0400] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [26/Aug/2008:17:23:16 -0400] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [26/Aug/2008:17:23:17 -0400] cupsdAcceptClient: 134 from localhost (Domain)
D [26/Aug/2008:17:23:17 -0400] cupsdReadClient: 134 POST / HTTP/1.1
D [26/Aug/2008:17:23:17 -0400] cupsdAuthorize: No authentication data provided.
D [26/Aug/2008:17:23:17 -0400] Get-Jobs ipp://localhost/jobs/
D [26/Aug/2008:17:23:17 -0400] cupsdProcessIPPRequest: 134 status_code=0 (successful-ok)
D [26/Aug/2008:17:23:17 -0400] cupsdReadClient: 134 POST / HTTP/1.1
D [26/Aug/2008:17:23:17 -0400] cupsdAuthorize: No authentication data provided.
D [26/Aug/2008:17:23:17 -0400] CUPS-Get-Printers
D [26/Aug/2008:17:23:17 -0400] cupsdProcessIPPRequest: 134 status_code=0 (successful-ok)
D [26/Aug/2008:17:23:17 -0400] cupsdCloseClient: 134
D [26/Aug/2008:17:23:21 -0400] [Job 44] Getting supported attributes...
W [26/Aug/2008:17:23:21 -0400] [Job 44] recoverable: Network host '192.168.123.130' is busy; will retry in 10 seconds...
D [26/Aug/2008:17:23:21 -0400] Discarding unused printer-state-changed event...
D [26/Aug/2008:17:23:21 -0400] cupsdAcceptClient: 134 from localhost (Domain)
D [26/Aug/2008:17:23:21 -0400] cupsdReadClient: 134 POST / HTTP/1.1
D [26/Aug/2008:17:23:21 -0400] cupsdAuthorize: No authentication data provided.
D [26/Aug/2008:17:23:21 -0400] Get-Jobs ipp://localhost/jobs/
D [26/Aug/2008:17:23:21 -0400] cupsdProcessIPPRequest: 134 status_code=0 (successful-ok)
D [26/Aug/2008:17:23:21 -0400] cupsdReadClient: 134 POST / HTTP/1.1
D [26/Aug/2008:17:23:21 -0400] cupsdAuthorize: No authentication data provided.
D [26/Aug/2008:17:23:21 -0400] CUPS-Get-Printers
D [26/Aug/2008:17:23:21 -0400] cupsdProcessIPPRequest: 134 status_code=0 (successful-ok)
D [26/Aug/2008:17:23:21 -0400] cupsdCloseClient: 134

```

I thought it might be a firewall problem, so I ran:
~$ sudo ufw allow 161
~$ sudo ufw allow 162
~$ sudo ufw allow 9100

I'm not sure if that was correct (or necessary) but each time the response was
"Rules updated"


Any ideas?


edit: I read on the HPLIP site that hpijs should be unnecessary, so I uninstalled that and hpijs-ppds.  After doing that, the error message on the cups localhost:631 Printers page for this printer says "/usr/lib/cups/filter/foomatic-rip failed"

---

### Post by r.stiltskin on 2008-08-26
Solution:
I completely removed hplip and hplip-data (note that I had already completely removed hpijs, foomatic-db-hpijs and hpijs-ppds),
downloaded hplip-2.8.7.run from hplip.sourceforge.net  and ran the automatic installer.

While it was running, I noted that there were 7 missing "optional" dependencies which it automatically downloaded & installed; two of these were marked as "REQUIRED dependency for option 'network'", so maybe that was part of my problem.

After building, a setup wizard ran which did almost everything by itself (but for some reason it didn't find the printer by itself - I had to enter its ip address manually).  It gave me a choice of 2 drivers - I chose the first one that was listed (not the one called 'recommended').

Printing to this printer now seems to work perfectly.

 Out of curiousity I went into the CUPS "modify printer" process to see what was different.  I notice that there are now 2 new items listed in the "device" drop-down menu that were not there before:
HP Fax (HPLIP)
and
HP Printer (HPLIP)

Also, the device uri that the wizard entered is now:
hp:/net/Photosmart_C7200_series?ip=[my printer's ip address]
and the driver it is using is
HP Photosmart c7200 series Foomatic/hpijs (en)
which seems to be a new item in the list.  Previously, I was trying to use "HP PhotoSmart C7200 Foomatic/hpijs (recommended) (en)".  Note that the slight differences in upper/lowercase are not accidental - I copied these names exactly.  I haven't compared to see if there are actually any differences in the drivers.

As an extra bonus, it also installed Photosmart_C7200_fax (this is a multifunction printer), which I hadn't even thought of installing before.  Presumably I can now send faxes directly from the computer, although I haven't tried that yet.

---

