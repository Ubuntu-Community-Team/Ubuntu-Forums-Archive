---
title: "Kile + Sweave: 1 step compilation"
date: 2011-05-05
forum: Education &amp; Science
---

### Post by mech14 on 2011-05-05
I have set up Kile 2.0.1 and Sweave on my OSX hackintosh to typeset from *.Rnw -> *.PDF in 1 step, as a shortcut. The steps to set it up on Linux should be the same, and should work with the Beta of the new one as well, not sure.

This required me to set up several stages of the build and then add them all into a QuickBuild tool. In all, 3 steps are being done:

1) Sweave: Rnw -> tex
2) PDFLaTeX from Sweave product: tex -> PDF
3) View PDF: open PDF

Here are the steps how to set it up:
Click on Settings -> Configure Kile -> Tools -> Build

1) Creating a SWEAVE build tool:
a) Create "New Tool...", Give it a name like "Sweave", click "<Custom>", select PDFLaTeX from the menu
b) Under the "General" tab inside "Command:", type in 
        R CMD Sweave
c) Under "Options:", type in:
        '%source'
(Note the single quotes for the Options)
d) Make sure the 3 check-marks are selected
e) Advanced tab: make sure the following are selected:
-Type: Run outside of Kile
-Class: Latex
-Source extension: Rnw
-Target extension: tex
-the rest of them are blank/default
d) Menu tab: choose "other" or anywhere you want it

2) PDFLatex from Sweave:
a) Again, create "New Toll...", give it a name like "PDFLaTeXfromSweave", click "<Custom>", select PDFLaTeX from the menu
b) Under "General" tab, inside "Command:" type in:
         pdflatex
c) Under "Options:" type in:
         -interaction=nonstopmode -synctex=1 '%S.tex'
d) Make sure the 3 check-marks are selected
e) Advanced tab: make sure the following are selected:
-Type: Run outside of Kile
-Class: Latex
-Source extension: tex
-Target extension: pdf
-the rest are black/default
d) Menu tab: choose "other"

3) QuickSweave:
a) Create "New Tool...", give a name like "QuickSweave", click on "<Custom>" and select QuickBuild
b) Under "General" tab, click Add then add these 3 tools:
-Sweave
-PDFLaTeXfromSweave
-ViewPDF
b) "Menu" tab: choose where you want this to appear
c) Enter for changes to take effect

4) Create a shortcut:
-Settings -> Configure Shortcuts and create a shortcut for the new QuickSweave build.

DONE!

Keep in mind that instead of PDFLatex you can use 'latexmk'. You'll have to figure out how to make it run. This is useful if you use Bibtex or other tools to compile your Rnw file.

Have fun

---

### Post by SkippoGuangiacomo on 2011-07-25
Cheers for that. It was very helpful! 

Thank you very much!

---

### Post by komunisk on 2011-10-17
Very helpful! It will save me a lot of time!

Thanks!

---

### Post by iseppo on 2011-10-28
This does not seem to work in (K)ubuntu 11.10 (Kile 2.1.0, KDE 4.7.2). I get "[Sweave] failed to start" messages in the "Log and Messages" tab while Output tab has everything correctly:

[FONT="Courier New"]
*****
*****     Sweave output: 
*****     cd "/home/[...]/p2ringandmed"
*****     R CMD Sweave /home/[...]/p2ringandmed/lopetajad.Rnw
*****
[/FONT]

(running the last line in Konsole works by itself)

It seems to be a bug in Kile, as I think I have tried most everything.

---

### Post by tweev69 on 2011-10-28
Yup me 2.  I thought I had it working about 2 hours ago but then I have NO clue what i did.

I was just trying to get the sweave part to work.  Annoying.  Bash file it is.

---

