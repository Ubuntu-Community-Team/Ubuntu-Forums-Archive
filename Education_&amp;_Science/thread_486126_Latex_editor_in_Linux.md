---
title: "Latex editor in Linux"
date: 2007-06-27
forum: Education &amp; Science
---

### Post by Freiburg05 on 2007-06-27
Hi there.

    I've used Latex to write my thesis, using Miktex + LeD in windows and Tetex + texmaker in Ubuntu. I'm trying now to reduce my Windows usage to a minimum, and I have a little problem here. I can't find a latex editor for Linux which equals the features of LeD in Windows. Texmaker is ok to edit files or create documents based on single files, but it doesn't have project features, or the possibilities to create documents from templates. I tried  also Kile and winefish, but I chose Texmaker over them (Kile is not much better than texmaker, and it's a KDE application -I'm using Gnome-. Winefish has still a long way to go in my opinion). 

     I tried to use LeD in Ubuntu with Wine, but the controls don't respond often and it gets hung up frequently.  


      So after this long story, this is what I would like to know:

             - If I can get properly running LeD with Wine this would be my ideal solution.
             - If not, find another editor for Linux (not WYSIWYG). I'm trying to use texclipse plugin for eclipse, and I find it pretty good, but eclipse consumes a lot of resources in my laptop so I'd rather use another solution. 


      Maybe I'm being a bit restrictive, I know, but any suggestions are wellcome. If you think I should give another chance to one of the programs above I'll glad read your reasons.

      Bye!

---

### Post by Bachstelze on 2007-06-27
I like Kile as a LaTeX editor, but it's a KDE app...

---

### Post by Freiburg05 on 2007-06-27
Hi! 
 
     Thanks for the quick replay. I'm looking for the features of last version of Kile, and it looks pretty good, maybe I'll give another try. 
     I'm also looking for the possibility to run texnicCenter in linux but in the home site they say it's quite difficult. 
     Another chance would be to use winEdt with wine, which seems to work great, but winEdt is not free, so I think I'll pass. 
     That was about editors running under Windows. But, like I said before, if not with LeD I'd rather use an editor for Linux.

---

### Post by xadder on 2007-06-28
Kile runs fine in gnome also, after a little setup. I've heard good things about auctex (for emacs fans) also, but I'm a vi user ;)

---

### Post by Freiburg05 on 2007-06-28
Thanks for the answers. 

      I have a little question about Kile. Anyone knows if you can add new templates? If yes how?

---

### Post by Freiburg05 on 2007-06-28
I think I found it.
 
       You can create new templates and they'll be stored in /home/username/.kde/share/apps/kile/templates
 
  Ok sorry for not looking for it earlier!

---

### Post by zenkaon on 2007-06-28
Hi,

I use KDevolop for writing my LaTeX, It's very good at colouring things in and tabbing sections. Plus the integrated shell means you only need one programme open. Oh, and a built in spell checker and autocomplete.

I know that you use gnome, but you can still install and use KDE apps.

---

### Post by dada1958 on 2007-06-28
Gedit and the LaTeX Plug-in is the best, for me at least :)

---

