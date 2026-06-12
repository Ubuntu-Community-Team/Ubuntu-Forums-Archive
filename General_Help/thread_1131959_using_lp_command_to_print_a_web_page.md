---
title: "using lp command to print a web page"
date: 2009-04-21
forum: General Help
---

### Post by jsdegard on 2009-04-21
Hello 

I am looking into a way of saving a web page as a pdf.  My default printer on the server running Hardy is a cups-pdf printer.  If I print a test page or run the command 'lp <filenam>', it saves a pdf file to my root/PDF directory.  This is great, except I want to do this with web pages.  I was hoping I could do something like 'lp wget <pageurl>', but of course this does not work.  I do not have much firepower when it comes to command line.  Can anyone help, or is this impossible?

Thanks

---

### Post by zigx on 2009-04-21
You might be able to do something like this:
[http://dsl.org/cookbook/cookbook_24.html#SEC354](http://dsl.org/cookbook/cookbook_24.html#SEC354)

Take a screenshot from the cli?

I'm sure u could probably find some utilities to convert that to a PDF then spool the pdf.

just an idea, but ill admit its pretty hackety feeling heh.

---

