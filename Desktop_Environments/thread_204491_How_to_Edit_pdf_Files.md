---
title: "How to Edit pdf Files?"
date: 2006-06-27
forum: Desktop Environments
---

### Post by larry on 2006-06-27
Dear All,
Probably it is a hopeless question, but it is still worth a try: is there any #free# tool under Ubuntu to edit pdf files?
Cheers

Larry

---

### Post by aysiu on 2006-06-27
[QUOTE=larry]Dear All,
Probably it is a hopeless question, but it is still worth a try: is there any #free# tool under Ubuntu to edit pdf files?
Cheers

Larry[/QUOTE] Yes. KWord.

---

### Post by larry on 2006-06-27
I see. But before I delve into Kword, please put my mind at rest: can I really modify a pdf file using Kword? Perhaps I did not make myself clear: I can of course produce a pdf in many ways, but my problem is: given a pdf (and nothing else), can I modify it (e.g. remove text, cut & paste figures etc...?).
Cheers

Larry

---

### Post by Jucato on 2006-06-27
AFAIK, KWord is so far the only word processing app in Linux that allows you to import,*edit*, and export to PDF. OpenOffice.org only exports to PDF.

---

### Post by aysiu on 2006-06-27
[QUOTE=larry]I see. But before I delve into Kword, please put my mind at rest: can I really modify a pdf file using Kword? Perhaps I did not make myself clear: I can of course produce a pdf in many ways, but my problem is: given a pdf (and nothing else), can I modify it (e.g. remove text, cut & paste figures etc...?).
Cheers

Larry[/QUOTE]
Yes, you can modify it. You may notice the formatting shifts a bit, but you can adjust that from within KWord.

Just a note: how to import PDFs in KWord is obvious. But to export them back to PDF, you actually have to go to **Print** and print to PDF instead of your printer.

---

### Post by larry on 2006-06-27
[QUOTE=aysiu]

Just a note: how to import PDFs in KWord is obvious. But to export them back to PDF, you actually have to go to **Print** and print to PDF instead of your printer.[/QUOTE]

Is it so obvious? Well, I have never used it before, but when I tried opening/import pdf files, Kword did not recognize the format.
Many thanks

Lorenzo

---

### Post by aysiu on 2006-06-27
[QUOTE=larry]Is it so obvious? Well, I have never used it before, but when I tried opening/import pdf files, Kword did not recognize the format.
Many thanks

Lorenzo[/QUOTE]
This is how you do it.

---

### Post by larry on 2006-06-27
[QUOTE=aysiu]This is how you do it.[/QUOTE]

My apologies: I was trying the same on Fedora Core 5 (the system installed on the PC I use at work).
There, the import pdf option was not displayed (why?).
Yeah, on Ubuntu it is really trivial.
Many thanks

Larry

---

### Post by UphillSkier on 2007-02-09
I just discoverd that kpdf  will let you select and cut both text and graphics from pdf files and let you paste them into other applications.  Evince is hopeless at this.

You can also select some text and have kpdf speak it! Neat.

---

### Post by mexlinux on 2007-02-09
You must try pdfedit
[http://kde-apps.org/content/show.php?content=51831](http://kde-apps.org/content/show.php?content=51831)

There is a deb in Treviño's repositories
[http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/)

---

### Post by CoolRat33 on 2008-04-12
HI 
I also searched for a long time to find a good PDF editor for Linux.  PDFedit seems to be developing nicely, but it was just not easy enough to use for my purposes.  I needed a tool that would allow me to add highlighting and notes to PDF documents as I read them AND be able to search for words within the document. 

Finally after months of trying different things, I found Qoppa Software's PDF Editor.  Its not free, but until an Open Source alternative is available, maybe many of us will find this program useful

Qoppa PDF Editor offers a lot of features including:
- add highlighting,
- add comments,
- crossout-text,
- extract text embedded in the file,
- scan to PDF (can scan and insert directly into a PDF document),
- modify pages,
- add or remove pages from a document,
- add hyperlinks
- and other etc. etc. features

The program is written in JAVA and there are versions for Linux, Mac and Windows so you can use the same program on WinXP and Linux if you are dual booting.

I tested it in my Ubuntu 7.10 and found all its features to be fully compatable with Adobe Acrobat -- when I created highligting or notes in Qoppa PDF Editor and then opened it inside Adobe Acrobat 7, all of the highlighting and notes were intact! Great! Perhaps more researchers and students can switch to Linux now that a good PDF tool that allows highlighting and comments is available!

Check out Qoppa Software at [http://www.qoppa.com/psindex.html](http://www.qoppa.com/psindex.html)

---

### Post by CoolRat33 on 2008-04-12
posted twice by accident :(

---

### Post by larry on 2008-04-12
> **mexlinux said:**
> You must try pdfedit
[http://kde-apps.org/content/show.php?content=51831](http://kde-apps.org/content/show.php?content=51831)

There is a deb in Treviño's repositories
[http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/)

Hi,
For what I aim at (mainly stapling together different pdf's), pdf toolikit is free (as in beer) and fine for me:

[http://www.pdfhacks.com/pdftk/](http://www.pdfhacks.com/pdftk/)

Cheers

Larry

---

### Post by mexlinux on 2008-04-14
Latest inkscape included in Hardy has the best support for PDF

---

### Post by nikkkko on 2008-04-15
> Latest inkscape included in Hardy has the best support for PDF
How is it better then the Gutsy version, Inkscape 0.45? I didn't know that Inkscape could import pdf's? Also, as far as I am aware, Inkscape can only output uncompressed pdf's and has no transparency support.  (I have a single page A4 document which, when output in pdf by Inkscape comes out at 56Mb with no transparency.  Same doc in Scribus comes out at 2Mb with transparency.)

I love Inkscape - using it right now - but it's not strong on pdf's.

---

### Post by nikkkko on 2008-04-15
If I could type the sound of me eating my own words, I would. Just installed Inkscape 0.46 and :

> I didn't know that Inkscape could import pdf's?
- it imports pds's
> Also, as far as I am aware, Inkscape can only output uncompressed pdf's and has no transparency support.
- it exports compressed  pds's

My test file went down from 56 to 2MB in size and my transparencies were retained.

Nice

---

### Post by MugenDraco on 2008-04-18
Quick question about pdfedit.  I want to insert a picture into the file.  Help says to hit Insert, but that does absolutely nothing.  Anyone know how to insert pics?

---

