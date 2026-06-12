---
title: "pdfedit &amp; Foxit Reader (Windows)"
date: 2008-05-07
forum: Desktop Environments
---

### Post by hosammy on 2008-05-07
I am using Hardt 8.04 LTS formal release.
I have installed the pdfedit through apt.

I consolidate two pdf files by adding the 2nd pdf file pages to the 1st pdf file and succeeded. This file can be viewed in Ubuntu acroread or other pdf viwer in ubuntu.

I then emailed the consolidated file to a Windows XP user who uses the Foxit Reader 2.0 for Windows to view pdf file (because the Foxit Reader occupies lesser disk space and runs faster than Adobe Reader). The Windows user informs me that he can only read the 1st file's content but nothing can be found about the 2nd file's content in the consolidated file.
I open my Windows XP and use the Foxit Reader for Windows to check and found that the Windows user is telling the truth.
Question: Is it the pdf problem or the Foxit Reader problem?

Please advise ...

---

### Post by chewearn on 2008-05-07
Find someone with Windows Acrobat Reader to open the file and compare.  If you have difficulty finding someone, post an example file here and I will check it for you.

---

### Post by MrFSL on 2008-05-07
I googled. Found this software:
[http://www.pdfsam.org/](http://www.pdfsam.org/)

Downloaded, extracted, and ran the Java (JAR) file.

Merged 4 pdf documents and tested against foxit and adobe (both Linux and Windows) and everything worked 100%.

The bonus... I have used ghostscript primarily to manipulate pdf docs. Often the only thing I do is merge or split. This application worked wonderful and has a very intuitive interface - plus its free.

Doesn't answer your question but perhaps it will fix your problem.

Greets!
;)

---

### Post by hosammy on 2008-05-08
> **AstalaVista said:**
> Find someone with Windows Acrobat Reader to open the file and compare.  If you have difficulty finding someone, post an example file here and I will check it for you.

I scaned 2 pages, the 1st page I write a big "1", the 2nd page I write a big "3" and save as s94.pdf as the 1st file, I then scaned one page which I wrote a big "2" and save as s95.pdf. Then I used the pdfedit to merge the 2 files into one s94-95.pdf in the order of big 1,2,3 as pages 1, 2 & 3 respectively. This new file is viewable for all 3 pages in acroread, xpdf & evince but fails in Foxit Windows.
see attachment which had been zipped due to the upload limitation.
:confused:

---

### Post by hosammy on 2008-05-08
> **MrFSL said:**
> I googled. Found this software:
[http://www.pdfsam.org/](http://www.pdfsam.org/)

Downloaded, extracted, and ran the Java (JAR) file.

Merged 4 pdf documents and tested against foxit and adobe (both Linux and Windows) and everything worked 100%.

The bonus... I have used ghostscript primarily to manipulate pdf docs. Often the only thing I do is merge or split. This application worked wonderful and has a very intuitive interface - plus its free.

Doesn't answer your question but perhaps it will fix your problem.

Greets!
;)

Thank you, pdfsam can work but a little bit complicated since the 2 files merge then the consolidated file pages will be 1,3,2 instead of my expected 1,2 & 3. To suit my purpose by using pdfsam, I need to split to single page first, then merge them together. ie, it is missing the reordering page function.

---

### Post by chewearn on 2008-05-08
> **hosammy said:**
> I scaned 2 pages, the 1st page I write a big "1", the 2nd page I write a big "3" and save as s94.pdf as the 1st file, I then scaned one page which I wrote a big "2" and save as s95.pdf. Then I used the pdfedit to merge the 2 files into one s94-95.pdf in the order of big 1,2,3 as pages 1, 2 & 3 respectively. This new file is viewable for all 3 pages in acroread, xpdf & evince but fails in Foxit Windows.
see attachment which had been zipped due to the upload limitation.
:confused:

Looks like a Foxit problem; I open in Acrobat Reader 8, no problem see all three pages.  In Foxit, see only page 1 and 3.

Try using pdftk:
[http://www.pdfhacks.com/pdftk/](http://www.pdfhacks.com/pdftk/)

Install link:
[apt://pdftk](apt://pdftk)

It's a command line tool, but I have been using the Windows version of pdftk for a long time.

---

### Post by hosammy on 2008-05-08
pdftk is a command line program not so user friendly.
I have tried to use the pdfill (pdfill.com) to reorder the file and the Foxit Reader can read the file right.So I don't whether it is exactly the Foxit Reader problem or the pdfedit problem. Anyway, I will send an email to Foxit.

---

