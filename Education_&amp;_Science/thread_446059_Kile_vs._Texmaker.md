---
title: "Kile vs. Texmaker"
date: 2007-05-16
forum: Education &amp; Science
---

### Post by skywatcher on 2007-05-16
Just in case no-one's noticed, Kile beats Texmaker handsdown when it comes to performance, or at least this is my experience. I am working on a research report that currently runs into over 50 pages, with nearly 30 eps figures and images. Compiling this document with Kile takes a few seconds at most. And I don't mean compile only -- I mean compile, dvips, view ps. Texmaker takes a looong time to compile the same job, let alone the other conversions.  I also tried Texmaker on Windoze and compared it with WinEdt. Same thing -- Texmaker is slow.

Has anyone else had similar results? If so, I would advise would-be thesis authors to stay clear of Texmaker. :lolflag: 

Cheers

---

### Post by neoflight on 2007-06-01
hmm.. thats interesting....i dont  think its the kile or texmaker that compiles it...they simply call the commands that to be run on the text file...i dont see how texmaker is slowed down due to the size of the *.tex file....

could you run the same file from the command line only and see how long it takes to  run it?

---

### Post by briansers on 2007-06-02
I'm a little surprised that there is a noticeable difference in the compile speeds, but then I'm not a programmer, so there may be a good reason for it.  I use Kile exclusively for its utility. I tried texmaker early on, when I first started using Linux, but Kile was more useful.

---

### Post by Fingolfin on 2007-06-02
Every toolbar icon in TeXMaker (or Kile for that matter) is just a front-end for the command that launches a program that does the conversion.
For example: a click on DVI to PS icon will simply call on dvi2ps application to do the job of creating Postscript file from DeVice Independent format and it is done in the background so neither of the two LaTeX editors should have any impact on the speed.
Example 2: compilation of a *.tex file will invoke command like 'pdfetex file_name.tex'.

As there could be different compilers under the teTeX system (old latex engine versus new pdfetex for example, and the similar existence of different DVI translators) it may be that TeXMaker is just configured to get the slower ones to do the job?!

---

### Post by ghorwin on 2007-06-21
From the programmers perspective, there could be an explanation for this. TexMaker spawns new processes with QProcess for all external tools. At the same time these processes are connected with communication slots which are called whenever the process sends something to stdout or stderr. This is most likely the cause for the slowdown. I don't know by heart how Kile is spawning these processes, but from my experience with numerical solvers, a computational intensive process spawned via QProcess takes longer (somethings a factor of 2) compared to the same process started from the shell.

However, if what was described is correct, the slowdown is much bigger than a factor of 2. This could then only be caused by poorly written==very slow communication handlers for the spawned console processes.

Anyway, something worth to be investigated by the TexMaker folks.

Just my two cents...
Andreas

---

### Post by mamaolo on 2007-08-20
I found both nealry the same speed, but Kile a bit faster.
My problem with Texmaker, which makes me spend more time, is that it doesn't identify the **name of an included file** when you have error (but Kile does), so Kile is faster, at least for me!.
I would prefer Texmaker, as I must manage with [COLOR="Red"]*Micro$oft*[/COLOR] Win at work, so I could use the same editor I usually use at home.
Could you suggest any solution?

Marcelo

---

### Post by itaylor on 2008-09-09
I find some aspects of Texmaker frustrating, like the lack of keyboard shortcuts for many things, but the speed wasn't one of them. I compiled a 180 page thesis with 42 figs no problem, but that was PDF figures and PDFlatex.

I found using Kile in Gnome to be annoying because not everything worked right, but maybe I should try it again just to compare.

Also, I chose jEdit as the best I could find cross platform editor to do what I wanted. The LaTeX tools plugin doesn't bring it quite to the level of Texmaker or Kile, but gets you part way there.

---

### Post by mrgnash on 2008-09-09
I found them both pretty annoying. In terms of newbie ease, without going against the standard way of doing things (e.g. LyX), I think Gedit with the LaTeX plugin is about the best at the moment.

Vim is where it's really at, though :P

---

### Post by Vivaldi Gloria on 2008-09-10
I use kile for a simple reason - In texmaker you cannot change the background colour.

---

### Post by kozimodo on 2009-05-07
The only deal breaker for me was that TeXMaker did not do inverse search.  Since it now works with inverse search, I now have a new LaTeX front end.

---

### Post by InfernalNeutrino on 2009-05-07
> **mrgnash said:**
> Vim is where it's really at, though :P

Agree. Kile is neat and all, but I quickly hit the point where all the pretty buttons just got annoying and cluttery to me. The vim latex plugin is actually quite nice IMO. I can see why people use kile of course (pretty slick and beginner-friendly) but if you really are interested in "performance" use something lighter :)

---

### Post by lethalfang on 2009-05-08
> **kozimodo said:**
> The only deal breaker for me was that TeXMaker did not do inverse search.  Since it now works with inverse search, I now have a new LaTeX front end.

