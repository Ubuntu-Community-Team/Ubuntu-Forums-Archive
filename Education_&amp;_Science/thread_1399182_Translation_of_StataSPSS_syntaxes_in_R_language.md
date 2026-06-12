---
title: "Translation of Stata/SPSS syntaxes in R language"
date: 2010-02-05
forum: Education &amp; Science
---

### Post by Benic on 2010-02-05
I need to translate in R language a bunch of SPSS syntaxes and Stata do-files. Being a casual user of R, making scripts is a slow process. Is there a kind of translation software or a dictionary that could help me?

Thanks,
Benic

---

### Post by gunksta on 2010-02-05
Not that I am aware of -- but if you find something, post it here. I'm sure there are other folks who would be interested in something like sqlFairy for stats tools.

Unfortunately, all of these tools are closer to full programming languages than they are to data descriptions like SQL and the differences are much larger. While there are differences from database to database, they more or less do the same thing. While this is true at a high level of abstraction for stats packages, the structural/logic differences are much more complex.

---

### Post by Benic on 2010-02-05
I found some dictionaries that give the translation for few specific commands. It's a beginning. The problem is the logic of languages that is very different from one program to another. Because of that, there doesn't seem to be a comprehensive translation tool that takes full sentences and translate them.

---

### Post by gunksta on 2010-02-05
I doubt you find a tool to do that for you. R is a programming language, not a single application. Mapping syntax from a limited language, like SPSS syntax to R, which has a completely different data model, would be complex.

---

### Post by Benic on 2010-02-05
Yeah, I guess you're right... I was asking in case someone had a hint.. From my own experience with some very simple procedures (factor analysis, different types of regression, bootstrapping, etc.), it takes kilometers of lines with R, so the learning curve is quite steep. I know the possibilities are quasi-unlimited, but I'm unable to unlock them.

---

### Post by gunksta on 2010-02-08
It's been a while since I have written SPSS syntax, but I do understand where you are coming from. For example -- tables in R are incredibly flexible, but it takes several lines to produce what most of us want.

From my experience, the best way to use R is to first look at CRAN and see if what you are trying to do has already been done. If it has been, you're in luck. Life just got easier. I also recommend writing functions that do what you want, rather than trying to rewrite the syntax every time. When I start a project, I usually write one or two functions to make the tables I will need to see and then I re-use this function throughout my work.

The trick to using R is to think like a programmer, not a SPSS user.

---

### Post by Benic on 2010-02-09
Do you know if there's a GUI that can help you learn the programmation of some simple commands by selecting specific operations to do with a table and then pasting the lines into a txt file or something like that?

---

### Post by gunksta on 2010-02-09
For Ubuntu?

---

### Post by Benic on 2010-02-09
Ubuntu or Windows. I know Rkward a little bit, but it's not very stable as far as I know (compiled SVN version, version in repo doesn't work for me).

---

### Post by gunksta on 2010-02-09
I haven't had too many problems with RKward, but I haven't really pushed it. When I get into something big, I tend to go command-line-commando.

There are some other GUI-oriented interfaces you could try out. You can install RCMDR. It's stable AFAIK and it's in the repos.  It's absolutely butt-ugly, but there's quite a bit there. 

While it is a PITA to set up, [JGR]("http://jgr.markushelbig.org/JGR.html") is a really nice front-end to R. One the website there are very specific steps on the web-site for installing. Follow them or it won't work. Supposedly JGR be integrated with [Deducer]("http://www.deducer.org/pmwiki/index.php?n=Main.DeducerManual") although I've never actually done this. I did use JGR for a while when I first started playing with R and it is very nice and if Deducer is everything it claims to be, it could be what you are looking for.

Another option that I haven't played with, but that I am looking forward to is Cantor, which is part of the KDE 4.4 SC, which was released today. It's a GUI front-end for R, MAXIMA, and Sage. I've never used it but I'll probably write up a short review here as soon as I get a version of it running on this system.  It appears to be in competition with Rkward, but I won't offer an opinion (yet) on which is better. If Cantor really shines, development on RKward may be affected. It could spur on the RKward devs or discourage them. It's hard to know in advance.

---

### Post by Benic on 2010-02-09
Nice! Thanks a lot for all those tips, it will definitely help me to complete this contract I'm working on. I will give them a try as soon as possible.

---

### Post by Benic on 2010-04-26
> **gunksta said:**
> 

There are some other GUI-oriented interfaces you could try out. You can install RCMDR. It's stable AFAIK and it's in the repos.  It's absolutely butt-ugly, but there's quite a bit there. 



I've tested it recently and you're right. It's ugly for sure! But the good thing is that you can actually visualize tables, something very useful when you're not sure about what you're doing when you're manipulating them. Also it shows error line by line. So if you mess up big time, it will show you where you're wrong and you can correct the script quickly.

---

### Post by Benic on 2010-04-28
> **gunksta said:**
> Supposedly JGR be integrated with [Deducer]("http://www.deducer.org/pmwiki/index.php?n=Main.DeducerManual") although I've never actually done this. I did use JGR for a while when I first started playing with R and it is very nice and if Deducer is everything it claims to be, it could be what you are looking for.

Finally, Deducer is available. I've also tested it and it works quite well. In my case, way better than RKward (which is always down with some bug). You have to install JGR first and then Deducer and use it inside a JGR terminal. 

This is what I was looking for. I don't have time (sorry!) to read tons of manuals to learn simple R command. With Deducer, I can run command from menus and then copy the code and do whatever I need to do. This is how I used to learn other statistical tools and I was at first glance overwhelmed by the sheer complexity of R when I had to do simple operations. As someone wrote: "It's easy to do difficult things but hard to do simple things." I don't want to start a war, but so far I must agree with this guy.... ;-)

Deducer is definitely an useful tool for a R outsider like me.

---

