---
title: "Can't get ForwardDVI working with Kile with Texlive on Feisty"
date: 2007-04-30
forum: Education &amp; Science
---

### Post by KSam on 2007-04-30
Hi,
I searched the forums for a solution to my problem, but I couldn't find anything, so hence my post. I recently installed Feisty cleanly, and installed Texlive and then Kile. Everything works fine, except for my beloved ForwardDVI function (which I used without problems under Edgy).

I've gone into "Configure Kile" and set up  LaTeX to run the Modern configuration (i.e. latex -src -interaction=nonstopmode '%source'), and the same for ForwardDVI. When I try to compile the file using latex, it seems to compile correctly, but ForwardDVI complains that the DVI file is missing.

Now the curious thing is that for some reason the latex command isn't running latex, it's running pdfetex. When I run 'which latex' it gives me "/usr/bin/latex", and 'ls -l /usr/bin/latex' gives me  "/usr/bin/latex -> pdfetex" Surely that's not what how it should be configured or? As a result a DVI file isn't even created; instead I get a PDF file.

How can I fix this? I've tried removing texlive and installing it again, to no avail. The texlive packages I have installed are:
[LIST]
[*]texlive-base
[*]texlive-base-bin
[*]texlive-common
[*]texlive-latex-base
[*]texlive-latex-recommended
[*]texlive-pdfetex
[*]texlive-fonts-recommended
[*]texlive-doc-base
[/LIST]
Any suggestions? Am I missing any packages or is something wrong with my config?

Many thanks in advance,
Sam

---

### Post by slaanco on 2007-05-01
is latex setup in Kile properly ?
try to uninstall texlive-pdfetex and then run it

---

### Post by KSam on 2007-05-04
Thanks for your reply. I figured out what was wrong in the end; there's nothing wrong with texlive, pdfetex and kile, it was an issue with my document. Specifically, I used an underscore in one of my \labels by accident, and that caused pdfetex to fail silently. This is what stumped me initially - it didn't give any error message and indicated that it finished successfully, when it hadn't. Maybe this is something for a bug report?

Anyways, as part of my trying to fix this, I learnt more about the latex system (putting it down here for future reference): pdfetex is like the Swiss Army Knife of TeX in that it can output in both PDF and DVI format. It figures out automatically which format to output as from the symbolic link it is called from, so if 'pdftex' is called then it outputs a PDF file and if 'latex' is called then it outputs a DVI file. This is why it's OK that latex links to pdfetex.

Moral of the Story: don't use underscores in \label !

2nd Moral of the Story: You can never stop learning! :)

---

