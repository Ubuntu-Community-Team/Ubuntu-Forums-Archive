---
title: "R - Recursive plotting using for statement"
date: 2009-12-27
forum: Education &amp; Science
---

### Post by Mr_Pag on 2009-12-27
Greetings all,

I am trying to save myself a bit of effort creating some exploratory plots in R by using a control structure to make me some pngs of my 20 or so independent vs a single dependent variable. i.e.

```

for (i in 1:20) {
  png(file=paste('plotA',i,sep=''))
  plot(sprintf('%s%.0f','val$A',i),pfarg$Y)
  dev.off()
}

```

The trouble is with my code is that the sprintf returns a character value in inverted commas, i'd like to convert this into a variable I can plot against Y. Any ideas?

Many thanks in advance.

Alan

---

### Post by gunksta on 2009-12-27
As they would say over on the R-User mailing list, it would be easier if you'd included your data set. I will assume that you have a dataframe called foo.data and that if you write names(foo.data) you get:

[1] x1, y1, y2, y3

I will also assume that x1 is your independent variable that you want to plot against and that y1-y3 are the dependent variables you would like to plot against.

Disclaimer - When I make this many assumptions, error is inevitable. You may need to adjust this code.

For something this simple, I would avoid your apparent methodology. Too complicated. So, let's fake-up some data.

```

x1 <- round(abs(rnorm(10)) + 1:10,2)
y1 <- rnorm(10)*10
y2 <- round(abs(rnorm(10)) + 22:13,2)
y3 <- abs(rnorm(10))

foo.data <- data.frame(x1, y1, y2, y3)
rm(x1,y1,y2,y3)

```

OK. That's good enough for some fake data. We've got some positive, some negative and one really faked inverse "relationship".

Now, we want to take your starting point and play with it.

```

for (i in 2:length(names(foo.data))) {
  png(file=paste('plot_',names(foo.data)[i],sep=''))
  plot(foo.data$x1, foo.data[,i])
  dev.off()
}

```

There are a number of advantages to this method. For starters, it's simple and you get useful names for your plots. You can see that I have plots called plot_y1, plot_y2, etc. plot_y2 should look like there is an inverse relationship, they others will probably not look like a meaningful relationship.

I called on foo.data in a couple of different ways, and I used the way that made it easiest for me. I was going to give you an example of how to do this with apply(), but my brain has decided to stop working.

I am going to bed. Good night.

---

### Post by Mr_Pag on 2009-12-28
Gunksta,

Thank you again to take the trouble to reply to my R queries. I very much appreciate the help that you and Ahmatti have given me through my course. And thank you for taking the trouble to approximate my dataset, I should have included some kind of indication of my data. Your example nailed it (positively) regardless!!

Best regards,

Alan

---

