---
title: "Including eps in LaTeX file"
date: 2006-11-16
forum: Education &amp; Science
---

### Post by lwr on 2006-11-16
I'm trying to compile (not sure if that's the right word) my LaTeX coursework, which includes an esp graphics file. My code is [here]("http://www.truthdesigns.co.uk/integration_notes.tex"). I found somewhere on the web that said to type latex integration_notes dvips -Ppdf in the terminal. I don't know if I might have a required package missing?
Thanks

Luke

---

### Post by girishv on 2006-11-16
It is called latexing (la-te-ch-ing). Open a terminal and change your directory to the directory you have your integration.tex file. Then run the command

latex integration_notes.tex

## it creates a dvi file called integration_notes.dvi, if there are no errors
## make sure that the figures are in the same directory too

## your file has only two errors about newline (at line nu 73 & 77
## as these donot affect the final output, just enter when it stops
## then run
dvips -Ppdf integration_notes -o

## this will create a pdf file by name integration_notes

Goodluck

Girish

---

### Post by lwr on 2006-11-16
Thanks for replying. When I run the second line of code, it creates a PostScript file, not a pdf. Do you know why this is? How can I change to to a pdf? Thanks again.

Luke

---

### Post by Eric_T on 2006-11-16
dvips mean dvi->ps.
To get a PDF you have to use the dvipdf command.
So this should give you what you want:
latex integration_notes
dvipdf integration_notes.dvi

---

### Post by hod139 on 2006-11-16
You can also produce pdf's directly using pdflatex
```

pdflatex integration_notes.tex

```

Note however, that pdflatex doesn't work with eps figures yet (technically it is still beta software.)  You will have to convert all eps figures to pdfs using the command epstopdf.  However, pdflatex will work with png's and jpg's which is really nice.

---

### Post by lwr on 2006-11-16
Thanks for that. All works well. The graphic seems to be of a lower quliaty in the pdf, but I guess that's something to do with it no longer being a PostScript file. Thanks again for all you help.

Luke

---

### Post by hod139 on 2006-11-16
Looking at your source code, there is a mistake.  You shouldn't be putting the file extension when using the \includegraphics command.  It should be:

```

%\newline  %% You should be letting latex place stuff, why are you trying to move it?
\begin{figure}[htb]  % You can use the htb to tell latex: place **h**ere if possible, if not try **t**op of page, if not try **b**ottom of page. 
\centering
\includegraphics{fig1}  % Do not put file extension, only name
\caption{Example Figure}
\label{fig:fig1}
\end{figure}
%\newline   %% Again, let latex place stuff where it wants to

```

---

### Post by lwr on 2006-11-16
Hi thanks for your suggestions. I didn't realise I didn't need the file extension for the graphics file, as we've only been taught to do things like \includegraphics{fig1.jpg}. The \newline lines are there from when I tried to remind myself that I needed to include the graphics file later, and I just forgot to remove them. Unfortunately, it's already been handed in so I can't implement your improvements, but thanks anyway. I'll be sure to bear this in mind in future.

---

### Post by Xgkkp on 2006-11-17
> **hod139 said:**
> You can also produce pdf's directly using pdflatex
```

pdflatex integration_notes.tex

```

Note however, that pdflatex doesn't work with eps figures yet (technically it is still beta software.)  You will have to convert all eps figures to pdfs using the command epstopdf.  However, pdflatex will work with png's and jpg's which is really nice.

On The Mac latex port (Texshop etc) it deafults to pdflatex, and to get around the eps problem it defaults to including the package 'epstopdf' on it's standard document template - this automatically converts any eps files to pdf when the document is compiled. I haven't tested it on ubuntu but I imagine it would work the same.

---

### Post by hbj on 2006-11-26
Have you tried using LyX?  [http://www.lyx.org/]("http://www.lyx.org/")
It allows you to see things like eps figures and equations on the screen as you are working.  Equation entry is especially nice - you just type things like you would in LaTeX and it does the formatting and displays the equation as you type.  My students have learned to use it very quickly and one has written reports with over 100 pages.  LyX handles it with ease and remains fast and responsive.  Use the lyx-qt version.  I highly recommend it.

---

### Post by LJM on 2007-01-10
Hello. I thought I'd continue in the same thread with a related question on including eps figures in LaTex.

I've recently moved from Windows MikTeX to TeXlive and I am using code that used to work there:

\usepackage{epsf} %in preamble

\begin{figure} %in body
\begin{center}
\epsfxsize=70mm
\epsfbox{pb.eps}
 \end{center}
\caption{Caption text}
\end{figure}

As I "latex document-name.tex" I get the following error:

(pb.eps
! Could not open file pb.eps, ignoring it.
\epsfgetbb ...Could not open file #1, ignoring it}
                                                  \else {\chardef \other = 1...
l.45 \epsfbox{pb.eps}

The file pb.eps is of course in the same folder as document-name.tex and I can view it perfectly using the viewer. 

Any ideas why it cannot be opened? 

Thank you in advance. --LJM

---

### Post by fadder on 2007-01-10
Sorry, can't help with the above, but maybe you should be using the graphics or graphicx packages instead of epsf. (I use \usepackage[dvips]{graphicx} for everything.
epsf is very old now, and graphicx has many great options. Check out the document l2tabuen.pdf (google for it), which gives lists of "old" packages, and their suggested modern replacements.

By the way, jpeg2ps is great for converting from jpg to .ps also.

---

### Post by LJM on 2007-01-10
Thanks for the hints. I had no idea the epsf package was dated. I replaced it with the graphicx one, as you said, and by compiling to dvi it worked alright. Thanks! (By the way, what does "[dvips]" do when you include the package? What if one doesn't add that option?)

There's still something that puzzles me, though. As I make a pdf file from the dvi one using dvipdf at the terminal and then open it with Document Viewer, it will show the picture alright, but it says that the document's format is dvi--but it's not, it's pdf! 

What's going on?

---

### Post by neoflight on 2007-01-10
> **lwr said:**
> Thanks for that. All works well. The graphic seems to be of a lower quliaty in the pdf, but I guess that's something to do with it no longer being a PostScript file. Thanks again for all you help.

Luke

if you like a printout then print the ps file rather than the pdf. ps might look bad on the screen but good on paper. 

to generate diagrams, you can use openoffice draw, inkscape ....both can directly make eps.... matlab can generate eps too...but one word of advise...

**always save  a copy of matlab plot - mygraph.fig from which you saved as mygraph.eps. **

---

### Post by neoflight on 2007-01-10
> **LJM said:**
> Thanks for the hints. I had no idea the epsf package was dated. I replaced it with the graphicx one, as you said, and by compiling to dvi it worked alright. Thanks! (By the way, what does "[dvips]" do when you include the package? What if one doesn't add that option?)

There's still something that puzzles me, though. As I make a pdf file from the dvi one using dvipdf at the terminal and then open it with Document Viewer, it will show the picture alright, but it says that the document's format is dvi--but it's not, it's pdf! 

What's going on?

good. generally do not include the eps file extension when you call the figure while using graphicx package. 

try deleting the dvi before you open the pdf ???
and may be include the extension while opening the pdf? 
just dumb questions :???:

---

