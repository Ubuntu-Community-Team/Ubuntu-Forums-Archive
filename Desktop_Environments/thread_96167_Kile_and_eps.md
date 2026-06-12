---
title: "Kile and eps?"
date: 2005-11-28
forum: Desktop Environments
---

### Post by Axios on 2005-11-28
Hi

I use Kile, but I cant compile a eps in my pdf document. Png works fine, but no eps.
I need the eps, because that is what we use in my study group.
How do I get this to work?

Thanks

---

### Post by sunshinerecorder on 2005-11-28
Hello!

If you use pdflatex then you simply cannot use .eps files. You have to convert them with epstopdf <file.eps> into a pdf file and then include this new pdf file into your LaTeX document.

---

### Post by Axios on 2005-11-28
[QUOTE=sunshinerecorder]Hello!

If you use pdflatex then you simply cannot use .eps files. You have to convert them with epstopdf <file.eps> into a pdf file and then include this new pdf file into your LaTeX document.[/QUOTE]

Why is this not possible?

I use pdflatex. Should I use something else then?

---

### Post by Axios on 2005-11-28
Can anybody tell me how to set Kile up, so that it can compile my latex document with eps to pdf?

doesn't matter if it converts to something else first..

---

### Post by neoflight on 2006-03-15
[QUOTE=Axios]Why is this not possible?

I use pdflatex. Should I use something else then?[/QUOTE]

pdflatex doenst know how to use boundingbox parameters in an eps file...

if u insist on using eps, then use latex instead of pdflatex...

latex file.tex => file.dvi  ----> view using xdvi
dvips file.dvi => file.ps ---> view using gv 
ps2pdf file.ps ==> file.pdf -- > view using  xpdf or acroread....


if u want pdflatex then convert the eps file to pdf file.... or some applications let u save the figures as pdf directly lile matlab 7.1

in kile several combinations are possible...
hope this helps...

---

