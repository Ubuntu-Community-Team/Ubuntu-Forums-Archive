---
title: "Paste dpecial characters from pdfs"
date: 2009-03-02
forum: General Help
---

### Post by jARLAXL on 2009-03-02
Hello everybody,

It is really important to me and i guess to many more to paste pdfs accurately but it seems to me that this is a major issue since the best way to communicate documents(pdf) with incompatible OS(windows) still has serious problems. 
In other words i have the following problem: When i copy some special characters from some pdfs then these are pasted wrong. 
I guess this is the bug i described here: [https://bugs.launchpad.net/ubuntu/+bug/287072](https://bugs.launchpad.net/ubuntu/+bug/287072)
Anybody has a clue for a workaround or where to start looking for a workaround?
I just want to have a pdfviewer that does a few things only correctly: view, copy and paste correctly.
Any solutions, alternatives, workarounds, possible causes, directions at what to look, are most welcome.
A little help here please.

---

### Post by Rallg on 2009-03-02
It appears that formatting instructions, within the PDF, interfere with how the characters appear as plain text. I have looked at the PDF file that you linked from launchpad.

I have tried exporting a table to PostScript, or opening the file in another application (such as Scribus). In each case, the page appear correct within the application, but when text is selected and copied out, the plain text has problems, as you noted.

Have you tried this: In Windows, install ghostscript and GSview. Open the PDF file in GSview. Is it correct? If you export as text from there, is it correct?

---

### Post by jARLAXL on 2009-03-02
Hello Rallg and thank you for your prompt reply.
I don't have windows. Do you recommend me to install it? Apparently it is a file created from a windows machine that's why the fonts cannot be recognised properly in linux. Will try to find anyway some windows machine to test if GS works there. Would like to add that the pdf i gave as an example in that bug report is a mere example of pdfs with such behaviour i encounter every day)

---

