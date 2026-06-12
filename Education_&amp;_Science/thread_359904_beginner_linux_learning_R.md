---
title: "beginner linux learning R"
date: 2007-02-12
forum: Education &amp; Science
---

### Post by thermophile on 2007-02-12
Hi
I've been running kUbuntu for about 6 months on my second puter, but still on the steep part of the learning curve.  I'd like to get into network analysis of genetic and geochemical datasets and think that R is the program for me.  a quick google search turned up tons of tutorials for R.  Do any of you R gurus have a suggestion(s) for a good general intro to R or network analysis specific tutorials?
thanks

---

### Post by WebDrake on 2007-02-12
Can you give some more idea about what you want to know on network analysis?  As in, small-world or scale free networks, degree distribution, shortest path analysis, network diameter, etc. etc. etc.?

I can't recommend you R-specific stuff as I'm a beginner in that myself, but I could recommend you some useful literature on the general network topics if that would interest you.

Since this is an R thread, can I add my own query to yours .... I know that typing "source("filename")" will read in a given file/function, but how do I automatically read in a set of functions at startup, either project-specific (when I start R in a given directory, say) or general?  R is not like Octave, it does not automatically parse the startup directory for functions....

---

### Post by thermophile on 2007-02-12
I think scale-free, is that the same as distributed network analysis.  I have molecular data for geographically distinct microbial communities.  I want to see if there are sources and or sinks of diversity.  and if there's any resemblance between the network structure and the geographic distances that'd be cool to find too.  obviously, this is something that I just started thinking about so I need to do a lot more research to determine the applicability of network analysis to my data.  But I've been avoiding learning R for a year or 2 now so thought I should bite the bullet
thanks

---

### Post by WebDrake on 2007-02-12
Well, in one way, networks are networks are networks .... Check out Béla Bollobás' book "Random Graphs", for example.

Other texts (in alphabetical order....)

Albert, R. and Barabási, A.-L. (2002). Statistical mechanics of complex networks. *Reviews of Modern Physics* **74**, 47-97.
Dorogovtsev, S. N. and Mendes, J. F. F. (2002). Evolution of networks. *Advances in Physics* **51**, 1079-1187.
Newman, M. E. J. (2003). The structure and function of complex networks. *SIAM Review* **45**, 167-256.

Hope that helps. :)

---

### Post by akniss on 2007-02-12
> **thermophile said:**
> Do any of you R gurus have a suggestion(s) for a good general intro to R or network analysis specific tutorials?
thanks

There are some good links here:
[http://www.ubuntuforums.org/showthread.php?p=717367#post717367](http://www.ubuntuforums.org/showthread.php?p=717367#post717367)
If you are willing to buy a book to learn R, I HIGHLY recommend Modern Applied Statistics with S by Venables and Ripley.

---

