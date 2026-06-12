---
title: "Problem with Kile (compiling with pdflatex)"
date: 2005-12-23
forum: General Help
---

### Post by UeB on 2005-12-23
First i am not sure if this is the right place to ask but the forum in the kile hompage seems not be used very often and i want to fix my problem quckly.

The Problem:
I got some .tex files from a friend and i can creat pdf files from them without problems but if i try to edit this tex files with kile i get loads of errors even if i only add a space to a comment.
the problems acure as soon as kile has to save the tex files and the friend who sended me the files were created with winedit so i thourght it is some sort of coding problem an i tried dos2unix before i edited the tex files but errors were exacly the same.
If i do the same changes with gedit and then compile the edited tex file with kile to pdf everything is fine! so it must be a problem with kile or the editor of kile.

thanks!

---

### Post by afhp on 2005-12-23
What are the errors that you get ?

---

### Post by UeB on 2005-12-23
just some bullshit that has nothing to do with the changes i made like:
[PDFLaTeX] numerik3.tex => numerik3.pdf (pdflatex)
[PDFLaTeX] finished with exit status 1
./chapter1.tex:184:Overfull \hbox (4.00525pt too wide) in paragraph
./chapter1.tex:1194:Paragraph ended before \text@ was complete.
./chapter1.tex:1194:Missing $ inserted.
./chapter1.tex:1194:Missing } inserted.
./chapter1.tex:1194:Display math should end with $$.
./chapter1.tex:1194:Extra }, or forgotten \endgroup.
./chapter1.tex:1288:\begin{equation*} on input line 1190 ended by \end{proof}. \end{proof}
./chapter1.tex:1321:Overfull \hbox (23.92662pt too wide) in paragraph
./chapter1.tex:1402:Overfull \hbox (7.50266pt too wide) in paragraph
./chapter1.tex:0:Underfull \vbox (badness 1337) has occurred while \output is active []
./chapter1.tex:1574:Paragraph ended before \text@ was complete.
./chapter1.tex:1574:Missing $ inserted.
./chapter1.tex:1574:Missing } inserted.
./chapter1.tex:1574:Display math should end with $$.
./chapter1.tex:1574:Extra }, or forgotten \endgroup.
./chapter3.tex:0: destination with the same identifier (name{theorem.\protect \T1\textsection \protect \kern +.1667em\relax 2.1}) has been already used, duplicate ignored\penaltyl.375 \begin{theo}
./chapter3.tex:0: destination with the same identifier (name{theorem.\protect \T1\textsection \protect \kern +.1667em\relax 2.2}) has been already used, duplicate ignored\penaltyl.531 \begin{theo}
./chapter4.tex:0:Underfull \vbox (badness 10000) has occurred while \output is active []
./chapter4.tex:0: destination with the same identifier (name{theorem.\protect \T1\textsection \protect \kern +.1667em\relax 5.1}) has been already used, duplicate ignored\penaltyl.756 \begin{theo}
./chapter4.tex:0: destination with the same identifier (name{theorem.\protect \T1\textsection \protect \kern +.1667em\relax 5.2}) has been already used, duplicate ignored\penaltyl.816 \begin{theo}
./chapter4.tex:0: destination with the same identifier (name{theorem.\protect \T1\textsection \protect \kern +.1667em\relax 5.3}) has been already used, duplicate ignored\penaltyl.877 \begin{theo}
./chapter4.tex:0: destination with the same identifier (name{theorem.\protect \T1\textsection \protect \kern +.1667em\relax 6.1}) has been already used, duplicate ignored\penaltyl.1071 \begin{theo}
numerik3.tex:15:\begin{equation*} on input line 1569 ended by \end{document}. \end{document}
[PDFLaTeX] 12 errors, 6 warnings, 5 badboxes
(and i only changed a COMMENT i line ONE and before the change it only had 6 warnigs)

but as i said if i do the same changes with gedit everything is fine.

---

