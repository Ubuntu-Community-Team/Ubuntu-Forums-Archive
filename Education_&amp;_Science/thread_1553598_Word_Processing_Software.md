---
title: "Word Processing Software"
date: 2010-08-15
forum: Education &amp; Science
---

### Post by SuperMiguel on 2010-08-15
So im a Electric Engineer Student and im looking for a word processing software.. I been using Open Office/ MS Office for long time, so far is been working fine. But i see all this posts about Latex.. What is the benefit of it for a Engineer student?? do you guys have examples of a document created in MS Word compared with the same one created in Latex???

Also whats the difference between Latex and Lyx???

---

### Post by Cilph on 2010-08-15
Hello, Supermiguel. I'm a (Dutch) Electrical Engineering student and I prefer to use LyX for my documents. LyX is a graphical LaTeX environment which makes it much simpler to create documents for beginners who don't know most of the LaTeX commands. Usually pure text-only LaTeX is fed into a 'compiler' that generates a dvi/pdf file.
The advantage LaTeX gives (to me), is that all you have to do is type your work and not worry about the layout (and figure/table numbering/toc!) of the document. LaTeX takes care of all that. Another main benefit would be the easy to use mathematical equations. It also works really well with MatLab figures.

---

### Post by FreeTheBee on 2010-08-15
To get an idea of what it looks like you could check the LaTeX wikipedia page. Personally I prefer to use LaTeX in the classical way, writing the code myself. In the beginning this is a bit slow, but as you get used to it, I think it is more efficient to just keep writing instead of needing to go to menus and such. But to each his own of course. If you use an editor like Kile or TeXmaker a lot of the commands can be found in menus as well. Sometimes this can be nice if you need something you don't use very often and kinda forgot.

One of the main advantages was pointed out by Cilph. When you specify properly what is what in your text, like sections, figures and so on... there is not need to worry about crossreferences, citations and similar. Another nice advantage is the output. TeX produces much nicer output than any word processor imho. I remember looking at some comparison of a document in word and TeX a long time ago, I couldn't find it write now, but will post the link later if I can find it.

