---
title: "Trouble printing to a windows share printer"
date: 2009-03-01
forum: General Help
---

### Post by miross on 2009-03-01
Trying to print to an HP 940c shared printer on Windows XP without success.  I've been searching the forums and googling off and on for a couple of weeks and have not been making any progress.  

If this more appropriate for another forum, let me know and I will repost.

I have 8.10 on a Dell Inspiron 1000 Laptop.  Sharing folders with the windows machine works fine.   I am able to find the printer fine when adding through System | Administration | Printing.

I am able to add the printer with no problems in the Printer Config and/or CUPS web page.  Getting these errors in the [http://localhost:631/admin/log/error_log](http://localhost:631/admin/log/error_log) when I try to print a test page:

E [01/Mar/2009:18:45:53 -0600] [Job 13] Tree connect failed (NT_STATUS_BAD_NETWORK_NAME)
E [01/Mar/2009:18:45:53 -0600] [Job 13] Unable to connect to CIFS host, will retry in 60 seconds...

I've tried changing device URI from WORKGROUP/SHARE to just IP address in the Printer Config and through CUPS | Add a printer.
Neither have worked. 
 
The device URI currently is smb://10.10.10.103/HP%20940c.   I verified my smb.conf does NOT have this entry: msdfs proxy = no.  I've also tried using this for the device URI with this format: smb://networkusername:password@SERVER/PRINTER

Any ideas on what I can try next?   Is it even possible to print to a shared printer on windows?  Any help would be greatly appreciated.  Thanks in advance!

---

