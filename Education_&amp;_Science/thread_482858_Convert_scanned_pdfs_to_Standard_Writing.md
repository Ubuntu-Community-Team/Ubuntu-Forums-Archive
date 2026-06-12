---
title: "Convert scanned pdfs to Standard Writing"
date: 2007-06-24
forum: Education &amp; Science
---

### Post by asdir on 2007-06-24
Hi there!

I have got literally 100s of .pdf-files that contain scanned papers. Since it is hard to work with those .pdfs I'd like to know if there is any easy way to convert them to normal writing so I can use the search function and copy & paste things.

I know that some scanners offer an option to scan papers so that it comes out as text. However, I do not have the originals so I cannot do that. (And printing and rescanning them would be way to tedious.) Is there any Linux-program that could help me?

Thx so far

Dirk

---

### Post by tweedledee on 2007-06-24
> **asdir said:**
> Hi there!

I have got literally 100s of .pdf-files that contain scanned papers. Since it is hard to work with those .pdfs I'd like to know if there is any easy way to convert them to normal writing so I can use the search function and copy & paste things.

I know that some scanners offer an option to scan papers so that it comes out as text. However, I do not have the originals so I cannot do that. (And printing and rescanning them would be way to tedious.) Is there any Linux-program that could help me?

Thx so far

Dirk

pdftotext (man pdftotext to see how it works).  It should be installed by default; if not, then install poppler-utils to get it.  There are a variety of other OCR programs in the repositories that work with image files, so if pdftotext doesn't work you can try those, but you'd have to batch convert your pdfs to png or some other open image format first.

---

### Post by asdir on 2007-06-24
Thx for your answer, it really helped.

For all others that come here and have the same question: I found that the following link gives a nice list of appropriate programs.

[http://www.linux-ocr.ekitap.gen.tr/]("http://www.linux-ocr.ekitap.gen.tr/")

---

### Post by euler_fan on 2007-06-24
Thanks for posting that link. I bookmarked it for my own future reference as I get the feeling it will come in handy with a document I have a hard copy of but lost the electronic version to a hard drive failure.

It would save me plenty of time and effort to just scan in the final version, convert it to text, and then stop worrying about where my hard copy went. :)

---

### Post by Masapena on 2007-06-25
I also thank tweedledee for the advice. I had looked for years for a program like this for Windoze. Its almost mindblowing that it's included by default in Ubuntu!

:popcorn:

---

