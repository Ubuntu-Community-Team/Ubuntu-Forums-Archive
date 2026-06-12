---
title: "Help me choose a text editor"
date: 2008-07-24
forum: Education &amp; Science
---

### Post by gunksta on 2008-07-24
I am working on a project to translate some SPSS syntax to R-CRAN. Does anyone know of a text editor for Linux that does Syntax highlighting for SPSS and R and supports split screens? I've looked at several obvious Linux based text editors and can't seem to find one that meets my needs.

Gedit will do syntax highlighting for R-CRAN but doesn't for SPSS syntax. Unlike Gedit, Bluefish also supports split screens, but it also lacks SPSS syntax highlighting.

So far the only tool I have found that seems to meet my requirements for this project is a Windows program called Notepadd++ which is open source at least.

---

### Post by WinterWeaver on 2008-07-24
Dunno if you have tried this one, nor if it will meet your full requirements, but after I got used to VIM, I cannot use another text editor.... ever.

If you install the GVIM package, you'll get the GUI version.

Note that Vi takes some getting used to, as It has 3 different modes to work in, namely command, insert and visual (not really sure if this last one is a mode).

Also, I always tell people that want to switch to vim (after they see me work in it :P )... "Make sure you can Touch-Type before you try Vim or GVim, or you will just get frustrated.

PS: you will have to go through one or two tutorials to get a hang of vim, but once you've done that, and you start using it more and more, you will never look back :).

PS: dunno if I'll re-ignite a war here... :P .... but there is also emacs, you can give that a go as well (I dont have any experience in it, so I'm not saying anything more ^_^ )

Have fun!

WW

---

### Post by Anzan on 2008-07-24
For a friendly Vim try Cream.

---

### Post by gunksta on 2008-07-25
It looks like emacs may be out of the discussion. There is an extension for emacs called Emacs Speaks Statistics but it doesn't work with SPSS syntax. It prefers (understandably) the S type statistical languages.

I found an old page with a syntax highlighting file for vim, but I haven't played around with it yet so it may or may not work.

It looks like Jedit can do R syntax but I can't find anything for SPSS. But, Jedit looks easier to learn than vi/emacs and it can do split screen work.

---

### Post by Tart on 2008-07-25
I use Rkward, and I really love it.
You can check it out here. 
[http://rkward.sourceforge.net/](http://rkward.sourceforge.net/)

It is also available in repositories, or if you just go to Add/Remove >> Education and Rkward will be there.

---

### Post by gunksta on 2008-07-25
A tool like Rkward would be too specialized. I only have a few requirements, but they are absolute necessities. I am going to translate from SPSS syntax to R code, and I want to be able to see both files, side by side and I would prefer to have syntax highlighting in each.

I downloaded and installed Jedit but it seems to be nearly as complicated as vim, and not nearly as high on the geek cred, so I may reconsider. Plus, I can't find SPSS syntax highlighting anywhere for it.

I found the syntax highlighting for vim but the style sheet is a little out of date. Guess I need to start there and clean it up.

---

### Post by Tart on 2008-07-25
Check Kate. Kate has plug-in with R script, but I'm not sure about SPSS

[http://en.wikipedia.org/wiki/Kate_%28text_editor%29](http://en.wikipedia.org/wiki/Kate_%28text_editor%29)

[http://kate-editor.org/](http://kate-editor.org/)

---

### Post by gunksta on 2008-07-29
I settled on vim. Thanks for all the suggestions.

---

### Post by achristoffersen on 2008-08-04
What are your experiences with vim+r-cran+spss? I cant find a suitable Tinn-R or Notepad++ replacement under gnome-ubuntu.

Will try out Cream - but emacs+ess have had me to confused...

---

### Post by gunksta on 2008-08-04
If all you need is a good text editor for R, I would probably just used gedit. To turn gedit into a truly useful application you will need to also install the package, gedit-plugins. This package includes useful plugins like an embedded terminal, etc. 

As for SPSS syntax, I have been less fortunate. I have found a couple of SPSS syntax files for vim (google for spss syntax vim) but I can't seem to make them work. 

I like vi/gvim because it will let me use a split screen, so I can have two files open at the same time and see/read them both at the same time, which is better for me (in many cases) than 2 tabs.

But, gedit has a lot of advantages on the simplicity front.

Jedit can also do R syntax as can the R-CRAN front-end called JGR.

I have found that R-CRAN is very well supported in Linux text apps but SPSS is a pain.

---

### Post by gunksta on 2008-08-04
Oh yeah. I have also noticed that Notepad++ works very well under wine, so it's possible that Tinn-R and other tools you may like do too.

---

