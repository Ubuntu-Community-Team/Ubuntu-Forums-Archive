---
title: "Cannot Print Flash Page from PBS Kids"
date: 2008-11-29
forum: Desktop Environments
---

### Post by kc0dxf on 2008-11-29
I'm trying to print out a coloring book at PBS Kids.  When I click on the print icon, a print dialog box comes up and allows the selection of a printer and the pages to print.  But when I select ok, nothing happens and nothing is queued up.

I have an HP Deskjet 640c using hpijs via the parallel port.  All other printing works fine.  I am using Firefox 3.04 from the Ubuntu package.  Flash version 9, r124.

Any ideas?  Is Flash not able to print on Ubuntu?

---

### Post by aysiu on 2008-11-29
I don't know how to fix your problem, but a workaround may be taking a screenshot of the page and printing the screenshot.

---

### Post by blehman419 on 2008-12-09
I was having the same problem, and I went to [http://localhost:631](http://localhost:631) and set my default printer.  I am now able to print all the free coloring book pages I want from Nick Jr. Hope this gets you up and running!

---

### Post by leehach on 2009-01-04
blehman419, your advice worked for me.  I didn't even realize that there was no default printer set, but once I set it, printing worked fine.  

It's a little bizarre because previously the print dialog came up which listed the printers to choose from.  It's not clear to me why the printer needs to be set as the default when you pick the printer in the print dialog anyway, but it's working now.

---

### Post by roscopico on 2010-02-01
Hi all .  I'm having a similar problem.

I'm using a HP deskjet f2210 
Driver: HP DeskJet F2100 Foomatic/hpijs, hpijs 2.8.2 

I set the default both at localhost and in system.  When I hit "print" the document submits, but then the printer says "complete" without actually printing anything.

Does anyone have any ideas?

TIA

---

### Post by roscopico on 2010-02-01
what does it mean when the print job document name is (stdin)?  all others either have a URL or a CUPS listing.

I appreciate any help someone might be kind enough to offer.

Thanks!

---

