---
title: "Pdf issue when using multiple pdf documents"
date: 2008-12-22
forum: General Help
---

### Post by meazz1 on 2008-12-22
I have manual that consists of over 500 pages of pdf documents.
In Windows, I could open up any one of the pdf documents and go to a different page or chapter by clicking on a link in any page.
In my 8.10, I am not able to do that. I have tried different pdf readers already.

Do I have to add some symbolic link or anything?
Can anyone help?

---

### Post by tigerstripedcat on 2008-12-22
And you tried the most recent version of acroread? kpdf?   That's odd.  So do you have just a single 500-page pdf, or several hundred pdfs that are linked together?  If they are linked together (I've never really seen this before though) they would be extremely dependent on the directory structure and hopefully the links aren't absolute paths.  If they are more than one pdf, any chance you can just print this out to one giant pdf?

---

### Post by meazz1 on 2008-12-22
> **tigerstripedcat said:**
> And you tried the most recent version of acroread? kpdf?   That's odd.  So do you have just a single 500-page pdf, or several hundred pdfs that are linked together?  If they are linked together (I've never really seen this before though) they would be extremely dependent on the directory structure and hopefully the links aren't absolute paths.  If they are more than one pdf, any chance you can just print this out to one giant pdf?

I guess I  can print them out to be one.
The question is, how would I do that? In doing so, would I be able to use links from one pad to take me to the right page?

---

### Post by namdung on 2008-12-22
I'm assuming that your pdf book has links to different pages in the same book. Pls ensure that the links are properly working.

Try Acrobat reader even though it's not FOSS and it hogs up loads of memory.
[http://get.adobe.com/reader/otherversions/](http://get.adobe.com/reader/otherversions/)

---

### Post by meazz1 on 2008-12-22
> **namdung said:**
> I'm assuming that your pdf book has links to different pages in the same book. Pls ensure that the links are properly working.

Try Acrobat reader even though it's not FOSS and it hogs up loads of memory.
[http://get.adobe.com/reader/otherversions/](http://get.adobe.com/reader/otherversions/)

Yes, it has links and I already tried Adobe Reader. It did not help.

---

### Post by TimScully on 2009-01-18
Have you checked to be sure that the pathnames used in your hyperlinks really match the actual pathnames of the files. I stumbled into a similar problem and it turned out to be due to the fact that Windows pathnames are not case sensitive, but Unix/Linux pathnames are case sensitive. An upper/lower case mismatch between hyperlink and file path is all it takes to cause problems.

---

