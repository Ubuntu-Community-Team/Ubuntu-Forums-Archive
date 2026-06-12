---
title: "how to do simple main effect in R?"
date: 2009-11-30
forum: Education &amp; Science
---

### Post by orduek on 2009-11-30
I know its not a specific R forum but I just wasn't able to find an answer anywhere.
I'd like to know how can I check for simple main effect using R.
I did ANOVA (mixed model) and found an interaction, now I need to analyse the interaction. how can I do that?

---

### Post by akniss on 2009-11-30
> **orduek said:**
> I know its not a specific R forum but I just wasn't able to find an answer anywhere.
I'd like to know how can I check for simple main effect using R.
I did ANOVA (mixed model) and found an interaction, now I need to analyse the interaction. how can I do that?

If you can provide a simple example, that would help. What do you mean "analyse the interaction"? Mean separation?  

You might try: ```
?model.tables
```

---

### Post by samden on 2009-11-30
Yes, it is very hard to know what you are talking about. It sounds like you need basic statistics help to determine what you actually intend to do - and you don't need anyone to know anything about R to give you that.

Are you a student? If so, take your problem to a lecturer / teacher who can explain the statistical issue to you. Then if they don't know anything about R, come back here and explain what you want to do a bit better so we can help you.

I presume you ran a linear model, then ran anova(model). Have you tried summary(model)? That will give you some more information, including contrasts.

---

### Post by orduek on 2009-11-30
I'll explain a bit more:
I have a mixed model with 2 between subject variable (A and B) each has 2 levels. and one within variable (C) also with two levels.
When I run ANOVA (using aov or something like that) I get a significant interaction, lets say A*B was significant. 
now I need to further analyse the simple main effect, for example A at b1 and A at b2. these are the simple main effect the compromise (i think this is the right word) the interaction.
an example table will look like that in R:

A  B  C  value
1  1  1   20
2  1  1   23
1  2  1   23.5
2  2  1   32
1  1  2   37
etc.

I hope now its better?
thanks.

---

### Post by samden on 2009-11-30
Note: I'm no statistics expert, this is just something to try until someone suggests a better solution. It should give you an idea of the effects anyway.

Considering there are only two levels in the variable, try dividing the dataset into B=1 and B=2, ie:
B = 1:
A C value
1 1 20
2 1 23

B = 2:
A C value
1 1 23.5
2 1 32
etc.

You could then run a linear model on each of the reduced datasets and see what results you get.
model <- lm(value ~ A + C + A*C)
anova(model)

I am sure there will be a better way of doing this however, and I will watch this thread for a better suggestion, as I'd find it useful myself.

---

### Post by orduek on 2009-12-01
how do I divide the data?
if I have the list with the two levels, how can I tell R to list the data only with B=1?

and BTW - this method is OK for within subject variable but when you do a simple main effect on a between variable you should use the error term you of the entire model (based on the fact that larger N is better)

---

### Post by earlycj5 on 2009-12-01
> **orduek said:**
> how do I divide the data?
if I have the list with the two levels, how can I tell R to list the data only with B=1?

and BTW - this method is OK for within subject variable but when you do a simple main effect on a between variable you should use the error term you of the entire model (based on the fact that larger N is better)

Could create a new subset of the data where B=1

```

x <- subset(data, data$B==1)

```

That way you only have the data you want in a new object.  I'm sure there are other ways, this is R after all.  ;)

---

