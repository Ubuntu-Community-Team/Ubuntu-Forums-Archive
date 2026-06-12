---
title: "BibTeX: author-date citation treated like one word?"
date: 2009-09-25
forum: Education &amp; Science
---

### Post by Mander on 2009-09-25
I am using LaTex to write a social science thesis, which means I am using a Harvard (author-date) citation style.  I have a couple of citations that have two authors with long names. I can't figure out how to get these citations to wrap to the next line at the margin, like normal text.

For example, if I have a paragraph that carries on to the margin, like this, and want to put a citation into it that is sort of long (Jiminez Martinez and Valdez Diaz 2009:158-159), it should wrap at whatever word is at the end of the paragraph.  However, when I have citations like this, the whole citation is treated as if it were a sinlge word instead of four or five.  It makes the paragraph spacing look really wierd.

Does anyone know how I can fix this?  There aren't any extra {} in the .bib file.

---

### Post by Xnst on 2009-09-28
Hi,

have you tried to add some hyphenation marks '\-' in the author's names in the .bib file. Like

Jim\-inez Mart\-inez, Val\-dez Diaz

I guess you get the idea. I do not know if this works, just a guess.

---

### Post by samden on 2009-09-28
Xnst, I think Mander is wanting the lines to wrap between the words, not hyphenate. I'm stumped unfortunately.

Mander, try posting this question at the LaTeX Community forum:
[http://www.latex-community.org/forum/](http://www.latex-community.org/forum/)

---

### Post by Mander on 2010-01-26
I finally found the answer.  In a nutshell, bibtex inserts non-breaking spaces into the .bbl file when the document is compiled.  See [here]("http://newsgroups.derkeiler.com/Archive/Comp/comp.text.tex/2007-11/msg00301.html") and [here]("http://newsgroups.derkeiler.com/Archive/Comp/comp.text.tex/2007-11/msg00370.html") for details.

The important bit is to try enclosing the author's last name in curly brackets in the bibtex file. So, using my previous example:

Jiminez Martinez and Valdez Diaz 2009:158-159

@ARTICLE{martinez09citation,
author = {{Jim\'{i}nez Mar\'{i}inez}, Emiliano and {Valdez D\'{i}az}, Francisco},
title = {Citation},
journal = {Journal},
year = {2009},
volume = {13},
pages = {150-160},
}

It's worked for me so far, anyway!

---

### Post by Mander on 2010-01-29
On further research, while putting the names in curly brackets helps, my real problem was a conflict between the natbib and hyperref packages.

Use the "breaklinks" option in hyperref:
\usepackage[breaklinks]{hyperref}

Then you can have hyperlinks *and* line breaks in your citations!

---

