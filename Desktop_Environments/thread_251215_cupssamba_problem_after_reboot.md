---
title: "cups/samba problem after reboot"
date: 2006-09-05
forum: Desktop Environments
---

### Post by bongobonga on 2006-09-05
I have a usb printer attached to a server and I share that printer using a samba. Everything was working fine until I had a power out which forced a reboot, and now I can't seem to print over the network from windows machines. 
I use cups to control the printer. I can see the printer on the network from windows machines, and it works fine if I print from the server itself, but I can't print from windows boxes. I get an error such as "Windows cannot print due to a problem with the current printer setup." I've tryed reinstalling the windows drivers for the printer, but with no luck.  

I have also checked the cups error_log, all I get when I try to print from windows is:

Accept Clinet: 5 from localhost:631
ReadClient: 5 POST / HTTP/1.1
ProcessIPPRequest: 5 status_code = 0
ReadClient: 5 POST / HTTP/1.1
ProcessIPPRequest: 5 status_code = 0
CloseClient: 5

Has anyone any ideas what could be causing my printing problems? Since this problem only happend after a dirty restart, could there be a lock file somewhere that was never removed? 


The relevent lines from the smb.conf are:

printcap name = cups
printing = cups

[printers]
browseable = yes
printable = yes
public = yes
use client driver = yes
path = /tmp
guest account = smbprint
guest only = yes
create mode = 0777

---

