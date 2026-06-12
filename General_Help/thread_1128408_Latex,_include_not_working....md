---
title: "Latex, include not working..."
date: 2009-04-17
forum: General Help
---

### Post by jsjohnsen on 2009-04-17
Hi...

I am pretty new in the linux world, so the answer to this question is properly pretty simple.

I can not get the include function in LaTeX to work, if the file is not located in the same folder as the main file.

I wrote this example

\documentclass[11pt]{report}

\begin{document}
Hello world
% first include
\include{test2}
% second include
\include{../test2}

\end{document}

The first include is working but the second is not - Why?
The error message I get is:

[PDFLaTeX] Test.tex => Test.pdf (pdflatex)
[PDFLaTeX] finished with exit status 1
./Test.aux:0:No file ./../test2.aux.
Test.tex:6:I can't write on file `../test2.aux'. \include{../test2}
Test.tex:6:Emergency stop. \include{../test2}
[PDFLaTeX] 2 errors, 1 warning, 0 badboxes

and through the Gui I have set the permissions to read and write and create and delete files, inclding all files and sub folders, any idears of what is wrong??

---

### Post by jsjohnsen on 2009-04-17
The solution was simple....

you can not use \include{} to insert a tex file, to do this you must use \input{}

Of some unknown reason this works in windows with miktex, but not in linux.

Best Regards
Jesper

---

