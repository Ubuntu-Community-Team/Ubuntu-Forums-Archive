---
title: "writing scientific/mathematic papers"
date: 2006-08-15
forum: Education &amp; Science
---

### Post by shoagun on 2006-08-15
Hi,

I've heard a lot of good things about producing nicely formated documents with free software.  However, trying to look at all the different tools and opinions out there has become a little overwhelming.  I've looked at FAQs for LaTex, Lisp, TeXmacs, Maxima, etc. and I'm more confused than when I began.  I would like to hear what other people do to produce their scientific/mathematical papers; what programs do you use, what process do you go through from start to finish?  I'm hoping this will help me narrow my focus a little.

Thank!

---

### Post by st14n on 2006-08-15
I use LaTeX, and Emacs with auctex as my editor. Don't know about the others you mention as I haven't tried them. Look at  [this thread]("http://www.ubuntuforums.org/showthread.php?t=80344") to see install instructions. Of course there's no problem using another editor. Any text editor will do. If you're using KDE, Kile would be a good choise for starters I think (never tried it though). As for learning, just look at some examples and search for help on how to do things when questions appear. That's what I do and I always find answers.

---

### Post by sweettea on 2006-08-18
I've been a LaTeX user for years and write all my sci/math papers with it, actually, I pretty much use LaTeX for everything, posters, slides, tutorials etc. I've a musician in the family and use LaTeX for writing music.

As for editors, I've used TeXnicCenter and iTexMac. I'm just learning my way around Kile, and it seems satisfactory. 

Besides beautifully typeset equations, I find the referencing tool to be invaluable. I use JabRef as my referencing manager. I've used ProCite and Endnote and still like little ol' JabRef, it doesn't destroy my reference db and the portability is very nice. 

With regards to: "what process do you go through from start to finish?" Not sure what you're after but for me start to finish means, get LaTex (TexLive 2005), get an editor (Kile), get a reference manager (JabRef), tie them all together and then get to writing. There are a ton of sources for LaTeX code to get you going. 

If you mean the process of producing a LaTeX document from start to finish, this varies somewhat depending on if you have a glossary, nomenclature, want to make an index, so on and so forth. 

If you decide to go with LaTeX and Kile, be more than happy to help if I can.

---

### Post by chalex on 2006-08-18
the easiest thing to do is to install Kile and all of its helper programs, and to read the definitive intro guide to LaTeX: type "lshort.pdf" into Google.

---

### Post by shoagun on 2006-08-18
Thanks for the input!  Do you happen to know if kile works just as well on Gnome as it does on KDE?  

It sounds like simply having latex is enough.  I got the impression that many other programs were needed, mainly because there are so many other progams out there.

---

