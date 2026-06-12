---
title: "R histogram weird behavior"
date: 2013-06-13
forum: Education &amp; Science
---

### Post by PC_load_letter on 2013-06-13
Hi everyone,
    I encountered some unexpected behavior from the hist() function while doing a  curve-fitting assignment at work. 

First, upon typing this:
```
> hist(y,col="red")
```
[IMG]http://imageshack.us/a/img706/575/86115229.png[/IMG]

Then
```
> hist(y,prob=TRUE,col="red",ylim=c(0,1.5))
```
gets me this
[IMG]http://imageshack.us/a/img189/4480/79801553.png[/IMG]

Now, my question is: **Why there are densities (probabilities) larger than 1 ??????**

the problem gets even worse if I try to increase the number of rectangles, using the 'breaks' option, like this:
```
> hist(y,breaks=50,prob=TRUE,col="red",ylim=c(0,2))
```

[IMG]http://imageshack.us/a/img811/4592/95968279.png[/IMG]

Any idea what is going on here?

---

### Post by steeldriver on 2013-06-13
Probability *density *is not the same as probability - the *area *(not height) of each bar should correspond to the probability that the value falls with the range of that bar, and of course that should be < 1 (in fact the area of all the bars together should equal 1)

So in your first 'Density' histogram, the height of the highest bar is maybe 1.1, but its width is only 0.2 i.e. probability that y lies in the range 0.8 to 1.0 is about 0.22

---

### Post by PC_load_letter on 2013-06-13
Thanks, that's what I figured.

---

