---
title: "R latex and OpenOffice"
date: 2010-06-15
forum: Education &amp; Science
---

### Post by orduek on 2010-06-15
Hi,
I'm using R to do some analysis for my Phd. 
In order to output some of the summaries of lm function I found a nice function that helps me build a nice table calls apsrtable.
This function output is a latex code that builds the table.
I' using openoffice in order to write my dissertation so I need to find a way to transform the nice latex table into my OO document.

Is there any solution?
Thank you.

---

### Post by gunksta on 2010-06-15
Yes, there is. Sweave is one of the coolest technologies built into R, but the default version is rather limited in that it wants to do latex only. Fortunately, this can be rectified.

You are going to want the [odfweave]("http://cran.r-project.org/web/packages/odfWeave/index.html") package.

A quick explanation - When I have used it in the past, I first wrote a R script that performed my analysis. Then, without leaving R, I run through my .odt file. It works just like sweave. You write your R code directly into the OOo file. Odfweave runs through the XML file, looking for R syntax, runs the code, and sticks the output into the file.

I have only had the opportunity to use this amazing piece of technology once, but it was really really amazing. If you get stuck during your project let me know.

---

### Post by hzambran_cl on 2010-06-15
You may try **latex2rtf** ([http://latex2rtf.sourceforge.net/]("http://latex2rtf.sourceforge.net/")) with a latex document containing your table, to create an rtf document, which you can easily import to  OOo.

---

### Post by earlycj5 on 2010-06-15
I'd second gunksta's recommendation.

latex2rtf is nice for a quick and dirty conversion, but for tables or other items that have formatting I'd pass and use odfweave.

Actually, I just used Latex for my dissertation.  ;)

---

### Post by orduek on 2010-06-17
thank you for the ideas.
For now apsrtable seems the most straight forward in creating a nice publishable table without to much trouble.
It seems that odfWeave requires a bit more complex learning.

---

