---
title: "R and odfWeave"
date: 2010-07-28
forum: Education &amp; Science
---

### Post by Axolotl9250 on 2010-07-28
Hi, could anybody direct me to some instructions on how to install and use odfWeave? I want to use it for my coursework and I need something that tells me how to use it from what to write in the document to how to send it to odfWeave. I've gotten so far as installing the required libxml2-dev thing and installing odfWeave with ```
install.packages("odfWeave", dependencies=TRUE)
``` and so far it has worked.

---

### Post by earlycj5 on 2010-07-28
> **Axolotl9250 said:**
> Hi, could anybody direct me to some instructions on how to install and use odfWeave? I want to use it for my coursework and I need something that tells me how to use it from what to write in the document to how to send it to odfWeave. I've gotten so far as installing the required libxml2-dev thing and installing odfWeave with ```
install.packages("odfWeave", dependencies=TRUE)
``` and so far it has worked.

Doesn't it work in the same fashion as sweave, just producing a different output format?

Of course there's always the help files.
[http://bm2.genes.nig.ac.jp/RGM2/R_current/library/odfWeave/man/odfWeave.html](http://bm2.genes.nig.ac.jp/RGM2/R_current/library/odfWeave/man/odfWeave.html)

---

### Post by gunksta on 2010-08-01
I am a big fan of odfWeave. Here are some simple pointers. If you need something more, tell me what you are trying to do and I'll see if I can help. DISCLAIMER - I am on the road for business next week (third week in a row . . . ) so my response time isn't going to be stellar.

That all being said. . . . 

First you need to load odfWeave.
```
library(odfWeave)
```

Then, in your .R code, you will need something like this.
```

file.out <- paste("test", ".odt", sep="")
results.setting <- "xml"
odfWeave(file="template.odt",dest=file.out)

```

Next up, we need to discuss what you need to put INTO the .odf file. In this case, a .odt file.]

Logically, odfWeave works very much like traditional Sweave. It allows you to insert R expressions into a document and have the expressions be auto-magically replaced by the actual results.

Very handy.

If you are going to do something very simple - you can put something like this into your document.

  	 	 	 	 	 	  ```
\Sexpr{foo.variable}
```
 
Otherwise it gets more complicated. Here is some sample syntax for a project I worked on a while back. I am taking a graphic and inserting it into a document.
```

  	 	 	 	 	 	  <<echo = FALSE, results=hide>>=
 count <- 1
 graphic.simple(t1, titles[1], thiscounty, "t1.png")
 @
 <<echo = FALSE, results=xml>>=
 cat(odfInsertPlot(file="t1.png", height=3,  width=4.5, external=TRUE))
 odfFigureCaption(“Source: MyDAUS 2008”)
 @
 
```

Truthfully, there's a lot you can do with odfWeave. To explain how it all works, would require me to re-write the manual and I am quite certain that I can not do a better job of writing the manual than the author can. I suggest reading the manual.

[http://cran.r-project.org/web/packages/odfWeave/index.html](http://cran.r-project.org/web/packages/odfWeave/index.html)

Like I said, if you have a specific implementation question - I am more than willing to help out. It is a little weird until you get used to it. Once you get used to it - It just feels powerful. Ridiculously powerful. I'm learning the Sweave system because I want to learn how to use LaTeX yo write semi-automated webpages to distribute my reports through. I'm getting to lazy to email people my results. But, that's a personal problem.

:guitar:

Enjoy.

---

### Post by gunksta on 2010-08-01
I should note - if you ask a more specific question - it helps if you include the data set and the syntax you are working with. In this case, the .odt file would be good to have too.

I realize that this is not always possible due to privacy concerns, HIPAA, IRB requirements, etc. But if it is possible, it makes it a lot easier to help you. If you'd like to PM me, that can work too.

If you're worried about confidentiality - I encrypt data sets when I am away from my laptop and my security protocols are pretty ridiculous because I work with a lot of HIPAA data.

---

### Post by Axolotl9250 on 2010-08-02
Thanks gunksta, I didn't really have a specific query, it was just more general use and syntax for its basic use, so I can include results and workings in my coursework easier. I have been using sweave which I found quite simple with the block code just putting R code in it and everything, but as in open office I got a riddiculous amount of plugins and things that make my researching and citing life easier it made sense to try and use odfWeave to bring more convinience into Open Office.

---

### Post by gunksta on 2010-08-03
Another option to consider - and one that I am trying to learn how to use more effectively is org-mode babel. If you are already using ESS to interact with R, babel gives you the ability to craft special org-mode documents which include embedded R syntax (and/or other languages such as perl, python, etc.)

Babel can then be used to produce HTML, LaTeX, and just about anything else you can think of (via LaTeX).

To me, it is very interesting but is thus far - more challenging to use than Sweave or odfWeave.

[http://orgmode.org/worg/org-contrib/babel/uses.php](http://orgmode.org/worg/org-contrib/babel/uses.php)

---

### Post by Axolotl9250 on 2010-08-03
I've just had a go at testing it with a few simple things: In the document I have this:
```
[FONT=Arial, sans-serif]Testing of odfWeave:[/FONT]
  
 [FONT=Arial, sans-serif]<<>>=[/FONT]
 [FONT=Arial, sans-serif]test <- c(5, 10, 15, 20)[/FONT]
 [FONT=Arial, sans-serif]test[/FONT]
 [FONT=Arial, sans-serif]plot(test)[/FONT]
 [FONT=Arial, sans-serif]@[/FONT]
 
```Then in the R console I used:

```
> library(odfWeave)
Loading required package: lattice
Loading required package: XML
> file.in <- "~/odfweavetest.odt"
> file.out <- "~/odfweavetestout.odt"
> odfWeave(file.in, file.out)

```
As this is most likely how I would be using this for putting my workings in coursework, nothing amazingly detailed, more like results and hypothesis testing - maybe models once I've finished the books I need to read and I'm doing my dissertation. So for many display things with images and such I would probably be happy with defaults. Anyway I ran it and it worked, up to the point that the plot does not appear in the document, but it appears in it's own image preview window, much like when you're creating them in R. 

I've read about various formatting options - is this something to do with these?
imageDefs <- getImageDefs()
imageDefs$dispWidth <- 4.5
imageDefs$dispHeight<- 4.5
setImageDefs(imageDefs)

I attached the document I'm getting all of this from - its largely stuff for background in the beginning and then gets on to actually using it at the end, which is where I've been working from.

---

### Post by Axolotl9250 on 2010-08-04
I remembered that if the syntax is largely like that used in LyX then in the << >>= I had to include fig=TRUE - then the image appeared. The quality of the the image isn't as good as I felt it was with LyX and Sweave. Is this because of it being a png image?

---

### Post by gunksta on 2010-08-05
Glad you got the image to appear. I have not noticed any problem with the quality of the PNG files. But, remember, you can adjust the quality of the png file.

---

