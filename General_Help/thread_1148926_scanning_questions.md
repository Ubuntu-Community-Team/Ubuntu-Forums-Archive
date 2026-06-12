---
title: "scanning questions"
date: 2009-05-04
forum: General Help
---

### Post by DougieFresh4U on 2009-05-04
I have never used a scanner on Ubuntu. I hooked up my 'hp scanjet 2300c' and I am assuming I use 'XSane image scanning program' as I see it installed under'Graphics'.
What do I need to do as scanner was recognized and I hit scan and this is what I got. I honestly don't know what I am doing :confused::confused:
Any help would be great in setting this up proper
Thanks

---

### Post by BslBryan on 2009-05-04
Your scanner is not supported in Ubuntu, as far as I know.  

I did some Googling and apparently in previous versions people have managed to make it work in greyscale, but since it is not supported.  

When upgrading to Vista, I had to give up my 3300C, which is newer than yours, because even Vista said it was obsolete.  

It's time to get a new scanner, I think.  :P

---

### Post by soro2005 on 2009-05-04
The scanner [should be supported]("http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD"). Unfortunately, I don't have any idea why it doesn't work for you. However, I recommend trying gscan2pdf, which should also use the sane backend afaik, but perhaps with saner presets.

Oops, it seems that your image has not been acquired by the scanner, but by your webcam. That's why it is scrambled. Try connecting the scanner first, then starting xsane (or gscan2pdf). You should hopefully get a selection. If it doesn't work, try installing the hplip package (no idea whether that's any good).

---

