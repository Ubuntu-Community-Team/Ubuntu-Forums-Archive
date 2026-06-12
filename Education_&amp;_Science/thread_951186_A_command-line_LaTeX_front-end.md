---
title: "A command-line LaTeX front-end"
date: 2008-10-17
forum: Education &amp; Science
---

### Post by jesushero on 2008-10-17
Hello, I have been working on a simple command-line LaTeX front-end to simplify and unify the process of building latex documents. The traditional way requires to run a command to build a DVI, a different command to build a PDF, and a series of commands to include BibTeX bibliography files. 

As of now, I have made a single bash-based program that will take options to tell it what to build and it will build it. It also includes a script by a contributor that makes A5 booklets with the pages sorted, ready to print and bind. It also has an option to create a .tex file with a basic layout in it to start with. I have also made another program, a LaTeX pre-processor, that scans the LaTeX file to figure out if it includes BibTeX entries. It then passes this on the the aforementioned program, that builds the document with no need to specify options. 

I am thinking of expanding the LaTeX pre-processor to follow include tags for either graphics or text, and ensure that everything is in place and in the correct format. If not, it should put it in the correct format.

Does anyone find this interesting? I'd like any comments or suggestions, as to what you would like to see implemented. Any input will be greatly appreciated. I am also more than happy to work together with anybody interested.

---

### Post by brunovecchi on 2008-10-18
You should check out the command line tool **rubber**. Look:

> **an automated system for building LaTeX documents**
This is a building system for LaTeX documents. It is based on a routine thatruns just as many compilations as necessary. The module system provides a great flexibility that virtually allows support for any package with no user intervention, as well as pre- and post-processing of the document. The standard modules currently provide support for bibtex, dvips, dvipdfm, pdftex, makeindex. A good number of standard packages are supported, including graphics/graphicx with automatic conversion between various graphics formats and Metapost compilation.

---