Do you know how do I configure inverse search for TexMaker for viewers like kdvi, okular, xdvi, etc.?

---

### Post by kozimodo on 2009-05-08
Open Options > Configure Texmaker and change the text in the DVI Viewer section to read:
```
xdvi -editor "texmaker %f -line" %.dvi -sourceposition @:%.tex
```
You may want to also change the Quick Build section to LaTeX + View DVI.  All this is in the site documentation: [http://www.xm1math.net/texmaker/doc.html#SECTION37](http://www.xm1math.net/texmaker/doc.html#SECTION37).

Cheers!

---

### Post by pallabbasu1234 on 2010-05-05
Just now kile is almost like a joke as the spellchecker is not latex aware. 

texmaker spell checker is not also excellent but much better.

Overall stability and crash is almost non-existent in texmaker. Kile had many problems on those fronts.

I am heavy user of latex and found texmaker is a much better option than kile. Also keep in mind the gedit-latex-plugin.

---

### Post by kleeman on 2010-05-06
Just for an alternate viewpoint:

I use lyx and then export to latex. After that it is easy to paste the latex into an appropriate template file and compile from the cli.

lyx as a frontend is much more intuitive than either kile or texmaker. imho

---

### Post by Timtro on 2010-05-06
> **kleeman said:**
> Just for an alternate viewpoint:

I use lyx and then export to latex. After that it is easy to paste the latex into an appropriate template file and compile from the cli.

lyx as a frontend is much more intuitive than either kile or texmaker. imho

They aren't the same thing. LyX tries to approximate a WYSIWUG (What You See Is What You Get) experience with LaTeX, while Kyle and TeXMaker are for those of us who want to write the code (What You See Is What You Mean, or WYSIWUM).

I don't have enough experience with LyX to be sure, but something tells me that if you want to do anything complicated or custom, LyX would have issues. That's not to say it isn't great for the 90% of people who only want out of the box functionality. And I could be dead wrong about it not being able to handle complex stuff. But to get complex stuff, you need to write code anyway, so why bother?

---

### Post by kleeman on 2010-05-06
> **Timtro said:**
> They aren't the same thing. LyX tries to approximate a WYSIWUG (What You See Is What You Get) experience with LaTeX, while Kyle and TeXMaker are for those of us who want to write the code (What You See Is What You Mean, or WYSIWUM).

I don't have enough experience with LyX to be sure, but something tells me that if you want to do anything complicated or custom, LyX would have issues. That's not to say it isn't great for the 90% of people who only want out of the box functionality. And I could be dead wrong about it not being able to handle complex stuff. But to get complex stuff, you need to write code anyway, so why bother?
Yeah I am well aware of the differences and have used all three extensively :lolflag:. I write highly mathematical papers all the time and lyx handles the complicated setups very nicely. It is rare that I have to dive into native latex code. Lyx is a very mature piece of software now and can do an awful lot. 

Where lyx is not strong is in getting a specified style for journal submission. That is when I export to latex and paste in the output into a latex template. All round quick and painless with only limited latex commands to remember (which is the whole point of kile and texmaker).

Not saying one method is superior for all applications or not just giving another alternative.....

---

### Post by PC_load_letter on 2010-05-07
On the thread topic: Kile by a mile :lolflag: 

My preference is Geany w/ the Latex plugin, very simple yet very powerful. 

Another surprise (for me at least): [Gummi]("gummi.midnightcoding.org/"), written in Python, very simple and not too many features & it's still under heavy development...but...it compiles and displays the pdf file in a second frame and almost in real-time!!! Well, there is a delay by a few seconds, but still. One more good reason to have a new wide screen monitor.  

Screenshot:
[http://gummi.midnightcoding.org/wp-content/uploads/20091012-1large(1).png](http://gummi.midnightcoding.org/wp-content/uploads/20091012-1large(1).png)

---

### Post by kleeman on 2010-05-07
There is also a latex plugin for gedit that works nicely with a dual panel viewer.

---

### Post by XCan on 2010-05-07
> **kleeman said:**
> There is also a latex plugin for gedit that works nicely with a dual panel viewer.

+1 to that!

---

### Post by pallabbasu1234 on 2010-05-11
Let me add my criteria for a gentleman's latex editor.

1) Reverse/ Forward serach.
2) Inline spell check.
3) Latex aware spell check

and also

4)Splitview, Tab
5)Auto completion
6)Bracket completion

There is none for linux :(, well if you do not like to go back to classical stuffs like emacs and vim.

---

### Post by Timtro on 2010-05-17
> **pallabbasu1234 said:**
> Let me add my criteria for a gentleman's latex editor.

1) Reverse/ Forward serach.
2) Inline spell check.
3) Latex aware spell check

and also

4)Splitview, Tab
5)Auto completion
6)Bracket completion

