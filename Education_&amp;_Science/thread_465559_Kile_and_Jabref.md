---
title: "Kile and Jabref"
date: 2007-06-05
forum: Education &amp; Science
---

### Post by dysonsphere23 on 2007-06-05
New to Linux and LaTeX.

I am running Ubuntu 7.04 and I am having trouble getting citations to register in Kile from JabRef.  

I have compiled a database in JabRef, and saved the .bib file in the same directory as the Kile .tex file.  When I click the LyX/Kile button in JabRef the citation appears in Kile.  However when I try to view the document by converting tex to PDF  the Kile log indicates that the references are undefined.

If I try Build>Compile>BibTex Kile tells me:
[BibTeX] Postdoc_proposal.bib => Postdoc_proposal.bbl (bibtex)
[BibTeX] finished with exit status 2

I was hoping that someone could help me through this as I see great potential in using these applications.

Thanks in advance

---

### Post by kleeman on 2007-06-06
Did you insert a bibliography command (using kile) in your latex file giving the location of your *.bib file?

---

### Post by dysonsphere23 on 2007-06-06
> **kleeman said:**
> Did you insert a bibliography command (using kile) in your latex file giving the location of your *.bib file?

No I don't believe I did that.  As I said I am new to this.  I will figure out how to do that I suppose.

Thanks

---

### Post by dysonsphere23 on 2007-06-06
> **kleeman said:**
> Did you insert a bibliography command (using kile) in your latex file giving the location of your *.bib file?

Ok so I did that and now when I try to convert to PDF or compile LaTeX:

[PDFLaTeX] Postdoc_proposal.tex => Postdoc_proposal.pdf (pdflatex)
[PDFLaTeX] finished with exit status 1
./Postdoc_proposal.bbl:1:Missing \begin{document}. \begin{thebibliography}{}
./Postdoc_proposal.bbl:1:Missing \begin{document}. \begin{thebibliography}{}
./Postdoc_proposal.bbl:3: Empty `thebibliography' environment on input line 3.
./Postdoc_proposal.tex:19: Citation `Bent2006' on page 2 undefined on input line 19.
./Postdoc_proposal.tex:0: There were undefined references.
[PDFLaTeX] 2 errors, 3 warnings, 0 badboxes or 

BibTeX :

[BibTeX] Postdoc_proposal.bib => Postdoc_proposal.bbl (bibtex)
[BibTeX] finished with exit status 2

Another tab comes up with .bbl extention that reads:

\begin{thebibliography}{}

\end{thebibliography}


Any other suggestions?

---

### Post by kleeman on 2007-06-06
Sounds like syntax problems. Here is a good introduction:

[http://theoval.sys.uea.ac.uk/~nlct/latex/novices/node46.html](http://theoval.sys.uea.ac.uk/~nlct/latex/novices/node46.html)

Edit: You might want to use the /bibliography{FILE.bib} command instead since this alllows you to specify an externl bibliography (FILE.bib)

---

### Post by dysonsphere23 on 2007-06-08
> **kleeman said:**
> Sounds like syntax problems. Here is a good introduction:

[http://theoval.sys.uea.ac.uk/~nlct/latex/novices/node46.html](http://theoval.sys.uea.ac.uk/~nlct/latex/novices/node46.html)

Edit: You might want to use the /bibliography{FILE.bib} command instead since this alllows you to specify an externl bibliography (FILE.bib)

Thanks, I will read that over carefully.  I appreciate your help.

---

