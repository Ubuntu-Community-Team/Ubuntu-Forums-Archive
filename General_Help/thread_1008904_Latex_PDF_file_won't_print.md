---
title: "Latex PDF file won't print"
date: 2008-12-12
forum: General Help
---

### Post by quazi on 2008-12-12
So I've compiled a file with pdflatex and it will not print under Intrepid (but has no problem under OS X).

If I open this file with evince and try to print, nothing happens whatsoever with no output in the terminal.  In acroread, when printing it seems as if its working, but after processing all the pages an error dialogue comes up and the printing process stops.  After going through the diagnosing stuff, I get the attached troubleshoot text as my output (zipped to avoid the ridiculously low size limit on text files).

Also the error message that pops up is ```
/usr/lib/cups/filter/pstopdf failed
```

What's strange is that it works printing some pages (I can print the first few fine), so there must be some part of the document causing the problem.

Any suggestions?

---

### Post by quazi on 2008-12-14
Well, I've started using Virtualbox as a workaround, but it's still kind of annoying.

---

### Post by borghal on 2008-12-14
I've got a similar problem here, very annoying. 

I can't print pdf from evince or acroread and only simple text documents. As soon as they're having graphics or advanced layout, the printer dies.

I still don't want to install virtualbox as a workaround, I'm using an old hardy machine to print. So much for "upgrade"... :confused:

---