There is none for linux :(, well if you do not like to go back to classical stuffs like emacs and vim.

I like TeXmaker if you really want something dedicated. I personally use Vim with the latex addon (sudo apt-get install vim-latexplugin) and it can do all that you want, although I could be wrong about the latex aware spell check.

---

### Post by pallabbasu1234 on 2010-05-19
Spellcheck provided with vim is reasonably latex aware. At least is it as latex aware as best windows editor like Texincenter or winedt.

TexMaker does not support splitview (as per as I know), other wise it would have been a great editor of choice. I am currently using it for last couple of months and like it a lot.

---

### Post by pallabbasu1234 on 2010-05-19
> **Timtro said:**
> I like TeXmaker if you really want something dedicated. I personally use Vim with the latex addon (sudo apt-get install vim-latexplugin) and it can do all that you want, although I could be wrong about the latex aware spell check.

I think the latex package is called vim-latexsuite in Jaunty (may be in karmic also). So if somebody likes to install it use: sudo apt-get install vim-latexsuite

---

### Post by fbkarsdorp on 2010-05-19
> **pallabbasu1234 said:**
> 
There is none for linux :(, well if you do not like to go back to classical stuffs like emacs and vim.

And why wouldn't you? Emacs in combination with Auctex en Reftex is just rock solid and has all the functionality you need.

---

### Post by pallabbasu1234 on 2010-05-19
Well I do, but to configure it one has to go through some auctex and emacs documentation. This is a little pain. Also remembering all the key combination takes some time to get used to.

---

### Post by fbkarsdorp on 2010-05-20
Well it's not that hard... The only really important key-binding is C-c C-c to compile your file. Then hit C-c C-c again to view the result. Here's my configuration:

; AUCTeX package
(require 'tex-site)
(require 'reftex)
(add-hook 'LaTeX-mode-hook 'turn-on-reftex)

; integrate RefTeX and AUCTeX
(setq reftex-plug-into-AUCTeX t)
; I always use natbib, make it the default style in reftex
(setq reftex-cite-format (quote natbib))

; I don't compile into dvi, only pdf, so:
(setq TeX-PDF-mode t)

; If you like to view your pdf's inside emacs 
; and to make it update automatically:
(add-hook 'doc-view-mode-hook 'auto-revert-mode)

; I want to view my output using evince, not xpdf:
(defun pdfevince ()
   (add-to-list 'TeX-output-view-style 
                    (quote ("^pdf$" "." "evince %o %(outpage)"))))

(add-hook  'LaTeX-mode-hook 'pdfevince t) 

; Set Dictionary to american
(setq ispell-dictionary "american")
; Turn on flyspell
(add-hook 'LaTeX-mode-hook 'flyspell-mode)
;set keybinding flyspell
(global-set-key [(f5)] 'flyspell-auto-correct-word)

---

### Post by pallabbasu1234 on 2010-05-20
> **fbkarsdorp said:**
> Well it's not that hard... The only really important key-binding is C-c C-c to compile your file. Then hit C-c C-c again to view the result. Here's my configuration:

; AUCTeX package
(require 'tex-site)
(require 'reftex)
(add-hook 'LaTeX-mode-hook 'turn-on-reftex)

; integrate RefTeX and AUCTeX
(setq reftex-plug-into-AUCTeX t)
; I always use natbib, make it the default style in reftex
(setq reftex-cite-format (quote natbib))

; I don't compile into dvi, only pdf, so:
(setq TeX-PDF-mode t)

; If you like to view your pdf's inside emacs 
; and to make it update automatically:
(add-hook 'doc-view-mode-hook 'auto-revert-mode)

; I want to view my output using evince, not xpdf:
(defun pdfevince ()
   (add-to-list 'TeX-output-view-style 
                    (quote ("^pdf$" "." "evince %o %(outpage)"))))

(add-hook  'LaTeX-mode-hook 'pdfevince t) 

; Set Dictionary to american
(setq ispell-dictionary "american")
; Turn on flyspell
(add-hook 'LaTeX-mode-hook 'flyspell-mode)
;set keybinding flyspell
(global-set-key [(f5)] 'flyspell-auto-correct-word)

Many thanks :), I would just like to know how to change the Ctrl+C Ctrl+C to both compile and view the file?. Thanks again...

---

### Post by fbkarsdorp on 2010-05-20
Its already for both purposes. If you edited a file, pressing C-c C-c (just hold the Ctrl...) will ask you if you want to compile using LaTeX. IF you haven't edited your file or after compilation, it asks you to view it using your defined viewer. If your using the code I gave you, this will be automatically evince. 

Belief me, its quit handy and you'll get used to it in no time.

---

### Post by niziris on 2011-05-01
lyx + geany with plugins for latex  ....I try Kile but it didn't go well with me (it is great but not for me)...texmaker is more elegant

---

