---
title: "Beamer and Lyx"
date: 2007-03-25
forum: Education &amp; Science
---

### Post by raja on 2007-03-25
I know very little about Tex or Latex, but have used Lyx a bit. I was impressed seeing some examples of Beamer for making presentations and wanted to try it. I installed it from the Ubuntu repository, but the beamer class is not recognised by Lyx (when i try to open the examples). Does anyone have experience using Beamer with Lyx ? Can you guide me ?

---

### Post by timmie on 2007-03-26
install the **latex-beamer** package and its dependencies and then you should be find...

The packages is well documented...

Post if you have more problems

---

### Post by kleeman on 2007-03-26
You may have to prompt lyx to research your system to find the new package.
Fire up lyx and under Tools---> Reconfigure
Then restart lyx and you may find beamer.

There are some sample lyx files in beamer you might want to open as templates.
On the texlive packages they are here:


/usr/share/doc/texlive-latex-recommended/latex/beamer/lyx/examples

---

### Post by raja on 2007-03-26
Thanks a lot. Reconfigure did the trick. I could not find any examples in my local directories, but tried out some from the distribution of latex-beamer on sourceforge. I will explore this over the coming days. Thanks again.

---

### Post by timmie on 2007-03-27
Hi,
you don't need to take them from SF. Once latex-beamer is installed they should be on the system:

```

bash$: locate "latex-beamer*.lyx"
/usr/share/doc/latex-beamer/lyx/beamerlyxexample1.lyx.gz
/usr/share/doc/latex-beamer/solutions/generic-talks/generic-ornate-15min-45min.en.lyx.gz
/usr/share/doc/latex-beamer/solutions/generic-talks/generic-ornate-15min-45min.de.lyx.gz
/usr/share/doc/latex-beamer/solutions/conference-talks/conference-ornate-20min.en.lyx.gz
/usr/share/doc/latex-beamer/solutions/conference-talks/conference-ornate-20min.de.lyx.gz
/usr/share/doc/latex-beamer/solutions/short-talks/speaker_introduction-ornate-2min.en.lyx
/usr/share/doc/latex-beamer/solutions/short-talks/speaker_introduction-ornate-2min.de.lyx


```

---

### Post by xadder on 2007-03-29
I don't use Lyx myself, but I think powerdot is available for lyx also. powerdot is the replacement for prosper (my favourite so far) and beamer, by the same author.

---

### Post by diego_baixista on 2008-08-15
Hello guys !!!

I've followed the tip given by "timmie"...
I have installed here the "latex-beamer" package, but i stil can't export it to .pdf ...

Why should i have to do next ???


:(

---

### Post by IanH on 2008-08-17
Are you getting any sort of error messages when you try to compile? 

Also, I'd second the Powerdot recommendation. I've worked with both, and Powerdot is much simpler to use (although it is a bit less powerful).

---

### Post by diego_baixista on 2008-08-26
Hi IanH

So...always when i try to view the document in .pdf format, it appears:

"There is no information to export to PDF (pdflatex)"

And also i'd like to export to latex(plain) but i don't have this option...it don't appear to me...

Do you know why it happens ??

Thanks.

---

### Post by kleeman on 2008-08-30
Sounds like you either do not have a pdf viewer installed or else you do not have the latex to pdf program (pdflatex) installed. 

Use synaptic to install the packages evince and texlive-latex-base 

Then fire up lyx and hit Tools---->  Reconfigure to get lyx to see your newly installed programs....

---

### Post by diego_baixista on 2008-08-31
Thanks Kleeman...

The only thing that i have to do was **reconfigure** Lyx...hahahah

That's it !!!

Thanks a lot...:lolflag:

---

