---
title: "Jaunty won't print.  Ghostscript filter problem?"
date: 2009-05-04
forum: General Help
---

### Post by xdevnull on 2009-05-04
I have a Konica-Minolta Bizhub 350 that I use to print at work.  The two previous versions of ubuntu (8.04/8.10) that I used printed flawlessly; I simply loaded the .PPD and boom.

Now however, it won't print at all.  It shows it is printing on my computer, the queue clears, I get the little notification that the print job is done, but the printer doesn't do anything - nothing.  Not even the test page print will print.

I fiddled with the options, loaded other PPD's, installed drivers that weren't obviously for the printer from the list of drivers, etc.  I've used the gnome printer interface as well as the CUPS web interface, deleting and adding the printer several times.  I know the printer works because it prints from a windows machine, and I know my system works because I can print to a different printer.

I did find the following on the OpenPrinting.com website:

> Rating given as "works mostly" because this printer is finicky about the postscript that it will accept: output of dvips does not work and anything filtered by Ghostscript appears to not work (meaning: the job is accepted then dropped silently); workaround: convert the postscript to pdf then back to postscript via Xpdf (or use HPIJS driver). PS output of Openoffice 2.0, Xpdf, and most other applications tried worked fine.

I don't know if this is really the problem, since I never had any trouble printing from any application in previous ubuntu versions.  I have no idea how to turn off Ghostscript filtering (even if you can).  I wondering if anything was turned "on" in Jaunty that was "off" in previous versions.  Any help is appreciated.

Thanks.

---

### Post by xdevnull on 2009-05-06
Shameless bump.....

come on....Nothing??

---

