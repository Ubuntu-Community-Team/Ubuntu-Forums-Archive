---
title: "Lyx question - latex preamble"
date: 2008-06-20
forum: Education &amp; Science
---

### Post by gatorbrit on 2008-06-20
Hi, I am trying to learn LateX using Lyx.  I like it so far.  Here is a question.

I want to put something in the header, and I understand I need to insert 
```
\lhead{my blurb}
```
into the LaTeX preamble.
So in LyX I go -> Document -> Settings -> latex Preamble 
and I type that in the box.

When I try to create the DVI file I get this error..

```
Undefined control sequence
LaTeX Error: Missing \begin{document}
```

But when I put in the \begin document after (or before) the \head I still get the same or similar error.

Thanks

Rich

---

### Post by timmie on 2008-06-24
PLease search here:
[http://news.gmane.org/gmane.editors.lyx.general](http://news.gmane.org/gmane.editors.lyx.general)

I did have this problem sometimes. But it is a issue of how latex and lyx interrelate. Sometimes you'll have to insert a title or author into the document.

---

