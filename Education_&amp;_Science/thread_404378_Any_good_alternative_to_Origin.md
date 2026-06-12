---
title: "Any good alternative to Origin"
date: 2007-04-08
forum: Education &amp; Science
---

### Post by in_flu_ence on 2007-04-08
As title, any good alternative that you find to be user-friendly and can work much like Origin?

Thanks

---

### Post by nanotube on 2007-04-08
not sure how "user friendly" you can consider it to be, but R has a very sophisticated data graphing capability.
[http://www.r-project.org/](http://www.r-project.org/)

---

### Post by in_flu_ence on 2007-04-08
Any good tutorials to start off with for R-Project?

I had seen alot about it but haven't have a chance to try it out.

---

### Post by akniss on 2007-04-08
> **in_flu_ence said:**
> Any good tutorials to start off with for R-Project?

I had seen alot about it but haven't have a chance to try it out.

[http://ubuntuforums.org/showpost.php?p=717367&postcount=6](http://ubuntuforums.org/showpost.php?p=717367&postcount=6)

---

### Post by nanotube on 2007-04-08
> **in_flu_ence said:**
> Any good tutorials to start off with for R-Project?

I had seen alot about it but haven't have a chance to try it out.

tons of them! :)
here are a couple of links to get you started:
[http://cran.r-project.org/manuals.html](http://cran.r-project.org/manuals.html)
[http://cran.r-project.org/other-docs.html](http://cran.r-project.org/other-docs.html)

the "introduction to R" is a good starting point (find it in the first link)

from the second like, you might like:
&#8220;Statistical Computing and Graphics Course Notes&#8221; by Frank E. Harrell (since you are looking at graphing stuff)
and if you are looking to do any kind of econometric analysis, then check out
&#8220;Econometrics in R&#8221;  by Grant Farnsworth 

and when you are looking for any kind of specific help with a problem, the r-project mailing list is *very* responsive and filled with really knowledgeable people. 

good luck!

edit: all of these are free PDFs. but if you find that these just aren't enough, then you could of course also spring for the actual books, as posted by akniss, above. :)

---

### Post by in_flu_ence on 2007-04-08
Does R be able to extract data from an excel/OOo spreadsheet and process the data from there on?

---

### Post by akniss on 2007-04-08
> **in_flu_ence said:**
> Does R be able to extract data from an excel/OOo spreadsheet and process the data from there on?

R documentation about import/export:
[http://cran.r-project.org/doc/manuals/R-data.html](http://cran.r-project.org/doc/manuals/R-data.html)

I find its easiest to save the gnumeric or excel files as .csv, then use the read.csv() function in R.

```
read.csv('filename.csv', header=T)
```

---

### Post by in_flu_ence on 2007-04-08
thanks. blame on my laziness for not reading that first:P

Let me try it out and pull some hair before i ask some other questions.

---

### Post by tkjacobsen on 2007-05-08
Take a look at labplot: [http://labplot.sourceforge.net/](http://labplot.sourceforge.net/)

---

### Post by briansers on 2007-05-08
Qtiplot is also good, sort of like Origin, and it will import Origin files.  I think that Qtiplot and Labplot interfere with each other if both are installed:
[http://soft.proindependent.com/qtiplot.html](http://soft.proindependent.com/qtiplot.html)

Grace has been around, but I haven't really used it:
[http://plasma-gate.weizmann.ac.il/Grace/](http://plasma-gate.weizmann.ac.il/Grace/)

I know there are some others.

---

### Post by euler_fan on 2007-05-09
> **in_flu_ence said:**
> Does R be able to extract data from an excel/OOo spreadsheet and process the data from there on?

Don't know, but it can handle .csv files just fine and both excel and OOo can save in that format. Otherwise, text files are well supported generally. You can write custom files and tell R how to read them in fact. See the "read" function in the R documentation.

R will basically take the columns of your file as variables and go from there treating each variable as a vector and forming a data frame by associating a set of variables to a common object and index. It works out nicely because it also establishes a standard order to the variables as well, so you can still treat the data frame as a matrix.

---

### Post by mrsurf on 2007-09-08
I tried out GRACE but it requires command line for examlpe for smoothning of curve  I could not fin what to do?? dO U HAVE ANY IDEA??
LABPLOT OF NO USE!
sCIGRAPHICA HAS LOTS OF BUGS!

DID U FIND ANY SOFTWARE WHICH CAN B USED FOR GRPAHING LIKE ORIGIN AND IMOPRT ASCII????
> **in_flu_ence said:**
> As title, any good alternative that you find to be user-friendly and can work much like Origin?

Thanks

---

### Post by nanotube on 2007-09-08
> **mrsurf said:**
> I tried out GRACE but it requires command line for examlpe for smoothning of curve  I could not fin what to do?? dO U HAVE ANY IDEA??
LABPLOT OF NO USE!
sCIGRAPHICA HAS LOTS OF BUGS!

DID U FIND ANY SOFTWARE WHICH CAN B USED FOR GRPAHING LIKE ORIGIN AND IMOPRT ASCII????

maybe try "extrema"? [http://exsitewebware.com/extrema/](http://exsitewebware.com/extrema/)

---

### Post by xadder on 2007-09-09
My favourite right now is pylab (matplotlib). More matlab-like, easier to get to know that R I think, and great quality graphics.

Ages ago I tried grace and really liked it at first. But then I often have data with gaps, and grace won't plot gaps (e.g. NaN), so  gave up on it.

---

### Post by sanjeevchs on 2010-09-25
QTIPLOT works well. Also Origin-7.5 works perfectly in wine...

---

