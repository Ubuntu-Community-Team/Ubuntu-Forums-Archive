---
title: "Error printing via CUPS using PPD file (long)"
date: 2006-07-07
forum: Desktop Environments
---

### Post by Linux-Freedom on 2006-07-07
I have been trying to setup printing from Ubuntu 6.06 to my Toshiba E-Studio 35 (E35).  I thought I followed all of the various HOW-TOs to setup the printer but it appears that I have missed something because it just will not print.   Below is a summary of where I am and what works and what doesn't:

1. I have setup a CUPS-PDF printer.  It works great.

2. I can ping the E35 printer (192.168.2.4).

3. I can even configure the E35 printer through Firefox ([http://192.168.2.4](http://192.168.2.4)).

4. I have followed the instructions at [http://linuxprinting.org/cups-doc.html](http://linuxprinting.org/cups-doc.html) (or so I thought :confused: ).

5. I have setup the printer using the CUPS web configuration ([http://localhost:631](http://localhost:631)).

6. I have obtained and copied the Toshiba E35 EFMN3020.PPD file into the /usr/share/cups/model and used this file when setting up the printer in 5.

7. The system has created an E35.ppd file in /etc/cups/ppd. 

8. The EFMN3020.PPD file pasted the test from cupstestppd (although a few warnings were provided, an overall pass was given).

9. When not printing, the icon in the Printers window shows ready.  I can print to the E35.  The print job shows up in the Jobs window of CUPS as active.  After a few minutes the state in the printer window changes to Pending: printer-stopped.  The E35 icon in the Printers window shows Paused 1 jobs and the actual status in the E35 Properties shows: Paused: /usr/lib/cups/backend/lpd failed.

10. The E35 only has the standard PCL 6 format.  So my guess is that the problem occurs when the computer is converting the file from Postscript to PCL 6.  Part of the problem was a rights issued but I have temporarily fixed that (see 12).

11. A snippet of the last few lines in error_log in /var/log/cups shows the following:

D [06/Jul/2006:23:50:46 -0500] cupsdReadClient: 5 POST / HTTP/1.1
D [06/Jul/2006:23:50:46 -0500] cupsdAuthorize: username="root"
D [06/Jul/2006:23:50:46 -0500] Get-Printer-Attributes ipp://localhost/printers/E35
D [06/Jul/2006:23:50:46 -0500] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [06/Jul/2006:23:50:46 -0500] cupsdReadClient: 5 POST / HTTP/1.1
D [06/Jul/2006:23:50:46 -0500] cupsdAuthorize: username="root"
D [06/Jul/2006:23:50:46 -0500] Get-Printer-Attributes ipp://localhost/printers/PDFPrint
D [06/Jul/2006:23:50:46 -0500] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)

12.  Earlier in the error_log I was getting cupsdAuthorize: Local authentication certificate not found!  This specific error disappeared once I entered the following: sudo chmod -R 777 /var/spool/cups.  However, it still would not print even after I restarted CUPS and printed again.  I also really do not want to make this directly world read.  So any other suggestions on how to make the authentication error go away would be appreciated.

13. The job does not appear to be passed from the desktop to the printer.  I say this because the job stays in the CUPS Jobs window and never hits the E35 Jobs window.

14. The E35 works great when I print from a Windows machine.

I sure hope someone can help because I am at a loss as to what I am missing or what is wrong ](*,).

---

### Post by Linux-Freedom on 2006-07-07
[LEFT][COLOR=#666666][FONT=Verdana]Just wanted to follow-up with my earlier post to advise that when I print a job from my desktop, the printer throws out pages with a line or two of garbage. So I definitely believe that my desktop is not converting the Postscript properly so the E35 GA-1040 printer can understand it.[/FONT][/COLOR][/LEFT]
 
[LEFT][COLOR=#666666][FONT=Verdana]Does anyone have any ideas that could help?[/FONT][/COLOR][/LEFT]

---

### Post by bohboh on 2006-07-07
I had problems with my printer and upgraded cups to 1.2.1 which fixed them, give it a go. I had to manually update as it wasnt available in the repos.

---

