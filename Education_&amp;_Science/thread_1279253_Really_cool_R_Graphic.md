---
title: "Really cool R Graphic"
date: 2009-09-30
forum: Education &amp; Science
---

### Post by gunksta on 2009-09-30
Recently I needed to make a funky graphic-table combo in R. Here's the challenge - To combine a vertical bar chart and the data table in a single graphic.

As much as I like R, it's graphics systems are mind-bogglingly complex. You have the base graphics system **PLUS** Lattice, ggplot, iplot, etc. There are way too many graphics systems. I couldn't even figure out which one I should focus on learning.

When in doubt, turn to the appropriate forum. I posted some stuff on the R-Users mailing list and got a fantastic reply from a guy named Marc.

[http://www.nabble.com/Barplot%2BTable-to25406046.html#a25408744](http://www.nabble.com/Barplot%2BTable-to25406046.html#a25408744)

I was able to take what he sent me, and learn from it. After playing around with it a little, I got the hang of it all and I was able to adapt what he sent me to my final project. I'll post the full version of what he sent me, since it was so useful as a learning tool.

Enjoy!

```

# Create data 
MyData <- matrix(c(57.1, 52.3, 13.5, 13.9, 7.9, 8.8, 5.4, 5.6, 
                    16.1, 19.4), 
                  nrow = 2) 

# Note that by using '\n' in the text, the label will be plotted on 
# two lines. '\n' is a newline character 
colnames(MyData) <- c("0 occasions", "1-2 Occasions", "3-5 Occasions", 
                       "6-9 Occasions", "10 or more\nOccasions") 

rownames(MyData) <- c("Androscoggin", "Maine") 


 > MyData 
              0 occasions 1-2 Occasions 3-5 Occasions 6-9 Occasions 
Androscoggin        57.1          13.5           7.9           5.4 
Maine               52.3          13.9           8.8           5.6 
              10 or more\nOccasions 
Androscoggin                  16.1 
Maine                         19.4 




# Set graph margins to make room for labels 
# See ?par 
par(mar = c(5, 8, 4, 1)) 


# Set colors 
MyCols <- c("black", "grey80") 


# Set label size 
MyCex = 0.75 


# Set lines for table data 
MyLines <- 2:3 


# do barplot, getting bar midpoints in 'mp' 
# See ?barplot 
mp <- barplot(MyData, beside = TRUE, ylim = c(0, 100), 
               yaxt = "n", cex.names = MyCex, col = MyCols) 


# mp contains the following. The mean of each column 
# is the horizontal center of each pair of bars 
 > mp 
      [,1] [,2] [,3] [,4] [,5] 
[1,]  1.5  4.5  7.5 10.5 13.5 
[2,]  2.5  5.5  8.5 11.5 14.5 


# Put a box around it 
box() 


# Draw y axis tick marks and labels 
axis(2, at = seq(0, 100, 10), las = 1) 


# Draw values below plot 
# Use the values of 'mp' from above. 
# See ?mtext 
mtext(side = 1, text = MyData, 
       at = rep(colMeans(mp), each = nrow(MyData)), 
       line = MyLines, cex = MyCex) 


# Get min value for the x axis. See ?par 'usr' 
min.x <- par("usr")[1] 


# Draw categories using mtext 
# See ?strwidth to get the length of the labels in 
# user coordinates, which is then used for 'at' 
# Setting 'adj = 0' left justifies the text 
mtext(side = 1, line = MyLines, text = rownames(MyData), 
       at = min.x - max(strwidth(rownames(MyData), cex = MyCex)), 
       adj = 0, cex = MyCex) 


# Draw the colored boxes 
# Same here for strheight as with strwidth above 
# Part of this is getting the vertical positioning to align with 
# the text and the horizontal position at the beginning of the labels 
# Note that we have to set 'xpd = TRUE' so that the points are drawn 
# outside the plotting region. See ?par and 'xpd' 
# We just need a single capital letter for strheight() to get the value 

VertOff <- strheight("X", cex = MyCex) * c(6, 8) 
HorizOff <- min.x - (0.85 * max(strwidth(rownames(MyData)))) 

points(rep(HorizOff, nrow(MyData)), 
        par("usr")[3] - VertOff, bg = MyCols, pch = 22, 
        xpd = TRUE, cex = MyCex) 

```

---

### Post by machoo02 on 2009-09-30
Very nice...thanks for sharing!

---

### Post by samden on 2009-09-30
That is snazzy. Don't us scientists get excited over funny things...
:)

---

### Post by ahmatti on 2009-10-01
Thanks a lot for sharing! That really is nice and I believe I may well use something similar in the future. Also I wish I had known about mtext a while ago, it would of really saved me some time... Well, I'll know it next time :)

---

### Post by gunksta on 2009-10-01
ahmatti - That is EXACTLY how I felt.

I'm glad people will be able to use this. I've also been playing around with the Lattice graphics system. Although it can not do the sort of things that I demonstrated in this sample, it does make it possible to quickly generate some nice graphs.

Once I get a little more under my belt, I'll throw it up here too.

---

### Post by Tart on 2009-10-01
Thank you for posting this graph.

---

### Post by UbuWu on 2009-10-01
Can you post the graph itself too?

---

### Post by samden on 2009-10-01
The code is completely self-contained UbuWu, just copy and paste it into an R console and you'll see the graph in a few seconds.

---

### Post by Tart on 2009-10-01
This is chart generated by the code above

---

### Post by gunksta on 2009-10-01
It looks like I may need to re-run the syntax on my own system. I noticed in Tart's graphic, the colored squares do not line up with the text, which is the whole point. I'll correct the code and repost it.

---

### Post by unutbu on 2009-10-01
Your code worked perfectly on my end.

Maybe Tart's looks different because of the conversion to png?

---

### Post by gunksta on 2009-10-01
Interesting. That IS what the output is supposed to look like.

Dunno. Maybe Tart will swing by tell us that he changed the vertical offset calculation or something.

---

### Post by Tart on 2009-10-02
Not sure what is going on. If I run the code chart looks like the one I posted (with text slightly misaligned). With pdf()[code] dev.off() chart looks fine, on the other hand jpeg() or png() [code] dev.off(), produce results similar to the one I posted above.

---

### Post by unutbu on 2009-10-02
Just out of curiosity, what GUI are you using? (I didn't know R had one).

---

### Post by gunksta on 2009-10-02
Tart, you may have stumbled onto something that I was resistant to believing.

When Marc sent me that code snippet, everything worked a charm. I took his code and adopted it into the structure of a project I was working on for work. I basically used his code to let me write a function that would create a series of charts that are structurally identical to the one that you made.

To do this, I had to change a few things, namely the size/shape of the graphical device. R defaults to 7x7 and I decided that I really wanted 5x3 (notation in XxY). When I got done monkeying around with Marc's syntax, I noticed that the alignment was way off in the .png files that I was making.

I thought it had something to do with my alteration of the device shape, but perhaps it had more to do with my decision to use the png() device.

Later this today, I'm going to run a couple of experiments to see if I can replicate what you are saying is happening. If I can, I will post a question to the R-users mailing list. Perhaps someone there can explain why png() lines things up differently than x11().

---

### Post by Tart on 2009-10-02
> **unutbu said:**
> Just out of curiosity, what GUI are you using? (I didn't know R had one).
I'm using Windows version at work, this is why I was able to do "Save as.." on charts, at home I use Rkward.

---

