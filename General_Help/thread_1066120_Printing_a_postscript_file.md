---
title: "Printing a postscript file"
date: 2009-02-10
forum: General Help
---

### Post by Riverglen on 2009-02-10
I've been playing around with a CAD application (Qcad).  Works well, but I am unable to print the drawings.  The program presents a print set-up dialog that has options to send the output to a printer or to a file.  But, the dialog doesn't include the printer I have installed as a selection, apparently because it isn't postscript capable.  Printing to a file results in a .ps file.

So, is there any straight forward way to either convert the .ps to something the printer can handle, or to enable the printer to handle .ps files?

I am using Ubuntu ver 8.10, and the printer is a Canon MX310.  I wasn't able to find a driver specifically designed for this printer and wound up using a driver for the Canon MP-180, which works fine for everything else I've wanted to print.

---

### Post by cbraxton on 2009-02-10
You might try converting the postscript file to pdf with the "ps2pdf" program.

---

### Post by Riverglen on 2009-02-10
That was suggested in the Qcad help file.  But I was unable to find it in the software repositories.  I'll take another look to see if I missed it somehow.

---

### Post by Riverglen on 2009-02-10
Looked around a bit and tripped over a solution to the problem.  First, I discovered that ps2pdf is already installed.  Discovered it by looking for a man page.  Then, I right clicked on the .ps file and discovered that I could open it in "document viewer", from which I can print it just fine without going through the conversion step at all.  Didn't even know that document viewer existed.  Duh!

---

### Post by tangerine12 on 2009-02-11
hehe...always look for the simple solutions ;D

Anyway, if someone else have the problem of converting postscript there are plenty of [postscript converters out there]("http://www.inkguides.com/merging-extracting-and-converting-postscript-files.asp#convert-postscript-to-and-from-documents-and-files")

---

