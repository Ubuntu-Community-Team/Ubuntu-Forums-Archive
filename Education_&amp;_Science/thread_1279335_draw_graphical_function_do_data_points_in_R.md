---
title: "draw graphical function do data points in R"
date: 2009-09-30
forum: Education &amp; Science
---

### Post by awayguy on 2009-09-30
i closed my last thread because it was wrong formulated.

question again: i've got this data: (i use programm R)

v2 <- c(0, 2, 4, 6, 6.2, 6.4, 6.6, 6.8, 7, 7.2, 7.4, 7.6, 7.8, 8, 10, 12, 14)
ph2 <- c(12.10, 11.94, 11.68, 11.11, 10.91, 10.74, 10.47, 9.71, 7.1, 4.24, 3.3, 3.08, 2.98, 2.86, 2.33, 2.11, 1.98)

i know how to plot this and change the styling, i recomend that:
plot(v2,ph2, xv2lab="volumen", ph2lab="phwerte", main="gra3", ph2lim=c(0,14), v2lim=c(0,16), pch=4, col="black")


but the problem now is: i wand aproximate a function to these v2 and ph2 points, and i dont know how to do that. i searched a lot, i took me allready some time to understand how to change the sty le etc.
but the aproximation would be very important. i would be glad if someone could help me out!

with regards

---

### Post by machoo02 on 2009-09-30
check out the nonlinear least squares function:
```
>?nls
```
and the SSlogis function:
```
>?SSlogis
```
They may do what you want, or at least are a starting point.

---

### Post by ahmatti on 2009-10-01
You could also use "splinefun" or "approxfun".

---

### Post by akniss on 2009-10-01
```
sudo R
install.packages("drc",dep=T)
q()

R
v2 <- c(0, 2, 4, 6, 6.2, 6.4, 6.6, 6.8, 7, 7.2, 
        7.4, 7.6, 7.8, 8, 10, 12, 14)
ph2 <- c(12.10, 11.94, 11.68, 11.11, 10.91, 10.74, 10.47, 
         9.71, 7.1, 4.24, 3.3, 3.08, 2.98, 2.86, 2.33, 2.11, 1.9)
plot(v2,ph2, xlab="volumen", ylab="phwerte", main="gra3", 
     ylim=c(0,14),xlim=c(0,16), pch=4, col="black",type="b")

library(drc)
drm(ph2~v2,fct=LL.5())->ph.drm
plot(ph.drm,log="")
```

---

### Post by awayguy on 2009-10-01
thanks mate, yes that looks like an approximation, but it still remains too imprecise. as i see there really special R skills needed to do a really good approximation. i think i will print the dots and draw it by hand. i will print it on a mm paper, but yes i helped.

i will propably do a 2 day R course, that the study offers.


but maybe you could help me in one thing more:

i have now this graph. the scale continues in 2-part steps. i want make also the 0.2 steps visible. I want make the number every 2 steps visible and, but the scale streaks should be every 0.2 step visible. you know how to do that?

with regards

---

### Post by gunksta on 2009-10-01
Look at the results of this:        (it assumes you have the vectors you provided in the OP)

```

plot(v2,ph2, xlab="volumen", ylab="phwerte", main="gra3", pch=4, col="black", type='o', xlim=c(0,16), ylim=c(0,14))
axis(2, at=seq(0,14,0.2), label=NA)
axis(1, at=seq(0,15,0.2), label=NA)

```

I did a couple of simple things here. I fixed a couple of minor syntax problems with your original plot statement and I gave you an x-y axis with 0.2 separation of the tickmarks. Then, just for grins and giggles, I drew a line to connect all the dots. This is NOT a function, it just connects the dots. I doubt this is what you want regarding the drawing, but it _is_ awfully precise.  :-)

What exactly are you trying to do here?

---

### Post by awayguy on 2009-10-02
thanks a lot

so now i figured out several main things how to work with graphs.

for example i made a new graphic:

