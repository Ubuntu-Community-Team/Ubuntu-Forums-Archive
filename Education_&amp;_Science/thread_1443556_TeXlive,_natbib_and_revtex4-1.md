---
title: "TeXlive, natbib and revtex4-1"
date: 2010-03-31
forum: Education &amp; Science
---

### Post by Miguel on 2010-03-31
Dear all,

A few months ago, the APS (American Physical Society) released the latest version of revtex, 4.1. The thing is, this requires a very up-to-date natbib package, while the one in TeXlive 2007 is considerably older. It's possible that even the natbib present in TeXlive 2009 is too old as well. 

I've just found out that Debian and by extension Ubuntu doesn't ship tlmgr, so that the only way to update tex would be through aptitude. 

So my question is what would be the recommended way to deal with all this. One option would be forgetting the packaged texlive and going to a vanilla install (not that cool). Another option would be overriding just the packages I need (i.e. just natbib and perhaps revtex4). Finally, is may be possible to install packages in $HOME/.texmf and, hopefully, the packages present here would override both /usr/share/texmf and /usr/local/share/texmf.

Comments? Reccomendations? Anything will be greatly appreciated.

---

### Post by jalirious on 2010-04-09
Until it aint broke, don't fix it. Stable release means nothing to these revtex4 mopes.

---

### Post by Miguel on 2010-04-09
> **jalirious said:**
> Until it aint broke, don't fix it. Stable release means nothing to these revtex4 mopes.

Pardon? I'll have to look "mope" in the dictionary.

---

### Post by jalirious on 2010-04-09
Mope = too much watching The Wire.

Ok, got natbib working with revtex4-1. In case anyone's interested;

Lucid beta 32-release.

Download natbib.ins and natbib.dtx to A_DIRECTORY

[http://tug.ctan.org/tex-archive/macros/latex/contrib/natbib/](http://tug.ctan.org/tex-archive/macros/latex/contrib/natbib/)

cd A_DIRECTORY
sudo su
pdflatex natbib.ins (can use tex, latex instead of pdflatex)
[creates natbib.sty, natbib.log, natbib.ltx, natnotes.tex]
rm  /usr/share/doc/texlive-latex-base-doc/latex/natbib/*
rm  /usr/share/texmf-texlive/bibtex/bst/natbib/*
rm /usr/share/texmf-texlive/tex/latex/natbib/*
[my previous unsuccessful installation attempts]
cp natbib.* /usr/share/doc/texlive-latex-base-doc/latex/natbib/ 
cp natbib.* /usr/share/texmf-texlive/bibtex/bst/natbib/
cp natbib.* /usr/share/texmf-texlive/tex/latex/natbib/
texhash /usr/share/

Open up a new terminal, or source ~/.bashrc
pdflatex paper.tex
bibtex paper
pdflatex paper.tex
bibtex paper
pdflatex paper.tex

outputs paper.pdf, references fine. If anyone with more nous wants to point out the unnecessary steps above then feel free.

Snoochie boochies.

---

### Post by samedirection on 2010-04-30
jalirious, can you confirm that the NEW TeXLive packages for Lucid (now TeXLive 2009!) also don't have the texlive package updater ('tlmgr')?  So that your choices are either to stick with the ubuntu repo (and update when if and as they release new TL2009 packages) or to go solo and install TL2009 from scratch (outside the deb-repo system), in which case you can use tlmgr.  (Sorry I don't need you to confirm the implications of this, but only whether 'tlmgr' is installed and apparently usable in the lucid texlive pacakges.  I'd be glad not to have to install the whole thing just to find out.  I've searched some of the file lists for the package and can't find tlmgr, but until I check everything it's inconclusive)

You could try to 'locate' it or try:
sudo tlmgr update --all --dry-run

which should give you an idea whether it's likely to work.

Thanks.

---

### Post by Miguel on 2010-04-30
> **samedirection said:**
> jalirious, can you confirm that the NEW TeXLive packages for Lucid (now TeXLive 2009!) also don't have the texlive package updater ('tlmgr')?  So that your choices are either to stick with the ubuntu repo (and update when if and as they release new TL2009 packages) or to go solo and install TL2009 from scratch (outside the deb-repo system), in which case you can use tlmgr.  (Sorry I don't need you to confirm the implications of this, but only whether 'tlmgr' is installed and apparently usable in the lucid texlive pacakges.  I'd be glad not to have to install the whole thing just to find out.  I've searched some of the file lists for the package and can't find tlmgr, but until I check everything it's inconclusive)

You could try to 'locate' it or try:
sudo tlmgr update --all --dry-run

which should give you an idea whether it's likely to work.

Thanks.

I'm in RHEL 5.5 right now, but I'm 95% sure that the Lucid packages don't have tlmgr.

---

### Post by samedirection on 2010-05-01
Thanks.  My suspicions too.  I'm doing a net install of the vanilla texlive  2009 just now.  It always worked fine before, and I need my tlmgr.

---

### Post by Miguel on 2010-05-01
> **samedirection said:**
> Thanks.  My suspicions too.  I'm doing a net install of the vanilla texlive  2009 just now.  It always worked fine before, and I need my tlmgr.

Samedirection, I'm in the verge of removing ubuntu-packaged texlive and switch to "vanilla" texlive. Do you get revtex 4-1 with texlive? Is there any other advantage/disadvantage that I should know about before switching to vanilla? Finally, do texlive users get security updates via tlmgr?

EDIT: BTW, I'm now on Lucid, and I can confirm that there is no tlmgr in the default packages.

---

### Post by venik212 on 2010-05-01
I was also unable to find tlmgr in the latest Kubuntu 10.04.  Maybe in 2020?

---

