---
title: "LaTeX  &quot;nomencl&quot; package with Vim"
date: 2011-06-24
forum: Education &amp; Science
---

### Post by Random_Dude on 2011-06-24
Hi,

I'm writing a document with LaTeX and I need to use the nomencl package. Its use is fairly simple and can be found here: [http://franz.kollmann.in/latex/latex.html#abbr](http://franz.kollmann.in/latex/latex.html#abbr)

The problem is Vim does not run the necessary steps to use the package when I type \ll. I found a link where a guy managed to solve this problem by changing the compiler.vim and texrc files: [http://www.mail-archive.com/vim-latex-devel@lists.sourceforge.net/msg00316.html](http://www.mail-archive.com/vim-latex-devel@lists.sourceforge.net/msg00316.html)

But the explanation is rather messy and I don't understand it.

Are there any Vim gurus out there who could explain how it's done? :)

Cheers :cool:

---

### Post by Random_Dude on 2011-06-27
I'll just post what is on the links so that people don't have to open them.

This is how you use the nomencl package:
> **14. List of Abbreviations**

              To include a list of abbreviations the following steps should be performed:

        
                                                                                                             1. 
Insert [FONT=Courier][COLOR=brown]**\usepackage{nomencl}**[/COLOR][/FONT] and                                 [FONT=Courier][COLOR=brown]**\makenomenclature**                                 [/COLOR][/FONT] at the beginning of the tex file (before \begin{document}).
                                                                                   2. 
 Insert [FONT=Courier][COLOR=brown]**\printnomenclature[*distance*]**[/COLOR][/FONT] at that position in the tex file, where the list of abbreviations should be listed.                                 The parameter *distance* defines the distance (e.g. 2.5 cm) between Abbreviation and Explanation.                                 
                                                                                   3. 
Insert the abbreviation in the tex as short and long form: [FONT=Courier][COLOR=brown]**\nomenclature{Abbr}{Abbreviation}**[/COLOR][/FONT]
                         
                                                          4. 
Execute [FONT=Courier][COLOR=brown]**latex file.tex**[/COLOR][/FONT] twice.                         
                                                          5. 
Execute [FONT=Courier][COLOR=brown]**makeindex file.nlo -s nomencl.ist -o file.nls**[/COLOR][/FONT]                         
                                                          6. 
Execute [FONT=Courier][COLOR=brown]**latex file.tex**[/COLOR][/FONT]
From: [http://franz.kollmann.in/latex/latex.html#abbr](http://franz.kollmann.in/latex/latex.html#abbr)


This is how a guy managed to automate this with \ll on vim: [http://www.mail-archive.com/vim-latex-devel@lists.sourceforge.net/msg00316.html](http://www.mail-archive.com/vim-latex-devel@lists.sourceforge.net/msg00316.html)
Apparently, the changes seem to be on the compiler.vim and texrc files (the information is on the link but it loses the layout if I post it here). However, they are quite confusing and I don't know in which file should I make which change.

Does anyone know how to do this?

Cheers :cool:

---

### Post by Random_Dude on 2011-07-08
bump

---

### Post by Random_Dude on 2011-07-20
Bump.

---

### Post by Random_Dude on 2011-07-27
Bump.

---

### Post by Random_Dude on 2011-08-07
Bump.

---

### Post by Random_Dude on 2011-08-16
Bump.

---

### Post by Random_Dude on 2011-08-23
Bump.

---

### Post by jeneverboy on 2011-08-24
I am runnin ginto the same kind of problem but then with \nomencl and TexMaker. I found three different ways on the net but none of them worked.
Now I just use the package listofsymbols

```
\usepackage[final]{listofsymbols}
```

and at the place where you want the list

```
\newpage
\listofsymbols
  \opensymdef
  	\newsym[Velocity]{symV}{V}
	\newsym[Time]{symt}{t}
	\newsym[Density]{symrho}{rho}     
    \newsym[Masa]{symm}{m}\\
  \closesymdef
```

at the moment I've got errors trying to use math in there, $\rho$ does not work.

---

### Post by jeneverboy on 2011-08-24
I've found an other solution with nomencl in Texmaker and with the command line solution.


the package
```
\usepackage{nomencl}
```

in the preamble (before begin document)
```
\makenomenclature
```

where you want your nomenclature
```
\printnomenclature
```

example of equation with definition of symbols
```
\begin{equation}
\frac{d}{dt} \iiint_{V} \rho \; dV = 0
\end{equation}%
	\nomenclature{$V$}{Velocity}%
	\nomenclature{$\rho$}{Density}%
```

and now the elaborate way of using it. In the command line
```
makeindex YourFile.nlo -s nomencl.ist -o YourFile.nls
```

---

### Post by Random_Dude on 2011-08-25
Thanks jeneverboy. :)

I've managed to use the package with the command line, but my idea was to not have to resort to it and do it directly on the editor.
The listofsymbols package might be a good idea for using next time, since my main point is usually to make a list of acronyms.

Cheers :cool:

---

### Post by jeneverboy on 2011-08-25
Yes, it was also my intention to do it in the editor, but unfortunately it doesn't work. Now I've made a simple and short shell script that runs:

-LaTeX
-makeindex
-LaTex
-Bibtex
-dvips
-ps2pdf

mainly because Bibtex requires a LaTeX-LaTeX-Bibtex-LaTex build, which is already an elaborate task.

```
 # LaTex - makeindex - LaTeX
latex YourFile
makeindex YourFile.nlo -s nomencl.ist -o YourFile.nls

bibtex YourFile
latex YourFile

 # DVI -> PS
dvips YourFile.dvi

 # PS -> PDF
ps2pdf YourFile.ps
```

run this is in your directory with
```
./NameOfShellScript
```

---

