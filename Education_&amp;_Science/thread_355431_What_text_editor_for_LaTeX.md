---
title: "What text editor for LaTeX?"
date: 2007-02-07
forum: Education &amp; Science
---

### Post by Zdravko on 2007-02-07
What text editor can you recommend me for writing a book? I already decided to use LaTex. The editor should also have a Windows version :KS

---

### Post by ssam on 2007-02-07
must it be the same editor in windows as linux?

gedit is a good simple editor in linux (its the ubuntu default text editor). it has spell checking and syntax highlighting.

---

### Post by parktownprawn on 2007-02-07
Well its a matter of taste. Do you want a  semi-wysiwyg interface like lyx or would you prefer something like emacs? 

I know both emacs and lyx run on windows.  A few years ago (the last time I actually used windows to do any work) I remember setting up lyx on windows was a bit irritating but things may have changed.

I've just started using the latex plugin for eclipse (texlipse) as my latex editor and I think its pretty good. Eclipse being java based will run on many platforms

---

### Post by parktownprawn on 2007-02-07
another option is texmaker which apparently runs on windows and linux

---

### Post by parktownprawn on 2007-02-07
instructions for setting up emacs and latex under windows:

[http://www.math.aau.dk/~dethlef/Tips/introduction.html](http://www.math.aau.dk/~dethlef/Tips/introduction.html)

---

### Post by boz on 2007-02-07
I like SciTE.  You can install it from the repositories and you can install a windows version.  [http://www.scintilla.org/SciTE.html](http://www.scintilla.org/SciTE.html).  Just pick the language you want to use.  TeX is available as an option.  When you're in Linux, though, gedit is just fine.

---

### Post by Typhoon on 2007-02-07
It depends on what you are writing. If it is a novel or something that is straightforward text, it simply does not matter much.

If you need to include indexing and a bibliography, then you want something that helps with these tasks. LyX does a pretty good job this way: it can help you find bibliographic references in a Bibtex database, and the index structure is OK.

I write legal texts that require multiple indexes (at least three: regular index, table of cases and table of statutes). The texts have *lots* of cross-referencing. For this, I haven't found anything that offers as much support as Emacs + Auctex + Reftex. There is also a "folding" mode that hides the latex markup if you like. The resulting screen is as readable as LyX.

There is also a good outlining feature with Auctex that gives you a lot of organising power.

HTH,
Typhoon

---

### Post by samden on 2007-02-08
I am completely new to LaTeX myself as well, but downloaded LyX last week. It seems pretty good and easy to understand. I haven't tried anything else, but can say LyX is good for a beginner anyway.

---

### Post by Typhoon on 2007-02-08
LyX is good. I am self-publishing a cookbook written by my wife. I used LyX to set it up and typeset it. The book has a lot of line drawings, so the layout was more complicated than simple text, but not complicated enough to use a desktop publishing program.

Using the LyX "boxes", I was able to get quite nice layouts with little stress. It is a very good program. 

Also, the exported LaTeX coding was remarkably clean, so if you needed to deal with "real" LaTeX for some reason you could write in LyX and then export.

Cheers,
Typhoon

---

### Post by Krimi on 2007-02-10
I've written many scientifical reports with LaTeX, but in win.
I've used MiKTeX + Texnic Center..
What whould be equivalent (better :-)) in Linux to these two??

---

### Post by briansers on 2007-02-10
In Windows I've used MikTeX with WinEdt.  That combination is most similar to my preferred TeXLive with Kile.  If you want everything to "look" the same, you'll probably want to use LyX, or maybe TeXmacs.

---

### Post by Steveire on 2007-02-10
> I've written many scientifical reports with LaTeX, but in win.
 I've used MiKTeX + Texnic Center..
 What whould be equivalent (better ) in Linux to these two??

Try Kile.

---

### Post by slaanco on 2007-02-11
definitely kile :)

---

### Post by neoflight on 2007-02-11
if you use gnome i would suggest you use [texmaker]("http://www.xm1math.net/texmaker/") 

```
apt-get install texmaker
```

---

### Post by tkjacobsen on 2007-02-13
> **ssam said:**
> must it be the same editor in windows as linux?

gedit is a good simple editor in linux (its the ubuntu default text editor). it has spell checking and syntax highlighting.

