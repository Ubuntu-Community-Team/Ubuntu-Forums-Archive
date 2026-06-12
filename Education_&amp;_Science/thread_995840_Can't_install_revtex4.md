---
title: "Can't install revtex4"
date: 2008-11-28
forum: Education &amp; Science
---

### Post by g3n1uss on 2008-11-28
Hi. I shoud use revtex4 in my scientific work, but I can't install it. Recently I've downloaded revtex4.tar.gz from [http://authors.aps.org/revtex4/revtex4.tar.gz](http://authors.aps.org/revtex4/revtex4.tar.gz). Inside there was README where was the following instuction:
To install REVTeX 4, put revtex4.cls, *.rtx, *.sty, and *.bst (files
listed under 'Essential Files' above) somewhere in your TEXINPUTS path
or whereever your TeX software looks for input files. Under the TDS,
you should install them into $TEXMFLOCAL/tex/latex/revtex4. The *.bst
files should go under $TEXMFLOCAL/bibtex/bst/revtex4. Run the
appropriate update command (texhash, initexmf -u, etc.).
I found that my TEXMFLOCAL is /usr/share/texmf-texlive/ , then I copied folder revtex4 from archieve to /usr/share/texmf-texlive/tex/latex/ and /usr/share/texmf-texlive/bibtex/bst/ , but my Kile didn't find revtex4 files. Maybe it looks another path to input files, how can I find my INPUTS path or what shoud I do to use revtex4? Thanks.

---

### Post by parktownprawn on 2008-11-28
i'm not sure about kile but an easy way to install revtex is to intall the package: texlive-publishers

---

### Post by g3n1uss on 2008-11-28
Thanks, It's really an easy way. Now I am downloading texlive-publishers...

---

### Post by g3n1uss on 2008-11-28
Thank you,man. It was really simple - Ubuntu-way.

---

### Post by marshtric on 2008-11-29
All you need to do is install RevTEX 4, as described in the package's README file. the package can be found at The RevTeX 4 Web Site [http://publish.aps.org/revtex4/](http://publish.aps.org/revtex4/). Install it somewhere that LATEX can see it. Test it by trying to LATEX a short RevTEX 4 document in some random directory (i.e., not the directory where you installed the class file.) Then, if you reconfigure LYX, it will find the class file and let you use the RevTEX4 textclass.

---

### Post by silbar on 2009-05-02
Greetings,

Before finding this thread I tried to install revtex4 with
```
sudo apt-get install revtex4
```
(I had earlier seen that there was such a package in Synaptic.)  The installation seemed to work.  

However, when I went to latex a file (using texmaker), it could not find revtex4.cls and other such files (.sty and .rtx).  Where did they end up?  

I would have thought they would automatically be placed in /usr/share/texmf or /usr/share/texmf-texlive.  Indeed, they _do_ seem to be there, in both.  So why didn't latex find them?

   Dick Silbar

---

### Post by silbar on 2009-05-03
In response to my previous posting -- what I've learned since then:

The revtex that appears in /usr/share/texmf/tex/latex is an older, obsolete version of revtex.  If I had gone to Synaptic to install it instead of with the apt-get command line, I would have seen the word "obsolete" in bold type and thus avoided it.  

The search in Synaptic on "revtex" also revealed the texlive-publishers, which is happened to begin installing before I start my posting.  It had finished before I got to my last paragraph, which is why there was a revtex folder (with the non-obsolete version) in /usr/share/texmf-texlive/tex/latex.  After I submitted the posting, I went back to texmaker and found that it could then compile and display my latex document.  So, I gather that texmaker uses texlive (or tetex?) instead of something older which relies on /usr/share/texmf.

So, things are working for me now (after having to install latex and gv as well as revtex4).

   Dick Silbar

---

### Post by jalirious on 2010-03-30
On beta1 lucid installing texlive-publishers or revtex (obsolete repository package) didn't do the trick. 
Nor did symbolic links from revtex4.cls to revtex4-1.cls.
Nor did installing revtex from the official site (from source).


! LaTeX Error: File `revtex4.cls' not found. 

Ideas?

---

### Post by jalirious on 2010-03-30
What a licker. All I had to do was change revtex4 in my .tex document to revtex4-1.

---

### Post by GaryP21 on 2010-03-30
glad it was an easy fix!

---

### Post by amol.h on 2010-07-07
Ubuntu Software Center installs obsolete version of RevTex. To use the revtex4 
in your latex articles, the easiest way to download the revtex4.tar.gz from 
[http://authors.aps.org/revtex4/revtex4.tar.gz](http://authors.aps.org/revtex4/revtex4.tar.gz)

Unzip the package and put revtex4 folder in  /usr/share/texmf-texlive/tex/latex/

Run $sudo texhash

And now good to go. Can easily use revtex4 in your latex documents.

---

### Post by buntuLo on 2010-09-04
texlive-publishers does not contain the most updated version of the ctan-package revtex.

thanks a lot, Amol.h, this was the right hint.
by the way, it works also for the newest revtex4-1.
cia'cia', Lo.

---

### Post by btgoss on 2010-10-17
Does anyone know how I would go about getting this package fixed, so that people will be able to get the proper revtex4-1 files?

Thanks.

btg a concerned citizen.

---

### Post by DLOM85 on 2010-12-23
Jalirious thanks a lot, you fix it.
> **jalirious said:**
> On beta1 lucid installing texlive-publishers or revtex (obsolete repository package) didn't do the trick. 
Nor did symbolic links from revtex4.cls to revtex4-1.cls.
Nor did installing revtex from the official site (from source).


! LaTeX Error: File `revtex4.cls' not found. 

Ideas?

---

### Post by slow photon on 2011-02-03
> **jalirious said:**
> What a licker. All I had to do was change revtex4 in my .tex document to revtex4-1.

After hours, literally, of trying to get revtex to work this is what did it for me.... Unbelievable

---

### Post by snehalshekatkar on 2012-03-17
> **slow photon said:**
> After hours, literally, of trying to get revtex to work this is what did it for me.... Unbelievable
This I also did but now it says something like this:
(./revsymb4-1.sty)) (./reftest4-1.aux)
Filename: reftest4-1.tex for revtex 4.1i 2009/10/19 (AO)
Type in file name (no extension)

\filename=
What am I supposed to do now?

---

