---
title: "Vim latex-suite and \cite{} completion not working"
date: 2008-10-19
forum: Education &amp; Science
---

### Post by tjansson on 2008-10-19
I am using vim and the latex-suite to write my thesis but there is a small thing that I can't seem to get working. I can't make vim autocomplete my \cite{}. 

I have a main document called main.tex and the file main.tex.latexmain to make latex-suite know that main.tex is the main file. I also have the following in my .vimrc file:
```

filetype indent on
filetype plugin on
filetype on
let g:tex_flavor='latex'
set grepprg=grep\ -nH\ $*

```

Inside my main.tex I include the references file called ref.bib 
```

\bibliographystyle{plainnat}
\bibliography{ref}

```
And my bibtex references are on the form:
```

@ARTICLE{ svenningsen2007crb,
    title = "Crustal root beneath the highlands of southern Norway resolved by teleseismic receiver functions",
    author = "L. Svenningsen and N. Balling and BH Jacobsen and R. Kind and K. Wylegalla and J. Schweitzer",
    journal = "Geophysical Journal International",
    volume = "170",
    number = "3",
    pages = "1129--1138",
    year = "2007",
    publisher = "Blackwell Publishing"
}

```
But if I try to use F9 command to complete the cite nothing happens, see the attached screenshot. Is there a special way the bibtex should be formated or what could I be doing wrong?

---

### Post by el_pazzo on 2008-10-22
Hi!
I'm having the same problem here.
The strange thing is: its working if you remove the *latexmain file!
of course then you can only use the cite-completion from within the file
where your \bibliography cmd is..

also: when i check my maps (:map) it lists a lot of stuff but _not_ F9..
so long,
el_pazzo

---

### Post by el_pazzo on 2008-10-22
what i just found out: typing <ctrl>-n inside a \cite{} lists all matching bibtex entries in a popup-menu.

---

### Post by tjansson on 2008-10-22
I turned out that the bibtex manager, kbibtex, I used was creating a extra whitespace in the bibtex entries like this:
```

@ARTICLE{ svenningsen2007crb,

```
After correcting them all to this:
```

@ARTICLE{svenningsen2007crb,

```
I now finally use \cite{<F9>

---