### Post by parktownprawn on 2007-06-29
Its probably over-kill but you could try texlipse ([http://texlipse.sourceforge.net/](http://texlipse.sourceforge.net/)) which is a plug-in for eclipse. (Personally I use emacs)

---

### Post by morningboat on 2007-06-29
Kile is a nice GUI choice. Personally I prefer emacs + AucTex + flyspell, since it is a very powerful editor with great efficiency. Even in windows [http://www.math.aau.dk/~dethlef/Tips/](http://www.math.aau.dk/~dethlef/Tips/) shows the way for emacs' conf.

---

### Post by Typhoon on 2007-06-29
I will add another vote for Emacs + Auctex + Reftex.

Yes, there is a steep learning curve for non-emacs folks, but Auctex gives a really good LaTeX environment. All of the essential construcs are available by keyboard and by menu. It also sets up the outliner to work well with LaTeX parts, chapters, etc. With a little effort, the outliner is almost as good as the old DOS programs like Thinktank and Grandview.

Reftex provides the indexing and cross-referencing muscle. I need multiple indexes in my writing, and I would despair without Reftex. It doesn't make indexing easy -- nothing can do that!, but it makes it bearable.

The other thing that LaTeX give me is the ability to write in numbered paragraphs as required by my publisher. Each major paragraph is of the form [Chap-Parno] and all indexing and cross-referencing is with reference to paragraph numbers.

If your needs are only slightly less demanding, have a look at LyX. It is not strictly speaking a LaTeX editor, but it is a killer app. You can work within an easy-to-use editor but have (most) of the power of LaTeX at your command. 

Cheers,
Typhoon

---

### Post by UCAP on 2007-07-02
You might want to look at Texmaker as well: [http://www.xm1math.net/texmaker/](http://www.xm1math.net/texmaker/)

---

### Post by arkanabar on 2010-07-06
You may also wish to look at this wikipedia page:  [http://en.wikipedia.org/wiki/Comparison_of_TeX_editors](http://en.wikipedia.org/wiki/Comparison_of_TeX_editors)

---

### Post by FreeTheBee on 2010-07-06
For simple stuff you can look at texworks or gummi as well. I use the first sometimes for small things, otherwise I use kile. My experience in running winedt in wine were not so good, but I haven't spent too much time on it.

---

### Post by urukrama on 2010-07-06
> **dada1958 said:**
> Gedit and the LaTeX Plug-in is the best, for me at least :)

I also recommend Gedit with the Latex plugin.

There are plenty of alternatives, though, as many have mentioned here. There are a few threads about this in this subforum, if you want more recommendations. See for example [here]("http://ubuntuforums.org/showthread.php?t=1056284") and [here]("http://ubuntuforums.org/showthread.php?t=355431").

---

### Post by matthew.ball on 2010-07-08
You could try Gummi, well it looks promising...

---

### Post by mech14 on 2010-07-09
I'm from OSX TeXShop, which is not a good novice product (despite its clean interface). After learning/using LaTeX the hard way (i.e., with TeXShop) I decided to explore.

So far, I find Kile the best option for Ubuntu/OSX (other than VimLaTeX and Aquamacs) and LEd for Windows.

Things I like about Kile:
-autocompletions
-shortcuts
-foldings
-templates
-project management
-modifiable engines (for example, I have it generate HTML and view it with one shortcut; I have is Sweave, which produces a *.tex file, and runs PDFLatex on it, and previews it all in 1 step; I'm working on having it perform Latexdiff and typeset the diff.tex right away)
-version above 2.0 has vim-editor integrated, which is nice if you use vi/vim
-color syntax
-smart error handling
-many more features that beat TeXShop hands down.

I've used LEd a bit and it seems most similar to Kile. So, I highly recommend Kile.

---

### Post by daspliff12345 on 2011-08-15
> **dada1958 said:**
> Gedit and the LaTeX Plug-in is the best, for me at least :)

Dude I have been trying for months to get the GEDIT bibtex plugin to work so I can add references without any success...any tips? It just gives ma a question mark when i compile it. Also what doc style and reference style do you use predominantly?

---

### Post by tommpogg on 2011-08-15
I recomend vim or emacs with a latex plugin.

They are hard to learn but you can use them for a lot of stuff.

---

### Post by atma on 2011-08-23
it may sound a stupid question, but is there a latex editor that allows finding and replacing in all open documents?

thank you

---

### Post by incognus on 2011-08-23
> **Freiburg05 said:**
> Hi there.

    I've used Latex to write my thesis, using Miktex + LeD in windows and Tetex + texmaker in Ubuntu. I'm trying now to reduce my Windows usage to a minimum, and I have a little problem here. I can't find a latex editor for Linux which equals the features of LeD in Windows. Texmaker is ok to edit files or create documents based on single files, but it doesn't have project features, or the possibilities to create documents from templates. I tried  also Kile and winefish, but I chose Texmaker over them (Kile is not much better than texmaker, and it's a KDE application -I'm using Gnome-. Winefish has still a long way to go in my opinion). 

     I tried to use LeD in Ubuntu with Wine, but the controls don't respond often and it gets hung up frequently.  


      So after this long story, this is what I would like to know:

             - If I can get properly running LeD with Wine this would be my ideal solution.
             - If not, find another editor for Linux (not WYSIWYG). I'm trying to use texclipse plugin for eclipse, and I find it pretty good, but eclipse consumes a lot of resources in my laptop so I'd rather use another solution. 


      Maybe I'm being a bit restrictive, I know, but any suggestions are wellcome. If you think I should give another chance to one of the programs above I'll glad read your reasons.

      Bye!

Kile or Texmaker. I prefer Kile; it works faster on my system for some reason. But others tell me Texmaker works faster on their's. You can also have a look at the lyx project. 

[http://www.lyx.org/](http://www.lyx.org/)

I know most hardcore latex users hate it, but it's checking out.

Cheers!

---

### Post by BeRoot ReBoot on 2011-08-23
I've written my graduate, masters and doctorate dissertations (in Physics) with LaTeX, on emacs. I found absolutely no lacking "project features". What are you talking about?

---

### Post by kbaumen on 2011-08-30
+1 for Vim + LaTeX plugin.
 
It's a lot faster then having a full IDE. It might seem awkward at first (if you haven't used Vim before) but then again, so does LaTeX itself if you have used WYSIWYG text editors before and still a lot of people use it.
 
Bear in mind that this is a different experience then using Kile, Texmaker or whatnot and it's purely a matter of preference which to use. But I do recommend it.

---

### Post by rojaasensei on 2011-08-31
There's a good overview of LaTex software for Linux at:

[http://www.charlietanksley.net/philtex/editors/](http://www.charlietanksley.net/philtex/editors/)

---

