---
title: "Difficulties with media9 package"
date: 2012-10-17
forum: Education &amp; Science
---

### Post by expz on 2012-10-17
Having trouble installing/using the media9 package with texlive.

Error:
I try to compile the file test.tex:

\documentclass{article}
\usepackage[english]{babel}  % Rumored to be required by media9, language irrelevant
\usepackage{media9}  
\begin{document}
\end{document}

using

# pdflatex test.tex

LaTeX Error: File `media9.sty' not found.

Double check:

# apt-get install texlive-latex-extra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
texlive-latex-extra is already the newest version.

texlive-latex-extra contains media9 according to this list: 
[https://launchpad.net/ubuntu/quantal/+package/texlive-latex-extra](https://launchpad.net/ubuntu/quantal/+package/texlive-latex-extra)

================
Attempted fixes:

0. Using tlmgr:

tlmgr: command not found. It looks like Ubuntu took it out?

1. Manually adding media9 package:

$ sudo -i
# kpsewhich -var-value TEXMFLOCAL
/usr/loca/share/texmf
# unzip media9.zip -d /usr/loca/share/texmf
# texhash
# pdflatex test.tex

This had no effect.

2. Unzip media9.zip from CTAN into my source folder.

Of course, now pdflatex finds the style file, but it couldn't compile it. The error was:

! Undefined control sequence.
<argument> \msg_error:nnn 
           {media9}{support outdated}{l3kernel}\tex_endinput:D 

I commented out similar lines (it looks like error handling) and produced similar errors:

! Undefined control sequence.
l.90 \pdftex_if_engine:T

etc.

================
Configuration:
* Ubuntu 12.04 
* texlive-full 

This  looks like something Google would solve in a jiffy, but I couldn't find  anyone with similar problems. Much thanks to anyone who can help.

---

