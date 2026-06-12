---
title: "Printing to PDF - in the mirror"
date: 2006-02-06
forum: Desktop Environments
---

### Post by hfilimonescu on 2006-02-06
Hello everybody,

I need to print an OpenOffice.org Document to a PDF printer, but the output has to be in the mirror.

[IMG]http://www.filimonescu.de/sample.png[/IMG] and [IMG]http://www.filimonescu.de/sample2.png[/IMG]

Does anyone of you *if* it is possible and if yes *how*?

Thank you, Horia.

---

### Post by ekarni on 2006-02-06
I haven't tried this; don't know if it will work, but anyway:  You could print it to a file (postscript- .ps) then use the ImageMagick "convert -flop" tool to flip the .ps horizontally, then use ps2pdf to convert the resulting .ps to a .pdf.  Yeah, it's ugly - hopefully someone else has a cleaner way.

---

### Post by hfilimonescu on 2006-02-07
:D it works!!!

Thanks alot!!!

I have just tried it out. Apparently it has problems with big documents, but I am still happy with the result.

----- For those who want to know how exactly -----
1. install imagemagick
2. install gs (Ghostscript - to open .PS files)
3. run the command: convert <source_file.ps> -flop <target_file.ps>
---------------------------------------------------

For converting the ps to pdf I used the cups-pdf package

Bye!

---

