---
title: "Batch PDF Tools in Ubuntu"
date: 2009-08-05
forum: Desktop Environments
---

### Post by spmsrh on 2009-08-05
Hi all,
I have an amazon kindledx which I am using with ubuntu.

I am able to use convert (imagemagick) and ooo for getting most of my PDFs made, but I am faced with a couple of problems, most of them realted to the author field of PDF

1. Whenever I make a PDf it is tagged with my name as an author. I would like to modify this if possible. It turn that even ooo does not provide a way to edit the author detail of a doc file. at least I could find out how to do it, please guide me

2. I have many pdfs from others with the same problem (no origina doc), does anyone know a batch PDF properties editor or even a single editor will do for now.

Thanks
Regards

SP

---

### Post by kaibob on 2009-08-05
It's not easy, but you can use Ghostscript with a pdfmark file. A sample command line is:

```
gs -sDEVICE=pdfwrite -dQUIET -dNOPAUSE -dBATCH -sOutputFile=output.pdf input.pdf pdfmark.txt
```

The pdfmark.txt file has to be in the same directory as the input.pdf and has the following format:

> % Document information
[/CreationDate (D:20090805) 
/Creator (kaibob)
/Title (Test document title)
/Subject (Test document subject)
/Keywords (kaibob test ubuntu)
/Author (kaibob) 
/DOCINFO pdfmark

For multiple files, a simple shell script could be used.

I created a test pdf using the above pdfmark.txt file. I have attached a screenshot of this document's Evince properties sheet.

---

### Post by spmsrh on 2009-08-06
Thanks. This is a lifesaving solution.

I also researched for the same in windows and it turns out only adobe acrobat (not reader) does the same task.

I dunno how a shell script for the same would be made. Considering that gs requires pdfmark.txt for all files and the title to change, a shell script solution is at the moment a little tough for me.


Thanks a lot.

A further comment. I could not at the moment figure out how to change the author field in OpenOffice

---

