---
title: "Default Dapper install + Samba + Windows print"
date: 2006-07-03
forum: Desktop Environments
---

### Post by HarveyB on 2006-07-03
Hi

Trying to sort out a default install issue with 6.06 and printing to a Windows NT machine. 

Problem: Adding a printer from the Window NT server works with the default install but on rebooting the machine I have to redo the "Connection" for the printer. Once established the printer works for the rest of the session. Sending a print job to the printer after a reboot fails with a "Printer paused" and the status reads "Paused: /usr/lib/cups/backend/smb failed".

I have read a number of other posts with various amounts of info including installing the full Samba package and setting the local machine up as a server. At this point I am trying to simply add the Windows shared printer, I don't need to share any of my services with the network.

Is there additional settings/programs with the default 6.06 install that needs to be added/changed to complete this basic task? Why doesn't the printer "remember" my connection settings between reboots?

Cheers
Harvey

---

### Post by HarveyB on 2006-07-04
UPDATE

As an update to trying to get this sorted out without installing a bunch of new packages to my system, I have just completed a complete new format & default install off the installation cd with no updates applied. My first operation was to set up the network to match our work settings and then I added a printer from our NT server. 

Again it prints fine during that session however after a reboot I need to go through the "connection" process again from the printer settings menu box. What am I supposed to do to have it remember the connection details????

Thanks in advance for any help/advice provided.

---

