---
title: "CUPS Printing problems after update on 10.10"
date: 2010-11-08
forum: Desktop Environments
---

### Post by rmccarri on 2010-11-08
Hi Everyone,
I noticed a couple of days ago, a bunch of cups updates went through.  I just tried printing some PDF files today and my printer is skipping pages.  I have a 20 page document and I get the first couple of pages, one later on and nothing else. The job just stops with no errors that I can find.  Everything seems normal in the cups logs, syslog, dmesg and messages.  has anyone else run into this issue?

I'm running a Brother 5270 networked printer.

---

### Post by rmccarri on 2010-11-08
Just to give some more information, I can ping the printer and access the HTML based config setup.

---

### Post by rmccarri on 2010-12-13
I'm continuing to have these printing problems after several weeks.  Is anyone else having a problem with the Brother drivers after the latest CUPS update?  I cannot find any errors in any of the logs, so it seems like the job is getting sent fine, but it will not print.  Printing from Windows computers isn't a problem, so it doesn't seems like the device itself is borked.

---

### Post by ScottyD135 on 2010-12-13
> **rmccarri said:**
> I'm continuing to have these printing problems after several weeks.  Is anyone else having a problem with the Brother drivers after the latest CUPS update?  I cannot find any errors in any of the logs, so it seems like the job is getting sent fine, but it will not print.  Printing from Windows computers isn't a problem, so it doesn't seems like the device itself is borked.

I'm having similar, but different symptoms.  I'm using 10.04, a brother DCP-7020, having NO problems with local printing, but can't access the printer through any of our my networked computers (windows/mac).  My brother drivers haven't had any problems for local printing through ubuntu...

---

### Post by ebow on 2010-12-19
Hello All,
I installed 10.10 one week ago. Can't get my Brother HL-5380DN working. It's connected via network. When following System->Administration->Printing, the installer sees the printer over the network, downloads a driver and installs it. Then everything looks fine, except that it doesn't print. Reboot doesn't help.

The printing troubleshooter tells me 'The queue 'HL-5380DN' is not enabled. Rhe reason given is: 'Destination printer does not exist!'. To enable it, select the 'Enabled' checkbox in the 'Policies' tab ...

If I  try that, a 'Print Error' shows up: There was a problem sending document 'Test Page' (job 1) to the printer. If I then follow the Printing troubleshooter dialogs, I end up at the same place as before: I should enable the printer.

Any ideas?

---

### Post by Harkainian on 2010-12-21
I have a HP Photosmart D110 that couldn't print at all after the update!

---

### Post by nocx on 2011-01-07
Same problem with Epson NX115 and both 10.10 desktop and UNE

---

### Post by maarten256 on 2011-01-07
Similar issue here... A bunch of updates were published through the update manager (ubuntu 10.10) a couple days ago, and now I can't seem to be able to print PDFs anymore... I've got a HP PSC2200, and I am able to print a good test page to it.

When I try to print a PDF (from evince) the print job fails... Running the debugger results in a status message being reported stating "/usr/lib/cups/filter/pdftoraster failed".

Anybody have the same issue? Any suggestions (would hate to have to reinstall CUPS)?

Thanks,

---

### Post by Endless_Nameless on 2011-01-31
Ubuntu 10.10 here.

I am having similar problems. It seems that all files that I send to network printers are not sent at all. No error messages appear, it just say "processing" for a print job.

I tried different printers (Lexmark, HP and Xerox), but none seem to work. The funny thing is that this happen only with PDFs... images and OO docs are ok.

---

### Post by Enigma2 on 2011-02-25
I have the Brother MFC 7440 and same problem here. Every time you try to print (Networked) the printer is not enabled. So what gives now? How are we suppose to print?

---

### Post by Enigma2 on 2011-02-26
For all of those that still have a problem with CUPS and 10.04 here is a solution I found in another post.

From your printer, get the info of the Network. What you care is the IP address of the printer.
Then go to System, Admin, Printing, highlight your printer and click properties. You want to change the Printer URL. DO NOT click Change just edit at this window. (If you click change it will try to find a printer). In that window type Socket:// and the IP number. Hit enter and you are ready. 

Hope this helps but my Brother works like a charm. This is not a permanent solution but will get us by until the guys that really know:) fix the problem with the CUPS

---

### Post by sostentado on 2011-04-04
@Enigma2... ur just drunk i think...

First, go to [http://localhost:631](http://localhost:631) then you will be at CUPS webgui. Then on scroll down and look for Find Printer Drivers, search for your device. If the driver is not in there, then that's the primary problem why you can not print even samba detects it and already added your printer.

---

### Post by Enigma2 on 2011-04-04
The driver in NOT available at CUPS website. This is a multifunction unit that up to the latest Ubuntu update had no problems. Now it does. Also the driver is not the problem. The problem is that Ubuntu will not see this unit on the network. (Wireless). I am far from being an expert on Ubuntu. I was using Linux (Madrake) a few years ago, then I moved to Macs that I still use as my main box. I always though loved Linux so here I am. What I mean is that I do not pose as an expert but I just put here what I found on another Thread from people with the same problem. It worked for me. By the way I am always drunk. :)

---