To get a good overview of LaTeX I would suggest to check "the not so short introduction to latex"
[http://www.ctan.org/tex-archive/info/lshort/english/lshort.pdf]("http://www.ctan.org/tex-archive/info/lshort/english/lshort.pdf")

---

### Post by SuperMiguel on 2010-08-15
> **FreeTheBee said:**
> To get an idea of what it looks like you could check the LaTeX wikipedia page. Personally I prefer to use LaTeX in the classical way, writing the code myself. In the beginning this is a bit slow, but as you get used to it, I think it is more efficient to just keep writing instead of needing to go to menus and such. But to each his own of course. If you use an editor like Kile or TeXmaker a lot of the commands can be found in menus as well. Sometimes this can be nice if you need something you don't use very often and kinda forgot.

One of the main advantages was pointed out by Cilph. When you specify properly what is what in your text, like sections, figures and so on... there is not need to worry about crossreferences, citations and similar. Another nice advantage is the output. TeX produces much nicer output than any word processor imho. I remember looking at some comparison of a document in word and TeX a long time ago, I couldn't find it write now, but will post the link later if I can find it.

To get a good overview of LaTeX I would suggest to check "the not so short introduction to latex"
[http://www.ctan.org/tex-archive/info/lshort/english/lshort.pdf]("http://www.ctan.org/tex-archive/info/lshort/english/lshort.pdf")

So you just use a regular tex editor like gedit, and then run pdflatex or something like that?

---

### Post by ssam on 2010-08-15
i like latex because it means i dont have to worry about formatting, it is done very well automatically.

[http://en.wikibooks.org/wiki/LaTeX](http://en.wikibooks.org/wiki/LaTeX) is also a good reference.

and an example: see the templates at [http://accelconf.web.cern.ch/accelconf/JACoW/templates/templates.htm](http://accelconf.web.cern.ch/accelconf/JACoW/templates/templates.htm)
if you download the 4 files in the latex column, and run
```

latex JACoW2009A4.tex
latex JACoW2009A4.tex
dvips JACoW2009A4.dvi

```
then you will get a postscript file. (latex needs to be run twice to get all its numbering correct)

---

### Post by SuperMiguel on 2010-08-15
> **ssam said:**
> i like latex because it means i dont have to worry about formatting, it is done very well automatically.

[http://en.wikibooks.org/wiki/LaTeX](http://en.wikibooks.org/wiki/LaTeX) is also a good reference.

what latex editor you guys use??

---

### Post by FreeTheBee on 2010-08-15
Here is a comparison of LaTeX, MS Word and OOo, if you scroll down a bit there is a pdf with the different outputs (at the The Document) section. It is not the one I had in mind though.
[http://oestrem.com/thingstwice/?p=65]("http://oestrem.com/thingstwice/?p=65")

You can use any editor, but some are more convenient than others. There are several editors specialised in LaTeX, such as TeXmaker, TeXworks and Kile. In windows I used Winedt and in Ubuntu Kile. Recently I started to use gVim with the vim-latex package, as I thought this could be a nice cross platform alternative.

You could use gedit as well. There is a LaTeX plugin for it, which makes life a little easier. Among other things, it adds compile buttons.

---

### Post by SuperMiguel on 2010-08-15
> **FreeTheBee said:**
> 
[http://www.ctan.org/tex-archive/info/lshort/english/lshort.pdf]("http://www.ctan.org/tex-archive/info/lshort/english/lshort.pdf")

Will read that..

Im also trying to run this on my Mac, running OSX, the only editors i find are TeXShop and Lyx (on lyx i cant get the spell checker) on TeXShop i cant even find a spell checker..

---

### Post by ssam on 2010-08-15
> **SuperMiguel said:**
> what latex editor you guys use??

i use vim. i have it set to do syntax highlighting and spell checking. i have a Makefile with the build commands in. i use bzr for version control. i use [texwordcount]("http://www.comp.nus.edu.sg/~kanmy/software.html") for word counting.

---

### Post by SuperMiguel on 2010-08-15
as you notice already i never used Latex before.. I may want to put it first on my mac, and then in my ubuntu box.

So whats the easiest way (program wise) to get stared on Latex on OSX?

---

### Post by FreeTheBee on 2010-08-15
I know TeXshop is popular and supposed to be easy to use. I don't have a mac so cannot really judge, but friends of mine used it. TeXworks is another simple editor that runs in windows, linux and osx. I like a little more options personally, but perhaps it is a nice one to start with. It seems TeXmaker also runs in osx, out of the three I would probably pick that one.

A quick google search for texshop spell check, showed that this feature can easily be added.
[http://www.uoregon.edu/~koch/texshop/links.html]("http://www.uoregon.edu/~koch/texshop/links.html")

Besides an editor you need a LaTeX distribution of course, for osx this would be MacTeX. There is some info on installing LaTeX in the first appendix of the lshort guide.

Another good source of information is the tex faq,
[http://www.tex.ac.uk/cgi-bin/texfaq2html]("http://www.tex.ac.uk/cgi-bin/texfaq2html")

---

### Post by SuperMiguel on 2010-08-15
> **FreeTheBee said:**
> I know TeXshop is popular and supposed to be easy to use. I don't have a mac so cannot really judge, but friends of mine used it. TeXworks is another simple editor that runs in windows, linux and osx. I like a little more options personally, but perhaps it is a nice one to start with. It seems TeXmaker also runs in osx, out of the three I would probably pick that one.

A quick google search for texshop spell check, showed that this feature can easily be added.
[http://www.uoregon.edu/~koch/texshop/links.html]("http://www.uoregon.edu/~koch/texshop/links.html")

Besides an editor you need a LaTeX distribution of course, for osx this would be MacTeX. There is some info on installing LaTeX in the first appendix of the lshort guide.

Another good source of information is the tex faq,
[http://www.tex.ac.uk/cgi-bin/texfaq2html]("http://www.tex.ac.uk/cgi-bin/texfaq2html")

Texmaker looks pretty good :)

---

### Post by SuperMiguel on 2010-08-15
Do you still use commands in texmaker?

---

### Post by gunksta on 2010-08-15
LaTeX, Word, OpenOffice.org, Lyx

So many tools and so little time. There are some obvious benefits to a tool like LaTeX in terms of the ability to easily add mathematical equations, pictures, bibliographies, etc. Whatever else - latex makes your document look good.

But, for most college length documents a word processor can make a document look good enough and will probably remain a necessity for group projects. After-all, what are the odds that you'll be able to do that under-grad group project in a core humanities class in latex? When I was in school - not much.

The other thing that latex and emacs org-mode bring to the table that is worth mentioning is literate programming. The neat thing about literate programming is being able to write my program the way my head works and then let the computer re-arrange things before sending my code out to python, R, etc. It's fantastic. Again - not so great with group projects since nobody else in the company I work for uses it - but when it's just me I LOVE me some literate programming.

Could be useful to explore.

---

