---
title: "What do you use to create presentations?"
date: 2008-03-13
forum: Education &amp; Science
---

### Post by ackey on 2008-03-13
I've been fighting for a long time to find an easy, attractive, powerful way to make talks.  I'm in physics, so my talks are mostly LaTeX expressions, tables, and images, possibly with labels & highlighting.  

"Back in the day" (before I used linux) I used a MikTeX plugin in power point.  I've used OpenOffice, but I find the formula editor very painful.   I tried making slides in LaTeX with some success - it was nice when I was copying things from papers I had written.  However, layout was horrible.  I tried the PROSPER package and had absolutely no luck.

I'm now trying BEAMER and I am relatively happy so far.  However, I haven't actually tried putting in images yet to see how the layout works.  I've been very impressed with the users guide and the simplicity of using the class.

Any advice on the "best" way to make a presentation?  I write LaTeX in emacs - I tried looking at beamer in LyX and was mostly confused.

Also, does anyone have any good BEAMER themes/color themes?  I'm surprised I wasn't able to find a site with a bunch of them (in addition to what is included in the package).  I've found a few themes made with a specific school's logo and colors, but that's it.

---

### Post by DrOlaf on 2008-03-13
I use your combination of emacs, auctex and beamer for all my lectures now myself. Graphics are a bit tricky at the beginning, but as long as you stick with the formats used by your LaTeX installation things work well (I use pdflatex, which likes jpg, png and of course pdf). 

I haven't found many beamer themes online either, but [this one]("http://www.cert.fr/dcsd/THESES/sbouveret/francais/LaTeX.html") is pretty good.

---

### Post by rfruth on 2008-03-13
Google docs has a presentation editor - works for me [http://documents.google.com/support/presentations/bin/answer.py?answer=49008&topic=11965]("http://documents.google.com/support/presentations/bin/answer.py?answer=49008&topic=11965")

---

### Post by slaanco on 2008-03-13
Beamer for sure is the best, has very nice schemes which are optimised for beamers, so it would allow u to use some stupid color combinations which would result in unredable presentation.

:)

---

### Post by kleeman on 2008-03-15
I use Open Office Presentation and lyx. The former used to be a pile of crap but has improved a lot recently. I export Math from lyx to pdf and convert to jpeg (using the usual convert utility) and suck that into OO. OO handles pictures and graphs very well and the export to pdf function makes platform independent presentations. I work in applied math/earth science.

---

### Post by earlycj5 on 2008-03-15
OpenOffice, any presentations that I give are required to be PowerPoint file format so I don't have a choice.

---

### Post by NikoC on 2008-03-17
If I have sufficient time to prepare for a presentation I use Beamer, if not openoffice or keynote on my Mac.

---

### Post by xadder on 2008-03-17
I've been using prosper (from the same author as beamer) for years, and have been happy with this. I looked at beamer some time ago, but it seemed more complicated to change setups than prosper.

I think both have now been superceded by powerdot though.

---

### Post by euler_fan on 2008-03-17
I've used beamer, but the powerdot package looks very interesting.

I do all my latex though Texmaker. Admittedly I don't usually use most of the bells and whistles therein.

---

### Post by DrOlaf on 2008-03-17
I haven't kept up with powerdot's development recently, so I'll check it out and see how it compares.

Both approaches produce pdf files, so once you have made them you can use [KeyJnote]("http://keyjnote.sourceforge.net/") to add some eyecandy to the presentations, if that's your thing. Myself, I'm a recovering [ab]user of transitions and animations. I'm trying to make my audience more interested in the content than in the delivery vehicle.

---

### Post by SanderVermolen on 2008-03-17
I have used PROSPER in combination with LyX for quite a while. This worked out of the box. THE solution for tex presentations for me. No complex setup and all the Latex power you need. I tried Beamer too, but PROSPER was simply easier to use.

---

