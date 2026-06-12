---
title: "Driver for Dell Laser Printer 2335dn"
date: 2011-01-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Fredhoud on 2011-01-13
I have a network Dell 23335dn laser printer/copier/scanner, shared via a static ip address among several other computers. Unfortunately I can't use it with my Ubuntu Linux 10.10 laptop directly, unless I go through the Virtualbox OSE, running Windows XP in order to print and scan. I was successful at printing, but not scanning.  Something is blocking access to my computer, even though from the scanner's menu box you can see the Dell Latitude D530 laptop. I posted a separate message about the scanning issue, but never heard from any body.  I hooked the printer directly to my laptop via a USB port, and a message popped-up "no driver's available for Dell 2335dn". Is there any hope in the near future to have a driver for a Dell 2335dn laser printer/copier/scanner?

Thanks,
FredHood

---

### Post by darkhelmetchris on 2011-01-14
Hi Fredhoud,

I hear your pain.  One of my customers has a Dell 2335dn multi-function unit.  I remember the model number because it was only last week that I had to work on it.  She uses Windows as the workstation OS, and I installed a Linux-based server for her two year ago.  Here are my findings that I think relate to your situation:

1.  Printing from Linux:  I was very frustrated with this, and just recently found the following files that MAY be useful (I have not had a chance to return to the customer and try this, as it was only for my own printing from the Linux server):
[http://ftp.us.dell.com/printer/Dell2335dn_Driver_ONLY_Linux_v1.05.tar.gz](http://ftp.us.dell.com/printer/Dell2335dn_Driver_ONLY_Linux_v1.05.tar.gz)
[http://ftp.us.dell.com/printer/Dell2355dn_GM_Linux.tar.gz](http://ftp.us.dell.com/printer/Dell2355dn_GM_Linux.tar.gz)
[http://ftp.us.dell.com/printer/Linux-Lemongrass.tar.gz](http://ftp.us.dell.com/printer/Linux-Lemongrass.tar.gz)
also, it may be worth trying just for fun:  often network-ready printers include compatibility with the HP LaserJet III or 4 PCL drivers - try and see, it could be worse.  You might get a bunch of garbled output, or.. you just might get a test page to print with that driver.  I have had much success with this method when faced with no other option.  There may also be some other driver that is compatible of which I am unaware.

2.  Scanning from Linux:  so far I have no solution here for the Dell 2335dn, so please let me know if you come up with one.  The product info claims it will do scan-to-PDF, but I feel it's important to note that this unit seems to only make PDFs using the proprietary Windows client software, and does not seem to me to generate the PDF directly on the printer before transmission to a computer, as I would have expected.  I don't know about you, but I like the printer to do the grunt work first, and then send the finished product to a computer, not waist my workstation CPU with file conversions.

At the time I was asked to make the Dell 2335dn scan to her computer, the customer was in a pinch, and after poking around for a while, she asked me for an alternate solution, as time was very important to her for this task.  I suggested that she might consider buying a cheap Brother unit, as they typically have built-in PDF creation in their network-ready models, so she bought an MFC-7440N and it worked great, out of the box, in minutes, with no special software.  I was so surprised and impressed with this model, that I purchased one for my wife and I to use at home.  I chose this particular unit over several other brands/models as it was only $160 (CDN) and had the features we wanted:  web browser configurable with built-in PDF conversion (scans, makes a PDF or JPG inside itself, and uploads directly to an FTP server via built-in ethernet interface) with no computer pre-processing.   Simple and easy.  Higher models will send directly to a Samba/Windows share without e-mail or FTP.  I just hit scan on the printer, and open up the network share where it uploaded the PDF by way of FTP.  I used the document feeder for a 36-page scan to PDF.  There are also supported Linux drivers for printing, and I even got faxing out of it (which I don't use).  So, if you are not afraid to throw a little cash at a problem, that's an easy answer.  This was not meant as an advertisement - it was just a nice surprise to me to see this functionality in a low-end consumer product.

---

### Post by darkhelmetchris on 2011-01-14
Further to my previous post, if you're trying to get scanning working via Windows inside a VirtualBox, that should work just fine.  You might want to make your virtual ethernet adapter use bridged mode in order for the 2335dn to auto-detect your broadcast of the Windows scanner-client software - depending on your subnet and NAT choices.

With this method, I did notice that PDF was still a problem, but I did get scanned pages as images in JPG to work (which was not good enough if you ask me).  I believe that the ability to create PDF was not installed automatically from the installation CD - and I have been meaning to contact Dell about that.  However, as you can see in the above post, I "solved" the problem by means of changing the rules of the game.  Not truly ideal, but practical and not expensive.

---

### Post by darkhelmetchris on 2011-01-14
Gosh, a new search just got me another option for you for printing.  You might try here:
[http://www.openprinting.org/ppd-o-matic.php?driver=pxlcolor&printer=Dell-3100cn&show=0](http://www.openprinting.org/ppd-o-matic.php?driver=pxlcolor&printer=Dell-3100cn&show=0)
to see if that PPD works for you.  Please let me know, as I might still implement a solution for my customer's 2335dn.

---

### Post by darkhelmetchris on 2011-01-14
Hmm, Ubuntuforms may have already answered this.  See here:
[http://ubuntuforums.org/showthread.php?t=1371932](http://ubuntuforums.org/showthread.php?t=1371932)

Which will lead you to this:
[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R203589&SystemID=PRN_LSR_2330D&servicetag=&os=UB80&osl=en&deviceid=14894&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=0&libid=40&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=283791](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R203589&SystemID=PRN_LSR_2330D&servicetag=&os=UB80&osl=en&deviceid=14894&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=0&libid=40&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=283791)

and gets you this file:
[http://ftp.us.dell.com/printer/R203589.tar.Z](http://ftp.us.dell.com/printer/R203589.tar.Z)
the PPD file appears to be in the folder /ppd_files/GlobalPPD/

The other forum poster indicates this worked very well for his 2335dn for printing.

---

### Post by Fredhoud on 2011-01-15
:D Many thanks to "darkhelmetchris".  I am now able to scan in PDF or any other format, and print via the Virtualbox OSE with my Dell 2335dn.  That is such a relief as I have one Dell 2335dn at home, and two exact units at work.  After you suggested to switch the virtual ethernet adapter to "Bridge mode", it worked like a charm.  Now I can print and scan via Virtualbox OSE.  It's not the perfect situation.  I wish that there was a full functional driver for Ubuntu, but it's better than nothing at all.

Thanks again,
Fredhoud

---

### Post by darkhelmetchris on 2011-01-20
Were you able to print from Ubuntu using the drivers from above?  I will be going to see my customer next week and it would be handy to know if the Linux driver works for you.

---

