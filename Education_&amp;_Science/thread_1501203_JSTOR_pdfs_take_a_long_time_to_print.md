---
title: "JSTOR pdfs take a long time to print"
date: 2010-06-04
forum: Education &amp; Science
---

### Post by PGScooter on 2010-06-04
I've noticed that it takes a long time to print JSTOR pdfs on my printer. But on other printers it goes very fast. I guess those printers just have a larger buffer/cache ?

In any case, is there anything I can do to the pdfs to speed up the process? I think that JSTOR pdfs are images but they did add text so that you can search.

Thanks

---

### Post by PC_load_letter on 2010-06-05
> **PGScooter said:**
> I've noticed that it takes a long time to print JSTOR pdfs on my printer. But on other printers it goes very fast. I guess those printers just have a larger buffer/cache ?

In any case, is there anything I can do to the pdfs to speed up the process? I think that JSTOR pdfs are images but they did add text so that you can search.

Thanks

It was always my impression that the pdfs at JSTOR (at least the old ones) are in image format. So each page was converted to pdf from a high resolution image scan, I don't know that for a fact, but it's a guess. 

I just compared a pdf article from there and it was more than twice the size of a similar pdf article I produced w/ LateX, both had the same number of pages.

---

### Post by PC_load_letter on 2010-06-05
It may help to reduce the JSTOR pdf file size for your printer then. From the terminal type:

```
pdftk JSTOR.pdf output NEW.pdf compress

```

If you don't have pdftk installed, just type:

```
sudo apt-get install pdftk
```

Let's know how it goes.

---

### Post by PGScooter on 2010-06-05
Thanks for the tips PC_load_letter,

Unfortunately, that didn't change anything. I tried several of pdftk's options, including compress and flatten.

Also I should specify that by "taking a long time to print" what I mean is that one page prints at a normal speed, then a minute goes by, and another page prints at normal speed, etc.

---

### Post by wilee-nilee on 2010-06-05
Are you downloading the pdf or just printing it off the net? I always download them, and congratulations on finding Jstor that is a excellent resource, use it often myself. I think Linux is known for slower printer by and large, I have a old HP so I expect it to run slow.

---

### Post by PGScooter on 2010-06-06
> **wilee-nilee said:**
> Are you downloading the pdf or just printing it off the net? I always download them, and congratulations on finding Jstor that is a excellent resource, use it often myself. I think Linux is known for slower printer by and large, I have a old HP so I expect it to run slow.

I agree, Jstor is great! I do download them. I remember before they would offer different qualities of download (and accordingly different file-sizes). Actually the printer is slow whether the job is submitted by a linux computer or windows computer.

I think that there's no solution. If I want to print a pdf that has images, it will be slow unless the printer is powerful.

---

### Post by wilee-nilee on 2010-06-06
> **PGScooter said:**
> I agree, Jstor is great! I do download them. I remember before they would offer different qualities of download (and accordingly different file-sizes). Actually the printer is slow whether the job is submitted by a linux computer or windows computer.

I think that there's no solution. If I want to print a pdf that has images, it will be slow unless the printer is powerful.

You must be a college student as I am, although I am a middle aged one.

---

### Post by PGScooter on 2010-06-06
> **wilee-nilee said:**
> You must be a college student as I am, although I am a middle aged one.

Yep, I am indeed :)

---

### Post by PC_load_letter on 2010-06-06
> **PGScooter said:**
> Thanks for the tips PC_load_letter,

Unfortunately, that didn't change anything. I tried several of pdftk's options, including compress and flatten.

Also I should specify that by "taking a long time to print" what I mean is that one page prints at a normal speed, then a minute goes by, and another page prints at normal speed, etc.

I have experienced this as well, my guess is that the time taken is for the page to be loaded into the printer's memory. 

Would you post a link to the pdf that you are having these issues with? So that if I find a workaround I'd know it. I have experienced similar issues w/ JSTOR specially with old papers that are converted from hi-res image scans.

---

### Post by PGScooter on 2010-06-06
> **PC_load_letter said:**
> I have experienced this as well, my guess is that the time taken is for the page to be loaded into the printer's memory. 

Would you post a link to the pdf that you are having these issues with? So that if I find a workaround I'd know it. I have experienced similar issues w/ JSTOR specially with old papers that are converted from hi-res image scans.

I have experienced this with most of them. Here is one:
[http://www.jstor.org/pss/2111186](http://www.jstor.org/pss/2111186)

Unfortunately I won't be able to test any workarounds you come up with because I'm away from the school.

---

### Post by anoop999 on 2010-06-07
Which printer and print driver are you using? I sometimes have problems printing large PDFs to my HP laserjet using the PostScript driver (very slow, or sometimes prints a couple of pages and then nothing), but it works with the Gutenprint driver.

---

### Post by PGScooter on 2010-06-07
interesting. Ok I will look into changing printer drivers once I get back in August. I do not know what the current setup is.

---

