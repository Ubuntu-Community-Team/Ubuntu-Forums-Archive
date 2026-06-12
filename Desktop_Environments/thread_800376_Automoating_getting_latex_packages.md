---
title: "Automoating getting latex packages"
date: 2008-05-19
forum: Desktop Environments
---

### Post by suby-luby on 2008-05-19
Hi All,

I just installed latex (bin, extras, and basic). However, it is asking for many packages (e.g., algorithm.sty). Two questions here:

1. is there a way to automate how to get these packages as opposed to having to go manually get the file and save it.

2. Even though the documentation talks about getting the packages in the form of .tar.gz and installing them under /usr/local/share/texmf/tex/latex and then rehashing to update the DB, I am not able to find the files in this format.

Please enlighten me, I am new to this.
Thanks:popcorn:

---

### Post by sdennie on 2008-05-19
How did you initially install the packages?  One thing you could try if you installed them with synaptic or apt-get would be to go to System->Administration->Synaptic Package Manager and search for latex.  Just go do the list (it will probably be fairly long) and install anything that looks vaguely interesting.

---

### Post by dvase on 2008-05-19
> **suby-luby said:**
> 
1. is there a way to automate how to get these packages as opposed to having to go manually get the file and save it.


On *nix systems, no, as far as I know.  FYI: This is possible on windows using MikTeX.

> 
2. Even though the documentation talks about getting the packages in the form of .tar.gz and installing them under /usr/local/share/texmf/tex/latex and then rehashing to update the DB, I am not able to find the files in this format.

These links may be of some help:
[http://www.tex.ac.uk/cgi-bin/texfaq2html?introduction=yes](http://www.tex.ac.uk/cgi-bin/texfaq2html?introduction=yes)
[http://www.tex.ac.uk/cgi-bin/texfaq2html?label=installthings](http://www.tex.ac.uk/cgi-bin/texfaq2html?label=installthings)



FYI: I use the [command line version of miktex]("http://miktex.org/unx/Default.aspx") to manage my latex packages on ubuntu.  You do have to compile the source to use it, but I think it is well worth the little extra effort.

---

### Post by mannheim on 2008-05-20
Most of these things are in the repositories. I think algorithm.sty is contained in the texlive-science package. So you just have to do:

```
sudo apt-get install texlive-science
```

and you should be good to go.

EDIT: You can search for an ubuntu package containing a specific file (such as "algorithm.sty") by going to [http://packages.ubuntu.com/]("http://packages.ubuntu.com/"). Scroll down to where it says "Search the contents of packages".

---

### Post by aroch1 on 2008-05-20
I didn't know about this package, but use TeX all the time on Ubuntu, you're a lifesaver!!!

---

### Post by suby-luby on 2008-05-22
```
sudo apt-get install texlive-science
```

and you should be good to go.

Thank you all for the info. I am learning a lot here.

I tried the previous command, in fact I was crazy-enough to try texlive-full and for some reason, still Kile complains about algorithm and algorithmic.sty 


I was reading the link you provided dvase and it says to issue

kpsewhich -expand-var "\$TEXMFLOCAL"

To know where to install packages, when I did, it returned

/usr/local/share/texmf

But then I was not able to find any texmf under /usr/local/share

I can live with manually installing few packages, but I am still missing something as to how to accomplish that

---

### Post by dvase on 2008-05-22
> 
I tried the previous command, in fact I was crazy-enough to try texlive-full and for some reason, still Kile complains about algorithm and algorithmic.sty

If you post a [minimal example]("http://www.tex.ac.uk/cgi-bin/texfaq2html?label=minxampl") along with the error output from Kile/LaTeX we may be able to more accurately diagnose your algorithm package issue.

---

### Post by suby-luby on 2008-05-22
> **dvase said:**
> If you post a [minimal example]("http://www.tex.ac.uk/cgi-bin/texfaq2html?label=minxampl") along with the error output from Kile/LaTeX we may be able to more accurately diagnose your algorithm package issue.

Here is the error:
./thesis.tex:13:File `algorithm.sty' not found. \usepackage
./thesis.tex:0:File `algorithmic.sty' not found.

---

### Post by dvase on 2008-05-22
I assume that you are doing a standard package inclusion command such as,

\documentclass{article}

\usepackage{algorithm}

\begin{document}

Your text here...

\end{document}



> **suby-luby said:**
> Here is the error:
./thesis.tex:13:File `algorithm.sty' not found. \usepackage
./thesis.tex:0:File `algorithmic.sty' not found.

Please post the contents of the "Output" tab (it should be next to the "Log and Messages" tab), it is the raw output of the latex compilation process. Thanks.

---

### Post by suby-luby on 2008-05-22
[QUOTE=dvase;5020939]I assume that you are doing a standard package inclusion command such as,

\documentclass{article}

\usepackage{algorithm}

\begin{document}

Your text here...

\end{document}


Even though I updated the index, it seems it still did not kick in. For some reason, logging out and back in, Kile stopped complaining about these two packages.

Any way, thanks a lot for your help.

---

### Post by mannheim on 2008-05-23
The texlive-science (or texlive-full) package **should** have installed these files:

```

/usr/share/texmf-texlive/tex/latex/algorithms/algorithm.sty
/usr/share/texmf-texlive/tex/latex/algorithms/algorithmic.sty

```

Perhaps you could check that they are really there. If they are, perhaps you should check rhat the text installation really knows they are there, by doing:
```
kpsewhich algorithm.sty
```
(This should give one line of output, giving the full path to algorithm.sty, as above.) If you don't get that one line of output, you could try getting tex to rebuild its list of files by doing:
```

sudo texhash

```
After that, try the kpsewhich thing again.

---

### Post by castudil on 2009-01-07
```
sudo apt-get install texlive-science
```

did the job for me. it installed the algorithm.sty package correctly, following your steps, when executing

```
kpsewhich algorithm.sty
```

I can see

```
/usr/share/texmf-texlive/tex/latex/algorithms/algorithm.sty
```

then I compiled my tex file in Kile and worked perfectly,

Thanks

---

