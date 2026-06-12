---
title: "Lyx typesetting format"
date: 2010-05-11
forum: Education &amp; Science
---

### Post by nandugopan on 2010-05-11
Hi all,
       I am trying to use LyX to typeset my Masters Thesis..But I have run into some issues. My University thesis format requires:

Chapter heading: Times New Roman 14 pt bold Capitals Centered
Section headings:Times New Roman 12 pt bold Capitals Left adjusted
Subsection headings: Times new Roman 12 pt  sentence case Left adjusted
Paragraph headings: Times new Roman 12 pt bold  sentence case Left adjusted
Body of thesis: Times new Roman 12 pt Adjusted on both left and right with 1.5 spacing for text and double spacing for equations.

Left Margin: 1.5 inch
Right Margin:1.25 inch
Top Margin 2 inch on pages where chapter begins, 1 inch on all other pages
Bottom Margin: 1.25 inch

I just cant get the format right. Could anyone suggest an appropriate class, or changes that can be made into the LaTeX preamble, so that I can meet these requirements. Thanks in advance,
Nandu

---

### Post by sanderd17 on 2010-05-11
for the margins in LaTeX, you can look at the page [http://en.wikibooks.org/wiki/LaTeX/Page_Layout]("http://en.wikibooks.org/wiki/LaTeX/Page_Layout")

I'll do a searh on how to import another lettertype into LaTeX.

---

### Post by sanderd17 on 2010-05-11
```

\usepackage[12pt]{article}

\usepackage{mathptmx}
\usepackage{setspace}
\usepackage{titlesec}

\titleformat*{\chapter}{\fontsize{14pt}{14pt}\selecfont}
\titleformat*{\section}{\fontsize{12pt}{12pt}\selecfont}
\titleformat*{\subsection}{\fontsize{12pt}{12pt}\selecfont}
\titleformat*{\paragraph}{\fontsize{12pt}{12pt}\selecfont}


```

I guess this should do the sizes, I didn't try it myself. I don't know hwat you meen with Capital centered and those other tings so I can't help with that.

source: [http://www.tug.org/pipermail/texhax/2010-February/014293.html]("http://www.tug.org/pipermail/texhax/2010-February/014293.html")

---

### Post by hubie on 2010-05-11
Check with your university computer department.  Many universities provide a thesis template for you to use.  Mine used to provide them for LaTeX, Word, and Wordperfect. (OK, so it was a while ago....) :)

---

### Post by nandugopan on 2010-05-12
Thank you guys for your prompt replies.

@hubie: I checked with my Department and the University Computer Department. They do not have a LaTEX or LyX format. They suggest doing it on word. I prefer to do this in LyX for obvious reasons.

@sanderd17: Thanks for the code. But it doesnt seem to work for me. I t returns some errors. I have attached a screenshot herewith. Sorry, but I am quite new to LyX and have no working experience of LaTEX. 
 
Regards,
Nandu

---

### Post by sanderd17 on 2010-05-12
I think I've got the titles, can you import this in LyX? I'm not used to work with LyX.
```

\documentclass[12pt]{book}


\usepackage{mathptmx}
\usepackage{setspace}
\usepackage{titlesec}

\titleformat{\chapter}[display]
  {\fontsize{1pt}{1pt}\selectfont}
  {%\titlerule[1pt]%
   %\vspace{1pt}%
   %\titlerule
   \vspace{1in}%
   %\LARGE\MakeUppercase{\chaptertitlename} \thechapter
   }
  {1pc}
  {\titlerule
   \vspace{1pc}%
   \large\bf
   \chaptertitlename\ \thechapter: }




\titleformat*{\section}{\fontsize{12pt}{12pt}\selectfont}
\titleformat*{\subsection}{\fontsize{12pt}{12pt}\selectfont}
\titleformat*{\subsubsection}{\fontsize{12pt}{12pt}\selectfont}
\titleformat*{\paragraph}{\fontsize{12pt}{12pt}\selectfont}


\begin{document}
 \chapter{ch}
 \section{sec}
 \subsection{subsec}
 \subsubsection{subsubsec}
 \paragraph{par}
 
\end{document}


```

For the margins: see wikibooks.

This I have found in the titlesec package info.

---

### Post by nandugopan on 2010-05-12
@sanderd17

I tried saving it as a tex file and importing it to LyX..and then copy pasting my matter onto it. The output is all garbled up, not at all formatted

---

### Post by sanderd17 on 2010-05-12
Can you export your paper to tex, add those things to the head, save the tex and import is back into lyx?

---

### Post by sanderd17 on 2010-05-12
Just tought of somethint. If you install the writer2latex package, you can define your layout in openoffice, export it to latex and copy the header of the LaTeX file to your LaTeX file (please keep a backup). Maybe that will work. Or export your file with LyX to Open document, change the markup profiles with openoffice, export back to plain latex and import in LyX. It's yours to try.

---

### Post by kleeman on 2010-05-13
This site might be useful:

[http://www.thesis-template.com/](http://www.thesis-template.com/)

You may need to take one of the templates given and modify it to meet your institutions requirements. If you look at the Help in Lyx under customization they explain how to do this. It is complicated but having a template reasonably close would help I think. Disclaimer: I have never done this. 

Another option is to search for appropriate latex templates. Use lyx to write the thesis and then export to latex and then cut and paste into a template file. I use this for journal papers.

---

### Post by nandugopan on 2010-05-14
@kleeman and sanderd
Thank you for your inputs. But I cant seem to get them to work. I did not get a similar thesis format and because I am not advanced enough a user to switch between LATEX and LyX. But thanks for the help guys..

---

