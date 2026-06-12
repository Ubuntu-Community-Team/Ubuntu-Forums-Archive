---
title: "Creating readable pdfs?"
date: 2006-03-07
forum: Desktop Environments
---

### Post by NoNo_231 on 2006-03-07
Ok here is my problem. I found some threads about it but no answer. I make pdf and ps I read them but when I ry to copy something I take some "chinese" symbols. That also means I I can not open urls. I really need taht because I collect articles for the uni, and I must have an easy way to go back.

Under windows I used pdfcreator with the latest ghostscript and it worked. Before that I was taking the "chinese" result when I tried to copy some words.  Under Linux I tried cups-pdf, the print to file .ps, the konqueror-pdf but all they have the same "chinese" result. I came to believe that the problem is the postscript - ghostscript version. I tried to install the latest ghostscript but I lost it somewhere in the middle.

Any suggestions? I have to say that I take the picture of the document "printed" but is more like a picture, I cannot extract words of it.

---

### Post by anirban.sam on 2006-03-07
Use flpsed, is available in ubuntu universe repository. Use apt-get or synaptic to  get & install.

---

### Post by sbassett on 2006-03-07
Another easy option would be to use Open Office 2.0 (I would strongly suggest using the newest version via alien, though). This will allow export to PDF, including link support and searching of contents.

---

### Post by NoNo_231 on 2006-03-07
When I am writing docs I use Openoffice. The problem is when I "print" web pages and I want to reopen them for later use, or to use the adress as a refference. I am trying now flpsed.

---

### Post by soonindallas on 2006-03-07
I think sbassett meant "export pdf" from openoffice not "print pdf" (presumably with the cups pdf utility)

---

### Post by NoNo_231 on 2006-03-07
Yes export pdf I understood too. It is a very good utility. It is impressive that gives the Contents to pdf bookmarks. Really good. And I use it.

But the problem is when I read an article over internet via Firefox and I want to "print it" to pdf or ps. Whatever I tried the result was not readable.

flpsed is a good tool because you can write on ps or pdf the url for future use. 

However if somebody finds a way to print from firefox to **readble** pdf or ps it would be great because with flpsed you have to do the same job 2 times - first print then edit. 

Thank you all for your help

---

### Post by soonindallas on 2006-03-07
ok.  did you try cups-pdf ?  

EDIT: sorry, deleted my advice cos I saw in your first post you had.

---

### Post by NoNo_231 on 2006-03-07
Well I tried latest versions of cups-pdf (2.0.5), ghostscript (8.53) and gs-fonts (8.11). The same result. When trying to copy something I take symbols. More with pdftotext I take an empty txt.

---

### Post by bikeman on 2006-03-07
I was going to recommend using ps2pdf, but just checked and found that it does not work.  Evidently by printing to a .ps file, the data is changed to an image and is not kept as text.  I have a ton of pdf files that I created from the web (Firefox) by printing to .ps and now I cannot extract text from them.  I can copy the text as an image, which does not help you with URLs.

I am not familiar with flpsed, but there are two things you could try - instead of printing pages to .ps files, copy them and paste them into OpenOffice Writer, then export to pdf, or, you might try using OCR software (if there is any for Linux) to extract the text from the pdf files created from the .ps files.  Good luck!

---

### Post by NoNo_231 on 2006-03-07
Thank you for your info. I didn't know that by printing to a .ps file, the data is changed to an image and is not kept as text.

The pdfcreator that I used on windows uses ghostscript engine and so does cups-pdf. But using the same engine and the same fonts gives different results. It sounds a bit weird to me. I will look at it if I could figure something out.

For the time I do the copy n paste procedure on openoffice.

Thanks for the info & advice.

---

### Post by NoNo_231 on 2006-03-08
Well I finally found something. Using mozilla-suite and cups-pdf I finally made it to print pdf that can be used in the future (only in english). I have to say however that as I said above I used the v2.0.5 of cups-pdf (downloaded from official site). However it worked both with Ghostscript ESP 7.07 from ubuntu and 8.53 (downloaded from official site). 

PS. With Epiphany and Galeon the result was the same as with firefox.

---

### Post by towsonu2003 on 2006-03-08
what about:
save html in firefox (web page, html only)
open html in openoffice
export to pdf?

-Looks very ugly in more than simple web pages though... and exporting the screen I am currently viewing (reply to thread) to pdf and opening in Acrobat kills Acrobat (DoS)...

---

### Post by NoNo_231 on 2006-03-08
Thanks my friend, but too many steps (if it was just 1 or 2 docs, no problem) and for pages like this isn't really good. But **viewing with mozilla-suite and printing with cups-pdf printer** is no problem. The pdf is perfect.

The problem with all other exlporers is that they have a Mozilla postscript engine (as I saw at pdf properties) and konqueror has it's own printing engine. Mozilla-suite doesn't have one.

---

