---
title: "LaTex section problems"
date: 2011-10-14
forum: Education &amp; Science
---

### Post by jesper.okko.olausson on 2011-10-14
I'm writing my thesis using Latex but I've run into some problems. 
- I have a quote, the abstract in swedish, an english translation of the  abstract and the foreword before the begin(document) statement 
(writing this message on a mac so I don't know how to to all the proper  symbols) 

Those parts are all fine but everything after the begin(document)  statement become really strange? 
- All the section titles are on the same line as the text following it.
- The swedish letters ä and ö become a and o. 
- The ring in å is raised one half of a line above the ''a'' part of the  letter. 

When I tried to put the begin(document) statement before the first parts  then they also become as weird looking as the rest of the text. 

The beginning of my latex file looks like this:
\usepackage[utf8]{inputenc}
\usepackage[swedish]{babel}
\usepackage{amsmath}
\usepackage{graphicx}
\usepackage{makeidx}
\usepackage{float}




\title{Förändringar i reporäntan, hur påverkar de kvadratmeterpriset på bostadsrätter}
\author{Jesper Okko-Olausson}

\maketitle
\pagebreak


\maketitle
\vspace*{\fill}
\begin{center}

``What we know about the global financial crisis is that we don't know very much.''\\
Paul Samuelson - Pristagare av Sveriges Riksbanks pris i ekonomisk vetenskap till Alfred Nobels minne 1970

\end{center}
\vspace{\fill} 
\pagebreak


And then the the abstract in swedish, an english translation of the abstract and the 
foreword with the same statements to get them centered on separate pages before 



\begin{document}
\tableofcontents
\pagebreak





\section{Introduktion}

---

### Post by FreeTheBee on 2011-10-15
When I put the \begin{document} after the usepackage declarations everything looks fine here.

---

