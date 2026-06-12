---
title: "Latex advice"
date: 2009-06-05
forum: Education &amp; Science
---

### Post by uberdonkey5 on 2009-06-05
I recently saw latex and was really impressed by the quality of the output. I am considering learning how to use latex. Can any answer these questions:

1. how long would it take to learn to produce a good quality manuscript (with references) similar to that I could produce in open-office or word
2. can latex documents be exported to .doc and .odt types
3. is it easy to imbed images?
4. what book would you recommend to learn Latex
5. any problems encountered with it?

many thanks

ud5

---

### Post by hessiess on 2009-06-05
> **uberdonkey5 said:**
> I recently saw latex and was really impressed by the quality of the output. I am considering learning how to use latex. Can any answer these questions:

1. how long would it take to learn to produce a good quality manuscript (with references) similar to that I could produce in open-office or word
2. can latex documents be exported to .doc and .odt types
3. is it easy to imbed images?
4. what book would you recommend to learn Latex
5. any problems encountered with it?

many thanks

ud5

1) Couple of days, LaTeX does most of the hard work automatically, take a look at the [not so short introduction to LaTeX]("http://tobi.oetiker.ch/lshort/lshort.pdf"). If you already know HTML, its very simmaler in principle, but the syntax is vastly different.

2) As far as I know, no.

3) Dead easy, use the graphix package.

4) see 1

5) Not much, large tables can be rather messy and creating your own document style can be very difficult.

---

### Post by uberdonkey5 on 2009-06-05
thanks hessiess..

inability to convert to .doc files is a big problem when it comes to writing a paper collaboratively... not sure if I will use it as no-one I work with uses it.

---

### Post by hessiess on 2009-06-05
> **uberdonkey5 said:**
> thanks hessiess..

inability to convert to .doc files is a big problem when it comes to writing a paper collaboratively... not sure if I will use it as no-one I work with uses it.

It doesn't take long to learn, so just try it out anyway. Word processors produce ugly documents:D, maby you can convert your collogues to LaTeX.

---

### Post by uberdonkey5 on 2009-06-05
true! I should be less of a stick in the mud. OK, I will give it a go!

---

### Post by myle on 2009-06-05
It is easier than you can imagine to convince your colleagues to use LaTeX once you have learn the basics about it.

Just by working together with them at an initial stage, and showing that the underlying logic is very simple, while the mathematical symbols can easily be produced using a front-end like Kile, they will be convinced and try it themselves when they will see the quality of the final result.

Good luck.

---

### Post by hessiess on 2009-06-05
> **uberdonkey5 said:**
> true! I should be less of a stick in the mud. OK, I will give it a go!

Its always good to try out new ways of working.

Thinking about it, it would be imposable to convert a LaTeX document into a word processor document while retaining the beautiful formatting because you would be using the word processors(bad) typesetting algorithms, unless you just converted the whole lot into an image and included that ;).

---

### Post by Stefan_K on 2009-06-05
Hi ud5,

> **uberdonkey5 said:**
> 
1. how long would it take to learn to produce a good quality manuscript (with references) similar to that I could produce in open-office or word

It depends on your expectations. Very good results could be obtained quickly. If you want to diverge from the standard layouts it could take some time to find out how to achieve it.

> **uberdonkey5 said:**
> 
2. can latex documents be exported to .doc and .odt types

See [Converters from LaTeX to PC Textprocessors]("http://www.tug.org/utilities/texconv/textopc.html"). 

> **uberdonkey5 said:**
> 
3. is it easy to imbed images?

It's easy, the graphicx package mentioned by hessiess provides basic commands and a lot of features. pdfLaTeX is able to import pdf, jpg and png images, LaTeX only supports eps images. You could use one of the many image format converters.

> **uberdonkey5 said:**
> 
4. what book would you recommend to learn Latex

There's a lot of tutorials available online, have a look at [Introductions and Guides to LaTeX]("http://texblog.net/latex-link-archive/introduction-guide/").

There are some introductory books, but I cannot recommend one. The best general LaTeX book in my opinion is the "LaTeX Companion" by Mittelbach and Goossens, but that's better for advanced users, not easy for beginners.

> **uberdonkey5 said:**
> 
5. any problems encountered with it?


Sure, but I could solve it every time. There's a lot of documentation also for additional packages. Because the source code of LaTeX and of packages classes is available one could find out reasons and solve problems by looking into the source. Even if you cannot do it by yourself at the beginning there are some [LaTeX forums]("http://texblog.net/latex-link-archive/board-forum-group/") where experienced users would help you.

Stefan


--
[TeXblog.net]("http://texblog.net")

---

### Post by bryncoles on 2009-06-06
i know what you mean about collaborative projects, as its also my main worry for converting to LaTeX (which i still wanna do). though you just need to convince your colleagues to start using pdf annotation software!

also, may i humbly recommend [texmaker]("http://www.xm1math.net/texmaker/"), as it is a free, open-source cross platform latex editor and is starting me off nicely before i migrate to gedit and the terminal. its in the repos...

---

### Post by lodp on 2009-06-06
I think the most important advice to give to a starter-outer in Latex is: hang in there. The real benefits (i.e. the quality of the output, and the amount of time and work it saves you) only become apparent once you're a bit more proficient. 

No matter what you're trying to do, in the beginning you'll likely spend incredible amounts of time finding out how to do things that in a more conventional text editor would be available at the expense of a click.

I vividly remember the HOURS I spent trying to find out how to produce strikethrough text (turned out it needed an additional package which conflicted with other packages).

As for what books to use, somebody already mentioned the "Not so short introduction to LaTeX", it really is an excellent guide for beginners.

Here's another useful thing: [http://en.wikibooks.org/wiki/LaTeX](http://en.wikibooks.org/wiki/LaTeX)

---

### Post by uberdonkey5 on 2009-06-07
wow! thanks everyone for all the useful advice! I have installed texmaker and will try working with this.

---

### Post by samden on 2009-06-14
Good luck! If you are handy to the people you are collaborating with, you can just print a double-spaced version of the LaTeX .pdf file and get them to proof it the old-fashioned way. Many people (including myself) find that easier to do than doing it on a computer screen anyway. 

That's how I've got my supervisors to proof my thesis, made in LaTeX. They were all skeptical about it when I started using it, mainly because it meant I wasn't sending them Word files they could use "track changes" on. But I think they are impressed now they've seen the results!

---

