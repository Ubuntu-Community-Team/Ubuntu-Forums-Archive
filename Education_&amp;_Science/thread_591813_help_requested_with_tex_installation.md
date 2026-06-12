---
title: "help requested with tex installation"
date: 2007-10-25
forum: Education &amp; Science
---

### Post by vdbergh on 2007-10-25
Hi,

I just installed Ubuntu 7.10. All went very well.
However when installing (all) the livetex packages
I have a bad problem.

 latex file.tex 

This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 %&-line parsing enabled.
kpathsea: Running mktexfmt latex.fmt
I can't find the format file `latex.fmt'!

I thought this was a packaging problem but then I installed
teTeX from source and got a similar error.

This is pdfeTeX, Version 3.141592-1.21a-2.2 (Web2C 7.5.4)
kpathsea: Running mktexfmt latex.fmt
fmtutil: format `latex' not available.
I can't find the format file `latex.fmt'!

Are there any pointers. I am a scientist and I really need TeX!

Regards,
Michel

---

### Post by xadder on 2007-10-26
I have Gutsy running fine with LaTeX (texlive), so I don't know what the problem is. I found:

$locate latex.fmt
/var/lib/texmf/web2c/pdftex/latex.fmt
/var/lib/texmf/web2c/pdftex/pdflatex.fmt


Do you have those? I can't think of much to do though, except a broader google-search for the problem.

---

### Post by vdbergh on 2007-10-26
Hi,

After your reply I became convinced that there was something
wrong with my setup. After a while I found out what it was.

I had a hardcoded TEXINPUTS variable in my .bashrc. Since
texlive has different installation directories from tetex this
caused the postinstall scripts to fail. So I ended up with a broken install.

I tried uninstalling texlive and reinstalling but for reasons I don't understand this did not work. 

Since I did not succeed in rectifying the situation I did a fresh Gutsy
install and lo and behold texlive seems to have installed now
without problems. 

Thanks for your feedback,
Michel

---

### Post by ajohansen on 2008-02-23
I recently had a similar problem (see [http://ubuntuforums.org/showthread.php?p=4388869#post4388869](http://ubuntuforums.org/showthread.php?p=4388869#post4388869)). texlive would install, but the latex.fmt file would not be anywhere on the system.

It turned out that I had to *not* set TEXINPUTS when installing livetex. Commenting out the relevant lines in my .cshrc caused texlive to install properly with the latex.fmt file in /var/lib/texmf/web2c.

---

