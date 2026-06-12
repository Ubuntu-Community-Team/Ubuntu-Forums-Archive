---
title: "Help with R, boxplot"
date: 2011-04-03
forum: Education &amp; Science
---

### Post by Biblion on 2011-04-03
Hey guys, a little help with R would be appreciated.
What I need is to create a boxplot from file dores_05.txt using both columns h and srtm.
My first trhy ended with this:
> boxplot(h~srtm,data="dores_05.txt")
Error in eval(predvars, data, env) : invalid 'envir' argument

What should I do?

---

### Post by akniss on 2011-04-03
> **Biblion said:**
> Hey guys, a little help with R would be appreciated.
What I need is to create a boxplot from file dores_05.txt using both columns h and srtm.
My first trhy ended with this:
> boxplot(h~srtm,data="dores_05.txt")
Error in eval(predvars, data, env) : invalid 'envir' argument

What should I do?

R isn't finding your data file. Where is the "dores_05.txt" located? I can make this work using the following:
```
read.table("dores_05.txt")->dores
boxplot(h~srtm,data=dores)
```

---

### Post by Biblion on 2011-04-04
Thanks a lot!
I have one more question about R.
I have made a scatter graph, now I need to place a legend describing both data (red points) and lowess line (blue line with yellow triangles).
How do I do that?
Here is the graph-
[[IMG]http://i19.fastpic.ru/thumb/2011/0404/3d/8130bd9477b2b3800214e8f4a3d8fd3d.jpeg[/IMG]](http://fastpic.ru/view/19/2011/0404/8130bd9477b2b3800214e8f4a3d8fd3d.png.html)

I have started it this way-
> legend("topleft", pch=1, legend="h,srtm", fill=c("red","yellow")) 

Not sure about that.How do I describe the fill color, line style, etc.?

---

### Post by akniss on 2011-04-04
> **Biblion said:**
> 
I have started it this way-
> legend("topleft", pch=1, legend="h,srtm", fill=c("red","yellow")) 

Not sure about that.How do I describe the fill color, line style, etc.?

If you want multiple features in the legend, you need to specify them all in the call to legend. For example, in your legend you have two types of points, so you would specify them with ```
pch=c(1,2)
``` and do the same with text, lines, colors, etc. Something like this should get you started:

```
legend("topleft",pch=c(1,2),legend=c("Points","Lowess fit"),lty=c(0,1),col=c("red","blue"))
```

---

### Post by Biblion on 2011-04-05
So I have made it this way-

> legend("topleft",pch=c(1,2),legend=c("Points","Lowess fit"), lty=c(0,1),col=c("red","blue")), **pt.bg=c("red"),("yellow"))**
But the bold part doesen't work, how do I color the symbols?

---

### Post by Biblion on 2011-04-05
I have one more question, I have created a boxplot, what I need to do now is to create a label for the horizontal line and call it "median".The trickiest part is that there must be an arrow pointing on the median.
Something like that but with an arrow-
[[IMG]http://i19.fastpic.ru/thumb/2011/0405/d1/9b711576141f4c7aff955b3be59113d1.jpeg[/IMG]](http://fastpic.ru/view/19/2011/0405/9b711576141f4c7aff955b3be59113d1.jpg.html)

---

### Post by akniss on 2011-04-05
> **Biblion said:**
> So I have made it this way-

> legend("topleft",pch=c(1,2),legend=c("Points","Lowess fit"), lty=c(0,1),col=c("red","blue")), **pt.bg=c("red"),("yellow"))**
But the bold part doesen't work, how do I color the symbols?
It looks like you have one too many parentheses after the col=c()**)**, so nothing after that is part of the legend() function.

---

### Post by Biblion on 2011-04-06
That's still isn't working, but ok.
But what about the median label?
I suppose I have to use functions arrows and text together , but how exactly it's done:
> arrows(60,52,65,60, length = 0.25, angle = 30, code = 2,col = par("fg"), lty = par("lty"), lwd = par("lwd"))
Thatt the way arrow command looks, how do I add the text?

---

### Post by Biblion on 2011-04-09
If I need to create a boxplot for columns x and y from data file, how should I write down the command?
boxplot(x~y)
or
boxplot(x,y)

---

