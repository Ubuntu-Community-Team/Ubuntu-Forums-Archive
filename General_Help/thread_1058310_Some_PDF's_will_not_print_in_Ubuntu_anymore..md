---
title: "Some PDF's will not print in Ubuntu anymore."
date: 2009-02-02
forum: General Help
---

### Post by 73ckn797 on 2009-02-02
Is anyone else suddenly having problems getting certain PDF documents to print?

I have the HP Officejet 5610 All-In-One and have not had any issues printing any documents until today. My work occasionally requires printing PDF documents sent to me from a client.

I suspect that the PDF they are generating is the cause since other PDF's print just fine. I have tried using the default document viewer and the Adobe PDF reader in Ubuntu. Could this be any issue with a newer version of the PDF document creator they may be using?

Any suggestions to get these to print? I have to boot up Windows XP and they will print fine. 

When I informed my client that I do not use Windows they said that could be a problem.

Windows if necessary though not the preferred method/OS.

---

### Post by sedawk on 2009-02-02
Only to get this straight: you can perfectly view the documents
inside the viewer (evince, adobe's reader) but when you print
them printing fails?
Does printing stop after some pages (e.g. with images) or does it
not start at all? What happens if print (unprinted) pages page-by-page?

---

### Post by 73ckn797 on 2009-02-02
> **sedawk said:**
> Only to get this straight: you can perfectly view the documents
inside the viewer (evince, adobe's reader) but when you print
them printing fails?
Does printing stop after some pages (e.g. with images) or does it
not start at all? What happens if print (unprinted) pages page-by-page?

View = Yes
Print = fails, but only PDF's from the one client with error message of failure to print with option to diagnose. (see attached screen shot) Occurs with Evince and Adobe.

No partial printing either. Printer does not even begin print.

Edit: It is probably only an issue with the source. If so, then I am stuck.

---

### Post by jmail524 on 2009-02-02
I had a similar problem but it only occurred with large PDF documents. (50+ pages, I think.)  I was trying to read and print them with the Ubuntu included application Evince.  Reading the PDF documents was not a problem but printing wouldn't even stat on large documents.  I ended up installing the Medibuntu repositories and then installed 'acroread'.
Acroread doesn't seem to reproduce the printing problem so I'm guessing it is a bug in Evince. (Not sure, didn't look into it that closely.)

PS: Please check the legality of using the Medibuntu repositories where you live before installing the software.

Thanks.
Brian

---

### Post by 73ckn797 on 2009-02-02
> **jmail524 said:**
> I had a similar problem but it only occurred with large PDF documents. (50+ pages, I think.)  I was trying to read and print them with the Ubuntu included application Evince.  Reading the PDF documents was not a problem but printing wouldn't even stat on large documents.  I ended up installing the Medibuntu repositories and then installed 'acroread'.
Acroread doesn't seem to reproduce the printing problem so I'm guessing it is a bug in Evince. (Not sure, didn't look into it that closely.)

PS: Please check the legality of using the Medibuntu repositories where you live before installing the software.

Thanks.
Brian

The documents are only 2 pages!!!!

I have medibuntu enabled but have not, at this point, looked into any other programs to make things work.

The frustrating thing is that there are 2 clients that, in different ways, makes me have to use Windows XP to get my work done. OH WELL! As long as the work gets done and I get paid for my services.

---

### Post by sedawk on 2009-02-02
You might think about exporting the pages (as screenshots?) to gimp for
printing.

Or try your luck with something like PDFedit (Load, Save with new name,
try to print new file).
[http://en.wikipedia.org/wiki/List_of_PDF_software](http://en.wikipedia.org/wiki/List_of_PDF_software)

Or even more complicated:
Try to print to pseudo-PostScript printer (into a file).
Open that file with evince (or ghostview or ...) and try
to print again.

Awful, I know ...

---

### Post by todak on 2009-02-02
Ask the client if they have unintentionally protected the document from being printed. That is possible using Adobe Acrobat.

---

### Post by 73ckn797 on 2009-02-03
> **todak said:**
> Ask the client if they have unintentionally protected the document from being printed. That is possible using Adobe Acrobat.

Actually, that probably is not the problem since the PDF's will print in Windows. It is only happening in Ubuntu.

---

### Post by kaibob on 2009-02-03
> **73ckn797 said:**
> Is anyone else suddenly having problems getting certain PDF documents to print?...
I don't receive any error messages, but I occasionally find that evince will not print PDF documents. This happens most often with PDF statements received from my bank. The workaround I use is to enter the following in a terminal window:

```
lpr filename.pdf
``` 

I don't know if this will work for you, but it's easy to check and it's better than rebooting to Windows. I encounter this often enough that I have assigned lpr to the nautilus right-click menu.

---

