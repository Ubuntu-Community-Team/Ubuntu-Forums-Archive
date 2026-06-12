---
title: "Batch PDF-to-HTML Conversion?"
date: 2009-01-28
forum: General Help
---

### Post by camerong on 2009-01-28
Hey,

Pretty simple question with hopefully a simple answer: I have 157 PDF's in a folder which I need to convert to HTML files. How can I do this without doing it one-by-one?

I can use the command line okay.

Thanks,

Cameron

---

### Post by unutbu on 2009-01-28
The results are not perfect, but there is a tool called pdftohtml that you could use like this:
```

ls *.pdf | xargs -I{} pdftohtml {}
```
If the pdf files are in many directories, we could craft a command to work in that situation as well.

To convert a single pdf file:
```

pdftohtml input.pdf
```

For an explanation of the rest of the command, see 
[http://georgia.ubuntuforums.org/showpost.php?p=6626272&postcount=6](http://georgia.ubuntuforums.org/showpost.php?p=6626272&postcount=6)

---

### Post by camerong on 2009-01-28
Thank you very much, your help is much appreciated.

One problem though: Images are simply discarded.. I kind of need the images.. Is there another command that will preserve them?

Also, is there a way to skip the frameset thing and just make the long ones all on one page?

---

### Post by khedron on 2009-01-28
I've read the pdftohtml man page (with **man pdftohtml**) and it says that you can use the **-noframes** option to stop generating frames.

---

### Post by camerong on 2009-01-28
thanks that should take care of that..

any ideas on pictures? they kind of HAVE to be there.. i'll check man.

EDIT: so apprently -i means ignore images.. but I'm not using -i and it's ignoring images... wtf?

---

### Post by khedron on 2009-01-28
Maybe try the **-c** option? This forces "complex output", which is pretty vague but might do the trick.

---

### Post by camerong on 2009-01-28
that appears to make the command do absolutely nothing.. it *works* for a bit, and then there's no files created. odd.

i'm looking into xpdf but i'm clueless as to what i'm doing.. do you guys think it would be possible to do a longer conversion like from pdf->postscript->html?

---

### Post by camerong on 2009-01-31
okay, i really have to have this done.

if ubuntu just plan old lacks this ability.., what tool should I use on a windows machine to convert them?

thanks a lot

---

### Post by khedron on 2009-01-31
Funny... I got a pdf from the [pdftohtml ]("http://pdftohtml.sourceforge.net/")website ([http://pdftohtml.sourceforge.net/demo1/demo1.pdf](http://pdftohtml.sourceforge.net/demo1/demo1.pdf)) and converted it using the **-c** option:
```
khedron@wyenet:/var/www/pdf $ ls
demo1.pdf
khedron@wyenet:/var/www/pdf $ pdftohtml -c demo1.pdf
Page-1
Page-2
Page-3
khedron@wyenet:/var/www/pdf $ ls
demo1001.png  demo1002.png  demo1003.png  demo1-1.html  demo1-2.html  demo1-3.html  demo1.html  demo1_ind.html  demo1.pdf
khedron@wyenet:/var/www/pdf $

```I got the png files. Viewing it in my web browser worked ok, although the pictures were a bit displaced. There was a bit of a pause between it printing "Page 3" and the command completing; I assume that was the png-creation part.

I wonder what's different on your machine.

Edit: I found this link on Adobe's website. Maybe that might work? [http://www.adobe.com/products/acrobat/access_onlinetools.html](http://www.adobe.com/products/acrobat/access_onlinetools.html)
Edit: No, Adobe's didn't seem to work. But try this one, it worked on my demo pdf. [http://www.pdfdownload.org/free-pdf-to-html.aspx](http://www.pdfdownload.org/free-pdf-to-html.aspx)

---

### Post by camerong on 2009-01-31
I updated my ubuntu and -c worked excellently.. I dunno what happened, but fantastic!

Thanks a lot.

---

### Post by myersnsoda on 2009-02-01
> **camerong said:**
> I updated my ubuntu and -c worked excellently.. I dunno what happened, but fantastic!

Thanks a lot.

Cam; I am new to linux and ubuntu so my question is rather elementary, but relavent. I need to convert a few pdf files to word and spreadsheet format. I read your exchange with dherndon but I am not clear on what I need to do. Can you or d herndon help? Thanks guys...please keep it simple for the newbee!

---

### Post by khedron on 2009-02-02
Hmm, nothing does exactly what you want. However:

**pdftohtml** will convert to html. You can then open the html file in Openoffice and save as .doc.

So to take my demo1.pdf, you would first install pdftohtml:
```
sudo aptitude install poppler-utils
```
and then convert your pdf file on the command line:
```
pdftohtml -c demo1.pdf
```
and then open **demo1.html** in Openoffice.org and save as Word.

If that doesn't work, I found some web-based solutions: 
[http://www.koolwire.com/Default.aspx](http://www.koolwire.com/Default.aspx)
[http://www.zamzar.com/](http://www.zamzar.com/)
[http://www.freefileconvert.com/](http://www.freefileconvert.com/)

Apparently the first link there is the best, so try that one first.

---

### Post by shane2peru on 2009-05-21
OK, this is right up my alley.  I  have used pdftohtml several times, and have found it lacking!  Even with the -c option it doesn't come out correctly.  the pictures are incorrectly aligned, it also uses pictures for words that are underlined, and it doesn't line up!  That just is not acceptable.  Does anyone know of an alternate application?  Or some fancy commandline to do the trick?  Thanks

Shane

---

