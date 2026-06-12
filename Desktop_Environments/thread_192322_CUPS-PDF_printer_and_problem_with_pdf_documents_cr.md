---
title: "CUPS-PDF printer and problem with pdf documents created"
date: 2006-06-08
forum: Desktop Environments
---

### Post by VosaxAlo on 2006-06-08
Hi,

I have a strange problem with the creation of PDF documents through the cups-pdf virtual printer.

The cups-pdf printer was installed without any problem. For testing the printer I have used the "print test page" button and the "PPR Test Page.pdf" was correctly created. 
I have opened this document in Evince, copy the text, paste it in gedit and all function very well.

After, I have create a text with gedit, and printed it with cups-pdf. I have opened the pdf document in Evince, and the content is displayed correctly, but I can't select the text to copy. The document is like a picture. Why?

The only difference between the two documents is in the properties that we can display in Evince: 
The first document result created by nothing and produced by ESP Ghostscript 815.02.
The second document result created by Gnome Print Version 2.12.1. and produced by ESP Ghostscript 815.02.

So the first document is reusable, the second one not. Maybe a bug in the Gnome Print Version 2.12.1?

---

### Post by bryanlking on 2006-06-08
If you're producing PDF documents, they are not editable as they are not text documents.  They are intended to be portable documents that can be viewed on any operating system with a PDF viewer such as evince in Linux and Acrobat Reader in Windows.

---

### Post by VosaxAlo on 2006-06-09
[QUOTE=bryanlking]If you're producing PDF documents, they are not editable as they are not text documents.  They are intended to be portable documents that can be viewed on any operating system with a PDF viewer such as evince in Linux and Acrobat Reader in Windows.[/QUOTE]

Pardon me bryanlking, but english is not my primary language; maybe I have not correctly explained the problem. 

Naturally I know that PDF documents are not editable. With this thread I want say that when I print with cups-pdf then **I can't copy text out from a PDF document**.
I attached two examples of PDF: in the first I can copy text from, and with the second I can't.
The first PDF was created using the print test page of the gnome-cups-manager, the second was printed with cups-pdf from gedit.

---

### Post by bryanlking on 2006-06-09
Looking at the document properties, it looks like there are two differences.  I don't know it these have anything to do with it.

1.  On PPR Test page, creator is none
     On job_11, creator is Gnome Print version...

2.  Font type on PPR Test page is Helvetica
     Font type on job_11 is GnomeUni-DeJaVuSans

I know it's not a solution but perhaps a place to start,

BK

---

### Post by digby280 on 2006-06-12
I would guess that you are printing PDFs to a PDF printer that you added to gnome.  This - from what I can tell - will create a Postscript and print it to PDF, thus effectively making it an image and losing the ablity to select text etc.  There should be an option in the print menu in gedit to "Create a PDF document" (or something similar), this should print PDFs so that you can select the text etc.  At least that's how it works for me.

Hope this is helpful.

---

### Post by VosaxAlo on 2006-06-13
[QUOTE=digby280]I would guess that you are printing PDFs to a PDF printer that you added to gnome.  This - from what I can tell - will create a Postscript and print it to PDF, thus effectively making it an image and losing the ablity to select text etc.  There should be an option in the print menu in gedit to "Create a PDF document" (or something similar), this should print PDFs so that you can select the text etc.  At least that's how it works for me.

Hope this is helpful.[/QUOTE]

Hi digby280,

I have tried your solution. I have created a little text file with **gedit** and then printed with the "Create a PDF document". Now is true, I can copy out the text from the PDF created, but the problem is that if I paste the text in **gedit** again I see strange characters.

For Instance I wrote in gedit the following text:
"**[COLOR="DarkRed"]Text to testing PDF production[/COLOR]**"
and I have created a PDF document. I open the PDF in **Evince** and I select and copy the text. Then I paste the text into **gedit** again and following strange character are displayed:
"**[COLOR="DarkRed"]8I\X XS XIWXMRK 4(* TVSHYGXMSR[/COLOR]**"

I attach to this post the two files, so you can test if the problem is present on your PC too.

Any idea where the problem is? (Ghostscript, ???)

---

### Post by digby280 on 2006-06-13
I hadn't noticed that :-( .  It's the same on mine, so I would think it must be a bug of some description.  Maybe you should report it though bugzilla, unless someone else knows a solution.

On a more positive note though.  The PDF exporter in OpenOffice works fine and you can copy and paste text from the PDFs it creates without any problems, because it uses its own PDF creator.  It's not really a solution to the problem with cups-pdf but atleast it's a workaround.

Sorry I couldn't be any more help.

---

### Post by dmuir on 2007-12-04
I've got the exact same problem. Not only that, but documents that I print to PDF are unreadable in OSX Tiger. I sent an invoice from Gnucash to a client who's running OSX and all he got was a pdf will a whole ton of empty boxes where there should have been letters. No problem with opening the PDF on Windows though.

My guess is that maybe the font is missing, but I can't find any options to embed fonts.

Where's the best place to report these issues? Launchpad?

---

### Post by VosaxAlo on 2007-12-05
I have already reported this issue in Launchpad
here:[ bug report]("https://bugs.launchpad.net/evince/+bug/49631")

---

### Post by ellis rowell on 2008-01-31
I have found that the CUPS PDF printer produces some anomalies. I run a website which has a header with a coloured background on each page. The first line has a dark blue background while the second line has light blue. The Yellow text in the first is converted to green text on white and the second (red text) to red on white. The rest of the page prints correctly.

Regarding Evince, I have found that I can't select and copy from Evince, so I have installed Adobe Reader which allows you to do that.

---

