---
title: "LaTeX margins"
date: 2005-12-29
forum: General Help
---

### Post by Strife on 2005-12-29
I'm not sure if anyone else has experienced this problem, but for some reason, when I have a LaTeX document and I use the package fullpage, my margins get all screwed up.

Essentially what happens is that on the right hand side, I get margins less than an inch, and on the left hand side, I get margins larger than an inch. To see what I mean, take a look at this screenshot: [http://www.ubuntuforums.org/attachment.php?attachmentid=4916&stc=1&d=1135883021]("http://www.ubuntuforums.org/attachment.php?attachmentid=4916&stc=1&d=1135883021")

I have also experienced this problem on a Debian machine elsewhere, but surprisingly, another Ubuntu machine does not exhibit this problem.

Any ideas as to the cause of this?

---

### Post by Strife on 2005-12-29
Of course, I can solve this problem by doing a \usepackage[top=1in,right=1in,left=1in,bottom=1in]{geometry}, but it would be a lot nicer just to have to do \usepackage{fullpage}.

And I'm still really confused why on some machines fullpage works, while on others it doesn't.

---

### Post by hajk on 2005-12-29
I can't replicate your problem. Using A4-paper and producing PDF with pdflatex, the margins of my test document are the same (about 2.60cm > 2.54cm = 1in) when measured at magnification 100% on screen both in XPDF and in Acrobat Reader. The paper copy has margins of exactly 2.54cm printed on HP DeskJet 5850 printer with HPLIP/hpijs printer driver.

Looking at /usr/share/texmf/.../fullpage.sty also doesn't give me any hint as to your problem. 

Are you using pdflatex? It is known that the latex - dvips - ps2pdf route produces different PDF files...

Note: that's it! When I use latex - dvips - ps2pdf on my test file, I get the same margin problem in XPDF and in Acrobat Reader. So, just use pdflatex from now on...

---

### Post by Strife on 2005-12-30
Interestingly, I *was* using pdflatex. I get the same problem however I try to compile into a PDF.

I don't recall having this problem on my desktop, but since I am away from home for the holidays, I unfortunately won't be able to test that for a couple of weeks.

Thanks for giving it a go, though.

---

### Post by hajk on 2005-12-30
I notice that my version of pdflatex produces PDF-1.4 code (with correct "fullpage" margins), whereas ps2pdf produces PDF-1.2 code (with wrong margins). Comparing both PDF-files in an editor (vim) shows, among other differences, that the /MediaBox parameter is different. 

I wonder whether upgrading to a newer version of teTeX is worthwhile, the one in Breezy is rather old (2.0.2); the one in Dapper is 3.0.

---

### Post by Strife on 2005-12-30
Hmm... I'm also using backports, but I checked on a machine I have remote access to (one that doesn't have the margin issues), and it has the exact same version of tetex.

Interestingly, I decided to give it a try with a4paper instead of letterpaper, and fullpage works. Now if I weren't in America where we use these darn non-standard sizes and measurements, I would be fine. But perhaps that can shed some light on the problem.

I'll update if I find anything else out.

---

### Post by commike37 on 2007-01-08
I prefer to set my margins manually.  I find it works best that way.  Here's the LaTeX that I use.  This was designed for letter paper.
```
\setlength{\topmargin}{0in}
\setlength{\headheight}{0in}
\setlength{\headsep}{0in}
\setlength{\textheight}{9in}
\setlength{\oddsidemargin}{0in}
\setlength{\textwidth}{6.5in}
```
Also, if you're using tetex, don't forget to run the 'texconfig' command in the terminal.  Use that to set your paper size to letter and not A4.

---

