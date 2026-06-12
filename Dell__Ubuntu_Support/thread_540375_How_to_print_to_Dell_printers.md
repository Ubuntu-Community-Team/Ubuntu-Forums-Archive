---
title: "How to print to Dell printers"
date: 2007-09-01
forum: Dell  Ubuntu Support
---

### Post by diltonm on 2007-09-01
1) Download the free VMware Player or Server and run an authorized copy of Windows XP and install your Windows printer drivers. I prefer VMware Server so even if a game happens to crash my X session, the virtual machine remains unaffected.

2) Download PDFCreator from SourceForge and install in Windows XP.

3) Configure PDFCreator to print to your printer after saving the file.

4) Share the PDFCreator print driver and any Linux or Windows client should be able to print.

There's an added delay since PDFCreator first saves the file to a PDF (since that's what it's mainly for anyways) then it should print as long as you did item 3) and you can print regularly from within Windows.

Enjoy!

---

### Post by bgturk on 2007-09-02
HI, this is exactly what I was thinking of doing with my Lexmark printer. It  has no Linux drivers, so I am printing to it from a Windows Server 2003 running in Virtualbox that is sharing it on my local network.

However, still I have not been able to figure out how to print to PDFCreator from a Linux machine. When I do it from a Windows machine over the network the drivers are automatically installed and it works fine - saves a PDF file and then prints it automatically. From a Linux machine I tried the Generic->Postscript driver, but I wasn't able to print. What driver should I use?

Also another annoying thing is that in order to be able to print from another machine on the network, I need to be logged on the print server and be running PDF creator in the foreground. Otherwise it will not print anything until the next time I log on.

---

### Post by diltonm on 2007-09-02
Good question I should have mentioned that, I think I used RAW. The only thing I can get by printing directly to the Dell share is a blank page. This is odd since on the same hardware and printer but with SuSE this had worked. That's ok since this solution with PDFCreator gives me a record of all jobs that have been sent to the printer.

So, anyways, in Ubuntu try connecting to Windows SMB, RAW and share PDFCreator in the Windows VM.

And, the next printer I buy will be Linux friendly.

---

### Post by Lord Illidan on 2007-09-02
What model are DELL printers? Lexmark?

I only buy HP printers..and they work fine with Ubuntu.

---

### Post by diltonm on 2007-09-02
I think they are re-branded Lexmarks from my Googling. We used to have an HP, and that is probably what we will switch back to. The one we had also worked well with SuSE.

---

### Post by bgturk on 2007-09-05
> **diltonm said:**
> 
And, the next printer I buy will be Linux friendly.

Thanks. The Raw driver works fine with PDFCreator. 

My only remaining unresloved issue is that PDF Print Monitor has to be open in order for the printserver to accept print job. Is there a way to make it start automatically?

---

### Post by bgturk on 2007-09-05
To run PDFCreator as a service one needs to follow these steps:
[http://www.pdfforge.org/node/560](http://www.pdfforge.org/node/560)

---

### Post by diltonm on 2007-09-05
> **bgturk said:**
> To run PDFCreator as a service one needs to follow these steps:
[http://www.pdfforge.org/node/560](http://www.pdfforge.org/node/560)

I'm not completely sure I understand, PDFCreator acts as a print driver, there's no need to leave its window open or run it as a service.

---

### Post by bgturk on 2007-09-24
> **diltonm said:**
> I'm not completely sure I understand, PDFCreator acts as a print driver, there's no need to leave its window open or run it as a service.

It does not act a a print driver per se. It is essentially a virtual printer in Windows that accepts print jobs and saves them as PDF files. What is very useful is the additional feature it has - it can send the pdf files that it creates to the default printer - so you can indirectly print from your Linux box to an unsupported printer attached to your virtual windows machine.

---

### Post by diltonm on 2007-09-24
Yes, that was the point of my original post, thanks.

---

### Post by phr0ze on 2007-09-25
My dell printer works fine with the generic post script driver. However I eventually downloaded the redhat print driver from dell and extracted that to use in Ubuntu.

---

### Post by bogr@ on 2007-09-26
Hi phr0ze.  
What printer have you got, and which printer driver did you use from Dell?
Thanks

---

