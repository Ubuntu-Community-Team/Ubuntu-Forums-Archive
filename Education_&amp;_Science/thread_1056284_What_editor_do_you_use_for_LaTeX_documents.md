---
title: "What editor do you use for LaTeX documents?"
date: 2009-01-31
forum: Education &amp; Science
---

### Post by urukrama on 2009-01-31
I'm slowly migrating from OpenOffice to Latex for most of the writing I do. I still have a few projects I started in OpenOffice that would take way to long to migrate to Latex (yes, I know of the OpenOffice export to Latex feature), but every new project I start is in Latex. So far I really like it. It takes a while to master it, but I've got the basics down, and there is good documentation available.

So far I have been using Gedit with the Latex plugin. LyX is not at all what I want; Kile looks promising, but more involved than Gedit.

There are a wide variety of Latex editors for GNU/Linux.  Which is your favourite? Please discuss the merits (and demerits) of your choice.

If you voted for more than one, please explain.

---

### Post by ugm6hr on 2009-01-31
I find that the LyX GUI with a simple template is enough for me.

Only really use it for my CV at the moment though.

Looked at it originally because I'm looking to return to academia, and thought it would be useful to learn how to use it for my potential future thesis.

---

### Post by ravenon on 2009-01-31
For most of my work, I use Lyx to create mathematical documents. Most journal publishers want the LaTex file. As Lyx stores in its own format, I export to LaTex and use Kile or Texmaker to do any final edits.

---

### Post by tommers on 2009-01-31
I'm the same as ravenon.

---

### Post by hessiess on 2009-02-01
GVim.

---

### Post by ahmatti on 2009-02-01
Emacs with auctex for me!

---

### Post by meborc on 2009-02-01
texmaker all the way

edit:

i have also found a new project called [texworks]("http://code.google.com/p/texworks/"), which will try to become something like texshop on mac

i have installed it and found it quite good for my purposes, to install it follow these instructions from their website... i added texlive as i didn't have pdflatex installed on my debian setup:

