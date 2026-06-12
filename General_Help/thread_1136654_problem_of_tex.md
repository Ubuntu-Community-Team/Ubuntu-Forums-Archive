---
title: "problem of tex"
date: 2009-04-25
forum: General Help
---

### Post by slayerpl on 2009-04-25
I just install texlive2008 ,but I don't know how to use it . I wonder that is there a gui of tex for linux OS. by the way ,I am freshman  of ubuntu. Please help me !!!

---

### Post by mali2297 on 2009-04-25
There are a few guides for LaTeX at [http://www.latex-project.org/guides/](http://www.latex-project.org/guides/). You can use any editor to write the code and then compile it from a terminal with the command
```

pdflatex yourfile.tex

```
That will produce a PDF file.

If you want an editor that assists you in writing the LaTeX code, then you can check out [Kile](http://kile.sourceforge.net/). You can install it from Ubuntu's repositories. There is also a LaTeX plugin available for gedit (the default editor in Ubuntu); the package is called **gedit-latex-plugin** in the repositories.

---

### Post by ad_267 on 2009-04-25
Try kile or the gedit LaTeX plugin. For the gedit plugin you also need to install rubber. I think there's a few threads around about people's preferred LaTeX editors, a google search for Linux LaTeX editor should be helpful.

---

### Post by Stefan_K on 2009-04-30
Hi,

> **slayerpl said:**
> I wonder that is there a gui of tex for linux OS.

I'm preferring Kile that was already mentioned above. It depends on standard texlive packages, so perhaps the installation could be complicated after you've already TeX Live 2008 installed.

A good alternative is [TeXmaker]("http://www.xm1math.net/texmaker/"). I remember it could be installed without dependencies to older tex packages, it's just recommending some.

Stefan

--
[TeXblog.net]("http://texblog.net")

---

