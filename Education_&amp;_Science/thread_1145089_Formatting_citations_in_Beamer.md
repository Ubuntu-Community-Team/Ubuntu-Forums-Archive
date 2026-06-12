---
title: "Formatting citations in Beamer"
date: 2009-05-01
forum: Education &amp; Science
---

### Post by InfernalNeutrino on 2009-05-01
Hi,

So I'm creating a presentation regarding some of my work, and am in the process of learning the ropes of Beamer. Now, in my field it is customary to provide citations at the bottom of presentation slides and I was wondering if there was a method of automatically achieving this without using, say, the \vspace command to manually set the position. I attach the example source and a .pdf of it to illustrate what I mean. As you will see, the citation appears directly beneath the figure I am citing. I could manually move it down, but if I modify the slide it will mess up the layout. Hence the auto-bottom question. If anyone has any ideas, I would be most grateful. Cheers!

---

### Post by mister_pink on 2009-05-02
Well, initially I was just going to suggest you use \footnote, but that of course requires that you then have a number somewhere else refering to it... 

So, the easiest thing I can think of is to use something like this:

```
\footnotetext{\tiny{Steiner, et al., arXiv:0711.4652 [nucl-ex]}}
```
And to get rid of the number "0", add something like this to your headers
```
\renewcommand{\thefootnote}{}
```
and if you don't want the line, I think you need to add this to your headers:
```
\renewcommand{\footnoterule}{}
```

Not ideal perhaps...

---

