---
title: "odfTable"
date: 2009-09-06
forum: Education &amp; Science
---

### Post by gunksta on 2009-09-06
I know there are some R fans on this forum and I'm hoping some of you have more odfTable experience than I do (I'm just learning about this).

At the company I work for, we have a standard format for tables. I am trying to show how odfTable and R could be really really useful for some of our repetitive reports. Here's a quickie example that I hacked up in ASCII.

--------------------------------------------------------------------
|          Table 1 - Children Re-Entering Care                |
--------------------------------------------------------------------
| Report Period                                      |    N    |  %     | 
--------------------------------------------------------------------
| Period 1                                               |   44   |  6%   |
--------------------------------------------------------------------      
| Period 2                                               |   37   |  4%   |
--------------------------------------------------------------------

I have figured out how to use odf Table() to make a table that looks like this:

--------------------------------------------------------------------
| Report Period                                      |    N    |  %     | 
--------------------------------------------------------------------
| Period 1                                               |   44   |  6%   |
--------------------------------------------------------------------      
| Period 2                                               |   37   |  4%   |
--------------------------------------------------------------------

The problem is, I don't know how to make the header. I can use odfCaption to do something like this:

--------------------------------------------------------------------
| Report Period                                      |    N    |  %     | 
--------------------------------------------------------------------
| Period 1                                               |   44   |  6%   |
--------------------------------------------------------------------      
| Period 2                                               |   37   |  4%   |
--------------------------------------------------------------------
Table 1 - Children Re-Entering Care

But, that's not how we do tables. Trying to introduce a new table style AND a new tool is going to make my life more complicated than necessary. I'd like to get the company to start using R (other than myslf) and I think this could work, if I can figure out this table limitation.

Ideas are appreciated.

---

### Post by gunksta on 2009-09-07
I do realize my hypothetical tables look pretty messy. I forgot that the forum would collapse all of my spaces.

But the idea is there. I want to be able to "name" the table in an extended header, and not use a caption. 

Last night I came up with the idea of embedding the R table inside of a table I built in the original document. I helped me get most of the "look" I want, but it's not as scriptable as something that is produced completely within R.

I'd like to be able to have R create a document that produces a set of tables automatically, without requiring me to in and set them up by hand first.

---

### Post by ahmatti on 2009-09-16
I don't have any experience with odfTable, but you may want to have a look at **xtable**. You can use it to create tables in Latex and HTML, tables. I've used it to create some repetitive reports, and I really like it because you get all the power of Latex.

---

### Post by gunksta on 2009-09-17
I would love to use xtable/Sweave, but I'm afraid that is not an option. I need to be able to share the template and convincing other people in the company to learn LATEX is a losing battle from the very beginning.

Fortunately, I have gotten a lot of help from the R-users mailing list. I'm still working on the project and I haven't gotten everything figured out that I want, but it is shaping up very nicely. I'll try to remember to throw some syntax up here when I'm done.

---

### Post by akniss on 2009-09-17
Slightly off-topic: I've been looking into the odfTable.  Seems very useful, as I do all of my analysis in R and reports in OOo.  But I can't seem to get odfSweave to work due to a bad configuration of the XML package. Did you have any trouble with this package? Any tips on where I might look to get it up and running?

---

### Post by akniss on 2009-09-23
> **akniss said:**
> Slightly off-topic: I've been looking into the odfTable.  Seems very useful, as I do all of my analysis in R and reports in OOo.  But I can't seem to get odfSweave to work due to a bad configuration of the XML package. Did you have any trouble with this package? Any tips on where I might look to get it up and running?

Figured it out. On Intrepid, must have the libxml2-dev package installed.

---

### Post by akniss on 2009-09-23
> **gunksta said:**
> I know there are some R fans on this forum and I'm hoping some of you have more odfTable experience than I do (I'm just learning about this).

--------------------------------------------------------------------
| Report Period                                      |    N    |  %     | 
--------------------------------------------------------------------
| Period 1                                               |   44   |  6%   |
--------------------------------------------------------------------      
| Period 2                                               |   37   |  4%   |
--------------------------------------------------------------------
Table 1 - Children Re-Entering Care

But, that's not how we do tables. Trying to introduce a new table style AND a new tool is going to make my life more complicated than necessary. I'd like to get the company to start using R (other than myslf) and I think this could work, if I can figure out this table limitation.

Ideas are appreciated.

So I've been playing around with odfWeave now that I got the XML package to compile. The answer to your question is fairly simple, but not at all obvious from reading the ?odfTableCaption help. Just add the caption code BEFORE the table, and the caption will be printed above the table.

```
<<Table1,echo=FALSE,results=xml>>=
odfTableCaption("A table of numbers")
odfTable(data.frame(c(1:3)))
@
```

---

### Post by gunksta on 2009-09-24
Interesting indeed!

I have to admit. I would not have thought of using odfCaption() before the table. Clever. Very Very Clever.

I have also been playing around with R graphics and have found that it is possible to do much with the graphics.

I'm working on a report for the company right now where we have a very nice looking combination of table and barplot. Thanks to many of the people on the R-help mailing list I managed to figure out how to do it. R graphics are a mind-job but pretty neat.

Once I get past the project I will post some syntax.

But, now I also have to take the time to look at this clever idea!

---

### Post by samden on 2009-09-24
R graphics are very impressive, far nicer than Excel / Calc anyway! I have found a copy of Paul Murrell's "R Graphics" to be really useful. You still end up having to look stuff up online, but it gives a handy reference so you at least know where to start looking.

---

### Post by akniss on 2009-09-24
Absolutely! I rely almost completely on R graphics for all of my data presentation.  I started using it when writing my dissertation, and have not even considered switching to anything else since. It is extremely handy to be able to use a single program for data analysis and graphics.  Far superior to the combination of SAS/Sigmaplot that is common for many in my discipline.  

Some examples of plots I have created in R:
[http://w3.uwyo.edu/~akniss/plots/ddomort.pdf](http://w3.uwyo.edu/~akniss/plots/ddomort.pdf)
[http://w3.uwyo.edu/~akniss/plots/solutions_bw.pdf](http://w3.uwyo.edu/~akniss/plots/solutions_bw.pdf)
[http://w3.uwyo.edu/~akniss/plots/Figure2.pdf](http://w3.uwyo.edu/~akniss/plots/Figure2.pdf)
[http://w3.uwyo.edu/~akniss/plots/Fig1_control.pdf](http://w3.uwyo.edu/~akniss/plots/Fig1_control.pdf)
[http://w3.uwyo.edu/~akniss/plots/Figure_4.pdf](http://w3.uwyo.edu/~akniss/plots/Figure_4.pdf)
[http://w3.uwyo.edu/~akniss/plots/translocation-run2bw.pdf](http://w3.uwyo.edu/~akniss/plots/translocation-run2bw.pdf)
[http://w3.uwyo.edu/~akniss/plots/tsdrmort.pdf](http://w3.uwyo.edu/~akniss/plots/tsdrmort.pdf)

---

### Post by akniss on 2009-09-24
> **gunksta said:**
> Interesting indeed!
I'm working on a report for the company right now where we have a very nice looking combination of table and barplot. Thanks to many of the people on the R-help mailing list I managed to figure out how to do it. R graphics are a mind-job but pretty neat.

Once I get past the project I will post some syntax.


I would be very interested in the syntax for this. I tried a while back to place an ANOVA table into a plot, but finally gave up. It sounds like it is indeed possible, and I would be very interested in seeing your results.

---

### Post by gunksta on 2009-09-25
I'll post it later today or sometime Monday (time permitting).

To make it easier for people to find, I'll start a new thread.

---

