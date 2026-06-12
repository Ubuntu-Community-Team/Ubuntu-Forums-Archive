---
title: "Test installation of TexLive"
date: 2009-04-27
forum: General Help
---

### Post by jingpro on 2009-04-27
Hello All,

I am a newbie of Linux. Previously I used TexLive under windows together the editor LED. Now I plan to use TexLive under unbuntu.

I installed Tex (Full) and Texmaker from synaptic package manager, and I tested a simple Tex file, getting compiling error. So, I have a few questions:

(1) How to test whether TexLive is ready for use? Any shell command?

(2) Do I need to configure Texmaker to make it work for Texlive?

(3) I need a Tex editor which provide good compiling, viewing, shortcut menu, auto-completion environment, like LED under windows. I browsed the websites of Texmaker, Emac, gvim, vim-latex suite....., looks like texmaker most matches my requirement (but I did not tested each editor). DO you think my choice is correct? 

Thanks a lot for any of your suggestions.

-Derek

---

### Post by mali2297 on 2009-04-27
Can you post the content of the TeX file that you ran and the error message that you got?

---

### Post by jingpro on 2009-04-28
Thanks mali2297. Texlive works now.

---

### Post by Stefan_K on 2009-04-30
Hi Derek!

> **jingpro said:**
> 
(1) How to test whether TexLive is ready for use? Any shell command?
You could test those:
```
tex --version
pdflatex --version
kpsewhich latex.ltx
```
to check the information given. [kpsewhich]("http://texblog.net/hypertext-help/latex-tools/kpsewhich/") is a small tool for checking TeX variables and for finding TeX files.

> **jingpro said:**
> 
(2) Do I need to configure Texmaker to make it work for Texlive?

It should be able to run after installation, but of course you can adjust its options.

> **jingpro said:**
> 
(3) I need a Tex editor which provide good compiling, viewing, shortcut menu, auto-completion environment, like LED under windows.
TeXmaker is ok, but I'm preferring [Kile]("http://kile.sourceforge.net/") and I'm very satisfied with it. I don't have any problem just because it's needing some KDE libs. Installation of Kile by Synaptic will install the dependent packages. That works fine for me since years. It doesn't matter to me if somebody says "but it's KDE-like".

Currently beside on my workstation I'm also using Kile with TeX Live 2008 on [Eeebuntu on my eee pc S101 netbook]("http://texblog.net/latex-archive/linux/eee-pc-s101-eeebuntu/"), it's also working very well.

Stefan


--
[TeXblog.net]("http://texblog.net")

---

