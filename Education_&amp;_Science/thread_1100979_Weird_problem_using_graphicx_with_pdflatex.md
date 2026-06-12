---
title: "Weird problem using graphicx with pdflatex"
date: 2009-03-19
forum: Education &amp; Science
---

### Post by Milamber_Cubed on 2009-03-19
Hi All,

I have a LaTeX project (my PhD thesis!) that would compile (?) fine under an older version of Ubuntu but won't under 8.04. Stripping it down to it's bare minimum:

```

\documentstyle[12pt, graphicx, subfigure]{report}


\begin{document}


\include{review/review}

\end{document}

```

Produces the following error:

```

./thesis.tex:6:Paragraph ended before \@tempa was complete.

```

Removing graphicx from the list of packages or running the code through standard latex doesn't give me this problem.

The markup in review/review.tex is very basic indeed and doesn't try to import any images etc, but the full version does include a lot of PNG files, which is why I'm using pdflatex.

Any ideas on this would be really helpful as I am making changes for a re-submission and could do with being able to compile it without it freaking out. I'm not sure that this is actually causing any problems, in the output but it's making Kile refuse to continue my latex->bibtex->latex->latex->view workflow because the exit code from the first command is 1 rather than 0.

Any ideas?

---

### Post by skintythe1andonly on 2009-03-19
Hi

I usually start my documents with 

```
\documentclass{article}
\usepackage{graphicx}

\begin{document}
.....text
\end{document}
```

I'd never seen it start with \documentstyle before but according to google it works too. Try this method.... seems to work for me

---

### Post by Milamber_Cubed on 2009-03-19
> **skintythe1andonly said:**
> Hi

I usually start my documents with 

```
\documentclass{article}
\usepackage{graphicx}

\begin{document}
.....text
\end{document}
```

I'd never seen it start with \documentstyle before but according to google it works too. Try this method.... seems to work for me

I think that the way I am doing it is the "old" way, which I need to do in order to use a .sty file handed to me to ensure the document meets all the university regulations (not in the example I gave, to rule out that it was the source of the error).

I'll try it the above way, but I'm not sure if using \usepackage{name} will pickup settings from name.sty or not.


