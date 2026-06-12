---
title: "Install Latex"
date: 2006-10-25
forum: Desktop Environments
---

### Post by vidi on 2006-10-25
Hi all,

I'm new in Ubuntu since about one week. I'm using Edgy with all installed updates. So i have just tried to install and use latex like in [http://wiki.ubuntuusers.de/Latex](http://wiki.ubuntuusers.de/Latex) . All i get during compiling is that all commands in the Tex document are undefined. 

```
 tex test.tex
This is TeX, Version 3.141592 (Web2C 7.5.4)
(./test.tex
! Undefined control sequence.
l.1 \documentclass
                  [a4paper]{scrartcl}
? 
! Undefined control sequence.
l.3 \usepackage
               {ucs}            % Eventuell nicht noetig
? 
! Undefined control sequence.
l.4 \usepackage
               [utf8]{inputenc} % Für hoary hedgedog oder Systeme die Unico...

? 
! Undefined control sequence.
l.6 \usepackage
               {ngerman}            % neue Rechtschreibung (alt: german)
? 
! Undefined control sequence.
l.8 \usepackage
               [T1]{fontenc}
? 
! Undefined control sequence.
l.9 \usepackage
               {textcomp}
? 
! Undefined control sequence.
l.11 \begin
           {document}
? 
! Undefined control sequence.
l.13 \section
             {Mein erstes Dokument mit \LaTeX}
? 
! Undefined control sequence.
l.13 \section{Mein erstes Dokument mit \LaTeX
                                             }
? 
! Undefined control sequence.
l.15 Dies ist mein erstes mit \LaTeX
                                     \ geschriebenes Dokument. Es enthält d...

? 
[1] )
```

so what's wrong?

---

### Post by tigerstripedcat on 2006-10-25
Since you say your new, I'm guessing that you don't know about the miracle that is "apt-get"  learn more about it:

#man apt-get

and then do

#sudo apt-get latex

should be all you need

---

### Post by vidi on 2006-10-25
hi, thanks for the answer but i have installed tetex with apt.

now i have found my fail. I have used tex instead of latex.

so i am able now to create dvi from tex.

now, i have installed texlive-pdftex but i cant compile it

```

vidi@vidi:~/tex$ pdflatex test.tex
This is pdfeTeX, Version 3.141592-1.30.5-2.2 (Web2C 7.5.5)
kpathsea: Running mktexfmt pdflatex.fmt
mktexfmt: no info for format `pdflatex'.
I can't find the format file `pdflatex.fmt'!

```

---

### Post by tlau on 2007-03-19
There seem to be missing dependencies in some of the texlive files.  I was getting the same error as well about not finding the format file pdflatex.fmt.

sudo apt-get install texlive texlive-pdf texlive-latex-extra

seemed to do it for me, after a couple attempts.

---

### Post by bcrowell on 2007-03-19
It looks to me like you're trying to compile a latex file using tex. You need to use latex to do that: use the command "latex" rather than the command "tex".

---

### Post by ArponerO on 2007-03-21
Hi,

Try using texhash as root. It will regenerate your tex configuration.

Anyway, you can always do: dvi2ps and then ps2pdf. pdflatex does not handle eps images and some other format I don't remember now. The last option is the safe one.

---

