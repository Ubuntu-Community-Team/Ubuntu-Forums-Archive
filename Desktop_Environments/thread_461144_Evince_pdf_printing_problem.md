---
title: "Evince pdf printing problem"
date: 2007-06-01
forum: Desktop Environments
---

### Post by fdimmling on 2007-06-01
Evince in Feisty does not print some PDF files. The print job is aborted and blocks subsequent CUPS printing jobs. The same file is printed by KPDF without problem. Any one knows the solution?

Friedrich :(

---

### Post by McHenry on 2007-12-16
I have the same problem and have logged it as a bug.

Are you using a HP printer ?

---

### Post by fdimmling on 2007-12-16
As far as I can see it does not depend on the printer. I have three Ubuntu computers running here, two of them still on Feisty, one with Gutsy. The printer server is Feisty and the notebook of my wife too. The PDF on the Gutsy machine can be printed from evince, the PDFs from the Feisty notebook mostly not. I had an Epson Stylus C86 before and since summer a HP Business Inkjet 1200d. Replacing the printer did not have any influence on the problem. Maybe there is some connection with the problem with gscan2pdf. gscan2pdf makes pdf files of scanned pages. On Feisty it produces just white pages, on Gutsy it works. On the Feisty machines I use KPDF to print the PDF files. It works in all cases so far.

Friedrich

---

### Post by tdmoore on 2007-12-17
For the record on this issue, I too have the same issue.
Running Gutsy (love it!!) and yet with an HP 1000 and Xerox Phaser 6110 neither will print directly out of evince.
Very frustrating and as a business owner forces my hand to other options.
Please fix this bug Ubuntu team....PDF is the de facto document format so we need it!

<ADDITION>
Just downloaded Acrobat Reader and installed.  Opened up document fine however will not print either!  Document I am trying to print is a credit card statement and is secured...must be the issue.  Will keep trying however this is something I still feel needs to be resolved.

---

### Post by fdimmling on 2007-12-18
> **tdmoore said:**
> For the record on this issue, I too have the same issue.
Running Gutsy (love it!!) and yet with an HP 1000 and Xerox Phaser 6110 neither will print directly out of evince.
Very frustrating and as a business owner forces my hand to other options.
Please fix this bug Ubuntu team....PDF is the de facto document format so we need it!

<ADDITION>
Just downloaded Acrobat Reader and installed.  Opened up document fine however will not print either!  Document I am trying to print is a credit card statement and is secured...must be the issue.  Will keep trying however this is something I still feel needs to be resolved.

I am rather shure your problem is a different one. I can print about one third to one half of the PDF documents with evince from Feisty and all from the Gutsy machine. With KPDF and Acrobat I could print all documents with Feisty (the computer with the acrobat now is running Gutsy). Thus I just switched to KPDF for printing in Feisty.

Friedrich

---

### Post by tdmoore on 2007-12-18
Appreciate the reply and your suggestion.

Evince works fine for non secured PDF's on both my printers and so does Acrobat Reader.

Secured or password protected both fail...still working on this but hope to find a solution.

---

### Post by tdmoore on 2007-12-21
Interesting experimenting with this and asking for help.

Easy file.  Writer document in OOo, exported to PDF.  No security, no issues.

NEVER printed in evince, however did print in Adobe Acrobat reader.

Really want to know why a native Linux app will not do the job.  Love Ubuntu however this is really a deal breaker for me.

Anyone?

---

