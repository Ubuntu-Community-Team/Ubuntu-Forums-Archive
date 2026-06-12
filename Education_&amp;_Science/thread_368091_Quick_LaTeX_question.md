---
title: "Quick LaTeX question"
date: 2007-02-22
forum: Education &amp; Science
---

### Post by cinnabar on 2007-02-22
I've been adding figures to a recent write-up I've been working on in LaTeX using kile (article class).  Whenever I add a figure (all pdf figures using pdfLaTeX) the filename is always shown above the figure and the caption in the output pdf file.  I've tried all sorts of things (graphicx package versus praphics package, etc.) and searched on google for some time but can't figure out how to get the filenames to go away on the pdf output.

I have noticed that if I use eps files and compile using LaTeX, that the file names don't show up.  Any ideas?

---

### Post by Toufik on 2007-02-23
I can't reproduce your problem.  It works perfectly for me with

```

...
\usepackage{graphicx}
...
\begin{figure}
 \includegraphics[width=12cm]{image.pdf}
 \caption{blabla}
\end{figure}
...

```

What do you write?

---

### Post by cinnabar on 2007-02-23
Toufik, thanks for checking.  I found the problem.  When the name of the pdf file has a space in it, everything after the first space is printed above the figure.  Not sure why this is but when I changed the name of the file to a single phrase with no spaces, it works fine.  Hope that helps out somebody else in the future.

---

### Post by slaanco on 2007-02-25
do u have the same problem when building .dvi file ?

---

### Post by hod139 on 2007-02-28
> **Toufik said:**
> 
```

...
\usepackage{graphicx}
...
\begin{figure}
 \includegraphics[width=12cm]{**image.pdf**}
 \caption{blabla}
\end{figure}
...

```
You shouldn't include the file extension when including graphics.  Also,  a neat trick for sizing images is to set them relative to the pagewidth.  That line would become 
```

\includegraphics[width=0.5\textwidth]{image} (set the image to be 1/2 the width of the page.)

```

---

### Post by Toufik on 2007-03-01
Nice trick for the pagewidth.  But remember that, it is always better to resize the image outside LaTeX (for instance Gimp), except of course for .eps!  Here above, it was just a quick test.

For the extension, I don't agree.  If you don't include file extension, latex will try to guess the extension, starting from  .eps, then (I don't remember the exact order after) .png, .jpg, ...  Basically, from the best to the worst (in LaTeX mind).  When you have a graphic, I don't see any reason not to give its extension.  It's less work for the compiler ;) and you know for sure the file that will be used.

---

### Post by hod139 on 2007-03-01
> **Toufik said:**
> 
For the extension, I don't agree.  If you don't include file extension, latex will try to guess the extension, starting from  .eps, then (I don't remember the exact order after) .png, .jpg, ...  Basically, from the best to the worst (in LaTeX mind).  When you have a graphic, I don't see any reason not to give its extension.  It's less work for the compiler ;) and you know for sure the file that will be used.
The reasons are 1) let LaTeX pick the format it likes best, and 2) compatibility between LaTeX and pdfLaTeX.

---

