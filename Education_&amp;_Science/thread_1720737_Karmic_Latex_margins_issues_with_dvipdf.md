---
title: "Karmic: Latex margins issues with dvipdf"
date: 2011-04-03
forum: Education &amp; Science
---

### Post by wannabegeek on 2011-04-03
Hi all,

I have been trying to fix a problem with my latex page numbers for a few years now.

I use the geometry package to have small margins all around, 2cm sides and top and 1cm bottom. But, when I print these latex  files the margins are not true to my settings. Further more, sometimes the page number would interfere with the text. 

I thought this was a latex problem...

It turns out that if you use evince to open the .dvi file you'll see the proper margins. Then using print preview, you'll see that the margins are not true here, but they are in the normal viewer mode !

To get the bottom margin I wanted of 1cm, I had to enter 0.5cm. This sounds congruent with a known bug I read about.  [http://sites.google.com/site/ourcomputernotes/latex/how-to-fix-the-margin-problems-when-creating-a-pdf-in-ubuntu](http://sites.google.com/site/ourcomputernotes/latex/how-to-fix-the-margin-problems-when-creating-a-pdf-in-ubuntu)

I just printed from evince the .dvi file and the bottom margins turned out OK. 

But, .dvi files won't print the figures, so I need to convert to pdf or ps or eps.

That's where I'm stuck, because using dvipdf or dvips does not use the margin settings at all.

I don't want to use pdflatex because then I can't use .eps files. I've learned that eps files are the way to go for good looking documents especially if using screen captures from bench equipment with funky resolution. 

any help is greatly appreciated,
wbg

---

### Post by Chronon on 2011-04-04
My first thought would be an inconsistency between the paper size you used in your .tex source and that used in dvips/dvipdf.

Does it help to explicitly set the paper size?

---

### Post by wannabegeek on 2011-04-04
I did try dvipdf -sPAPERSIZE=letter file.dvi

Which did not help.

Today I tried the above w/o paper size and it worked on Lucid. where as I am running Karmic.

However, I did not print the file yet from Lucid just looked at the print preview.


thanks for your interest,
wbg

---

### Post by wannabegeek on 2011-04-07
I'm just about ready to call this one solved

When I print from evince (print preview as well), the margins are messed up. 

When I use lpr filename.pdf, (after dvipdf filename.dvi) then they appear to follow
my specifications with geometry package.

I lost my cm ruler so can't compare right yet.  Definitely the bottom margin is smaller than
is has been when printing from evince.

See OP for details.

wbg

---

### Post by Chronon on 2011-04-10
So maybe a bug in evince then?

---

### Post by wannabegeek on 2011-04-10
> **Chronon said:**
> So maybe a bug in evince then?

I think so...I have never files a bug report so I probably should learn now.

I tried evince on a few different computers, one running Ubuntu 10.04 and centOS and my own 9.10...all three print differently.

It seems safest to use lpr command for now.

Bake to writing up more latex docs....
cheers,
wbg

---

