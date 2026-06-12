---
title: "Ubuntu printer setup not right..."
date: 2005-10-14
forum: Desktop Environments
---

### Post by hajk on 2005-10-14
Hi, I just installed Breezy on my laptop, including configuring a network HP DeskJet 5850 printer. The setup of the printer is identical to that on my desktop running Debian Sarge, down to the same PPD file used. In Breezy I used the System/Administration/Printing menu to do the setup, in Sarge I did it via localhost:631 (which has been disabled in Breezy).

Printing a test page in Breezy produces a special "Ubuntu" page (not the standard CUPS test page), and it doesn't print right -- moved up by about 2.5 cm (1 inch), clipping the top part of the page. The printer has been set up for single-sided printing, which happens OK for the test page. Yet, when I print a self-produced PDF-file (from pdflatex), the page layout is OK but the printer is all of a sudden in double-sided mode (in Sarge: same layout, but single-sided).

I wonder what is going on here...

Problem 99% SOLVED, see my last post this thread.

---

### Post by sinbad782 on 2005-10-19
Hmm, no idea although there now seem to be two different sets of drivers for the HP printers. I found that the foomatic driver worked best for me (in the HP group, not the HPLIP group) with my LaserJet 6MP. 

I don't know what it's like for newer printers though.

---

### Post by majikstreet on 2005-10-19
[QUOTE=hajk]Hi, I just installed Breezy on my laptop, including configuring a network HP DeskJet 5850 printer. The setup of the printer is identical to that on my desktop running Debian Sarge, down to the same PPD file used. In Breezy I used the System/Administration/Printing menu to do the setup, in Sarge I did it via localhost:631 (which has been disabled in Breezy).

Printing a test page in Breezy produces a special "Ubuntu" page (not the standard CUPS test page), and it doesn't print right -- moved up by about 2.5 cm (1 inch), clipping the top part of the page. The printer has been set up for single-sided printing, which happens OK for the test page. Yet, when I print a self-produced PDF-file (from pdflatex), the page layout is OK but the printer is all of a sudden in double-sided mode (in Sarge: same layout, but single-sided).

I wonder what is going on here...[/QUOTE]
I'm not 100% sure, but Ubuntu seems to default to using A4 letter size, which is not OK if you are in the USA or use USA paper. I would try fiddling with the letter sizes to fit your local size.

-m

---

### Post by mark on 2005-10-22
Look for the file */etc/papersize* and edit it for your local needs.  The default is A4, which led to some stange results here in the US, where Letter is the accepted default.

---

### Post by Petrush on 2005-10-24
We have the same problem using A4, pages printe some cm'
s too high. From acrobat & some others it's ok, but the testpages prints wrong.

UPDATE:
/etc/papersize was set to "letter". Changing to A4 solves the problem! Thanx!

---

### Post by hajk on 2005-10-24
The following setup worked for my HP DeskJet 5850 network printer with (in my case) IP 10.0.0.160, using the new HP Linux Imaging and Printing system (HPLIP) which is already running in Breezy by default:

1. Get the proper CUPS URI for this printer with the command (as user)
    "hp-makeuri 10.0.0.160", resulting in "hp:/net/deskjet_5800?ip=10.0.0.160".

2. Open System/Administration/Printing, click on New Printer, choose CUPS
    (IPP) printer using the above URI.

3. Choose printer brand name HP (HPLIP) -- not HP -- and accept the 
    recommended driver.

4. Configure, in my case for A4 paper size and double-sided printing off.

5. Print the Ubuntu test page -- it worked perfectly. 

Why only 99% SOLVED? Because printing my test.pdf file directly with 
"lp test.pdf" puts the printer suddenly in double-sided mode. This does not happen when printing this PDF file from inside Evince, Xpdf or Acrobat Reader.
It happens only with PDF files, not when (for example) dumping a directory listing to the printer with "ls | lp".:confused:

---

