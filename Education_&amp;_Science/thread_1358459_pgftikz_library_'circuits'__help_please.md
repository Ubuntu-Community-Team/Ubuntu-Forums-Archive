---
title: "pgf/tikz library 'circuits' ?? help please"
date: 2009-12-18
forum: Education &amp; Science
---

### Post by peter_kint on 2009-12-18
Hi,
Trying to compile a small tikz-circuit example (in Lyx) on page 289 of the pgf manual:

```
\begin{tikzpicture}[circuit ee IEC]
  \draw (0,1) to [resistor] (3.5,1);
  \draw[circuit symbol unit=14pt]
        (0,0) to [resistor] (3.5,0);
\end{tikzpicture}
```

Apparently, I dont have the correct 'circuit' library, the latex-log gives errors on this:
 p, li { white-space: pre-wrap; }  **! I can't find file `tikzlibrarycircuit.ee.code.tex'.**
How can I solve this?



1. With downloading a file and then putting it somewhere? If yes, then 

2. Where can I find this file?
3. Where do I have to put it afterwards so that Lyx can find it?
4. Can't I just install (I searched for it in synaptic) a pgf/tikz pakage with all the    libraries included?


Why is latex so good an hard at the same time? Sigh.
Thx for reading.
Peter.

---

### Post by StephenWoods69 on 2010-01-10
I'm not sure what exactly you need but if it is this file then you can get it here
[http://minimals.contextgarden.net/pragma/justtex/texmf-context/tex/generic/pgf/frontendlayer/tikz/libraries/circuits/](http://minimals.contextgarden.net/pragma/justtex/texmf-context/tex/generic/pgf/frontendlayer/tikz/libraries/circuits/)

I hope tis helps.

---

### Post by tommpogg on 2012-05-10
I have the same problem... and the link didn't help too much: what should I do with the files once I have downloaded them?

Thanks

---

### Post by overdrank on 2012-05-10
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

