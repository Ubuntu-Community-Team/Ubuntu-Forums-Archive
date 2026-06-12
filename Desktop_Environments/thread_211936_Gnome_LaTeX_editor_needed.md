---
title: "Gnome LaTeX editor needed"
date: 2006-07-09
forum: Desktop Environments
---

### Post by tibbe on 2006-07-09
Could someone recommend me a good LaTeX editor for Gnome? More specifically I would like an editor that resembles Rhythmbox, Gedit and other Ubuntu/Gnome applications in terms of interface and usability.

---

### Post by Rui Pais on 2006-07-09
hi,
give a look at texmacs and lyx (not sure about this one but i thing it edits LaTeX too).

---

### Post by Spie on 2006-07-09
LyX and TeXmacs are WYSIWYG editors. Are you looking for that?

For editing LaTeX source, try TeXmaker. Not from the repositories (with Qt libraries), but the static binary from the [site]("http://www.xm1math.net/texmaker/download.html") (without Qt libraries). This is the best I could find, but I also miss a real Gnome-like application.

---

### Post by asimon on 2006-07-09
AFAIK there is no real LaTeX editor which uses Gnome libraries. The best LaTeX editor in my opinion is [Kile](http://kile.sourceforge.net/), but the mentioned Texmaker is very similar and has no dependency on KDE. If you are fanatically and only want to use Gnome apps then you have probably to use gedit. I suppose it does at least syntax highlightning.

---

### Post by tibbe on 2006-07-09
I probably should have mentioned that I don't want a WYSIWYG editor. At the moment I'm looking into using GEdit together with a LaTeX plugin. Also, since TeTeX is no longer maintained at source I'm unsure if I can wait for TeXLive to be available or if I should install TeTeX and later remove it.

---

### Post by leeyee on 2006-07-09
Well, why not gedit? I think it's a good choice for you, especially its markup language views. To be honest, I don't like extra applications....
This is, of course, my own opinion.

---

### Post by neoflight on 2006-07-09
i have used texmaker. its a good one.

i have also used kile (compiled from source...but it needs several KDE stuff)...

Gedit can be made to use for latex editing. emacs is another option. Vi is also used....

---

### Post by chajuram on 2006-07-09
I like kile a lot. but gedit or emacs should be the one for you. 

Chajuram.

---

### Post by Wolki on 2006-07-09
A full LaTeX plugin for gEdit is soemthing the devs want for quite some time... If you're interested in writing it, I'm sure it'd be appreciated :)

However, there are some gtk-based LaTeX editors:
AmyEdit:
[http://amyedit.sourceforge.net/](http://amyedit.sourceforge.net/)
WineFish:
[http://winefish.berlios.de/](http://winefish.berlios.de/) (berlios seems to be down right now, but should hopefully be up again soon)

I have not used either of them, unfortunately, so I can't tell you how good they are.

---

### Post by tibbe on 2006-07-09
There's a guy who has started working on a LaTeX plugin for GEdit, I'll see if I can lend him a hand. Basically what I need is syntax highlighting plus the ability to see the results (i.e. the generated PDF) in the editor (you, a preview window/tab kind of thingy).

---

### Post by Wolki on 2006-07-09
> **tibbe said:**
> Basically what I need is syntax highlighting plus the ability to see the results (i.e. the generated PDF) in the editor (you, a preview window/tab kind of thingy).

Hm, it should already do syntax highlighting.

Not sure about embedding a pdf renderer in gedit... then again, I quite like evince, and with the external actions gedit plugin, creating a "preview in evince" menu entry in gedit shouldn't be that hard.

---

### Post by Fredo on 2006-08-25
I tried out both. Personally, I didn't like Winefish at all. Maybe it has good features, but it did't invite me to try them out.

AmyEdit looks very good, very clean, fast. It has syntax highlightning and a "Preview" button, which runs (pdf)latex and opens your favorite document viewer. It is not that feature rich (no structure browser or such things), but that's not it's point. It is good for Ubuntu, and perfect for Xubuntu, I would say ;-)
Nevertheless, it still has some bugs (doesn't open files in any other encoding than UTF-8, for example), and the development is currently a one man's job.

Do some polishing and build a deb-Package, and it would be a really good LaTeX-Editor for (X)Ubuntu.

---

### Post by dada1958 on 2006-08-25
I'm using Gedit as LaTeX front-end editor right at this moment, I wrote about it in this forum earlier, I really do love Gedit ...

---

### Post by Spie on 2006-09-30
I recently switched from TeXmaker to gEdit with the LaTeX-plugin and it is just perfect!

---

### Post by Fredo on 2006-09-30
I didn't know there is an explicit LaTeX-plugin for gEdit. Until now, I helped myself out with the external-tools-plugin. Where can I get that LaTeX-plugin?

---

### Post by JGuru on 2006-09-30
**gedit** editor is a good one for basic tasks. Unless you want anything
 more sophisticated.

---

### Post by arkangel on 2006-09-30
[Texmaker]("http://www.xm1math.net/texmaker/shots.html") is a good option  , it has several  tools  and shortcuts and it is easier to use, the learning curve is fast 

gedit too  but you need a plugin and it doesnt do what texmaker can do, i like the autocompletion feature in gedit though.  Texemacs  well i never tried , and i will never try ...;)

---

### Post by arkangel on 2006-09-30
> **Fredo said:**
> I didn't know there is an explicit LaTeX-plugin for gEdit. Until now, I helped myself out with the external-tools-plugin. Where can I get that LaTeX-plugin?

[here ]("http://live.gnome.org/Gedit/LaTeXPlugin") or [here]("http://www.michaels-website.de/latex.html")

---

### Post by dada1958 on 2006-10-08
That LaTeX plug in for Gedit looks very nice. It requires rubber for compiling the source files. When I installed rubber it also put teTeX on my system so that is used instead of my TeXLive 2005. How can I set the path in rubber to TeXLive?
TIA

---

### Post by der_joachim on 2006-10-09
LyX has both a QT and GTK frontend.

---

### Post by CancelloCornorosso on 2006-10-23
Actually I'm using the LaTeX-plugin for gEdit + rubber. They work fine, but I'd like to try out Winefish as well. The problem is that I use texlive and Winefish requires to install tetex.
Does anyone know a way to use winefish with texlive?

thanks

---

### Post by Nonno Bassotto on 2006-10-24
I'm using Gedit with the LaTeX plugin, and I'm fine. The only problem I experience is that when I compile a DVI it opens in XDvi rather than Evince. Does anybody else experience this problem or know how to fix it?

---

### Post by dada1958 on 2006-10-24
> **CancelloCornorosso said:**
> Actually I'm using the LaTeX-plugin for gEdit + rubber. They work fine

The rubber in the Edgy Eft repositories also requires teTeX, is there a way to install it without?

---

### Post by dada1958 on 2006-10-25
Ok, I installed rubber from the tar.gz, not that hard but how do I get it working with my regular TeXLive2005?

---

### Post by Spie on 2006-10-28
If you first install TeXlive and after that Rubber, then Rubber doesn't complain that it needs TeTeX.

---

### Post by dada1958 on 2006-10-29
That's right, rubber doesn't do anything but showing that box that it is compiling the source to PDF :(

---

### Post by juniper on 2007-03-14
i have been searching for this for a while, but now dice.  i found gedit and winefish all severely lacking.  i am a gnome user and i have to say that kile is by FAR the best ide for latex in linux.

i currently use gvim and latexsuite.  if you are comfortable with vim, this is probably your best bet.

---

### Post by AtrejuT on 2007-04-07
well, you can compile winefish from source (which is not really difficult) to circumvent the tetx-requirement.

---

### Post by weak_solution on 2007-04-09
I am running edgy amd64 and have installed TeTeX.  I am very, very new to Linux.  I tried to install the aforementioned LaTeX plugin for gedit by extracting the LateXPlugin-20061231.tar.bz2 file to /usr/lib/gedit-2/plugins.  The plugin now appears in the gedit preferences window, but I cannot activate it.  Can anyone help me get this plugin working?

Also, I was wondering if texmaker will run on the amd64 edgy?  The download says it is for the static i386.  If it is possible to run texmaker on edgy amd64, then I would really appreciate a quick how-to for texmaker installation.

I am trying to elliminate Windows from my life, but I need LaTeX, and I am afraid that I am addicted to WinEdt.  I think that either of these Linux editors will work for me, if I can get them running.

---

### Post by dada1958 on 2007-04-09
I have the Gedit LaTeX plug-in running with Feisty x86-64, to get it running can be a pain, you have to get the LaTeXPlugin folder out of the LaTeXPlugin-20061231.tar.bz2_FILES one.
TeXMaker is in de Feisty repositories so I suggest you to upgrade asap ...

---

### Post by weak_solution on 2007-04-09
Thank You.  It seems I had properly extracted the folder and doc, but had put them in the wrong place.  Didn't know that ./gnome was hidden.  

The LaTeX plugin is now working, but I need in install rubber next. I have downloaded rubber-1.1.tar.gz.  I have read the installation instruction in the ReadMe file.  My question is :  Where do I extract the .tar.gz file to install?  Does rubber need to be installed somewhere in LaTeX?

---

### Post by kikuhi on 2007-04-09
Try Geany ([http://geany.uvena.de)](http://geany.uvena.de)). This is cool one.
-KiKuHi

---

### Post by dada1958 on 2007-04-09
> **weak_solution said:**
> Thank You.  It seems I had properly extracted the folder and doc, but had put them in the wrong place.  Didn't know that ./gnome was hidden.  

The LaTeX plugin is now working, but I need in install rubber next. I have downloaded rubber-1.1.tar.gz.  I have read the installation instruction in the ReadMe file.  My question is :  Where do I extract the .tar.gz file to install?  Does rubber need to be installed somewhere in LaTeX?

Extract the tar.gz in your home folder and follow the instructions in the README file.

---

### Post by weak_solution on 2007-04-09
Thanks again.  Its working. :) 

I just wanted to say that I installed edgy 3 days ago (my first Linux experience).  I have now successfully installed the driver for my ATI x200M graphics card, Beryl, Firefox32, teTeX, gedit LaTeX plugin, and rubber.  

It has been frustrating and required intense learning.  I could not have done it without the Ubuntu community.  THANKS!

---

### Post by Iljo on 2007-06-04
Hi to all, I am new here, just registered.. I was looking for good TeX editor and after surfing around came to this forum which helped me, thnx. 
> **Nonno Bassotto said:**
> I'm using Gedit with the LaTeX plugin, and I'm fine. The only problem I experience is that when I compile a DVI it opens in XDvi rather than Evince. Does anybody else experience this problem or know how to fix it?
It bothered me too, I like simple Evince so... After I realized it had nothing to do with default dvi viewer in gnome I thought there must be something in source code. And it is, but you don't have to compile anything. Ok here it goes...

In file ~/.gnome2/gedit/plugins/LaTeXPlugin/backend.py go to line that says (line number 239 in my version):
```
os.system("xdvi -unique -s 6 -bg white -editor %s \"%s.dvi\" &" % (DBUS_INCANTATION, self._filenameTrunc))
```
and just replace that line with:
```
os.system("evince \"%s.dvi\" &" % self._filenameTrunc)
```
Save that file and run Gedit again, it should work.

Oh... I am using Ubuntu feisty and F6 does not work for me when I want to compile tex to pdf so I changed my shorcut to something that works. If anyone is interested it is done just like previous problem I had. Take a look in file ~/.gnome2/gedit/plugins/LaTeXPlugin/__init__.py if you want to change that too...

---

### Post by danomatika on 2007-06-30
gedit works great for me.  I have the latex plugin installed, but don't really use it all too much.  Once you know the various tags, you don't use the gui as much but I do like the auto completion.

One thing I noticed was it didn't seem to run my .bib files through bibtex so I instead created a set of custom commands for gedit that I use instead of the rubber plugin stuff.

Just go to Tools->New and add them this way:

Latex to PDF
```
[LIST]
[*]**Description:** latex to pdf (no bib)
[*]**ShortCut Key:** I use CTRL t
[*]**Commands:**
pdflatex $GEDIT_CURRENT_DOCUMENT_NAME
evince ${GEDIT_CURRENT_DOCUMENT_NAME%\.*}.pdf
[*]**Input:** Current document
[*]**Output:** Display in bottom pane
[*]**Applicability:** local files only
[/LIST]
```

Then I have a second command at Ctrl B that runs the same as above but also uses bibtex:
```
**Commands:** 
pdflatex $GEDIT_CURRENT_DOCUMENT_NAME
bibtex ${GEDIT_CURRENT_DOCUMENT_NAME%\.*}
pdflatex $GEDIT_CURRENT_DOCUMENT_NAME
pdflatex $GEDIT_CURRENT_DOCUMENT_NAME
evince ${GEDIT_CURRENT_DOCUMENT_NAME%\.*}.pdf
```

$GEDIT_CURRENT_DOCUMENT_NAME is a gedit enviornment variable of the open document name and ${GEDIT_CURRENT_DOCUMENT_NAME%\.*} is the same minus the extension.

Basically, when you run either command (or gedit " tool") it creates a pdf and automatically opens it in evince.  Any errors will show up in the shell output bottom pane so hit Ctrl F9 to open it.

As I do some coding, my setup is a bit more gui-less using only the gedit syntax highlighting and plugin auto completetion.

---

### Post by bgturk on 2007-10-09
I just installed the LatexPlugin by untarring it into ~/.gnome2/gedit/plugins/ and it seems to work, however I am missing the auto completion feature. Is anybody else experiencing this problem?

---

### Post by jseligma on 2008-01-02
For anyone finding this thread when trying to troubleshoot the use of rubber with gedit + LaTeX plugin (as I did), note that there is a known bug when using rubber with files whose path contains a space:
[https://bugs.launchpad.net/ubuntu/+source/rubber/+bug/122489]("https://bugs.launchpad.net/ubuntu/+source/rubber/+bug/122489")

This link contains a link to a [patch]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=364420")  by Wouter Bolsterlee, which (on my system) had to be applied to 
/usr/share/rubber/rubber/rules/latex/__init__.py

---

### Post by mohbana on 2008-02-02
i used to use [http://www.latexeditor.org/](http://www.latexeditor.org/) on windows, i currently use Kile until a decent gnome implementation is released, by teh way kile is waaay better hardly any configuration work on my end.

---

### Post by keredson on 2008-04-11
try [http://desigle.org/]("http://desigle.org/").

---

### Post by itaylor on 2008-04-15
Looks promising. The preview is very nice. Do you have plans for further development or interest in suggestions for additional features? A "recent files" list in the file menu would be convenient, for instance.

---

### Post by keredson on 2008-04-16
itaylor:
yep. looking for input.  (and "recent files" has just been added)

---

### Post by Oliver W. on 2008-06-17
I've been using [TeXlipse (http://texlipse.sourceforge.net/)]("http://texlipse.sourceforge.net/") for some time now. It needs Eclipse of course, so it's not standalone like Kile (which is an extremely nice app - if you don't mind the KDE-libraries).

Just another pointer. ;)

---

### Post by redseventyseven on 2008-07-15
> **keredson said:**
> try [http://desigle.org/]("http://desigle.org/").
Looks promising! I had a bit of trouble compiling the poppler-python package, but the comments to this post from one of your other projects helped enormously.

[http://code.google.com/p/gpapers/wiki/Installation](http://code.google.com/p/gpapers/wiki/Installation)

---

### Post by xen on 2008-07-22
The 0.6 version of python-poppler doesn't seem to exist anymore. Anyone got any ideas where I can get it?

Cheers

---

