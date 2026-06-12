---
title: "Lyx, Latex and images"
date: 2008-10-11
forum: Education &amp; Science
---

### Post by 77_Chris on 2008-10-11
Hi!

I have a problem inserting images (I use .png) into my Lyx-document.
Well, inserting is not the real problem, but when I try to generate a PDF I get the following error message:

Paragraph ended before \@tempa was complete.

I searched the latex code but could not find anything.
What I can do without any error is to export the document to dvi but the inserted images are missing.

Thanks in advance,
Chris

---

### Post by drorata on 2008-10-12
Make sure you're using the following package:
```
\usepackage{graphicx}
```

Then, I add a .jpg file using the following code:

```
\begin{figure}
\centering
\includegraphics[scale=0.7]{filename.jpg}
\caption{A caption and a reference \cite{REF08}}
\label{fig}
\end{figure}
```

I think it should work with .png's as well.

One last thing, in general I'd recommend, as long as it is possible, to insert vector based figures, since they are scalable! If it is an .eps for example, then you can easily convert it to PDF using:
```
epstopdf
```

I hope it was helpful.

Have a nice week.

---

### Post by castudil on 2008-10-12
sometimes when I need to put more than one figure side by side,

the *subfigure * command comes to save my life :)

you have to include the package...

```
\usepackage{subfigure}  % use for side-by-side figures
```


and example of use

```

\begin{figure}[h!]
\begin{center}
\subfigure[caption_for_first_image]{
\includegraphics[scale=0.5]{fig/figure_a}}
\subfigure[caption_for_second_image.]{
\includegraphics[scale=0.5]{fig/figure_b}}
\caption{This is the caption for the whole figure.}
\end{center}
\end{figure}

```


look here for a depicted example

[http://andy-roberts.net/misc/latex/latextutorial6.html](http://andy-roberts.net/misc/latex/latextutorial6.html)


Happy Ubuntuing!

---

### Post by mrgnash on 2008-10-13
Thanks Castudil, I wasn't aware of this package until now -- I am sure that it will come in very handy :D

---

### Post by ad_267 on 2008-10-13
If you're still having problems then post a basic example of what you're trying to do and someone will help you out.

---

### Post by 77_Chris on 2008-10-16
Hi!

I did not have the time to investigate the real reason for my problem but changing the documentclass solved the problem in an easy way.

Thanks a lot for your help.

Cheers!

---