### Post by etavi on 2006-08-18
You could also try Lyx (for info check [http://www.lyx.org/)](http://www.lyx.org/)), it's in the Ubuntu repositories...I've used it and I'm very happy with it.

You can jump into writing a document, check the results way faster than learning Latex. (though that would help later)
"Users already acquainted with "raw" LaTeX will find that LyX offers full LaTeX transparency and export of LaTeX documents."

---

### Post by it.henrik on 2006-08-18
gedit + latex + dvipdf -> great papers :)

---

### Post by Markus Valkeapaa on 2006-08-18
> **sweettea said:**
> ... I use JabRef as my referencing manager. I've used ProCite and Endnote and still like little ol' JabRef, it doesn't destroy my reference db and the portability is very nice... 


sweettea,
Thank you for the tip about JabRef. Have used Endnote in Windows and was wondering about replacement.

-Markus

---

### Post by ekarni on 2006-08-18
> Do you happen to know if kile works just as well on Gnome as it does on KDE?

It sounds like simply having latex is enough. I got the impression that many other programs were needed, mainly because there are so many other progams out there.

Kile works fine under Gnome.

Latex is one part of the puzzle.  Per the usual unix philosophy of building lots of small tools and gluing them all together, you'll most likely want at least some of the extra programs mentioned in earlier posts.

Kile is a frontend to latex with features like autocomplete, syntax highlighting, etc. that make latex easier to use.  It also brings in converters to produce PDF output, etc.  Similarly, JabRef is a great frontend for the BibTex bibliography system, which can feed into latex.  Everything is free, so provided you've got a decent internet connection, there's not much to lose by trying everything and finding out what best fits your needs.

---

### Post by thk on 2006-08-18
Depending on your field, you will find LaTeX either wonderful or a PITA. Journal editors do not care if your manuscript is beautiful. They want line numbering and in many cases (especially book editors) manuscripts submitted in word format. After years of LaTeX, I've switched to LyX which I think is terrific. However, once OOffice gets serious bibliography support (what is in the works for v3 is far superior to bibtex) and a high quality equation editor/layout engine, I will likely switch for good. (You can currently embed LaTeX equations in OOffice with a third-party plugin, so really its just the bibliography bits that will be the last straw.) I will miss LaTeX, but its time to move on...

---

### Post by sweettea on 2006-09-19
Interesting. I've been using LaTeX for a while now, and have not encountered any submission or publication problems in my field. The journals supply the style files and away you go! Maye it just takes a while for some journals to come around.

---

### Post by Awale on 2006-09-20
Hello, I have been trying to use latex for a while, with kile as frontend. It is great, but it requires you learn the latex tags and so on. So, I looked for something more symple and visual. I found Lyx to be the thing I was looking for, with the posibility to add custom latex blocks and much more, but It has many issues you should take on account:

[LIST=1]
[*]It doesnt support UTF-8 enconding, or if it does, its a really well hidden feature... This is something bad, since todays almost every piece of soft has support or even brings utf8 as default. If I want to export a file to kile, I cant since everything is filled with funny interrogations.
[*]Besides of the encoding of the files, the program is built in I-dont-know-which encoding, so, if you use ubuntu in other language than English, for example Spanish in my case, you will find wierd characters instead of ñ, á, é, í, ó, ú, ü (hope in this forums it displays ok...[/LIST]I have been trying to solve this problems, but I have not much experience with linux yet, and less about encodings. Could someone tell me how to solve this problem, or if next versions of lyx will actually support other languages for true? ( I use version 1.4.2 )

thanks very much

---

### Post by hvbakel on 2006-09-20
If you're looking for a good reference manager for OOffice, try bibus. Works much better than endnote for me.

---

### Post by mhw on 2006-09-20
Kile definitely works under Gnome.

I would recommend Lyx; The 1.4 version is much better than 1.3.x. It's available through apt-get/ Synaptic.

HTH,

Matt

---

### Post by Miguel on 2006-09-27
LaTeX rocks. Plain TeX also rocks, if you are hardcore enough (I am not). Usually the first thing I do after installing ubuntu is apt-get install tetex. teTeX is probably the most famous TeX bundle in Unix world, and mikTeX does the work under Windows.

You can use whatever editor you want, because most if not all of the editors in linux support LaTeX syntax highlighting. If you want more icing like autocompletion and the like, you'll have to look a bit. If you like emacs, try aucTeX. If you like vim, you have vim-latexsuite.

Regarding journals, most self-respecting journals in Physics and Maths (I'd guess all math journals require some form of TeX) accept LaTeX. Actually, the style of Physical Review (the most important physics-only magazine) is bundled with teTeX. It's called revtex4. I personally will never send an article to a journal that doesn't accept TeX. 

Once you leave the WYSIWYG world you will never look back. Why? [list]
[*] It is true cross-platform, being plain text
[*] You spend more time thinking on what you write, not how
[*] Captions, footnotes, formulas, references, indexes, page numbering, headers,... easy peasy. And it won't break your document.
[*] Different magazine? Just change one single word
[*] It looks *exactly* the same on every single machine. That's why its programmed using integers
[*] Only uses CPU cycles and memory when you need it. And it runs OK on Damn Small Linux systems.
[/list]

---

### Post by pau on 2006-09-28
Well, there is a notable exception... Nature does not supply a style  ](*,) 

As for me: vim (not gvim) + Latex + bibtex + zsh + gnuplot + shell scripts + xfig is the perfect combination to write papers... Especially vim; once you start with it you cannot avoid to map everything, ab etc and you miss these features when you're on a terminal, surfing etc...

---

### Post by didobuntu on 2006-09-29
> **pau said:**
> Well, there is a notable exception... Nature does not supply a style  ](*,) 

As for me: vim (not gvim) + Latex + bibtex + zsh + gnuplot + shell scripts + xfig is the perfect combination to write papers... Especially vim; once you start with it you cannot avoid to map everything, ab etc and you miss these features when you're on a terminal, surfing etc...

Yesss .. add also pstoedit to convert postscipt files into fig files and there you can easily add comments and more ...

When using LateX for EPS figure .. there is the PSFRAG package which renders very beautifully

---

### Post by Orestes on 2006-09-30
Hi,

I'm currently using LaTeX and gedit, and I have a small problem. My University requires me to use Harvard style referencing. I found a module, but because ubuntu likes to mess with standard install directories :p , I've got no idea on how to configure it. I have to come up with ubuntu-ified versions of these directories:
```

prefix=/opt/TeX
texlib=$(prefix)/lib/texmf
bstdir=$(texlib)/bibtex/bst/harvard
stydir=$(texlib)/tex/latex/local
docdir=$(texlib)/bibtex/doc/harvard
htmldir=/people/archsci/archsci-www/utils/latex2html/styles

```

So far, I've come up with:

```
prefix=/
texlib=/var/lib/tex-common/
bstdir=/usr/share/texmf/bibtex/bst/
stydir=/usr/share/texmf/tex/latex/
docdir=/usr/share/doc/
htmldir=/usr/share/doc/

```

Which doesn't work.

Does anyone know how I can either install this package or find another way to use the harvard referencing style?

Many, many thanks in advance for your help.

---

### Post by kleeman on 2006-09-30
This might be useful:

[http://jo.irisson.free.fr/bstdatabase/faq.html](http://jo.irisson.free.fr/bstdatabase/faq.html)

---

### Post by Nonno Bassotto on 2006-09-30
If you don't want to use Kile (which is heavily KDE based) there's also TeXmaker (by the same author, I think) which is a bit more lightweight. Unfortunately the version in the repos is a bit buggy. :(

---

### Post by Orestes on 2006-10-01
> Unfortunately the version [of texMaker] in the repos is a bit buggy. 

Isn't it just? The thing that annoys me is the way it can't handle some directory structures - it won't run LaTeX in the directory you're working in. It means that if I want to use it, I have to run it combination with an Xterm to run latex/pdflatex &c.

---

### Post by Old Jimma on 2006-10-01
Y'all:

Here is my opinion:

I used LaTex for years and years and then became employed in  a Federal agency that mandates that all manuscripts of any type be writen in Word. You might argue with this and think it is stupid, but that is the world as it is.

So, I began writting manuscripts in Word. There is one HUGE advantage of Word to LaTex: you can share the document with the rest of the world. You can argue that Word stinks, but that advantage is a huge advantage that, in my experience, and has outweighed every advantage LaTex has to offer. Try sharing a LaTex file with a random person, and ask them to add their comments in the text (external review and revision is a part of the scientific process). You'll see what I'm talking about.

So, as unpopular this opinion is, I feel that is worth expressing to the the contributors to this thread. It is something to think about.

The problem, as I see it is that OpenOffice is nice, but an underperformer when it comes to development of scientifc manuscripts that need to be shared with the rest of the world. As another writter in  this tread suggested, it is time for OO developers to think about this and enhance OO to include this as a powerful tool for scientific communication with the rest of the world. Otherwise, OO is a somewhat limited, albeit free, tool.

I'm thankful for OO. However, I hope that OO developers will think about this.

Sincerely,
Phil Smith
Duluth, GA

---

### Post by kleeman on 2006-10-01
> **Phil Smith said:**
>  There is one HUGE advantage of Word to LaTex: you can share the document with the rest of the world. 

The problem, as I see it is that OpenOffice is nice, but an underperformer when it comes to development of scientifc manuscripts that need to be shared with the rest of the world. As another writter in  this tread suggested, it is time for OO developers to think about this and enhance OO to include this as a powerful tool for scientific communication with the rest of the world. Otherwise, OO is a somewhat limited, albeit free, tool.

I'm thankful for OO. However, I hope that OO developers will think about this.

Sincerely,
Phil Smith
Duluth, GA

It depends who you are collaborating with. I write papers with lyx which is a latex frontend and share with coauthors who use latex. No problem there. I also set homework exercises for an undergrad Math class and a lot of them want Word format. I use Abiword for this as it's a lot less sluggish than OO.

---

### Post by dwight on 2006-10-01
> **Phil Smith said:**
> Y'all:
 There is one HUGE advantage of Word to LaTex: you can share the document with the rest of the world. 

Why do you assume that the rest of the world uses MS Word? Sure, if your agency has decided "We use Word" then everyone there will be able to read and edit what you send out, but how can you make the generalization from your agency to the entire world? I know people who have set up their mailboxes so that mails with attached doc and xls files are rejected. So you certainly couldn't share your papers with these people. 

Anyone I want to share my files with will usually have no problems with Latex.  You mentioned "trying to share a latex file with a random person". Why would you do this? Do you share your .doc manuscripts with people you meet at the supermarket? I doubt that. One is more likely to share documents with co-workers and people in the same field who are very likely  to have similar tools available to them. So while in your office people have Word in mine they have Latex.

---

### Post by Nonno Bassotto on 2006-10-01
> **Orestes said:**
> Isn't it just? The thing that annoys me is the way it can't handle some directory structures - it won't run LaTeX in the directory you're working in. It means that if I want to use it, I have to run it combination with an Xterm to run latex/pdflatex &c.

I don't know. This always works for me. The bug I'm referring to is the fact that it highlights random lines while you're writing. Better, it highlights the line you're writing, but then it keeps it highlighted, until you scroll it out of the screen.

---

### Post by rplantz on 2006-10-04
> **dwight said:**
> You mentioned "trying to share a latex file with a random person". Why would you do this? Do you share your .doc manuscripts with people you meet at the supermarket? I doubt that.

I think that Phil exaggerated and that you took him a little too literally. :) Let's face it, in most fields, chances are better that a co-worker will know Word than know LaTeX.

Having said this, a couple of years ago I converted a textbook (on assembly language) I am writing from Word to LaTeX. I was new to LaTeX, and there was quite a learning curve for me. It was well worth the effort! Every minute I've spent learning LaTeX has paid off in productivity, plus it has produced a much more professional book.

When it was still in Word, every time I updated my book, I spent most of my time trying to correct formatting problems. I never did get it to behave completely right.

Learning how to format things in LaTeX has also taken a lot of my time. The difference is that I can eventually figure out how to get things done the way I want. With Word, the best I could do is get things close, then hold my breath while I printed the book. It usually took several printings to get a master copy that was kinda close. (This is a 400-page book, and we print 25 - 50 copies at a time.)

One mistake I made early on was thinking I could learn enough online. I finally bought two books -- "Guide to LaTeX, 4th ed." by Kopka and Day, and "The LaTeX Companion, 2nd ed." by Mittelbach and Goossens. I wish that I had bought them much earlier. They make it a lot easier to find how to do something when I get stuck.

My current LaTeX project is learning how to use the beamer class. I'm giving a talk in a couple of weeks, and beamer has allowed me to produce a pdf file that is my presentation.

Since I'm now retired, I get to choose my toys, and Word is not one of them. As for collaboration, I also get to choose my playmates. :)

---

### Post by maubp on 2006-10-05
> **it.henrik said:**
> gedit + latex + dvipdf -> great papers :)
I like pdflatex better, it lets you have hyperlinked tables of contents etc.

Personally, I like using latex for papers - but the big issue is that very few journals outside of maths and physics will accept it.  For the most part, you have to supply word documents :(

---

### Post by Nonno Bassotto on 2006-10-05
> **rplantz said:**
> I think that Phil exaggerated and that you took him a little too literally. :) Let's face it, in most fields, chances are better that a co-worker will know Word than know LaTeX.


It depends. I'm a mathematician. In my field chances are faaaaaaaaaaar better that a coworker will use TeX or LaTeX, rather than Word. At least if you want to do something more complex than a letter.

---

### Post by junglepeanut on 2006-10-07
I remember the first HW assignment for my graduate classical mechanics course I spent hours trying to get just right as my professor wanted professional looking papers (i.e. not hand-written.) So I used MS Word and turned in the worst looking document in the whole class. My professor took me aside and asked me why I didn't use LaTeX, I had just heard of it was my response. Needless to say my next assignment (plus many hours of reading) turned out very nice. Now, I hate using anything else.

Recently, my wife did her thesis..in MS Word on a Mac. Ugh, we had so many issues, but we were able to work it out, as thankfully there was no math in the document. But getting the formatting correct was not easy. I was going to LaTeX it for her, but the school actually only wanted word. I was stunned as I had come to the conclusion that anything professional had to be done in LaTeX. 

I have since learned again, if you are in a science field, especially Mathematics or Physics, you probably can only turn in documents in LaTeX. But outside the field it appears the world is not catching on. Oh it seems novelists use it quite a bit too.

I love LaTeX.

---

### Post by unfknblvbl on 2006-10-09
You can share LaTeX with the rest of the world easier via PDF or its TEX file than you can with word. Why?

1) LaTeX is free to download so you need no $$ to get it, where as MS word is not, but it has free alternatives.

