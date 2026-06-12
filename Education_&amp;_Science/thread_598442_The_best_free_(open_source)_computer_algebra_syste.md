---
title: "The best free (open source) computer algebra system (CAS) software in your experience"
date: 2007-10-31
forum: Education &amp; Science
---

### Post by wirawan0 on 2007-10-31
What is the best CAS software in your experience? Please let me know of your experiences, what you are using it for, etc. If you have experience with more than one, let me know. Please share what you like and what you don't like about it. I am trying out AXIOM, Maxima, yet still can't settle with one of these. I often trigger the bugs in them, causing them to crash.

What are options available out there? I know these:
[LIST]
[*]maxima
[*]axiom
[*]mathomatic (just knew about this a few hours ago)
[*]what else?
[/LIST]

Wirawan

---

### Post by lad.kocb on 2007-11-05
I think the best will become sage

[http://www.sagemath.org/]("http://www.sagemath.org/")

since it contains e.g. maxima embedded and the aim
seems to be to include as much as possible.

The sage download is about 300 MB, since it contains
preconfigured python with libraries and maxima as well as
other independent CAS.

It is all about 
"Building the Car Instead of Reinventing the Wheel"
as the [www.sagemath.org](www.sagemath.org) says

---

### Post by iml on 2007-11-15
SAGE is great but probably overkill if you only need to use Maxima. Moreover all of the major constituent packages are already in the Ubuntu repositories. You can also use their web interface without installing anything. PARI and GAP are also important computer algebra systems; it's worth looking over the SAGE wiki at what software they've chosen to fill specific needs.

---

### Post by wirawan0 on 2007-11-24
Ah... finally there is a reply! I looked into sage after I saw your posting. Thanks for pointing out. Looks very nice. I read recently an article in Computing in Science and Engineering (CiSE) about Python / iPython being used as numerical workbench (somewhat like octave). So this is a nice continuation if we can work everything in python. It's interesting that there was no reference to Maxima as its predecessor  in the website. What is it based on, then? Is it a newly written CAS software, basically?

---

### Post by Matthew Bartram on 2007-11-30
I think SAGE is written as a moderately basic CAS with the power of linking together multiple other CASses to create a very powerful system.
I haven't done much with SAGE, though it looks very good. On the occasion that I tend to just use maxima, in the form of wxMaxima.
What I would like to see with SAGE, is being built into a deb, and linked with other libraries properly rather than having them all in its download - so it would use the native python, native maxima, etc., and install properly, rather than just sitting in whatever directory you put it in.
Also nice would be to be able to import it via one import command in python - so you can easily use it from within a preferred python IDE.

Maxima at the moment seems to have a problem with drawing graphs. And it's had other significant bugs before - I don't know if this is a trend, or if it's normally quite reliable.

SAGE, when in the notebook mode (an interface through a browser), sometimes seems to get stuck, so I have to stop it (from within the notebook, not hard kill) and start it again.

---

### Post by omologos on 2010-11-07
> **Matthew Bartram said:**
> I think SAGE is written as a moderately basic CAS with the power of linking together multiple other CASses to create a very powerful system.
I haven't done much with SAGE, though it looks very good. On the occasion that I tend to just use maxima, in the form of wxMaxima.
What I would like to see with SAGE, is being built into a deb, and linked with other libraries properly rather than having them all in its download - so it would use the native python, native maxima, etc., and install properly, rather than just sitting in whatever directory you put it in.
Also nice would be to be able to import it via one import command in python - so you can easily use it from within a preferred python IDE.

Maxima at the moment seems to have a problem with drawing graphs. And it's had other significant bugs before - I don't know if this is a trend, or if it's normally quite reliable.

SAGE, when in the notebook mode (an interface through a browser), sometimes seems to get stuck, so I have to stop it (from within the notebook, not hard kill) and start it again.

Making a .deb for sage is a very complicated task. It has many dependencies, and it needs to use ver particular versions to work, as well as a very particular environment. 

Importing all of sage as a Python library is even more difficult. Focusing in those things would heavily halt sage development.

---

### Post by LordDelta on 2011-01-15
I'd have to agree on the SAGE count.

It also is to my knowledge the only package to rival the commercial Mathematica with a free online version, [http://www.sagenb.org/](http://www.sagenb.org/)

Not as pretty, but not bad either. I've used it for a couple classes, and Wolfram's online version has plenty of holes in it as well, despite the nicer gui.

Though, I'm not the most knowledgeable user on the subject of math packages, admittedly.

---

