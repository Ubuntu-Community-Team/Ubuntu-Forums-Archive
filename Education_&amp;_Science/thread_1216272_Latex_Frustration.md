---
title: "Latex Frustration"
date: 2009-07-18
forum: Education &amp; Science
---

### Post by DBQ on 2009-07-18
Hi everybody.  I have spent hours trying to figure this out.  When I compile my latex I gets this error:

! LaTeX Error: Float(s) lost.

See the LaTeX manual or LaTeX Companion for explanation.
Type  H <return>  for immediate help.
 ...                                              
                                                  
l.44 \end{algorithm}

Now, sometimes, commenting out a random line helps. Any pointers? I feel really frustrated.

---

### Post by beren.olvar on 2009-07-18
I have never found this error, but found this googling
[http://www.tex.ac.uk/cgi-bin/texfaq2html?label=fllost](http://www.tex.ac.uk/cgi-bin/texfaq2html?label=fllost)

If you cant find the problem right away you should try commenting out your floats one by one to see which one is the problematic.

hope it helps.
cheers!

---

### Post by DBQ on 2009-07-18
I seen this page.

What strange, is that sometimes commenting out a random line makes the error go away.

---

### Post by beren.olvar on 2009-07-18
Just wandering, because I havent seen your code, but maybe you have an extra parenthesis or brace, then commenting out a line with some combination of them may yield an ok synthax. Of course this is very unlikely to happen if you are using a syntax-highliting editor.
Maybe you could post a shorter version of your file, that keeps the error, to see what is going on?

good luck!

---

### Post by Chronon on 2009-07-18
I just discovered a bug today having to do with label declaration in figures.  Apparently, declaring a caption after the label can cause all sorts of bad numbering and confusion on what subsection a figure belongs to.

I don't know if this has anything to do with your problem, but it at least sounds a bit similar.  So maybe check to make sure that labels are declared near the end of your environment.

---