Try the gedit-latex plugin with that:
[http://live.gnome.org/Gedit/LaTeXPlugin](http://live.gnome.org/Gedit/LaTeXPlugin)

---

### Post by damian.rohraff on 2007-02-18
I would also recommend Kile. I think it is the best LaTeX environment for Linux. If you know WinEdt already, it shouldn't be a problem for to to migrate :)

---

### Post by commike37 on 2007-02-18
My personal preference on Ubuntu is texlive + texmaker.

---

### Post by Mateo on 2007-02-26
the only thing about gedit is that the spell check doesn't work that well.  It thinks any word with an apostrophe is misspelled.

---

### Post by freda on 2007-02-26
In the following website [http://www.qweas.com/download/web/text_editors/ ](http://www.qweas.com/download/web/text_editors/ ) , it provides many kind of text editors, i don't know which one is optimum for you, you can have a look!

Good luck!

:)

---

### Post by ahmatti on 2007-03-16
If you wan't to use the same editor in windows and linux I'd recommend texmaker or SciTE [http://www.scintilla.org/SciTE.html](http://www.scintilla.org/SciTE.html). Scite is pretty configurable and has syntax highlighting.

---

### Post by eljalill on 2007-03-24
Since no-one has mentioned it yet, 
I just have to put in a word for winefish!
It's in the repositories, 
doesn't have much fuss, has a good spell chekc, which actually recognises commands (although not options), and has, the most important for me, a big window. No stuff around, which keeps you away from the actual document!

But you need to know how to write in Latex already for it, I gues...

PS: And the logo is the cutest of them all!

---

### Post by NikoC on 2007-03-26
Agreeing here with eljalill, I'm also using winefish which is available via repos!

---

### Post by qetuR on 2008-09-23
> **Krimi said:**
> I've written many scientifical reports with LaTeX, but in win.
I've used MiKTeX + Texnic Center..
What whould be equivalent (better :-)) in Linux to these two??

I'd say that you should install the TEX packages; texlive,-base and -common. And install Kile, Kile looks very similar to Texnic Center I'd say.

Boath in repo. Just download and have a look.

---

### Post by slaanco on 2008-09-23
vim + vim latex suite :)

---

### Post by hubie on 2008-09-23
> **slaanco said:**
> vim + vim latex suite :)

What is the vim latex suite?  I do my latex in vim but I have been too lazy to learn how to streamline it.  I still do it like I learned it oh so many years ago:  exit the editor, run latex, run one of the dvi conversion routines, then view it in the appropriate viewer.  I know there are better ways to do it, but I just stick with what I've been doing (also, I don't bother looking at the compiled product very often, so I don't need that near-WYSIWYG functionality).

---

### Post by kaspar_silas on 2008-09-23
The original poster said "I decided to use LaTeX". I guess then your not totally fluent in latex. In that case Lyx is a great option as it has a gentle learning curve. Plus you don't have to stop writing all the time to look up how to do that thing you want to do. 

That said having learnt latex now im happy to use other editors now. In fact I was playing with winefish earlier and the minimalist look is very pleasing I may switch to that for a while.

---

### Post by brunovecchi on 2008-09-25
> **hubie said:**
> What is the vim latex suite?  I do my latex in vim but I have been too lazy to learn how to streamline it.  I still do it like I learned it oh so many years ago:  exit the editor, run latex, run one of the dvi conversion routines, then view it in the appropriate viewer.  I know there are better ways to do it, but I just stick with what I've been doing (also, I don't bother looking at the compiled product very often, so I don't need that near-WYSIWYG functionality).

The vim latex suite is an ftplugin for gvim, it's in hardy's repos. It has some neat functionalities, like document templates, streamlined .tex compiling, lots of keyboard shortcuts, new menus... it also detects all the tex packages you have installed and makes them accessible to you via a nice GUI menu. Oh, and also, it has this tooltip feature when you want to add references to indexes, it shows a list of the available options.
I know it has much more, but that's all I know for now. 