ve1<-c(0,1,2,2.2,2.4,2.6,2.8,3,3.2,3.4,3.6,3.8,4,4.2,4.4,4.6,4.8,5,5.2,5.4,5.6,5.8,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,21.5,21.6,21.8,22,22.2,22.4,22.6,22.8,23.3,24,25,28)
phsb<-c(3.17,3.49,3.74,3.78,3.82,3.86,3.9,3.92,3.95,3.97,4.01,4.03,4.08,4.09,4.12,4.14,4.16,4.18,4.2,4.23,4.25,4.27,4.3,4.37,4.45,4.54,4.62,4.69,4.75,4.85,4.93,5.02,5.12,5.23,5.36,5.52,5.77,6.25,7.46,9.42,10.07,10.25,10.45,10.58,10.75,10.87,10.99,11.15,11.32,11.45)

plot(ve1,phsb, labels=NA, ylab=NA,xlab=NA, tck=0, xlim=c(0,28), ylim=c(0,14),pch=4, col="black",xlab="Volumen KOH [ml]", ylab="pH-Werte [pH]", main="V2.3, Titrierung von Schwacher Base: CH(3)COOH")

axis(1, at=seq(0,28,2), tck=0.023)
axis(1, at=seq(0,28,1), tck=0.023, lables=NA)
axis(1, at=seq(0,28,0.2), tck=0.015, labels=NA)
axis(2, at=seq(0,14,2), tck=0.023)
axis(2, at=seq(0,14,1), tck=0.023, labels=NA)
axis(2, at=seq(0,14,0.2), tck=0.015, labels=NA)



this gives me pretty that what i want, but there is one question more:
what should be done if the command: (e.g) " axis(2, at=seq(0,14,0.2), tck=0.015, labels=NA) " , is allready typed in and executed and I notice a mistake and want to remove it?
after execution the graph is modified through the new command (here: " axis...), but is there this posibilty to move one step back, respectively to delete the step " axis(2, at=seq(0,14,0.2), tck=0.015, labels=NA) " with a special command like "rm" ?

with regards__

---

### Post by hubie on 2009-10-02
I don't think there is an undo type of command that you are looking for.  The easy thing to do is to not issue your complicated plot commands one command at a time, but put them in a script that you source.  For instance, if you put all your plot commands in a file, say myplot.R, then each time you edit the script you can run it by typing ```
source("myplot.R")
```.

The slick way to do it, and I have never gotten around to trying it myself because I am lazy, but if you type your script from within vim (or emacs, etc.), you can run the script from within the editor.

---

### Post by gunksta on 2009-10-02
When I work in R, I typically have 2-3 files, although it is largely for convenience and not strict necessity. Let's call the first file main.R. This tends to vary but regardless of the name, it would be the main routine for my analysis. The second file is usually called functions.R. Lately, I have been using odfWeave and as a result, I also tend to have a file called report.R which is basically responsible for building my reports.

I don't know if you are doing one graph or 100. If you are doing just a few graphs, the best approach is what you are doing. No. To the best of my knowledge there is nothing in R that resembles the undo command of a word processor, although it would be neat to have  such a thing in the interactive mode. If you notice a mistake, the best thing to do is either close the display via the mouse or use dev.off() to close the current device.

If you are going to do a bunch graphs on different variables in your data set that all need the same basic structure, then you can take the code you have worked out here and use it to build a custom function for R. I would put this into the functions.R file. Then, you can source("functions.R") to gain access to the new function.

The structure of a function is like this.
```

trivial.function <- function(variableA, variableB){
# Your function here.
# This is a trivial example
if(a<=b){a} else {b}
}

```

You don't have to define the your variable types for the function. You can just name them and use them, which is nice, but can be dangerous if others are going to use your functions (they could send the wrong type of info to your function).

The advantage of working out a custom function is that it minimizes the odds that you will make a syntax error and need to start over when making a graph. And, if you do, the time cost of doing it over becomes trivial. It's also easier to work out a loop if you need to do this many many times.

---

