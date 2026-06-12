---
title: "printer says it printed, but it didn't..."
date: 2008-08-10
forum: Desktop Environments
---

### Post by Browner87 on 2008-08-10
I have Ubuntu 8.04 installed on a computer I'm using as a web and file server. I just moved from XP to Linux and my problem is a shared printer. It's an HP Laserjet 1018 and uses USB to connect. My computer recognizes the printer and hp-toolbox says it's fine, but when I print t says the printer has started a job, device is  busy, print job completed. HOWEVER, the document no more printed than made me a milkshake. No lights flashing, no noises, nothing. My printer just sat idle the whole time. Does anyone have any suggestions?:(

---

### Post by bmac on 2008-08-10
Have you installed the HPLIP print driver? See enclosed link....

[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

Hope this helps....

---

### Post by Browner87 on 2008-08-12
srry - internet was down for a while :P

ya - installed driver and rebooted and still nothing. Everything says that it was successfully printed, but nothing comes out of the printer...

---

### Post by lisati on 2008-08-12
First of all, don't panic! 

Are you printing something using a printer connected to another machine? If so, read on!

Sometimes when I print something from my laptop (Ubuntu) using a printer connected to my desktop (which normally runs XP), my laptop tells me that it has printed, even though it's still printing.

What could be happening is that the print job has been forwarded to the computer with the printer, which then takes over responsibility for printing it. Then, as far as the first computer is concerned, printing has finished. The computer with the printer SHOULD have something to show what's in its print queue.

---

### Post by Browner87 on 2008-08-12
no - I'm using RealVNC to remote access the machine and print DIRECTLY from it. I opened openoffice writer on the machine directly connected to the printer, and this is what happened.

---

### Post by lisati on 2008-08-12
> **Browner87 said:**
> no - I'm using RealVNC to remote access the machine and print DIRECTLY from it. I opened openoffice writer on the machine directly connected to the printer, and this is what happened.

Anyway, I'd expect something to show up on the print queue for the machine with the printer.

Anyone else with an idea?

---

### Post by Browner87 on 2008-08-12
Hmmm... seems to depend on what I look at apparently. After installing HPLIP driver, I got a tray icon and when I click it it still says processing under status of the job, but under the hp-toolbox control panel, it says everything is all done...

---

### Post by Browner87 on 2008-08-17
If anyone has any more ideas it would be greatly appreciated. This is the only reliable printer in the house and it's very remote from all other computers to physically hook into.

---

### Post by bmac on 2008-08-17
Have you tried printing a test page from the HP icon (right click on icon & select HP device manager, I believe it's under actions)? I'm wondering if Open Office is printing it as a PDF and putting it in a folder. When you click print in open office does it show your printer in the "Printer" "Name" or does it show PDF? Have you tried printing from any other application?

---

### Post by Browner87 on 2008-08-18
Nope - I've tried test pages and they don't print either. It says printing, then says Started a printing job, then says complete then says Idle. Yet, nothing prints...

Please - anyone? Does anyone have much experience with HP printers in Ubuntu?

---

### Post by Browner87 on 2008-08-26
Nobody has any more ideas?

---

### Post by drock3322 on 2011-12-01
I am having this exact same problem!  It's so strange!

The drivers seemed to install perfectly and my PC seems to think the printing went fine, but the printer "doesn't print the document so much as it makes me a milkshake".

I've tried printing a .pdf from Adobe, and a .txt file from gedit.  

I have Ubuntu 11.10 64 bit installed on my Acer 1410 notebook.  I'm trying to print to an HP Laserjet 1000 because this printer won't work anymore with Windows 7 (don't get me started on that...)

The post someone made about it seeming like it's printing to a file somewhere makes sense. Is there a way to find this file? What are .prt files named in linux?  

Based on all the difficulty people are having with Windows 7 64 bit (with 32 bit working in most cases), I have a feeling this may be a part of the problem.  The HP Linux site says it supports the HP LJ1000 under 11.10 but not necessarily the 64 bit version.

Please tell me I'm wrong?

---

### Post by sallym on 2012-01-05
Hello all.

drock3322, did you get this sorted? I'm having the same problem but with Ubuntu 11.10 34bit and Brother-7340 printer.

Any help appreciated!
Thanks.

---

### Post by drock3322 on 2012-01-05
sallym,

I haven't had any luck, no.  I think the issue is that the HP Laserjet 1000 printer is simply not compatible with any 64-bit OS. I haven't tried re-installing Ubuntu 32 bit since I don't think it's worth it, but I imagine that would work.  

Did you mean you are using a 64 bit or a 32 bit OS?

---

