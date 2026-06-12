---
title: "Problem setting up wireless network printer"
date: 2006-01-13
forum: Desktop Environments
---

### Post by backscratcher on 2006-01-13
I have an HP7260 printer connected to my wireless network using a 3Com OfficeConnect Wireless Print Server. I had no problems setting it up with the WinXP PC's on the network. However, I can't seem to set it up properly on my Ubuntu laptop which is also connected wirelessly to the network and the internet. The printer server manual indicates the following setup to be done:

For printer type, select Remote Unix (lpd)

Use the following data to complete the resulting dialog:

Name: Enter a name for this printer
Spool Directory: /var/spool/lpd/name_of_printer
Remote Host: IP Address of Print Server (e.g. 192.168.1.100)
Remote Queue: Ln (where n is the logical printer number)

However, in the Ubuntu Printer connection setup, it only asks for:
Printer Type: Unix Printer (lpd)
Host: 192.168.1.100
Queue: L1

When I try to print a test page, it fails.

I noticed that the Queue is missing everytime I revisit the settings.

Where should I enter the spool directory information? Is it still required? 

What should I do?

---

