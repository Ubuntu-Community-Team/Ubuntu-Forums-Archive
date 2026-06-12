---
title: "Where can I find bookantiqua font?"
date: 2009-04-13
forum: General Help
---

### Post by vevo on 2009-04-13
Hello,

I would like to compile a tex document using bookantiqua fonr (NOT ANTIQUA), as it is required for a publication.

I downloaded here
[http://zoonek.free.fr/LaTeX/FontInstall/Samples_TEX/](http://zoonek.free.fr/LaTeX/FontInstall/Samples_TEX/)

the file test-bookantiqua-1.tex

```

\documentclass[a4paper,12pt]{article}
\usepackage{fontsmpl}
\usepackage[default]{font-bookantiqua}
\begin{document}
\fontsample
\end{document}

```

Tried to compile:
```

$ latex test-bookantiqua-1.tex

```

got this error:

```

! LaTeX Error: File `font-bookantiqua.sty' not found.

```


I have been looking for this font (said to be for MAC OS) but I did not find it. Can someone help me? 

Thanks in advance,
Vevo

---

### Post by ad_267 on 2009-04-13
Shouldn't the publication be able to supply the font then?

Book antiqua is just a Microsoft copy of Palatino, you can use Palladio which is again very similar with \usepackage{mathpazo}.

---

### Post by vevo on 2009-04-13
> **ad_267 said:**
> Shouldn't the publication be able to supply the font then?

they just give the .doc version of the document

> **ad_267 said:**
> 
Book antiqua is just a Microsoft copy of Palatino, you can use Palladio which is again very similar with \usepackage{mathpazo}.

Thanks for the advise, however, if someone knows where to find the bookantiqua font, I would prefer to use it.

vevo

---

### Post by ad_267 on 2009-04-13
If you don't manage to find the font, then you could use the ttf font and use xelatex to compile your document.

---

### Post by vevo on 2009-04-13
> **ad_267 said:**
> If you don't manage to find the font, then you could use the ttf font and use xelatex to compile your document.

I know how to compile using xelatex, but I do not know what you mean with "use the ttf font". I suppose that ttf stands for true type font. Could you be more detailed, please?

thanks

---

### Post by ad_267 on 2009-04-13
Yes, Xelatex allows you to use true type fonts in a document. You can put the font into ~/.fonts and then include in your preamble:

\usepackage{fontspec}
\setromanfont{Book Antiqua}

---

### Post by vevo on 2009-04-13
> **ad_267 said:**
> Yes, Xelatex allows you to use true type fonts in a document. You can put the font into ~/.fonts and then include in your preamble:

\usepackage{fontspec}
\setromanfont{Book Antiqua}

Ok, how to use the font with xelatex is now clear, thanks.
Do you know where I can find the ttf for bookantiqua?

---

### Post by ad_267 on 2009-04-13
If you have a windows installation and any of the applications listed [here]("http://www.microsoft.com/typography/fonts/font.aspx?FMID=187") then you should have the font in your Windows installation (I think they're in C:\windows\fonts).

Otherwise there's a download for it at [http://www.webdesignhelper.co.uk/design_elements/fonts/fonts_serif_1to6/fonts_serif_1to6.shtml](http://www.webdesignhelper.co.uk/design_elements/fonts/fonts_serif_1to6/fonts_serif_1to6.shtml) and on other sites if you search for it, although I'm not sure of the legality of these.

---