EDIT: yeah, it works BUT it messes up all of my formatting :( I am not proficient enough to start hacking through a sty file that's been built up over 30 years and porting over to the latest way of doing things.

The way I had things before should work and did work before I did an upgrade to 8.04.... hopefully a fix can be found. 

Thanks for the suggestion though.

---

### Post by hubie on 2009-03-20
Whenever I feel I can dive into an answer, I'm never on my Ubuntu machine!  I wanted to try out a few things, but I can only make some suggestions...

Anyway, it sounds like you need to roll back to LaTeX 2.09.  One thing you can try is to load the older tetex package to see if that does it.  I believe tetex was removed from 7.04 to 7.10, and from there on out the package is texlive.  If you upgraded from 7.10, then you should have been using texlive, so (and I don't know off hand how to do this), you can try rolling back your texlive package set to the earlier version.

You also mentioned that you were handed this particular sty file.  Did you get that from another student (like one of those sacred items that gets passed from one grad student generation to another , such as room keys), or did you get it from the university.  If not from the university, you can check with them to see if they have a more recent sty file for you to use.  The switch to LaTeX2e happened quite a while ago, so I would hope that the university has updated the style files.  I can't remember where my university kept the files, but there was a place where we could download style files as well as Word and Wordperfect templates.

You can also try switching to latex from pdflatex and converting all your images to eps format.  This can be done fairly straight-forwardly using the convert command from Imagemagick.  For instance, you can see an example in [this post]("http://usalug.org/phpBB2/viewtopic.php?t=13450&sid=d17a0f2d15ffd8a68ab6ab85d8825a96").

---

### Post by skintythe1andonly on 2009-03-20
I'd imagine it is probably something along the lines of a newer package misbehaving with this old style file. tbh you do not need to go down the root of latex->bibtex->latex->latex each time, you only need to bibtex if you change your bibtex file or actually add a reference, the file will still be produced using the bibtex output from the last time.

One other thing, I see you are using subfigure, I know I had that not working out for some reason last year but I cant remember what for. It may be asking a lot but does your style file work if you just use graphicx and exclude subfigures??

---

### Post by hugmenot on 2009-03-21
```
\documentstyle[12pt, graphicx, subfigure]{report}
```

I don&#8217;t believe this was ever the way to load packages. The square brackets in this line are only for optional class options like "12pt" or "twocolumn".

Use the normal \usepackage{graphicx} command for that.


EDIT: Okay I&#8217;m wrong. But according to [this page]("http://www.public.asu.edu/~rjansen/latexdoc/ltx-22.html") problems are to be expected because this usage will enable a "compatibility mode".

---

### Post by lad.kocb on 2009-03-23
I think that it would help to try to understand how TeX really works. 
Then one would not associate the problem with the Ubuntu version, 
but rather with the vesion of TeX/LateX package. The important 
change in LaTeX happened some ten years ago, going from
"documentstyle" to "documentclass" - in fact it meant the new version Latex-2e. 
The underlying TeX has not changed. In principle, all latex are tex
routines/functions/macros built over tex. From version to version 
of LaTeX there are some changes, but generally, it should all be
backward compatible. In practice, various small bugs and 
improvements are not always really compatible. In my case, I carry 
my sources between several Linux installations and the Mac OSX,
sometimes even cygwin on windows, and indeed, mostly it all works.

For your particular problem:
1. never use "documentstyle" any more. It is mainly phased out.
2. the version with brackets is basically the same as "usepackage",
   but not allways in practice. Sometimes the order might matter,
   and that you control by the order of "usepackage" commands.
3. "usepackage" is not much else than "input" of the corresponding
   class "cls" file (but keep using "usepackage")
4. You can try to use any ancient "sty" file, like e.g.   
   "thesis.sty"  
   using "  \input{thesis.sty}  " before the "\begin{document}".
   mostly it will work, if the basic class is the same.
   By this I mean: our thesis.sty was built on report.sty. 
   Thus I would use our thesis.sty with the current report class
   ( I have many old files where the graphics was (is) handled by:
     "\input{epsf.sty}" and they work with newest LaTeX versions,
     provided that I have the "epsf.sty" along with the sources)
5. To use LaTeX efficiently, some occasional look into the
   class files and style files is of great value. You gain 
   understanding of what latex (tex) is really doing

---

### Post by Milamber_Cubed on 2009-03-25
Thanks for all the suggestions, guys. Unfortunately, I'm on a bit of schedule here and can't re-implement the entire layout of my thesis!

I haven't been able to get rid of the error message, but will look into converting to eps and using standard latex rather than pdflatex.

I still find it odd that something that works fine in latex doesn't work in pdflatex, especially something so simple that doesn't even include any graphics; simply including the graphicx package is enough to cause the error. 

The latest version of latex is supposed to have backwards compatibility so that "most" 2.09 documents should compile as before, but this shows that any old documents using graphicx in pdflatex will not build properly. I have yet to figure out exactly how (i.e. if) the output is changed.... but I resent having the output tell me that there is an error of some kind!

The "error" causes the exit code of pdflatex to be non-zero meaning that any (sensible) automated build scripts would bail out. If the error really should just be a warning and nothing has changed in the output, then perhaps the labelling of this problem needs to be addressed? 

In any case, I have some things left to try and have tried some without luck... I'm thinking that the png->eps and using regular latex may be the best bet.

Thanks again!

---

### Post by mister_pink on 2009-03-26
Have you tried changing the headers to the new style and just \usepackage-ing your custom .sty file? It may or may not work, but it should be easy to find out. By using the old (and now very outdated) documentstyle you enter compatibility mode which presumably breaks graphicx.

Edit: Also, you may be disappointed with the results of converting pngs to eps files. Some things look fine, others come out looking really terrible. You can include png files when using latex using something called bmeps, but its a major major pain.

---

### Post by Milamber_Cubed on 2009-03-26
> **mister_pink said:**
> Have you tried changing the headers to the new style and just \usepackage-ing your custom .sty file? It may or may not work, but it should be easy to find out. By using the old (and now very outdated) documentstyle you enter compatibility mode which presumably breaks graphicx.


I tried this and it did not like it at all.

As I've said before, it seems that backwards compatibility for graphicx is only broken for pdflatex and not for latex. Which is pretty strange. 

> 
Edit: Also, you may be disappointed with the results of converting pngs to eps files. Some things look fine, others come out looking really terrible. You can include png files when using latex using something called bmeps, but its a major major pain.

That sounds a bit ominous.... I'll keep your comments in mind. I have a couple of weeks to play with, but want to spend as much of that writing as possible rather than messing around with TeX. :S

---

### Post by meborc on 2009-03-26
> **Milamber_Cubed said:**
> ...I have a couple of weeks to play with, but want to spend as much of that writing as possible rather than messing around with TeX. :S

hehe... i'm writing my master of sci. thesis right now, and i would love to fiddle with my latex template instead of writing the thing :) i have a "writers block" at the moment

i looked for all kinds of tamplates when i started, but they all looked a bit too bloated for my use, so i started a document from scratch and i have no problems so far...

sorry, not helpful at all ;)

---

### Post by Milamber_Cubed on 2009-03-26
> **meborc said:**
> hehe... i'm writing my master of sci. thesis right now, and i would love to fiddle with my latex template instead of writing the thing :) i have a "writers block" at the moment

i looked for all kinds of tamplates when i started, but they all looked a bit too bloated for my use, so i started a document from scratch and i have no problems so far...

sorry, not helpful at all ;)

Good luck!

In my case, the thing is basically written already - I just have some corrections to apply and then I'm done. This problem has appeared between my originial submission date and now... very perplexing indeed. 

Anyway, good luck with yours... I almost wish I had started from scratch now, but will stick with what I have. Maybe I will install 7.04 in a VM and run my latex documents through that!

---

