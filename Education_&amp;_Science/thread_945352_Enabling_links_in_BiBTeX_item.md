---
title: "Enabling links in BiBTeX item"
date: 2008-10-12
forum: Education &amp; Science
---

### Post by drorata on 2008-10-12
Using:
```
file = {:file_location/filename.pdf:PDF}
```
in the .bib file one can specify the location of a file on a local machine. Using:

```
url = {http://aaa.com/filename.pdf}
```

one can refer to an online location of the document.

My question is how to add a link within the PDF file which is produced at the end. I guess I should pick the right bibTeX style, but I couldn't find which is the right one.

Does anyone know how to do it?

Thanks in advance,
Dror

---

### Post by mrgnash on 2008-10-13
I think you need to load the hyperref package:

```
\usepackage{hyperref}
```

---

### Post by drorata on 2008-10-13
Dear Mrgnash,

The package is already loaded in the .tex - so I'm afraid the problem is somewhere else. My guess would be that I have to use a different style for the bibliography. At the moment I have the following two lines:
```

\bibliographystyle{amsplain}
\bibliography{references.bib}
```
(where the .bib file was generated using JabRef)

Anyway, thanks for the quick answer!
Dror

---

### Post by mrgnash on 2008-10-13
> **drorata said:**
> Dear Mrgnash,

The package is already loaded in the .tex - so I'm afraid the problem is somewhere else. My guess would be that I have to use a different style for the bibliography. At the moment I have the following two lines:
```

\bibliographystyle{amsplain}
\bibliography{references.bib}
```
(where the .bib file was generated using JabRef)

Anyway, thanks for the quick answer!
Dror

I see. Well, I have not had any experience with the AMS style myself (I have only used APA), so I'm not sure if this will help, but perhaps you could try the amsrefs package? See section 2.3 of the [documentation](ftp://ftp.ams.org/pub/tex/amsrefs/amsrdoc.pdf) for instructions on how to use it with BibTeX.

Hope that helps.

---

### Post by drorata on 2008-10-13
Thanks for the quick answer - I'm afraid that didn't help either. I tried to change to APA and to amsrefs and got tons of errors. Afterward, when I changed back to "plain" I had to re-compile, seperately, the .bib file; otherwise it simply didn't work. Any other ideas?

---

### Post by mrgnash on 2008-10-13
> **drorata said:**
> Thanks for the quick answer - I'm afraid that didn't help either. I tried to change to APA and to amsrefs and got tons of errors. Afterward, when I changed back to "plain" I had to re-compile, seperately, the .bib file; otherwise it simply didn't work. Any other ideas?

Don't you always compile manually? e.g: 

```
latex *document*
bibtex *document*
latex *document*
latex *document*
```

Doing that, you should be able to avoid errors when switching between styles, so long as you're using the standard \cite and \bibliography{file} commands in the document. If you still get errors, then you may need to delete *document.aux* and the other files besides your .tex and .bib source documents before re-compiling. 

If that still doesn't work then I don't know :(

---

### Post by drorata on 2008-10-13
> **mrgnash said:**
> Don't you always compile manually? e.g: 

```
latex *document*
bibtex *document*
latex *document*
latex *document*
```


I'm afraid I'm not that skilled. I'm using Kile and do the compilation directly from its interface...

> **mrgnash said:**
> 
Doing that, you should be able to avoid errors when switching between styles, so long as you're using the standard \cite and \bibliography{file} commands in the document. If you still get errors, then you may need to delete *document.aux* and the other files besides your .tex and .bib source documents before re-compiling. 

I tried it, nevertheless... I didn't help. The funny thing is that the .tex file is being compiled perfectly when I use "plain" or "amsplain" styles, accept from the links in the reference. Once I change the style everything crashes.

---

### Post by parktownprawn on 2008-10-14
You are correct in your guess that you need to use the right bibliography style file. 

The bibliography style you use will influence whether links appear in document.

you might want to try a natbib (abbrvnat,plainnat,unsrtnat) or revtex (apsrev, apsrmp) style.

i think they are in the texlive-publishers package

You can also try the script urlbst 
( [http://www.ctan.org/tex-archive/biblio/bibtex/contrib/urlbst/urlbst.html](http://www.ctan.org/tex-archive/biblio/bibtex/contrib/urlbst/urlbst.html) )
which converts a  .bst file to one that supports hyperlinks

i think it is in the texlive-bibtex-extra package

---

### Post by parktownprawn on 2008-10-14
I forgot to mention that you need to make sure that the style file, eg. plainnat.bst is actually installed on your computer or in the current directory otherwise it won't work

---

### Post by drorata on 2008-10-14
> **parktownprawn said:**
> You are correct in your guess that you need to use the right bibliography style file. 

The bibliography style you use will influence whether links appear in document.

you might want to try a natbib (abbrvnat,plainnat,unsrtnat) or revtex (apsrev, apsrmp) style.

i think they are in the texlive-publishers package

That indeed solved my problem. Now I have links from the text to the reference and from there a link to the location of the referred text.

**Note**: This method does not recognize the *"file"* field in the BiBTeX entry. In order to enable a link to a local file I had to insert the location of it in the *URL* field: ```
file://<location>/<filename>.
```

There is one drawback and one problem thou - Now the links to the reference in the text's body are of different format. I guess I'll have to get used to that ;) The problem is that now I get some warnings, something like that:
```
General personal notes.tex:9:Underfull \hbox (badness 5652) in paragraph
```
Any ideas? The funny thing is that line 9 contains nothing but a comment...

Anyway - thanks a lot for your help guys!

---

### Post by abidkts on 2008-11-11
dear drorata, I have the same problem. Can you please tell me in a little bit detail, how did you solve it?

---

### Post by drorata on 2008-11-11
So I am using *plainnat* style and it works. Pay attention to my note! I hope this is the answer you're looking for.

---

### Post by abidkts on 2008-11-12
Thanks a lot!!

---

### Post by drorata on 2008-11-12
One can have a look at this link for more info about this package:

[http://merkel.zoneo.net/Latex/natbib.php](http://merkel.zoneo.net/Latex/natbib.php)

---

