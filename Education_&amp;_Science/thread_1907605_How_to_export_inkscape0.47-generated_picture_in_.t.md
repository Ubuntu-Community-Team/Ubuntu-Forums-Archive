---
title: "How to export inkscape0.47-generated picture in .tex format to a LaTeX document?"
date: 2012-01-11
forum: Education &amp; Science
---

### Post by vasjapupkin on 2012-01-11
I've got a LaTeX a.tex document and a picture, created with inkscape0.47 and saved as b.tex file.
I want to \input that b.tex file with picture to a.tex.

I've included PSTricks package in a.tex as required, but still pdflatex  curses that it sees undefined control sequences in b.tex. I assume that I  should've used some more packages in a.tex? Can anyone help me out, how  do I do such an input? Failed to find a guide for my case, they all tell of eps/pdf import.

---

### Post by gleedadswell on 2012-01-23
> **vasjapupkin said:**
> I've got a LaTeX a.tex document and a picture, created with inkscape0.47 and saved as b.tex file.
I want to \input that b.tex file with picture to a.tex.

I've included PSTricks package in a.tex as required, but still pdflatex  curses that it sees undefined control sequences in b.tex. I assume that I  should've used some more packages in a.tex? Can anyone help me out, how  do I do such an input? Failed to find a guide for my case, they all tell of eps/pdf import.

Is there a particular reason you are saving your Inkscape picture as a .tex file?  The easiest picture format to import into a document prepared from TeX is an .eps.  Inkscape is able to save as .eps.  So unless there is a particular reason to save it as a .tex I'd just resave it as .eps then in your TeX document do

```

\begin{figure}
\includegraphics{graphicsfilenamewithoutepsextension}
\caption{\label{a_label}Write a caption here.}
\end{figure}

```

If you haven't already read it you should download and read the Not So Short Guide to LaTeX.

---

### Post by PGScooter on 2012-01-23
I agree with gleedadswell. The easiest thing would be to install LyX. With LyX you can insert an svg file directly so no need for any conversion. This way it's also easier if you need to go back and edit the original image. Of course, in the end, your svg file is converted (to an eps I think) but this is all handled by LyX.

---