Here's a link to the plugin's page: [http://vim-latex.sourceforge.net/index.php]("http://vim-latex.sourceforge.net/index.php")

---

### Post by eldragon on 2008-09-25
when i started using latex (and was clueless). i went with the editor of choice (vim) and downloaded 'the not so short introduction to latex' from the web, its the best latex reference manual ive seen. and helps you get started.

about the editor. use whatever you wish, shouldnt make a difference.

ive set up a small script to build and preview my documents:

```

#!/bin/bash
latex $1.tex
latex $1.tex
dvipdf $1.dvi
evince $1.pdf &

```

run with:
```

$ ./compile file

```
where your latex file is called file.tex

---

### Post by hugmenot on 2008-09-25
Unfortunately the latex-suite for vim is a bit undermaintained. My issue with it is that its compilation output window (i.e. quickfix list) is very poorly parsed and not pretty.
So I use latex-suite for the handy shortcuts and then simply the rubber package to compile. Rubber does a good job of cleanly extracting the important warnings and errors from the log.
Latex-suite is neat because of the shortcuts. One example is EFI, just type these letters and they will expand to a figure env with fields to fill in.

---

### Post by xadder on 2008-09-26
I also had issues with latex-suite last time I tried it. Sometimes it is magical, sometimes simple cut-n-paste causes nightmares, with added unwanted stuff(especially lots of $ signs if I remember right). I think some of the problem is the rather complex nature of vim these days, with the latex-suite needing for editing sometimes non-intuitive .vimrc and  plugin files in different directories.

These days I stick with normal vi or gedit+latex-plugin. The latter is quite nice actually.

---

### Post by ad_267 on 2008-09-28
+1 for gedit and LaTeX plugin.

---

### Post by earlycj5 on 2008-09-28
For cross-platform editing the only thing I've found that I really like is Texmaker (as mentioned above).

---

### Post by DrOlaf on 2008-09-28
I've been using emacs and auctex, mainly to prepare latex-beamer lectures. It usually works quite well, but sometimes it has me tearing my hair out and pounding my fists on my desk until they bleed. That may just be emacs though.

---

### Post by mihai.ile on 2008-11-30
Hello. This topic is quite old but I only found it now and I would like to say that I also use gedit + latex plugin and it's great!
Now I developed a plug-in myself to help a little my working experience in gEdit.

I created a split view that shows the pdf on the right side while i'm writing the .tex file. I don't really like to do ALT+TAB every time I want to see how my new paragraph looks like.

Now I tried to contact the gedit plug-in author to see if he could include this feature but didn't get any response. I wouldn't like to release the plugin as a standalone one, I see it more like an add-on to the original gedit latex plug-in.

What do you think about the idea? would you like using gedit for latex with my plug-in?

I think that the plug-in would have only one dependency for rendering pdf's from python.

---

### Post by mrgnash on 2008-12-01
Vim.

Gedit with the LaTeX plugin is superb too, though.

---

### Post by epitaph on 2008-12-01
> **mihai007 said:**
> Hello. This topic is quite old but I only found it now and I would like to say that I also use gedit + latex plugin and it's great!
Now I developed a plug-in myself to help a little my working experience in gEdit.

I created a split view that shows the pdf on the right side while i'm writing the .tex file. I don't really like to do ALT+TAB every time I want to see how my new paragraph looks like.

Now I tried to contact the gedit plug-in author to see if he could include this feature but didn't get any response. I wouldn't like to release the plugin as a standalone one, I see it more like an add-on to the original gedit latex plug-in.

What do you think about the idea? would you like using gedit for latex with my plug-in?

I think that the plug-in would have only one dependency for rendering pdf's from python.

I would really like this feature. I also get annoyed at having to continually check to see if the formatting is correct.

---

### Post by xadder on 2008-12-02
Hi miha007,

That plug-in also looks great to me. Try again with the gedit author maybe?H He/she may just have been too busy to deal with your mail.

---

### Post by mihai.ile on 2009-06-01
Oh well I finally managed to create a path for the gedit-latex-plugin so now it's easyer for the author as it should only apply my patch and that's it.

If you are interested in using the live preview in gedit latex plugin, I explained the steps over here [http://openmindedbrain.info/gedit-latex-plugin-live-preview](http://openmindedbrain.info/gedit-latex-plugin-live-preview) and you can download the patched from there plugin also.

---

### Post by xadder on 2009-06-01
Hi mihai007!

The Gedit plugin looks great, so I gave it a try.

I've downloaded and installed your plugin, and ticked the box. Still, I don 't see how to get the pdf in a side-window? What should I do to get that?
Thanks.

---

### Post by mihai.ile on 2009-06-01
do you have the plugin working in gEdit? if so, just open a .tex file and in the gEdit "LaTeX" menu  the last entry is for activating the split view.
Then just compile to pdf and the preview is updated (i use CTRL-ALT-7 shortcut which doesen't open a new window for preview after compilling)

---

### Post by kleeman on 2009-06-01
> **mihai007 said:**
> Oh well I finally managed to create a path for the gedit-latex-plugin so now it's easyer for the author as it should only apply my patch and that's it.

If you are interested in using the live preview in gedit latex plugin, I explained the steps over here [http://openmindedbrain.info/gedit-latex-plugin-live-preview](http://openmindedbrain.info/gedit-latex-plugin-live-preview) and you can download the patched from there plugin also.

Thanks that works great! Open source rocks.

---

### Post by xadder on 2009-06-01
Thanks mihai007,

I had missed that split-view option. Works great now :-)

---

### Post by amirtha on 2009-06-02
sorry i have don't know

---

### Post by meborc on 2009-06-02
i use texworks, it is program under development for texshop like interface for unix/mac/win

it is great :D

---

### Post by iopo on 2009-06-04
If you are new to latex, I will go with LyX. I wrote e few notes on it:

[http://people.bu.edu/acanidio/opensource.html](http://people.bu.edu/acanidio/opensource.html)

I think the biggest plus is that you can start using it without knowing anything about Latex. Also, since when you click to insert something you actually see the command, you will slowly learn the Latex commands.

---

### Post by spinoza666 on 2009-06-15
I second emacs with the auctex package. If you're going to write a book, learning emacs is well worth the effort, and will make you work much more efficiently. Just install emacs and auctex from the repos, and read up a bit on emacs on their website. Get the command reference card for emacs and auctex, and you are ready to go. After a couple of days, you will be latexing faster than ever before:)

---

### Post by Azrael3000 on 2009-06-15
Since I also recently switched from Win to Ubuntu I also need a new LaTeX editor. Until now I have been using the fantastic Led. Combined with JabRef for the Bibliography. Now what I really liked about Led was autocompletion and the reference list once you type \ref{ or biblist for \cite{
Is there any equivalent in Linux? Or can that be achieved in any editor?
Besides that I really don't need much, so no WYSIWYG and I get around these days with LaTeX commands, just the features above seemed handy to me.

---

### Post by mihai.ile on 2009-06-15
> **Azrael3000 said:**
> Since I also recently switched from Win to Ubuntu I also need a new LaTeX editor. Until now I have been using the fantastic Led. Combined with JabRef for the Bibliography. Now what I really liked about Led was autocompletion and the reference list once you type \ref{ or biblist for \cite{
Is there any equivalent in Linux? Or can that be achieved in any editor?
Besides that I really don't need much, so no WYSIWYG and I get around these days with LaTeX commands, just the features above seemed handy to me.

Actually the autocompletion is working in Gedit Latex plugin, give it a try and see if you like it (I suggest using the latest SVN version to be able to use the live pdf preview in split window also)

---

### Post by meborc on 2009-06-16
> **Azrael3000 said:**
> Since I also recently switched from Win to Ubuntu I also need a new LaTeX editor. Until now I have been using the fantastic Led. Combined with JabRef for the Bibliography. Now what I really liked about Led was autocompletion and the reference list once you type \ref{ or biblist for \cite{
Is there any equivalent in Linux? Or can that be achieved in any editor?
Besides that I really don't need much, so no WYSIWYG and I get around these days with LaTeX commands, just the features above seemed handy to me.

autocompletion works in texworks as well... [http://code.google.com/p/texworks/wiki/Building](http://code.google.com/p/texworks/wiki/Building)

be sure to install subversion as well for installation

---

### Post by Chronon on 2009-06-17
The LaTeX plugin for gedit seemed broken when I tried it.  I guess I should give it another go!  ;)

---

### Post by norman_ on 2009-06-24
> **Chronon said:**
> The LaTeX plugin for gedit seemed broken when I tried it.  I guess I should give it another go!  ;)

Works fine for me on 9.04

---

### Post by Azrael3000 on 2009-06-25
downloaded it yesterday, works fine indeed.

---

