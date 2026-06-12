---
title: "latex: eps and hyperref do not work together"
date: 2008-05-16
forum: Education &amp; Science
---

### Post by ntlam on 2008-05-16
Hi,

I am trying to make the reference clickable so I use

\usepackage[pdftex,other optiosn...]{hyperref}

the hyper-references work fine but no figures in eps come out. Most of documents say that pdftex do not support eps figures. 

so I try

\usepackage{hyperref}
\hypersetup{colorlinks=true,pdftex}

this time the output is dvi. I use dvipdfm to convert to pdf. The figures appear but the hyper-references do not work.

Any idea to help please...

Thanks

---

### Post by dvase on 2008-05-17
The method I use is to specify "dvips" in the hyperref setup options and then do a "dvips" conversion and then a "ps2pdf" conversion.

---

### Post by vrangforestillinger on 2008-05-17
I use pdflatex with hyperref (colorlinks only, no other options), and make pdf directly instead of going the detour to make dvis.

Of course, one big problem with pdflatex is the (lack of) eps-support. To include eps-figures, I convert them to pdf with epstopdf (CLi-program, availible in repos), and then include the pdf-files as figures (with \includegraphics). This works very well for me.

---

### Post by ntlam on 2008-05-18
I got it work now.

I use dvipdfm oftion for hyperref.

I dont want to convert eps figures to pdf format because the journal I'm submitting to either prefers eps or does not accept pdf figures.

---

### Post by ppm on 2008-05-20
Yes, dvipdfm seems to be the way to go if your images are in eps-format and pdflatex in case of jpeg images. I wish there was some advanced method to include images. Now a user has to always consider which format/method to use ... :mad:

---

### Post by ntlam on 2008-05-22
Anyone knows how to fix spacing between paragraphs? the spacing is not uniform sometime. It seems for me that how much space latex gives between two paragraphs depends on the paragraph lengths.

Any ideas?

---

### Post by vrangforestillinger on 2008-05-22
Hmm strange. I haven't seen variable paragraph skips before. But I usually use only paragraph indents and no spacing. 

This might be a setting in the style (the \documentclass) you are using. To manually adjust paragraph spacing:
```

\setlength{\parskip}{0.3cm}
\setlength{\parindent}{0cm}

```

Btw. Its easier to find solutions later on for other users if one starts a new thread for a separate problem.

---

### Post by Eothred on 2008-05-28
OK, so I think some of you might be interested in this:
If you use the "Latex - Image insertion" option in Kile, you can in fact also insert both png and jpg files even if you use latex compiling and not only for pdflatex. The reason is that it also creates the boundingbox I think(?). Very neat if you have to create ps or dvi for some reason!

Another thing, when I use dvipdfm option in the hypersetup, I lose the content list (bookmarks) in the dvi file. Any chance to get the bookmarks both in the pdf and dvi file (dvipdf would work, but it does not accept the dvi file if it has png or jpg pictures)? Not a serious problem though as I can just comment out the dvipdfm option in hypersetup while working on the document.

Could someone also explain me the difference between embedded and not embedded? (as in ps vs. eps) I never really understood that...

---

### Post by dfmalh on 2009-10-25
Hi, I am struggling to get a movie (.avi) into my thesis.

Here is my problem.

To get hyperref to work with my images (80) in my thesis as .eps (for publication) I did the following:

> \usepackage[dvipdfm, pagebackref]{hyperref}

It works when I compile it like this: latex --> dvi --> ps --> pdf

So to include my small movie (.avi) I did the following:

> \usepackage[dvipdfm, pagebackref]{hyperref}
\usepackage{movie15}

This does not work, because movie15 does not work with dvipdfm.

I did not want to use PDFLATEX because it does not include .eps, and if I want to use it, it would mean that I would have to change 80 images to .eps

I read somewhere that there is a package...

> \usepackage{epstopdf}

...that will convert EPS to PDF on demand... So I tried to insert it, and take dvipdfm out, ran PDFLATEX, but then I run into other problems...

Is there anybody who have figured a way out to create a PDF containing and EPS image and a movie? I really need help on this problem.

---

### Post by dfmalh on 2009-10-27
dvipdfm does not work with the movie15 package, or I could not make it work.

The only way that seems to work well is to convert the EPS images to PDF and use PDFlatex to compile. In the long run, it saves time as well.

---

