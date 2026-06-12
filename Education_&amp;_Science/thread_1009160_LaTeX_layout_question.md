---
title: "LaTeX layout question"
date: 2008-12-12
forum: Education &amp; Science
---

### Post by mister_pink on 2008-12-12
Hi all,

Just wondering if anyone has any ideas on how to solve this quite specific layout requirement. I'd like to be able to have a document with all the text on right hand pages, and then be able to define two types of figure, in-line ones with text wrapping, and then for larger figures I want to be able to place them on the facing pages on their own.

Any ideas? 

Cheers.

---

### Post by unihiekka on 2008-12-12
For that, you'd have to write your own definitions. As far as I can tell, such specific requirements are not in any packages available on CTAN.

---

### Post by mister_pink on 2008-12-12
I suspected that might be the case, but I don't really know where to begin. Can anyone point me in the right direction? I know how to create my own macros etc but I'm not sure how to even begin doing this.

I've not been doing latex for very long but I'm keen to get stuck into it, its quite good fun messing about instead of doing the actual content...

---

### Post by hubie on 2008-12-13
[This post]("http://www.latex-community.org/viewtopic.php?f=5&t=1089&p=3837") might be of some use.  It tells how to put figures and tables on verso and text on recto.

If you want to change the layout of figures on float pages, you might be interested in [floatpag.sty]("http://www.ctan.org/tex-archive/help/Catalogue/entries/floatpag.html").

---

### Post by mister_pink on 2008-12-13
Excellent, thanks. That's almost hit the spot. I'll have to play around a little more. I've commented out that line as per the bottom of the post, and the only thing that isn't quite right is that if there aren't any floats then I'd rather it put a blank page rather than text.

I tried adding \clearpage to one of the if statements but that didn't seem to work as I expected.

---

### Post by hugmenot on 2008-12-13
This is definitely not the right forum for this question.

The most experts are on the usenet newsgroup [comp.text.tex]("http://groups.google.com/group/comp.text.tex") or on [mailinglists]("http://www.tug.org/mailman/listinfo") found on tug.org

There&#8217;s also this forum: [www.latex-community.org](www.latex-community.org)

---

