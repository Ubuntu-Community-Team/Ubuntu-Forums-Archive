---
title: "Pure Latex"
date: 2008-07-27
forum: Education &amp; Science
---

### Post by KOTAPAKA on 2008-07-27
As far as I understand it Lyx only uses latex to create a WYSIWYG document processor. I want to use the original latex program. Does anyone know the name of the package?

---

### Post by meborc on 2008-07-27
as far as i understand, latex is just a protocol... a way of writing... you can write latex with any text editor

but to make things easier you could use texmaker or such

---

### Post by hugmenot on 2008-07-27
Install the texlive-latex packages. You don&#8217;t need necessarily all of them, the ones suffixed with -recommended are enough.

Then you write the documents with a text editor, there are specialized LaTeX editors that assist you with inserting markup into  your document and compiling it. Search this forum for recommendations. Myself, I use Vim to edit LaTeX documents, but that&#8217;s only a matter of habit. To compile I use the "rubber" package; it deals with everything needed to finish the document (e.g., "rubber -d mydocument.tex" for PDF output).

---

### Post by arkara on 2008-07-28
A great program for latex writing is kile

---

### Post by ppm on 2008-07-30
[http://tobi.oetiker.ch/lshort/lshort.pdf]("http://tobi.oetiker.ch/lshort/lshort.pdf")

---

### Post by dada1958 on 2008-07-30
TeXLive is in the repositories and for a lean & mean front end editor, have a look [here]("http://live.gnome.org/Gedit/LaTeXPlugin") ...

---

### Post by chrisby on 2008-07-30
I started out with Lyx and outgrew it too.  I personally love Texmaker.  If you don't want errors when compiling, I would suggest going into synaptic and installing every texlive package except the language packs that you don't need.

---

### Post by malrost on 2008-09-06
I was just reading about this in "The (Not So) Short Introduction to LaTeX" by Tobias Oetiker ([http://ctan.tug.org/tex-archive/info/lshort/english/lshort.pdf](http://ctan.tug.org/tex-archive/info/lshort/english/lshort.pdf)). This is listed on the LaTeX project documentation page.

The short answer: to use "pure" LaTeX, simply create an ascii text file using whatever editor you prefer: vim, emacs, gedit, etc. 

Name the file with a .tex extension, the run the following command:

```
latex foo.tex
```

If it it a properly-formatted LaTeX file, this will create a .dvi file. You then have several options for viewing, converting, and further working w/ the .dvi file.

That's it. If I understand you correctly, "pure" LaTeX is simply knowing how to properly format using LaTeX commands. That guide above is a good start.

The longer explanation from Oetiker's guide (bold added):

> To publish something, authors give their typed manuscript to a publishing company. One of their book designers then decides the layout of the document (column width, fonts, space before and after headings, etc.) The book designer writes his instructions into the manuscript and then gives it to a typesetter, who typesets the book according to these instructions.
    A human book designer tries to find out what the author had in mind while writing the manuscript. He decides on chapter headings, citations, examples, formulae, etc. based on his professional knowledge and from the contents of the manuscript.
    **In a LaTeX environment, LaTeX takes the role of the book designer and uses TeX as its typesetter. **But LaTeX is “only” a program and therefore needs more guidance. The author has to provide additional information to describe the logical structure of his work. This information is written into the text as “LaTeX commands.”
              
```

```

---

### Post by engla on 2008-09-06
`pdflatex' instead of `latex' will generate a .pdf directly which is normally what you want to do.

edit, addition: And how to write latex documents? The basics are super simple. Copy a barebones example file and start with it. Basic title things and \section{} etc are very simple and are really the core of what latex is.

For everything apart from that, look it up on the web, there are tons of guides and references. And there are thick books. But Latex is about keeping your hands off the presentation as far as possible, you just tell Latex _what_ you want to do (not _how_ to do it or what it is going to _look_like_)

---

