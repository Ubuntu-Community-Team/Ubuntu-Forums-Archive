---
title: "Problems Converting PDF to txt"
date: 2009-02-22
forum: General Help
---

### Post by sanford55 on 2009-02-22
Hi everyone.  I need to convert pdf multipage documents to some sort of editable text.  I have tried all the things I know of and all fail in Ubuntu, though it is very easy in Windows.  

First, I tried the utility pdftotext from the command line and it only converted the first page.  I tried adding f and l options to try to get it to do some more pages, but that did not work either.    

Second, I downloaded and installed the pdf converter plugin for abiword, and again, it only converted the first page. 

Third,I downloaded Kword, which is supposed to do the conversion.  It tried mightily, slowing my computer down to a crawl for about 20 minutes and then failed to do the job. 

Fourth, I tried the old cut and paste from the original PDF since I read in a post somewhere that Evince has OCR and that cut and paste should work.  Not a chance.  

Does anyone have any other suggestions?  I have found most of these techniques work for very simply PDFs, but the ones I am dealing with are PDF versions of journal articles I download from places like JSTOR, which is a source university libraries provide.  Again, I know it has to be doable since I have several windows programs that do it.  

Thanks in advance

Sanford

---

### Post by HermanAB on 2009-02-22
Here you go:
$ /usr/bin/pdftotext file.pdf file.txt

Cheers,

Herman

---

### Post by steveneddy on 2009-02-22
> **HermanAB said:**
> Here you go:
$ /usr/bin/pdftotext file.pdf file.txt

Cheers,

Herman

And if that doesn't work, try pdfedit.

```
sudo apt-get install pdfedit
```

---

### Post by Charles07 on 2010-10-08
Thanks!

---

### Post by CoolJohnB on 2010-10-08
I use pdfedit it will convert a pdf linear file which is most useful then you can extract the text and use copy/paste to put it into your wordprocessor, works great for me, hope it works for you.

---

