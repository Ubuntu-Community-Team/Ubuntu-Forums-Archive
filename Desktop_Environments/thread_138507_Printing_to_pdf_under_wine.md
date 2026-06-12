---
title: "Printing to pdf under wine"
date: 2006-03-02
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-03-02
I got a notation program under wine (Finale)
I want t o print to a pdf file from that program.
Is it possible to do so without installing the Acrobat Writer under wine (I don't ven know if that's possible...)?

G

---

### Post by cronholio on 2006-03-02
Install the printer driver for "QMS ColorScript 1000 Level 2" (on any Windoze CD or Google for it). Select this printer and print to file. It will be a standard PostScript (.ps) file. Name it accordingly and convert it to PDF using GhostScript.

---

### Post by tamaricky on 2007-04-16
How does one install this (or any) printer driver in wine?  I've tried several installers and they always crash after the EULA stuff.  Other things like Foxit, CutePDF etc, Adobe don't work either.

I have been printing Finale scores successfully with winePS through CUPS.  I made sure CUPS printer was set as the default, and it just worked. Kudos to the good folks of wine!

My problem is I can't get anything over 300 dpi... even if my CUPS default preferences are set to 1200 dpi.  I can't really see a 'real' printer in the print dialogs, & resolution preferences etc are all greyed out.  If a different postscript driver will solve this, I will be so happy.

I deal with orchestral scores so I really need good resolution... would love to free myself of the last remaining shackles of windows... any ideas?

---

### Post by ziffnabb on 2007-04-28
I am also running Finale under wine, but I cannot print from wine at all.  When I try, default printer shows up in the print window, but the only button that does anything, is cancel.

Was thinking of trying to install adobe reader under wine, but I suppose that is not going to work either.

Ziffnabb

---

### Post by ziffnabb on 2007-04-30
Guys:
I got it working.  Install cups-pdf.  Add a printer:
Choose Local
Forward
Change Manufacturer to Generic
Choose Postscript or Postscript Color
Forward
Name your printer
Apply

BEFORE you start Finale, change this PDF printer to default.  Fire up Finale.  Load your file, and go to file then print.  You should see the printer icon appear in the panel.  At this point my Finale freezes, so I just close it.  

Change the default printer back to the printer you want.  Go to Places, Home, PDF.  In thhis folder there should be a pdf file.  Open it, and print.  There you are.

The first time I tried this, my default printer would not print.  I noticed that the setting for my local printer had changed to network, so if this happens to you, just change it back to local.

Ziffnabb

---

### Post by airtonix on 2007-05-01
how come your not using the default pdf handling that is native to ubuntu?

abiword and openoffice both read pdf files, acrobat reader is availbale native to linux it also prints pdf files.

ummmm what else....the browser yeah with addons it also will print pdfs to your printer.

or are you wanting to print to a vitual printer that creates pdf files?

---

### Post by ziffnabb on 2007-05-01
I was trying to print from a windows program running under wine.  I could not find any other way for it to work.  This way is a bit of a pain, I'll admit, but it does work.  It is not something I will do every day, so I can live with it.

Ziffnabb

---

