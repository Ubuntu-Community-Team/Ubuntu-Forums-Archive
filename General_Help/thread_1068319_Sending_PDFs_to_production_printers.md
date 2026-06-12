---
title: "Sending PDFs to production printers?"
date: 2009-02-12
forum: General Help
---

### Post by yther on 2009-02-12
Hi, I'm having a bit of trouble printing PDFs to our office printers.

We have a couple of Konica Minolta printers that sort, staple, duplex, etc.  One is a "bizhub C450" with a Fiery RIP server, and the other is a "C6500" with a Creo server.  Now, I added the printers using CUPS and the appropriate PPDs; in the case of the 6500 I actually downloaded the PPD from the printer itself.

When I load a PDF in Okular, I do have access to the special settings, such as duplexing, stapling, and (as far as I can tell) all of the features.  They aren't in a nice dialog like on Windows, but they are there and I can set them.  The problem is that the job will never print because the wrong paper size is sent to the printer.

**Example:**  Document loads and shows page size of 8½×11 (also known as Letter).  In the print dialog I select that size as well.  However, what gets sent to the printer is something ridiculous like 10-13/15×7-9/10, and I then have to walk to the printer and either override this or delete the job.  :(

So I tried from Adobe Acrobat and that was horrible.  The printer box in there gives me *absolutely no* control other than paper size and which printer to use.  It displays an Options line but does not let me edit it, so I can't even use manual configuration with LPD options.

(I'm not even going to entertain the idea of sending a job to our Heidelberg press...)

This seems like a very bad situation if I am supposed to get actual work done.  Does anyone know either (1) how to fix Okular so that it respects my choices, or (2) any program that will do the same?

---

### Post by yther on 2009-02-19
I'm not generally one to bump threads, but... anyone using Ubuntu for actual office printing?

Today I was trying to look up some info on openprinting.org, but I swear that site must be hosted on a dialup machine in Timbuktu or something... nothing ever loads.  :(

---

### Post by yther on 2009-02-23
OK, I guess nobody here uses Linux in an office environment.  That figures.

Continuing my monologue, then, both Okular and Acrobat Reader will fail to produce a viable print job using a one-page file with standard 8½×11 paper size.  The job goes to the printer with weird page sizes and unworkable finishing settings.  However, I get what I expect with this:

```
lpr -P Fiery_X3eTY_bizhub_C450 '/home/rassilon/Documents/Quote No. 37406.pdf'
```

The page pops out of the printer using auto-selected paper and looks fine, no cut-off images or complaints.  This sort of thing is fine for PDFs, and I suppose I could create shell aliases to send jobs to all the printers, one for double-sided, one for stapled, another one for double-sided *and* stapled, but that would be a lot of aliases.  Also I'd have to convert my OpenOffice documents to PDFs just to be able to print them, which is silly.

Well, self, if I come up with any bright ideas, I'll be sure to let me know.  :)

---

### Post by xdevnull on 2009-05-04
I have no idea if this is at all helpful, but I have had problems with my bizhub - but not similar ones....my post is here:

[http://ubuntuforums.org/showthread.php?p=7212787#post7212787](http://ubuntuforums.org/showthread.php?p=7212787#post7212787)

I did find a quote about problems with Ghostscript filters but I honestly don't know if that is helpful at all.

---

