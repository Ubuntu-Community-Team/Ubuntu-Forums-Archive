---
title: "Nice R-Source highliting in Latex"
date: 2009-08-14
forum: Education &amp; Science
---

### Post by JPBurgard on 2009-08-14
Im trying to incorporate an R-Code into my latex document. As it is a bit longer i'ld like to have some highliting in order to improve readability.

I tried the listings Package and used also the literate option as described in [http://www.opensubscriber.com/message/r-help@stat.math.ethz.ch/4978909.html](http://www.opensubscriber.com/message/r-help@stat.math.ethz.ch/4978909.html) and [https://vgoulet.act.ulaval.ca/svn/documents/intro_S/trunk/introduction_programmation_S.tex](https://vgoulet.act.ulaval.ca/svn/documents/intro_S/trunk/introduction_programmation_S.tex)

But in my code I specify e.g. x.mean. And listings prints "**mean**" in bold even in combination with "x.**mean**".

My idea was that maybe the highliting from either kate or gedit could be used. But I did not find a way to transform the displayed highlited text into latex code.

Does somebody have an idea?

Thanks in advance,
Jan Pablo

---

### Post by gunksta on 2009-08-14
I am definitely NOT a LATEX wizard, but this might help. I know that vim can output syntax highlighting as HTML. If you then transform the HTML to LATEX (I don't know how to do that part) you could get the syntax highlighting you want.

It's just a thought and I'm not sure it's a good one.

---

### Post by ahmatti on 2009-08-18
I have used the this style file for Matlab  [http://www.mathworks.com/matlabcentral/fileexchange/8015](http://www.mathworks.com/matlabcentral/fileexchange/8015) and I like the output it produces. Its fairly easy to modify to produce similar results for R. Just changing the keywords for corresponding R ones and changing the comment character gives you a start. 

HTH

---

### Post by XCan on 2009-08-18
Kewl, thanks for sharing the link ahmatti. May indeed come in handy to write instructions for slow students. :)

---

