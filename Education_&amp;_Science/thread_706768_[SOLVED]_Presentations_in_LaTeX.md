---
title: "[SOLVED] Presentations in LaTeX?"
date: 2008-02-24
forum: Education &amp; Science
---

### Post by northern lights on 2008-02-24
At a recent conference, someone ran a presentation that layout wise looked very much as if it was done in LaTeX - is the such a style/package (i.e. instead of "book" or "article" can you make a presentation)?

---

### Post by Whiffle on 2008-02-24
[http://latex-beamer.sourceforge.net/](http://latex-beamer.sourceforge.net/)

Maybe?

---

### Post by ajeetraj on 2008-02-24
Hello, 

The easiest way to do it is is the following:

1. Download and install LaTeX Beamer class, which is used by most of the people for awesome presentations:
```
sudo apt-get install latex-beamer
```

The also you should get the user-guide from [here]("http://www.ctan.org/tex-archive/macros/latex/contrib/beamer/doc/beameruserguide.pdf")

2. To update it:

```
texmf/tex/latex/beamer
```

3. To test it:
```
beamer/solutions/generic-talks
```

Hope this helps :)

---

### Post by DaBigEd on 2008-02-24
I use latex/Beamer for all my presentations and would highly recommend it. There are also Poster classes out there if you need to prepare a poster for a conference.
[http://andreas.welcomes-you.com/projects/a0poster/](http://andreas.welcomes-you.com/projects/a0poster/)

---

### Post by ahmatti on 2008-02-28
There is also the class prosper [http://prosper.sourceforge.net/](http://prosper.sourceforge.net/) that I personally use and like a lot! I don't know how it compares to beamer since I never tried it...

---

### Post by NikoC on 2008-02-29
I also use beamer for making presentations... only the look of the audience -that most of the time only knows powerpoint- when they see the layout is so rewarding :)

---

### Post by DrOlaf on 2008-02-29
Likewise, I use latex-beamer - and I also use [KeyJnote]("http://keyjnote.sourceforge.net/") to process and present the final pdf. That has some really nice features (zooming in on a slide, highlighting areas) as well as some funky transitions.

The problem with using software that does things Powerpoint users never dream of is that I sometimes have the following conversations after my lecture:

Student: Nice presentation. How did you do that spotlight thing on the figure in your first slide?

Me: Do you remember what the content of the first slide was?

Student: Not really, but the effect was really cool.

Me: Where's the overhead projector and the Sharpies?

---

