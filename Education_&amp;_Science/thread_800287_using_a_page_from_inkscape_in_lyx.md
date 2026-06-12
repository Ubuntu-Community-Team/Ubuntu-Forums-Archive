---
title: "using a page from inkscape in lyx"
date: 2008-05-19
forum: Education &amp; Science
---

### Post by miko3k on 2008-05-19
Hi, I would like to use a full page drawn in inkscape in document written in lyx.

I tried exporting as .tex, added \usepackage{pstricks} to preamble and included my .tex file, but it produces lots of errors about unterminated control sequences. Actually I'm not even sure if this is right way to do the job.

I have chosen inkscape because I have no idea, how to craft page like this in inkscape: [http://img503.imageshack.us/my.php?image=asdfht2.png](http://img503.imageshack.us/my.php?image=asdfht2.png). Box in the lower part of page must be of precise size at precise location.

Of course, another option could be print them separately, or use some tool to merge pdf files together but I don't like it.

Any hints are appreciated :-)

---

### Post by amyst on 2008-05-20
If all you want to do is draw a box and put some text in at the precise location to the mm, you can do that directly in your latex editor without Inkscape. 

With Inkscape, I have never successfully converted .svg files to anything other than .svg. (I would be happy to know if this is wrong)

Information on drawing precise box can be find in Producing Mathematical Graphics section of lshort.pdf

---

