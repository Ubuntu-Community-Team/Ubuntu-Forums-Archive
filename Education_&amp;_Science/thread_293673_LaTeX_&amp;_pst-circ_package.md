---
title: "LaTeX &amp; pst-circ package"
date: 2006-11-05
forum: Education &amp; Science
---

### Post by mustang on 2006-11-05
Hi guys,

I use Kile for latex word processing. I am trying to draw electrical circuits in latex. I came across the pst-circ package which seems to perform that function.

The README:

> 
This version of pst-circ uses the xkeyval package, the extended
version of keyval.

Save the files pst-circ.sty|.tex in a directory, which is part of your 
local TeX tree. pst-circ.pro should be saved in ../texmf/dvips/pstricks/
Then do not forget to run texhash to update this tree.
pst-circ needs pst-plot and pst-tricks, which should be part of your
local TeX installation, otherwise get it from a CTAN server, f.ex.
[ftp://ftp.dante.de](ftp://ftp.dante.de)


So I downloaded pst-circ.sty & pst-circ.tex & pst-circ.pro from [here.]("http://www.ctan.org/tex-archive/graphics/pstricks/contrib/pst-circ/")

Followed the directions above.

Then I went into kile and tried to test it out. Here's the tex code:

```

\documentclass[a4paper,10pt]{article}

\usepackage{pst-circ}
%opening
\title{}
\author{}

\begin{document}

\pnode(0,1){A}
\pnode(3,1){B}
\resistor(A)(B){$R$}

\end{document}

```

Compiles fine when I build a dvi or a pdf. However, the output is messed up:

[DVI]("http://www.members.cox.net/vo154/test.dvi")
[URL="http://www.members.cox.net/vo154/test.pdf"]
PDF[/URL]

The output should be a resistor like [here]("http://pstcirc.free.fr/download/pst-circ.pdf") (top of pg 3)

Any help would be appreciated! :)

EDIT: now this is really weird. Using xdvi (as opposed to evince), the DVI file DOES show the output appropriately. But when I convert the dvi to a pdf and view it through evince or the official adobe reader, I only see an "R"

---

### Post by mustang on 2006-11-05
Sigh, spent maybe five minutes trying something else and came up with the solution. Turns out, kile (by default) uses dvipdfm to convert dvi to pdf. 

dvipdfm doesn't seem to work correctly (atleast with this package)

Use dvipdf instead

In kile:

Settings->Configure Kile->Build->DVItoPDF

Replace dvipdfm with dvipdf

---

### Post by parktownprawn on 2006-11-06
Glad you managed to fix your problem.

For future reference - pst-circ  is in edgy.

You just need to install the package

texlive-pstricks

You can install this without installing the rest of the texlive  stuff and it should work fine for texmf

---

### Post by Astrophysiker on 2008-03-29
I have a problem with this package. I used this example as source code, but the output (dvi and pdf) shows the labels at the wrong place. Here my dvi-file:
[DVI]("http://astrophysiker.as.funpic.de/test.dvi")
Putting more element means more labels at the same place.
Has somebody an idea whats going wrong?

Thx, Astro

---

