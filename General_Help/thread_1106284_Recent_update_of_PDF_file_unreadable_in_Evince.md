---
title: "Recent update of PDF file unreadable in Evince"
date: 2009-03-25
forum: General Help
---

### Post by howardf42 on 2009-03-25
I receive periodic updates to a contact list for an organization I belong to that is distributed in PDF format.  The last two updates have been nearly totally unreadable in Evince but are readable in kpdf.  

The underlying file is in .xls format created on Mac OS and saved in PDF 1.3 format.  Looking at the Properties of two recent versions of this file, one pre-problem and one post-problem, the only difference I can see is that the Mac OS version has updated from 10.5.2 to 10.5.5.  

The author of this file hasn't been able to identify any changes to his method of creating the PDF file recently that would offer a clue to the problem.

I am running Ubuntu 8.10 with the latest updates.  Any suggestions would be much appreciated.

Howard

---

### Post by jordilin on 2009-03-25
the only thing I can tell, is that I've always had problems with .xls files received from people using MACs, so I would not be surprised about your problem with pdfs. You can always install acroread package from repos (Acrobat Reader) and check if you can open those pdfs by the *official* reader.

---

### Post by howardf42 on 2009-03-25
Installing acroread works, but it's a lot of bloat to carry.  BTW, the newer, non-readable pdf's also have different looking thumbnails than their predecessors.  Does that mean anything?

---

### Post by jordilin on 2009-03-25
Maybe these new pdfs have some new feature that Evince is not supporting yet by default. Try to run evince in the command line and see if there is any debug output in the screen.
```
evince yourfile.pdf
```

---

### Post by howardf42 on 2009-03-25
Running Evince from a terminal generated the following:

```
howard@howard-laptop:~$ evince /home/howard/Desktop/DPCA Contacts MAR09.pdf

(evince:9178): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(evince:9178): atk-bridge-WARNING **: IOR not set.

(evince:9178): atk-bridge-WARNING **: Could not locate registry
```

About 5 Evince windows opened with nothing in them.  

Running Evince from the gui wasn't nearly as ugly.  The requested file opens, but about 95% of the text is replaced by strings of greyed blocks.  The general layout of the spreadsheet is discernable, but barely.

---

### Post by jordilin on 2009-03-26
I guess this must be something to do with Evince and the pdf producer used by the person who sent you the file. You could ask Evince developers if they actually do know anything about pdfs being produced by a Mac and Evince.

---

