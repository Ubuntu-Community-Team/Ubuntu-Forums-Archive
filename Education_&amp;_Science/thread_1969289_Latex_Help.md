---
title: "Latex Help"
date: 2012-04-29
forum: Education &amp; Science
---

### Post by DBQ on 2012-04-29
Hi everybody I am using a non-standard latex document class.  I need the chapters to have the following format:

Chapter 1

Chapter Title

However, when I do \chapter{Chapter Title} I only get:

1 Chapter Title


Below is the portion of the package that deals with a chapter command. Any ideas?

```

\def\5{\penalty500 }
\newcommand{\errexa}{\par\noindent\textit{Example}:\ }
\newcommand{\errexpl}{\par\noindent\textit{Explanation}:\ }
\renewcommand\chapter{\par \@afterindentfalse
                    \secdef\@chapter\@schapter}
\def\@chapter[#1]#2{\ifnum \c@secnumdepth >\m@ne
                       \if@mainmatter
                         \refstepcounter{chapter}%
                         \typeout{\@chapapp\space\thechapter.}%
                         \addcontentsline{toc}{chapter}%
                                   {\protect\numberline{\thechapter}#1}%
                       \else
                         \addcontentsline{toc}{chapter}{#1}\fi
                    \else
                      \addcontentsline{toc}{chapter}{#1}
                    \fi
                    \chaptermark{#1}%
                    \addtocontents{lof}{\protect\addvspace{10\p@}}%
                    \addtocontents{lot}{\protect\addvspace{10\p@}}%
                    \if@twocolumn
                      \@topnewpage[\@makechapterhead{#2}]%
                    \else
                      \@makechapterhead{#2}%
                      \@afterheading
                    \fi}
\def\@makechapterhead#1{%
  \vspace{1.5\baselineskip}%
  {\parindent \z@ \raggedright \reset@font
    \ifnum \c@secnumdepth >\m@ne
      \large\bfseries \@chapapp\space\thechapter
      \par\nobreak
      \vskip.5\baselineskip\relax
    \fi
    #1\par\nobreak
    \vskip\baselineskip
  }}
\def\@schapter#1{\if@twocolumn
                   \@topnewpage[\@makeschapterhead{#1}]%
                 \else
                   \@makeschapterhead{#1}%
                   \@afterheading
                 \fi}
\def\@makeschapterhead#1{%
  \vspace*{1.5\baselineskip}%
  {\parindent \z@ \raggedright
    \reset@font
    \large \bfseries  #1\par\nobreak
    \vskip\baselineskip
  }}
\def\@removefromreset#1#2{\let\@tempb\@elt
   \expandafter\let\expandafter\@tempa\csname c@#1\endcsname
   \def\@elt##1{\expandafter\ifx\csname c@##1\endcsname\@tempa\else
         \noexpand\@elt{##1}\fi}%
   \expandafter\edef\csname cl@#2\endcsname{\csname cl@#2\endcsname}%
   \let\@elt\@tempb}
\@removefromreset{footnote}{chapter}
\def\ps@headings{%
  \let\@oddfoot\@empty\let\@evenfoot\@empty
  \def\@evenhead{\thepage\hfil{\footnotesize\leftmark{}{}}}%
  \def\@oddhead{{\footnotesize\rightmark{}{}}\hfil\thepage}%
  \let\@mkboth\markboth
  \def\chaptermark##1{%
    \markboth {\uppercase{\ifnum \c@secnumdepth >\m@ne
      \if@mainmatter
        \@chapapp\ \thechapter. \ \fi
      \fi
        ##1}}{}}%
  \def\sectionmark##1{%
    \markright {\uppercase{\ifnum \c@secnumdepth >\z@
        \thesection. \ \fi
        ##1}}}}
\renewcommand\maketitle{\par
  \begingroup
    \renewcommand\thefootnote{\fnsymbol{footnote}}%
    \def\@makefnmark{\hbox to\z@{$\m@th^{\@thefnmark}$\hss}}%
    \long\def\@makefntext##1{\parindent 1em\noindent
            \hbox to1.8em{\hss$\m@th^{\@thefnmark}$}##1}%
    \if@twocolumn
      \ifnum \col@number=\@ne
        \@maketitle
      \else
        \twocolumn[\@maketitle]%
      \fi
    \else
      \newpage
      \global\@topnum\z@   % Prevents figures from going at top of page.
      \@maketitle
    \fi
    \thispagestyle{plain}\@thanks
  \endgroup
  \setcounter{footnote}{0}%
  \let\thanks\relax
  \let\maketitle\relax\let\@maketitle\relax
  \gdef\@thanks{}\gdef\@author{}\gdef\@title{}}
\def\@maketitle{%
  \newpage
  \null
  \vskip 2em%
  \begin{center}%
    {\LARGE \@title \par}%
    \vskip 1.5em%
    {\large
      \lineskip .5em%
      \begin{tabular}[t]{c}%
        \@author
      \end{tabular}\par}%
    \vskip 1em%
    {\large \@date}%
  \end{center}%
  \par
  \uppercase\expandafter{\expandafter\toks@\expandafter{\@title}}%
  \edef\@tempa{\noexpand\markboth{\the\toks@}{\the\toks@}}%
  \@tempa
  \vskip 1.5em}
\renewcommand\tableofcontents{%
    \if@twocolumn
      \@restonecoltrue\onecolumn
    \else
      \@restonecolfalse
    \fi
    \subsection*{\contentsname}%
    \@starttoc{toc}%
    \if@restonecol\twocolumn\fi
    }

%Added some things here to move chapters to the appropriate place on the next
% line (SL 4/4/12)
\renewcommand\chapter{\newpage%
                                          \vspace*{0.5in}%
                                          \global\@topnum\z@%
                                          \@startsection{chapter}{0}{\z@}%
                                   {-.6\baselineskip \@plus -3\p@}%
                                   {.4\baselineskip}
                          {\reset@font\Large\bfseries}}
\renewcommand\section{\@startsection {section}{1}{\z@}%
                                   {-.6\baselineskip \@plus -3\p@}%
                                   {.4\baselineskip}
                          {\reset@font\large\bfseries}}
\renewcommand\subsection{\@startsection{subsection}{1}{\z@}%
                                     {-.3\baselineskip\@plus -2\p@}%
                                     {.2\baselineskip}%
                          {\reset@font\large\bfseries}}
\renewcommand\subsubsection{\@startsection{subsubsection}{2}{\z@}%
                                     {-.3\baselineskip\@plus -2\p@}%
                                     {.2\baselineskip}%
                                     {\reset@font\normalsize\bfseries}}


```

---

