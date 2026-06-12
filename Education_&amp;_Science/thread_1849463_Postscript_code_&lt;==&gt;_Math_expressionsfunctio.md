---
title: "Postscript code &lt;==&gt; Math expressions/functions"
date: 2011-09-24
forum: Education &amp; Science
---

### Post by Evanfox on 2011-09-24
Hi all,

I was wondering where can I find a converter (or something like that) to get the postscript code expression for any mathematical formula (say x^2+3x+2=0) and vice versa.

Alternatively, I would also appreciate any suggestions on postscript tutorials so that  I can do that on my own!

Cheers!!
:-)

---

### Post by BeRoot ReBoot on 2011-09-25
Why are you writing postscript manually? FYI, postscript is mostly used as an intermediate language between document markup code (ie, HTML, LaTeX) and the publishing format (pdf, dvi, etc...). What are you trying to do?

---

### Post by Evanfox on 2011-09-25
Well,I kinda have to, because I draw things in LaTeX using PSTricks: I need to be able to typeset functions in postscript.
So, any ideas??

---

### Post by pjd99 on 2011-09-25
Why aren't you using LaTeX math environment to typeset formulae/equations? Tex->DVI->PS will give you a post script version, but I can't get much from a test PS file...
I don't think I quite understand what you're trying to achieve here...

Maybe some of these links will help:
PS geometry and maths: [http://www.math.ubc.ca/~cass/graphics/manual/](http://www.math.ubc.ca/~cass/graphics/manual/)
Extracting math from PS documents:[www.cs.berkeley.edu/~fateman/papers/mly-psmath.pdf](www.cs.berkeley.edu/~fateman/papers/mly-psmath.pdf)

---

### Post by jeneverboy on 2011-09-26
For vector based graphics I use inkscape. After googling around I found textext. with this you should be able to use laTeX code

[http://typethinker.blogspot.com/2008/06/integrating-inkscape-graphics-in-latex.html]("http://typethinker.blogspot.com/2008/06/integrating-inkscape-graphics-in-latex.html")

this seems a good option

---

### Post by Evanfox on 2011-10-24
Hi guys 

I think I found a solution that might help some others working with PStricks.

You just have to include the package infixplot (in your latex document)  that converts ordinary mathematical expressions into Postcript language. It works fine for me so I suggest you check out the manual for more details! :) 

Cheers!
Evan

---

