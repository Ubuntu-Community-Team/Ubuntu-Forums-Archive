---
title: "Connecting to a network printer"
date: 2009-04-10
forum: General Help
---

### Post by Phil Binner on 2009-04-10
I have a print server connected to my wireless router, with one printer attached. The windows machines on my network see it as \\SC0F644A\P1. I have set this up as a printer on my Ubuntu machine as Windows printer via SAMBA. I set this up as smb://liberty/SC0F644A/P1 and verified. I got a message that this was OK, and loaded teh printer driver. The only problem I encountered was when I identified the printer as an HP Laserjet 4 Plus it offered me a range of drivers. I assumed all these would be OK so I took the top one. It is a CUPS driver, but i don't know what that means.

All seems to have gone OK, but when I try to print nothing happens.

Any offers please.

---

### Post by bcom on 2009-04-10
Phil:

CUPS stands for Common UNIX Printing Systems.  It is a cross-platform print server built around the Internet Printing Protocol.


With regard to the printer driver, here is what I used for the HP laser jet:
HP LaserJet 1200 Foomatic/pxlmono (recommended).

If I remember correctly, Ubuntu will offer you a default choice, try the default.  Perhaps a change in the driver will do the trick for you.

---

### Post by Phil Binner on 2009-04-10
I tried all the offered drivers in turn - no joy. Further information though, when I try to print a test page from the printer set-up I get the message "idle - ERRSRV - ERRnoresource (No resourses currently available for request.) opening remote spool Test Page"

I guess there's something else I have to do to make resources available.

---

### Post by bcom on 2009-04-10
Ok!  I don't know what method you used to configure the printer.  Did you open up Firefox and, in the address box, type localhost:631.   This interface might offer more info and choices that could help. On the other hand, the results might be the same.

Also, for what it is worth, I use Ubuntu to print via a Lynksys, 2-port print server on a Windows network.  I did not install SAMBA.  When adding the printers, I choose LPD/LPR printer rather than Windows Printer via SAMBA.

For the device URL, I entered lpd://192.168.1.78/L2.  L2 is the printer queue.  It is another way to refer to P2 which is "windows" terminology.

192.168.1.78 is the IP address that I assigned to the print server. You would use yourprintserverip/L1, 2, or whatever port on the server is appropriate.

I have another printer connected to L1 (P1) the other port on the print server.

If all else fails, you could give setting up a LPD/LPR printer a shot.

---

### Post by Phil Binner on 2009-04-11
OK, that cracked it, though some fairly strange things happened along the way. What I did was to use the firefox page you suggested, and set up a new LDP printer from there. For the path I put in lpd://SC0F644A/L1, which worked. Thanks.

---

### Post by bcom on 2009-04-13
OK!  Glad it worked.  I'm sure its not a perfect solution but at least now you should be able to print.

---

