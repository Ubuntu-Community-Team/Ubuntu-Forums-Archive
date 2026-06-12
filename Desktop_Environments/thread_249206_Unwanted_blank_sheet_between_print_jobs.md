---
title: "Unwanted blank sheet between print jobs"
date: 2006-09-02
forum: Desktop Environments
---

### Post by Alan(UK) on 2006-09-02
I have an HP Laserjet 1100 connected to my router/firewall/printserver PC. The printer works fine from a Windows computer on the network.

My Ubuntu Dapper computer uses the recommended hpijs driver. The printer configuration is set to UNIX Printer(LPD). It prints fine but...

After each print job, the printer feeds a blank sheet which is cooked in the print engine and comes out warped - thus spoiling the sheet.

It feeds the extra sheet even when printing a single page file from gedit. It also does it when printing a document from OO.org WRITE. Printing the same .odf from OO.o in Windows to the same network printer does NOT feed the extra blank sheet at the end.

I can find no way of turning this 'feature' off.

---

### Post by bergi on 2006-10-28
Hi Alan(UK),

I have a similar problem with my printer.
I just bought a brother HL-2030 and while printing documents
mostly the second page (so it prints the first one and because of a bug it takes two instead of one sheet) in between is an empty one.
Looking for a solution I've found this page here: [http://www.pcwelt.de/forum/drucker/220636-brother-hl-2030-zieht-ein-blatt-papier-zuviel.html]("http://www.pcwelt.de/forum/drucker/220636-brother-hl-2030-zieht-ein-blatt-papier-zuviel.html")(German)

In one reply it's said that the printer gets a signal for printing an additional line, so there is "our" empty page. It's kind of communication problem (although its a problem between a ThinClient an the printer, I think the reason is a similar one).

Can anybody give an answer to solve the problem.
Could it be a bug in generally printing pdfs or in acrobat reader (nonfree i know) or in lpr or cups etc.?
By the way it's the first printer of mine which has such problems, also the first laser.

System: Student on Edgy (who likes to print in manual duplex), and HL-2030 (he does not :( )

---

