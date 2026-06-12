---
title: "Latex -&gt; HTML on Windows"
date: 2009-05-25
forum: Education &amp; Science
---

### Post by c174 on 2009-05-25
I'm trying to write a manual for a program I'm working on. I had this in mind

1) type formulas quickly using latex
2) take screen shoots from the program and add annotations in some graphics program
3) convert to manual to html
4) share the manual among colleagues by simply giving them an url.

I was expecting to use latex2html, but so far I'm not doing very well. It seems that neither \include nor \input is supported (?) So I can't split the document into multiple files... Also the docs for latex2html seem really old..

I'm using Cygwin on Windows.

Does somebody have a suggestion for me? Alternative ways to do it? Etc. I would be most grateful

---

### Post by leandromartinez98 on 2009-05-25
You can convert your formulas to and SVG graphic, for example, I frequently do that. Then I open them with inkscape and do what I want with them (actually inkscape has a latex->svg internal formula converter, but for me it never worked). To do so, you must:

```

latex yourlatex.tex
dvips yourlatex.dvi -o yourlatex.ps
pstoedit -f svg -dt -ssp yourlatex.ps yourlatex.svg

```

The attached script is a simple Tcl/Tk GUI interface for those three commands I've done. You must have, of course, pstoedit, tcl/tk and latex to use it.

Of course, after creating the ps file (after dvips), you can open the ps file in several graphic programs to use the formulas, but having the svg is very practical if you want more flexibility.

---

### Post by c174 on 2009-05-25
> **leandromartinez98 said:**
> You can convert your formulas to and SVG graphic, for example, I frequently do that. Then I open them with inkscape and do what I want with them (actually inkscape has a latex->svg internal formula converter, but for me it never worked). To do so, you must:

```

latex yourlatex.tex
dvips yourlatex.dvi -o yourlatex.ps
pstoedit -f svg -dt -ssp yourlatex.ps yourlatex.svg

```

The attached script is a simple Tcl/Tk GUI interface for those three commands I've done. You must have, of course, pstoedit, tcl/tk and latex to use it.

Of course, after creating the ps file (after dvips), you can open the ps file in several graphic programs to use the formulas, but having the svg is very practical if you want more flexibility.

Thanks for the tip!:) Looks like a nice way to convert a formula from latex to scaleable vector graphics.

However, that is actually not precisely what I am looking for. I want to write a document in latex, inspect in the normal way using dvips, and when I'm happy then convert it into html.

After a little more research I came across ht4tex -- does anybody have experience with this program? :D

---

