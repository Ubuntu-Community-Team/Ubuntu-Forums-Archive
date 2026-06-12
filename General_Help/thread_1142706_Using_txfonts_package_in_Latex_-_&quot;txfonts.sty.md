---
title: "Using txfonts package in Latex - &quot;txfonts.sty not found&quot;"
date: 2009-04-29
forum: General Help
---

### Post by lienx on 2009-04-29
Hi there!
 

 I'm writing my dissertation in Latex and want to use the "txfonts" package.  I am a physicist, and not very clued up with the more complicated computer stuff, and need some help.  I first used TeXniCenter in Windows as an editor but when I compiled, I got the error message `txfonts.sty' not found.  I made sure I had all the downloaded txfonts packages.  When I got that error message, it was searching for the "txfonts.sty" file in the directory Program Files/MiKTeX 2.7/tex/latex/txfonts.  I saved the folder with all the txfonts packages (also the txfonts.sty file) in exactly that directory.  Then I increased the priority of this path under the "root" tab in the executable "mo.exe" (in the directory MikTex\miktex\bin).  STILL I got the message that the "txfonts.sty" folder is not found.
 

 I then decided to rather use Kile in Linux since I'm already doing my research there.  On my laptop, I have Slackware, there I got no problem and none of these error messages, but on my desktop, I have Kubuntu.  AGAIN I got the same error message. "File `txfonts.sty' not found. \usepackage".
 

 I searched for the rest of the txfonts packages, and found it in the directory usr/share/texmf-tetex/fonts/afm/public/txfonts, then I saved the Linux version txfonts.sty file at exactly the same place, tried to compile again - same error.
 

 This error occurs for nearly any package I am using, for example using the natbib package, I got the message that the natbib.sty file is not found, so it is not something related specifically to txfonts alone.
 

 Can somebody PLEASE help?   
 I would appreciate it a lot ...

---

### Post by Anthon on 2009-04-29
when i do:
  apt-file search txfonts.sty
I get as output
  texlive-fonts-recommended: /usr/share/texmf-texlive/tex/latex/txfonts/txfonts.sty
so that is where Ubuntu's LaTeX seems to expects it. You should also be able to set the search path, for TeX, but I forgot how to do that.

---

### Post by Stefan_K on 2009-04-30
Hi lienx,

welcome to the board!

> **lienx said:**
> 
I searched for the rest of the txfonts packages, and found it in the directory usr/share/texmf-tetex/fonts/afm/public/txfonts, then I saved the Linux version txfonts.sty file at exactly the same place

tetex is obsolete, consider to install texlive. In the case of texlive you could install the package texlive-fonts-recommended mentioned by Anthon with Synaptic or in the terminal:
```
sudo apt-get install texlive-fonts-recommended
```
When I test with [kpsewhich]("http://texblog.net/hypertext-help/latex-tools/kpsewhich/"):
```
kpsewhich txfonts.sty
```
I'm getting the location /usr/share/texmf-texlive/tex/latex/txfonts/txfonts.sty.

Regarding MiKTeX: there' a [txfonts package]("http://miktex.org/pkg/pkginfo.aspx?dn=txfonts") that you could install by using the MiKTeX package manager.

Btw. if you installed a package manually call
```
sudo texhash
```
afterwards, or [texhash]("http://texblog.net/hypertext-help/latex-tools/texhash/") as root, or [mktexlsr]("http://texblog.net/hypertext-help/latex-tools/mktexlsr/"), to update the package database.

Stefan


--
[TeXblog.net]("http://texblog.net")

---

