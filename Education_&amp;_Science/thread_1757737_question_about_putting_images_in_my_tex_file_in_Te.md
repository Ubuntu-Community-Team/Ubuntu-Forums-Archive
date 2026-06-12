---
title: "question about putting images in my tex file in Texmaker"
date: 2011-05-13
forum: Education &amp; Science
---

### Post by Richard85 on 2011-05-13
I'm sure that I'm not the first person to ask this (couldn't find an answer either), but how does one put an image in a tex file. Now let me be a bit more specific. I know you need to use \usepackage{graphicx}, and the command is \includegraphics[scale=#]{image} but where do I put the image file? Furthermore, I'm using Ubuntu 10.04. Any help is appreciated!!!

---

### Post by not_a_phd on 2011-05-13
You are on the right path! Place the graphics file in the same path with your .tex document. Also, see this excellent link:

[http://en.wikibooks.org/wiki/LaTeX/Importing_Graphics](http://en.wikibooks.org/wiki/LaTeX/Importing_Graphics)

Regards.

---

### Post by Lateralis on 2011-05-14
In principle the image file can go anywhere.  For my thesis, I had individual chapter directories with subdirectories containing the figures.  So for instance:

```

\begin{figure}[t!]
\begin{center}
	\includegraphics[scale=0.7]{figures/Figure.eps}
	\caption{A caption}
	\label{a:label}
	\end{center}
\end{figure}

```

The path in parentheses could be either relative (as in this case) or absolute.  The choice is yours.

---

### Post by Richard85 on 2011-05-15
Awesome! thanks a bunch!

---

### Post by jeneverboy on 2011-05-18
I recommend .eps for figures, it gives the best quality!!

---

### Post by Lateralis on 2011-05-18
Yes. .eps files are vector graphics images, so they scale properly. Raster images and bitmaps suffer from pixelation when scaled without any care. 

I also recommend using Inkscape for vector diagrams and pictures. Very powerful, relatively simple but makes nice figures with a small file size compared to other programs. In my experience anyway! Most of my thesis diagrams were done in Inkscape.

---

