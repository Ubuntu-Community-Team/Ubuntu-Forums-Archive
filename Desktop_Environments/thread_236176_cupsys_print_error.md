---
title: "cupsys print error"
date: 2006-08-14
forum: Desktop Environments
---

### Post by amshali on 2006-08-14
Hi, I tried to configure cupsys but it encountered an error:


Unable to retrieve the printer list. Error message received from manager:
Connection to CUPS server failed. Check that the CUPS server is installed and running correctly. Error: the IPP request failed for an unknown reason.

Here is the log file:


D [14/Aug/2006:18:21:40 +0330] cupsdAcceptClient: 7 from localhost:631 (IPv4)
D [14/Aug/2006:18:21:40 +0330] cupsdAcceptClient: 8 from localhost:631 (IPv4)
D [14/Aug/2006:18:21:40 +0330] cupsdCloseClient: 7
D [14/Aug/2006:18:21:40 +0330] cupsdReadClient: 8 POST /printers/ HTTP/1.1
D [14/Aug/2006:18:21:40 +0330] cupsdAuthorize: No authentication data provided.
D [14/Aug/2006:18:21:40 +0330] CUPS-Get-Printers
I [14/Aug/2006:18:21:40 +0330] CUPS-Get-Printers client-error-not-found: No destinations added.
D [14/Aug/2006:18:21:40 +0330] cupsdProcessIPPRequest: 8 status_code=406 (client-error-not-found)
D [14/Aug/2006:18:21:40 +0330] cupsdCloseClient: 8



I checked my cupsys server. It's installed correctly and is running! 
My cupsys version is 1.2.2-1
What shall I do? Can anyone help me?

Thanks in advance,
amshali

---

