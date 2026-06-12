---
title: "A problem about the latex"
date: 2005-06-01
forum: Desktop Environments
---

### Post by sachi on 2005-06-01
Hi, dear guys

I just start to use ubuntu these days and I am a frequent latex user. However, I met a problem when I try to use the latex. I install all the packages via apt-get. The command "latex" works fine, but when I try to use dvipdf, it returns:

sachi@dshen:~/tex/tutorial/3$ dvipdf 3.dvi
dvips: Font cmr17 at 8000 not found; scaling 600 instead.
dvips: Such scaling will generate extremely poor output.
dvips: Font cmr12 at 8000 not found; scaling 600 instead.
dvips: Font cmsy8 at 8000 not found; scaling 600 instead.
dvips: Font cmti9 at 8000 not found; scaling 600 instead.
dvips: Font cmbx9 at 8000 not found; scaling 600 instead.
dvips: Font cmr9 at 8000 not found; scaling 600 instead.
dvips: Font cmr10 at 8000 not found; scaling 600 instead.
dvips: Font cmsy10 at 8000 not found; scaling 600 instead.
dvips: Font cmbx12 not found,  using cmr10 instead.
dvips: Design size mismatch in font cmbx12
dvips: Checksum mismatch in font cmbx12
dvips: Font cmbx10 at 8000 not found; scaling 600 instead.
dvips: Font cmsy6 at 8000 not found; scaling 600 instead.
dvips: Font cmti10 at 8000 not found; scaling 600 instead.

Can anybody tell me what's going wrong here? The resulting pdf is extremely bad, many characters are missing. Directly using "pdflatex" is a possible solution and it works, but still the qualify of the resulting pdf file is unbearably bad. The reason is also the font 600 is used. 

Has anyone of you guys met this problem before and provide me with some help?

Thanks so much in advance

Sachi

---

### Post by Alexander Kirillov on 2005-06-01
[QUOTE=sachi]Hi, dear guys

I just start to use ubuntu these days and I am a frequent latex user. However, I met a problem when I try to use the latex. I install all the packages via apt-get. The command "latex" works fine, but when I try to use dvipdf, it returns:

sachi@dshen:~/tex/tutorial/3$ dvipdf 3.dvi
dvips: Font cmr17 at 8000 not found; scaling 600 instead.
dvips: Such scaling will generate extremely poor output.
dvips: Font cmr12 at 8000 not found; scaling 600 instead.
dvips: Font cmsy8 at 8000 not found; scaling 600 instead.
dvips: Font cmti9 at 8000 not found; scaling 600 instead.
dvips: Font cmbx9 at 8000 not found; scaling 600 instead.
dvips: Font cmr9 at 8000 not found; scaling 600 instead.
dvips: Font cmr10 at 8000 not found; scaling 600 instead.
dvips: Font cmsy10 at 8000 not found; scaling 600 instead.
dvips: Font cmbx12 not found,  using cmr10 instead.
dvips: Design size mismatch in font cmbx12
dvips: Checksum mismatch in font cmbx12
dvips: Font cmbx10 at 8000 not found; scaling 600 instead.
dvips: Font cmsy6 at 8000 not found; scaling 600 instead.
dvips: Font cmti10 at 8000 not found; scaling 600 instead.

Can anybody tell me what's going wrong here? The resulting pdf is extremely bad, many characters are missing. Directly using "pdflatex" is a possible solution and it works, but still the qualify of the resulting pdf file is unbearably bad. The reason is also the font 600 is used. 

Has anyone of you guys met this problem before and provide me with some help?

Thanks so much in advance

Sachi[/QUOTE]
 Shouldn't it be dvipdfm ? This is wha I use - and have no problems.

Also:  "Font cmr17 at 8000" looks unusual. Scaling  8000 is humongous.

---

### Post by bojanp on 2007-12-31
Install tetex-extra package:

sudo apt-get install tetex-extra

---

### Post by vdawg on 2008-04-24
> **bojanp said:**
> Install tetex-extra package:

sudo apt-get install tetex-extra

I have been looking for this for over a year now!

I no longer need to leave it as ps, THANK YOU!!!!

---

