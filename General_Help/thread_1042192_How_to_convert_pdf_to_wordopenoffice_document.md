---
title: "How to convert pdf to word/openoffice document?"
date: 2009-01-17
forum: General Help
---

### Post by usien on 2009-01-17
How to convert pdf to word/openoffice document on ubuntu/linux?

---

### Post by ajcham on 2009-01-17
You can do this in OpenOffice 3.

First follow this [guide to installing OpenOffice3]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml").

Once done, run the command ```
sudo apt-get install openoffice.org-pdfimport
```

It's only a beta at the moment I believe, so it may be a little quirky, though I've not tested it myself.

---

### Post by HermanAB on 2009-01-17
OOo and also Scribus and The Gimp can do some PDF editing and saving as something else.

Otherwise, use /usr/bin/pdftotext

Cheers,

Herman

---

### Post by tgalati4 on 2010-03-10
apt-cache search pdf
pdftohtml filename

---

### Post by sussexslanter on 2010-03-15
> **HermanAB said:**
> 

Otherwise, use /usr/bin/pdftotext



...and how do I do that please?

---

### Post by coffeecat on 2010-03-15
> **sussexslanter said:**
> ...and how do I do that please?

pdftotext is a terminal app. You don't have to invoke the whole /usr/bin/ path. For a simple conversion of the whole pdf file, open a terminal and:

```
pdftottext filename.pdf filename.txt
```You get a plain text for with no formatting. For options, do 'man pdftotext' in the terminal.

pdftotext is part of poppler-utils, which contains these related apps (from Synaptic package description):

> This package contains pdftops (PDF to PostScript converter), pdfinfo
(PDF document information extractor), pdfimages (PDF image extractor),
pdftohtml (PDF to HTML converter), pdftotext (PDF to text converter),
and pdffonts (PDF font analyzer).

---

### Post by mike555 on 2010-03-15
probably the easiest way is an free online conversion like from ;   [http://www.pdfescape.com/](http://www.pdfescape.com/)

---

### Post by electriccarz on 2010-05-17
Thanks Mike, pdfescape.com is amazing.

---

### Post by robinpaschal on 2010-09-20
> **coffeecat said:**
> pdftotext is a terminal app. You don't have to invoke the whole /usr/bin/ path. For a simple conversion of the whole pdf file, open a terminal and:

```
pdftottext filename.pdf filename.txt
```You get a plain text for with no formatting. For options, do 'man pdftotext' in the terminal.

pdftotext is part of poppler-utils, which contains these related apps (from Synaptic package description):

This is not working properly. An error occurred. Terminal saying  the following..

> No command 'pdftottext' found, did you mean:
 Command 'pdftotext' from package 'xpdf-utils' (universe)
 Command 'pdftotext' from package 'poppler-utils' (main)
pdftottext: command not found


---

### Post by coffeecat on 2010-09-20
> **robinpaschal said:**
> This is not working properly. An error occurred. Terminal saying  the following..

```
No command 'pdftottext' found, did you mean:
 Command 'pdftotext' from package 'xpdf-utils' (universe)
 Command 'pdftotext' from package 'poppler-utils' (main)
pdftottext: command not found                      
```

You made a typo. it's pdftotext (PDF TO TEXT), not pdftottext (PDF TOT TEXT). It's all explained in the error message.

---

### Post by boyevil on 2011-06-03
> **mike555 said:**
> probably the easiest way is an free online conversion like from ;   [http://www.pdfescape.com/](http://www.pdfescape.com/)

yes yes, pdfescape is teh roxxxerz!!

---

