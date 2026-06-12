---
title: "Texmaker and *.bib files"
date: 2010-06-26
forum: Education &amp; Science
---

### Post by virsto on 2010-06-26
I have Texmaker working with Ubuntu 10.04, but not quite the way I would like. That is, I have my own bibliography file (HomeBib.bib) that contains all my bibliography references. I would like to have this file in 

/usr/share/texmf-texlive/bibtex/bib

where I believe it should be. Note, I have placed HomeBib.bib in this directory; but, Texmaker does not find it. For now I must have it in the same directory as the *.tex file that I am working with using Texmaker --- this is not what I would like.

How can I fix Texmaker and/or my system such that when I use bibtex it finds HomeBib.bib in 

/usr/share/texmf-texlive/bibtex/bib

Note, I have tried many different approaches to fix this (e.g. modifying the PATH) but so far I found nothing that works.

Your help on this problem would be greatly appreciated.

Thanks :)

---

### Post by nirmana on 2010-06-26
I have the same problem... well, even one worse... I cannot get the .bib file to compile. I simply read "process exited with errors" and the log file does not exist. While the .tex file has no issues. 

advice

---

### Post by nirmana on 2010-06-26
I have fixed my first problem... previously I was using Miktex (I have gotten over the fatal addiction and am now clean) and there you had to compile the .bib file separately and several times to get it to run. Whereas, in texlive one simply runs bibtex on the source .tex file after editing the .bib file. and all is good... my ignorance.

Nonetheless, I would also like to know how to place the .bib file in a separate directory from the source .tex file as all of my documents access the same .bib file

... one possibility is to edit the command line within the source tex file something like:   p, li { white-space: pre-wrap; }  \bibliography{\<path>\reference}
... but this is not very practical when it comes to publications.

---

### Post by virsto on 2010-06-27
> **nirmana said:**
> I have the same problem... well, even one worse... I cannot get the .bib file to compile. I simply read "process exited with errors" and the log file does not exist. While the .tex file has no issues. 

advice

Perhaps this could be of help to you, since the following works for me.

Some code snippets from my *.tex file

 p, li { white-space: pre-wrap; }  ```

implies that some form of preprocessing is performed on the replications to determine a practical value for $K$ \cite{Robinson07}. After the removal of these $K$ values from each replication, we can represent the remaining data in the form,

```...

 p, li { white-space: pre-wrap; }   ```

 \bibliographystyle{plain}
   % \bibliographystyle{IEEEtran}
   % \bibliography{OfficeA}
   \bibliography{HomeBib}

```where, I was experimenting with different bibliography styles (all of these worked ok). My bib styles are in the following location:

 /usr/share/texmf-texlive/bibtex/bib

And the following sequence of executions in Texmaker (using key shorcuts) on the source (*.tex) file is performed,

 F1 -> F11 -> F1 -> F1

generates the citation in the text with the proper entry in a Reference section. My PATH is as follows:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/share/texmf-texlive/tex/latex"

```
--V

---

### Post by nirmana on 2010-06-27
Thank you, Virsto... 
I was able to get the bib to work after all.  My error was in the fact I was trying to do an F11 on the .bib file itself.  Previously, I was using Miktex and this gesture was required... upon recently switching to Texlive, I have just learned this is not necessary. Following your recommendations all works fine. 

The issue still remains how to place the .bib file in a different location and have Texmaker find it.  I am also running texmaker 1.9.9 with texlive 2009 and ubuntu 10.04. I have tried a few suggestions, which apparently worked on older versions, but I cannot get it to work here... such as: 
[http://www.latex-community.org/forum/viewtopic.php?f=50&t=7686](http://www.latex-community.org/forum/viewtopic.php?f=50&t=7686)
not sure what I am doing wrong... 

Still searching... 

Thanks again. 

[URL="http://ubuntuforums.org/member.php?u=1006577"]
[/URL]

---

### Post by virsto on 2010-06-28
> **nirmana said:**
> Thank you, Virsto... 
I was able to get the bib to work after all.  My error was in the fact I was trying to do an F11 on the .bib file itself.  Previously, I was using Miktex and this gesture was required... upon recently switching to Texlive, I have just learned this is not necessary. Following your recommendations all works fine. 

The issue still remains how to place the .bib file in a different location and have Texmaker find it.  I am also running texmaker 1.9.9 with texlive 2009 and ubuntu 10.04. I have tried a few suggestions, which apparently worked on older versions, but I cannot get it to work here... such as: 
[http://www.latex-community.org/forum/viewtopic.php?f=50&t=7686](http://www.latex-community.org/forum/viewtopic.php?f=50&t=7686)
not sure what I am doing wrong... 

Still searching... 

Thanks again. [URL="http://ubuntuforums.org/member.php?u=1006577"]
[/URL]

Ok,
I suggest that you place your own *.bib files (e.g. HomeBib.bib) in 

```
/usr/share/texmf-texlive/bibtex/bib/mybibfiles/

```Then the  following will generate a file (ls-R) in /usr/share/texmf-texlive/ which will contain all of the information needed for Texmaker:

 
  ```

$ sudo texhash /usr/share/texmf-texlive
```

---

### Post by nirmana on 2010-06-28
> **virsto said:**
> Ok,
I suggest that you place your own *.bib files (e.g. HomeBib.bib) in 

```
/usr/share/texmf-texlive/bibtex/bib/mybibfiles/

```Then the  following will generate a file (ls-R) in /usr/share/texmf-texlive/ which will contain all of the information needed for Texmaker:

 
  ```

$ sudo texhash /usr/share/texmf-texlive
```


Brilliant!... this works wonderfully... the .bib file is now in a central location that all .tex files can access... I wonder then if it works for you as well. 

Thanks again and take care.

---

