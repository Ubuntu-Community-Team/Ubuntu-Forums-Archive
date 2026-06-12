---
title: "help with Latex compiler"
date: 2009-03-06
forum: General Help
---

### Post by ltrane2003 on 2009-03-06
I have made the move to Ubuntu and trying to use a Latex editor (Kile) having a problem with tikz file. I have installed tex live and the dot2tex package but when i try to run an existing Latex file it will not compile this is what i get 

! LaTeX Error: File `tikz.sty' not found. 

I am not sure if I congigured kile correctly. Also i get the same error in the terminal when i complile the same file.

here is the code where the error occurs

documentclass[12pt]{amsart}

\newtheorem*{problem}{Problem}
\newcommand{\bfrac}[2]{\displaystyle \frac{#1}{#2}}
\newcommand{\limit}[2]{\displaystyle \lim_{{#1} \rightarrow{#2}} }
\newcommand{\SU}{\subseteq}
\newcommand{\mb}[1]{\mathbb{#1}}

\usepackage{tikz,fullpage,amsmath,amssymb,amsthm}
\usepackage{fancyhdr}
\pagestyle{fancy}
\fancyhead[RE]{\rightmark}  
\fancyhead[RO]{\rightmark}        
\fancyhead[LE]{\leftmark}
\fancyhead[LO]{\leftmark}
\renewcommand{\headrulewidth}{0pt} 
\renewcommand{\footrulewidth}{0pt}  
\headheight 15pt
\headsep 20pt

---

### Post by renebs on 2009-03-06
Hi,

Run
$ mkdir -p ~/texmf/tex/latex/ 
if you still don't have those in your /home/user folder yet.
In case you do, search the web for this tikz.sty file,
go to your "local" latex folder (/home/user/texmf/tex/latex) create a folder with the name tikz, save in that folder your .sty file. and then update your latex by running:
$ texhash
hope this helps

---

