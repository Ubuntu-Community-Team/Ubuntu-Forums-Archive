---
title: "Windows to print to PDF Samba Printer"
date: 2006-02-15
forum: Desktop Environments
---

### Post by Armada73 on 2006-02-15
Im a very very big Newbie with Ubuntu and Linux after leaving 'C' programming around 15 years ago, for working in the publishing industry, so I do have a little bit of knowledge but please for the moment don't get too techy on me....

Anyway.

Following a walk through I have managed to set up a PDF printer in Ubuntu which works lovely, but I dont seem to be able to see it on the windows machines even though my HP Laserjet is seen across the network no problem.

do I have to issue any type of command to Samba to add this printer to the share list.

---

### Post by Armada73 on 2006-02-15
Okay, sorted that, just need to restart my linux box, windows can now see the PDF printer but on testing still have a few problems.


Locally.
I can print from the text editor fine, but not from other applications like  open office, firefox etc.

(I know open office has its own save as PDF option, but this is not what I am interested in need a global solution, not one thing for this and one thing for another)

Across network.
Although windows now sees the printer, printing to it, results in nothing happening, windows appears to print, but nothing appears in the print queue on the windows PC or the linux box adn no obvious PDF files appearing, so I am now stuck.

---

### Post by tagg3rx on 2006-02-15
Intresting - I have considered this before but with out an actual install of the network server build of adobe distiller i was of the impression it could not be done.  Course thats what open source is all about - saving you money and providing better souloutions.

I think to begin a good question is: What walk through did you follow?

---

### Post by anil_robo on 2006-03-15
[quote=Armada73]
Although windows now sees the printer, printing to it, results in nothing happening, windows appears to print, but nothing appears in the print queue on the windows PC or the linux box adn no obvious PDF files appearing, so I am now stuck.[/quote]

Armada you can try [my pdf how-to ]("http://ubuntuforums.org/showthread.php?t=140815")and see if it works for you.

---

### Post by bobpaul on 2006-03-20
Another thought: why not install a local pdf printer on the windows machine?

CutePDF works really well and is free as in beer, or you can use PDFCreator which is completely OSS (it's on SourceForge).

If you really need a network based solution, then Cups would be it as both CutePDF and PDFCreator will bring up a prompt for filename whenever you print to them (I've shared them across the network with samba and it's not fun). The downside I see with cups is that the filenames aren't carried across to the pdf, just some queue number.

Can you print PDFs locally on the linux machine using Cups? IE is it a network issue or a cups issue? (Or maybe both?) Get cups working locally first, then do the sharing to windows.

---

### Post by anil_robo on 2006-03-20
[quote=bobpaul]Another thought: why not install a local pdf printer on the windows machine?[/quote]

Yes, please use primopdf - it's the best free pdf printer for windows in my opinion.

> Can you print PDFs locally on the linux machine using Cups?
yes, everyone can.

> IE is it a network issue or a cups issue? (Or maybe both?)

There could be a number of issues - firewall, samba configuration, NAT, and possibly others too. However, I've not been able to pin the culprit so far.

> Get cups working locally first, then do the sharing to windows.

See this: [http://ubuntuforums.org/showthread.php?t=140815](http://ubuntuforums.org/showthread.php?t=140815)

---