2) For MS word users, LaTeX's installation on windows is very easy (MikTeX + TexnicCentre), so no brains are required. Its installation on Ubuntu is even easier than windows installation.

3) The size of the TEX and PDF files in general are far, far, far smaller in size than word documents.

4) After using word for 5 years and then using LaTeX for the other 5 years, I have found that what I do on one computer with LaTeX looks the same when I do the same thign on another computer. This cannot always be said for word.

5) I have used many different equation editors and nothing comes close to the power and beauty of LaTeX.

I don't dislike MS word, it is good for some stuff, but nothing compares to LaTeX.

EDIT:
You can also use LaTeX in perfect combination with METAPOST/METAFONT to produce some beautiful graphics in your LaTeX documents. Now one step higher than METAPOST is Asymptote ([http://asymptote.sourceforge.net/](http://asymptote.sourceforge.net/)) which I am currently learning and from their website you can see its very powerful. It does very nice graphs of functions that fit very nicely into LaTeX.

---

### Post by shoagun on 2006-10-21
Hi,

I thought I'd just let everyone know that, thanks to the input you all have given, I've been happily using LaTeX to write my papers and such.  I use TeXmaker, and it's been working really well for me, and it let me get started right away and learn all the basic/essential commands.  

The only problem I've had is that sometimes I want to insert hand drawn figures, and I've yet to find any good program form drawing (I've tried dia, Gimp, Xpaint, etc).

---

### Post by junglepeanut on 2006-10-22
I like to just "hand draw" them and then scan them in, I especially suggest this for thesis work, because when you really have time you can go back and make nice computer drawings. 

Otherwise I like OpenOffice Presentation or OpenOffice Drawing (very similar), if you have ever used MS Powerpoint to make your drawings, you will feel very at home in these environments.

I think "the Gimp" is good to but I start to get side tracked playing with all of the effects it has.

---

### Post by ekarni on 2006-10-23
Lately I've been using *ipe* for making simple drawings.  It's a lightweight vector drawing program that's in the repositories.  You might also look at *xfig* (also from the repositories) or *jpicedt* from [http://jpicedt.sourceforge.net/]("http://jpicedt.sourceforge.net/").  I haven't played with either one much, but they appear to offer a few more features.

---

### Post by dwight on 2006-10-24
I've been using Inkscape for creating good looking diagrams/drawings. It is capable of exporting to a plethora of formats (including ps/eps). 
Also, a good tool for having attractive text and/or formulas in diagrams is psfrag. This tool can be used to replace any text in a ps file with latex code.

---

### Post by J77 on 2006-10-25
LaTex's the only way.

Like many, I use emacs for writing stuff - Matlab for producing figures and the picture environment to implement them in my tex file.

When you have your preprint ready, download the journal's cls/sty files and you're away.

For presentation, I use:

latex foo.tex
dvips -Ppdf -G0 foo.dvi
ps2pdf -sPAPERSIZE=a4 foo.ps

Sorted 8)

(xfig for simple schematics)

---

### Post by Julolidine on 2006-10-28
The *only* sever advantage of Word of LaTeX is the editing mode.  I understand you can do a 'compare' with LaTeX, however, the ability to see everyone's notes and potential revisions is invaluable.  I usually have 2-3 professors in different fields, along with some other collaborators revising a paper.  

I much prefer to do everything in LaTeX, but unfortunately, this is not possible....I just try to integrate the two as much as possible.  I've tried some ps/pdf to doc converters, but they all suck.  I personally can't stand laying out figures in Word.  The spacing is never correct...

---

### Post by dmt195 on 2006-11-07
Unfortunately Word is used a lot in my work place and TeX is often seen as a backward step (even from some that have used it previously). Our reports need to be submitted in .doc and many people need to review them.
I'm writing a thesis using LaTeX at the moment and do prefer using it. Without the reference handling I would be in a bad place!
I use TeXnicCenter + MikTeX + JabRef, dabble with LyX, TeXmacs, etc. I would love to my work machine over to Edgy and use Kile + teTeX:)

---

### Post by boban on 2006-11-08
Hi!

I posted this in separate thread... but I got no anwser - maybe it wasn't notice... 

I have a problem with Kile and aspell under Ubuntu (Edgy)... I have installed dictionary for my language via aptitude (aspell-pl), but when I choose Tools->Spelling I got: "I(A)Spell could not be started.".

Aspell works when triggered directly from command line (aspell check filename).

---

### Post by Steveire on 2006-11-08
Not too useful to you, but I can tell you it works for me.
```

stephen@ubuntu:~$ aptitude search kile aspell | egrep '^i'
i A aspell                          - GNU Aspell spell-checker
i A aspell-en                       - English dictionary for GNU Aspell
i   kile                            - KDE Integrated LaTeX Environment
i A libaspell-dev                   - Development files for applications with GN
i   libaspell15                     - GNU Aspell spell-checker runtime library

```
Does it work through kate/kwrite etc?

---

### Post by boban on 2006-11-08
> **Steveire said:**
> Does it work through kate/kwrite etc?

I forgot to mention that I use Kile from Gnome... but aspell works invoked from command line... Hmm... Maybe there is some configuration file I have to change to point Kile to aspell (though in GUI settings I didn't find anything)...

---

### Post by Steveire on 2006-11-08
Hmmm. I don't know. Kile might too quite tied in to KDE to allow you to use that feature so. Install kwrite and see if you get spell checking through that. Install kate too. It might be that there's something in the kate part which is needed for the spell-checking.

---

### Post by boban on 2006-11-09
> **Steveire said:**
> Hmmm. I don't know. Kile might too quite tied in to KDE to allow you to use that feature so. Install kwrite and see if you get spell checking through that. Install kate too. It might be that there's something in the kate part which is needed for the spell-checking.

Thanks for your help... I found another way to check spelling directly from Kile... I installed ispell - and with ispell Kile works... But still - Kile should be ok with Gnome...

---

### Post by Eric_T on 2006-11-09
I use ViM 7.0 with latex-suite. It has a lot of great options for producing LaTeX code quickly.
For plotting, I use Matlab together with LaPrint, a nice little program to convert your matlab figure to eps and generate a .tex-file with ticks, legends and captions(using psfrags). For diagrams etc I use mainly xfig, with a script called figtex2tex, that again uses psfrags to translate all the text and numbers to tex-code. 
Very nice for getting a consistent look on your entire paper(which, IMO, is really important).

For presentations, I use the beamer-package with LaTeX.

---

### Post by roderikk on 2006-11-10
I also use bazaar (bzr) to do my version control and keep track of changes. Really helpful and easy to use to create a backup on my webserver.

---

### Post by adamkane on 2007-01-29
Use the TeXmacs frontend to Maxima and gnuplot.

TeXmacs + Maxima:
[http://arxiv.org/html/cs.SC/0504039](http://arxiv.org/html/cs.SC/0504039)

TeXmacs + gnuplot:
(See section 4. Graph Gallery)
[http://www.texmacs.org/tmdoc/examples/casdoc.en.html](http://www.texmacs.org/tmdoc/examples/casdoc.en.html)

However I don't think TeXmacs is UTF-8 enabled.

---

### Post by Toufik on 2007-01-31
Solution for Aspell and Kile working on GNOME :
[http://www.ubuntuforums.org/showpost.php?p=1872461&postcount=5](http://www.ubuntuforums.org/showpost.php?p=1872461&postcount=5)

Writing LaTeX equations in an OpenOffice document (writer and impress):
[http://www.ubuntuforums.org/showthread.php?t=334218](http://www.ubuntuforums.org/showthread.php?t=334218)

---

### Post by cinnabar on 2007-02-02
deleted

---

### Post by ahmatti on 2007-03-16
> **Phil Smith said:**
> 

So, I began writting manuscripts in Word. There is one HUGE advantage of Word to LaTex: you can share the document with the rest of the world. You can argue that Word stinks, but that advantage is a huge advantage that, in my experience, and has outweighed every advantage LaTex has to offer. Try sharing a LaTex file with a random person, and ask them to add their comments in the text (external review and revision is a part of the scientific process). You'll see what I'm talking about.



When you make pdf's out of latex you can share them with anyone and they look the same in all computers unlike MS office documents. And at least the journals I am publishing in anyway need a pdf for the reviewing process...

I recently started writing my papers in latex because I got tired trying to get proper format with MS office or Ooffice. I use Matlab for creating my figures and I get great output with eps files. Have you tried to add eps file to MS word document :lolflag: 

Unfortenately I publish in Agricultural engineering and veterinary science journals and not all of the them accept Latex. :( It is possible to use latex2rtf to produce files for such journals, but I find it doesn't do a very good job in converting equations.

For me also the only good thing in MS office compared to latex is the feature for tracking changes and making comments. I also like to use the comments feature in Adobe acrobat pro so I can comment pdf's without printing 'em. **Does anyone know a free software (with a gui) that can add comments to pdfs or ps files?** That would be really great!

---

### Post by ahmatti on 2007-03-16
> **ahmatti said:**
> . **Does anyone know a free software (with a gui) that can add comments to pdfs or ps files?** That would be really great!

I'm quoting my own post here, but I just discovered flpsed [http://www.ecademix.com/JohannesHofmann/flpsed.html](http://www.ecademix.com/JohannesHofmann/flpsed.html). You can add comments to pdfs with, excatly what I need. I compiled v. 0.39 from source and it works perfectly :)

---

### Post by raja on 2007-03-24
I think those writing for Physics or Math journals underestimate the difficulties of trying to use Latex in other fields. I write for medicine journals and almost all of them will only accept .doc or .rtf files. Also, in order to allow my co-authors to review and edit my manuscripts, I have to stick to word documents. Even attempts to switch to openoffice are frustrated by minor incompatibilities with word (not ooffice's problem, I know).

---