$ sudo apt-get install build-essential libpoppler-qt4-dev libhunspell-dev libdbus-1-dev texlive 
$ svn checkout [http://texworks.googlecode.com/svn/trunk/](http://texworks.googlecode.com/svn/trunk/) texworks-read-only
$ cd texworks-read-only
$ qmake-qt4
$ make
$ ./texworks

for more info **[COLOR="Red"]WATCH[/COLOR]** this great video on the project - [http://www.river-valley.tv/conferences/tug2008/#0103-Jonathan_Kew](http://www.river-valley.tv/conferences/tug2008/#0103-Jonathan_Kew)

---

### Post by lha on 2009-02-01
> **urukrama said:**
> There are a wide variety of Latex editors for GNU/Linux.  Which is your favourite? Please discuss the merits (and demerits) of your choice.

GVim & [Vim-LaTeX]("http://vim-latex.sourceforge.net/").

Vim-LaTeX provides a bunch of nice macros that reduce the amount of typing: simple stuff like typing `a to get \alpha, and more complex things like typing figure and pressing F5 in order to obtain
```

\begin{figure}[<+htpb+>]
	\begin{center}
		\includegraphics{<+file+>}
	\end{center}
	\caption{<+caption text+>}
	\label{fig:<+label+>}
\end{figure}<++>

```
(Control+J selects the next <+ +>-bit allowing you to quickly insert the parts of a figure environment that change from one figure to another.)

Forward and backwards-search are also handy: Control+click a paragraph or a formula in xdvi to find the corresponding location in the tex-file. The same thing works also in the reverse direction. In addition to these, there are a lot of other useful tools in Vim-LaTeX.

The downside of Vim is that some people find it difficult to learn. Nevertheless, it is a powerful editor when you learn to use it, and in conjuction with Vim-LaTeX, it really is worth the effort. (In fact, the 'effort' is not necessarily so large. I found it quite easy to switch from Gedit and Emacs to GVim.)

---

### Post by mali2297 on 2009-02-02
I use [JED]("http://www.jedsoft.org/jed/")+[latex4jed]("http://www.ctan.org/tex-archive/support/jed/latex4jed/"). It is similar to Emacs+AUCTeX (syntax highlighting, shortcuts to compile, etc) but JED is far lighter than Emacs.

---

### Post by hzambran_cl on 2009-02-02
I'm not a GNU/Linux expert yet, and unfortunately I'm not used to the commands of *vim *nor *emacs*, but I'm aware that, when you know them, they are powerful tools.

Having said that, I'm now using **Texmaker **([http://www.xm1math.net/texmaker/](http://www.xm1math.net/texmaker/)), after using *Kile *for a while. One of the main reasons for the change was that Texmaker has more than 300 mathematical symbols can be inserted in just one click, and that was a feature that I really missed in Kile.

*Lyx *can be a good choice for those starting with Latex, but after knowing some Latex commands, I'm feel more comfortable with Texmaker.

---

### Post by Crafty Kisses on 2009-02-02
Vim!

---

### Post by Simian Man on 2009-02-02
Another vote for vim.  If all the text files I edited were LaTeX source, I might try something like Kile, but vim just does everything well once you learn it.

---

### Post by xadder on 2009-02-04
In general I edit everything with vim, but for LateX I have started to use gedit with the LaTeX plugin. The latter gives completion, including accessing the bib files to suggest references. I tried vim-latex a while ago, but it often did things I didn't want (too much auto-completion!). gedit+latex has a very nice balance of ease of use + functionality.

---

### Post by briansers on 2009-02-05
I've used Kile almost exclusively since I switched to Ubuntu.  Before that on Windows I used WinEdt.

---

### Post by Mander on 2009-02-05
I'm still very new to LaTeX, having been a dedicated Word user for many years.  I switched because I wanted to avoid some of the formatting nightmares I endured with my MA thesis in my current work, and because I needed better reference management and wasn't about to shell out the money for EndNote.

I started with LyX but the process of inserting references really got on my nerves, because it was painfully slow with my old XP computer.  I started learning plain LaTeX so that I could use BibTeX more easily.  I used Texmaker on Windows and sometimes Notepad++ but I never really liked either one.  When I switched to Ubuntu I started with Gedit first, then switched to Kile.  

I like being able to see the document structure as I work, which is the main thing I like about Kile, Texmaker, and LyX.  I always worked in outline mode in Word.  I wish that LyX could export "cleaner" LaTeX; it has a better "outline" than the other two, particularly because you can move sections up and down in the hierarchy very easily.  Kile sort-of does this, but not as well as Word or LyX, and afaik Texmaker does not.

ETA:  I should say that I am a social scientist, and I rarely use any mathematical formulae in my work, so having math symbols readily available doesn't really matter to me.

---

### Post by samden on 2009-02-05
Gedit with the LaTeX plugin.

I was using TeXShop on the Mac, and when I switched to Linux I first used Texmaker. Texmaker is good if you want to use the GUI, but having got used to typing all the code myself it was just a nuisance, as the area of the screen you type in on Texmaker is quite small. So I switched to Gedit, and it does the job well, much closer to how I used to use TeXShop. And is lighter on system resources too.

If I could be bothered learning Vim or Emacs I am sure either would be better, but I don't have the memory for yet another load of keyboard shortcuts to maximise either of those programs. I have never tried Lyx because I figured if I am going to use LaTeX I would prefer to use actual LaTeX and have full control over my documents.

So that's a long way of saying Gedit is the best for me!

---

### Post by meborc on 2009-02-06
> **samden said:**
> Gedit with the LaTeX plugin.

I was using TeXShop on the Mac, and when I switched to Linux I first used Texmaker. Texmaker is good if you want to use the GUI, but having got used to typing all the code myself it was just a nuisance, as the area of the screen you type in on Texmaker is quite small. So I switched to Gedit, and it does the job well, much closer to how I used to use TeXShop. And is lighter on system resources too.

If I could be bothered learning Vim or Emacs I am sure either would be better, but I don't have the memory for yet another load of keyboard shortcuts to maximise either of those programs. I have never tried Lyx because I figured if I am going to use LaTeX I would prefer to use actual LaTeX and have full control over my documents.

So that's a long way of saying Gedit is the best for me!

if you miss texshop, check out [texworks]("http://code.google.com/p/texworks/")

---

### Post by briansers on 2009-02-06
Texworks looks interesting.  Is there a package for Intrepid yet?  I found one for Hardy.

---

### Post by amar on 2009-02-06
kile, though recently I have started to switch to gedit (with custom snipets)

kile was just taking too long to load on my eee pc and the screen size didn't help. Still use kile on my desktop.

---

### Post by meborc on 2009-02-08
> **briansers said:**
> Texworks looks interesting.  Is there a package for Intrepid yet?  I found one for Hardy.

i don't know, you can build it the way i described on the first page of this thread... works pretty good, although it has only the basic features... i truly hope this project gets off the ground and becomes something as good as texshop

---

### Post by NikoC on 2009-02-09
In the past I often used Winefish, but just recently I switched to Texmaker and now and then Lyx...
Really like them both!

---

### Post by sudomp on 2009-02-13
Emacs+pdflatex all the way. Once you get the hang of it, there is nothing as superfast and powerful.

---

### Post by sharon.gmc on 2009-02-13
I use Emax just because I started with it and I am used to it.  I never had any problem with it.  I love it!

---

### Post by TheAxeR on 2009-02-15
I like Gedit with the latex plugin.  It is solid system and gets out of my way.  I like that in the side panel it gives me an outline of my document based on the sectioning I have declared.   I have also played around with Texworks.  I believe that it has a bright future as long as they continue working on it.  I would love to see the compiling  system (rubber) that the gedit plugin uses put into Texworks, then I would switch over full time.

---

### Post by kjohansen on 2009-02-15
I use Kile in ubuntu, and LED when I am on windows.

---

### Post by myle on 2009-02-18
Kile because it has more easily accessible features even though you may ignore their existence.
It facilitates the use of special symbols and very common commands and it has a very useful autocomplete feature.

---

### Post by Borbus on 2009-02-19
I use the same thing I use for all my editing. Emacs, of course.

org-mode for emacs can make writing the outlines a lot easier and has a really nice table builder. Building tables in LaTeX can be a pain, but the org-mode table tool is reason enough to switch to emacs.

---

### Post by meho_r on 2009-02-22
Kile. I see many use Vim even for LaTeX-ing. Must check it out :)

---

### Post by urukrama on 2009-02-22
> **meho_r said:**
> Kile. I see many use Vim even for LaTeX-ing. Must check it out :)

As I am working on much older computers now that have a hard(er) time running Gedit, I too am slowly migrating to vim and vim-latex. Vim-latex is very good, and (what I like best) customisable. I'll spend some time on modifying the defaults, but once this is all set up, it will provide a very good writing environment.

---

### Post by earlycj5 on 2009-02-27
> **meborc said:**
> if you miss texshop, check out [texworks]("http://code.google.com/p/texworks/")

Interesting looking package.  Thanks for the link.  I might suggest this to lab mates for use on Windows.

---

### Post by meborc on 2009-02-27
> **earlycj5 said:**
> Interesting looking package.  Thanks for the link.  I might suggest this to lab mates for use on Windows.

i use texworks for my thesis... it seems to be working fine already...

it has active development going on, which is always a good thing

check out the mailing list and the bug/fix list to keep on pulse with it ;)

---

### Post by amylase on 2009-03-13
I use two simple ones:
1. OOoLatex in OpenOffice
2. Texworks

---

### Post by BeniBela on 2009-03-19
Great! Another thread to place an advertisement:
I used Texmaker, but since it lacks some features, I created a fork TexMakerX 
which also support things like interactive spell checking, code folding, completion markers and error highlighting.
Check it out at: texmakerx.sourceforge.net
(it would be pity if no one knows it after all the efforts)

---

### Post by ErnobmaS on 2009-03-25
I'll add my vote for Vim + Vim-LaTeX. As an engineering grad student, the code completion on figure/table references, ability to quickly insert maths (my new favorite is [FONT="Courier New"]`/[/FONT] expanding to [FONT="Courier New"]\frac{<++>}{<++>}<++>[/FONT]), code folding of sections, and the integration with BibTeX have been invaluable to me, not to mention the powerful cross-platform editing provided by Vim itself. Definitely worth the learning curve, in my opinion.

---

### Post by eumetaxas on 2009-03-25
Texmaker is my favourite.
Cross Platform, free, portable and supports unicode.
Need nothing else!

---

### Post by neoflight on 2009-03-28
i like texmaker very much. simple and fast.

---

### Post by vhegos on 2009-03-28
I use emacs for editing latex documents probably just because I use emacs for editing everything else and would rather learn a few new emacs tricks than another editor just for my latex docs.

---

### Post by ad_267 on 2009-03-29
I use Gedit or Vim.

I haven't really settled on either yet but seem to be moving towards vim. I use vim for all my other text editing and programming. 

Can you use vim-latex with normal command line vim? I can only seem to find documentation for using it with the graphical version, although to be honest I haven't looked that hard.

---

### Post by scrogster on 2009-03-29
I use texmaker - computers at my office are windows, linux (ubuntu) at home so having a cross-platform editor that looks and works the same on both OSes is important for me.

---

### Post by InfernalNeutrino on 2009-03-29
> **ad_267 said:**
>  
Can you use vim-latex with normal command line vim? I can only seem to find documentation for using it with the graphical version, although to be honest I haven't looked that hard.

Yes... just be sure to add whatever modifications you want to the correct .rc file :P . As far as I know, it functions completely the same, except perhaps you won't get the menu tools you do when you use gvim. I think that it requires vim >= 6.1.

---

### Post by nortexoid on 2009-03-30
> **BeniBela said:**
> Great! Another thread to place an advertisement:
I used Texmaker, but since it lacks some features, I created a fork TexMakerX 
which also support things like interactive spell checking, code folding, completion markers and error highlighting.
Check it out at: texmakerx.sourceforge.net
(it would be pity if no one knows it after all the efforts)

Interesting. Those are basically all the features I miss in the plain old Texmaker.

---

### Post by zazuge on 2009-04-09
I use Vim with Makefile.
why makefile? you ask.
well i suffered from the formating nighmare 3 years ago when i was using xp & Msoffice for my thesis .
to begin with i don't use even use wordprocessors if i don't have some kind of thesis work.
now i'm using the project tree aproach for thesis works (vs the single file one)
it's much easier to add and modify your thesis if you identify the context & content from filenames
the main file use "\include" command to attach chapters to main document.
and every chapter(or part) is a directory that contain multiple files as subchapters ,this way it's much to add and remove content.
in the end the makefile compile the new or mdified files generate the dvi and pdfs.
i think it's difficult to setup but when done it's usier to work with (and faster then any WYSIWYG).
-------updated 4/12/2009
that was unnecessary bloating ;) 
but i needed to feel pleased about myself :p

---

