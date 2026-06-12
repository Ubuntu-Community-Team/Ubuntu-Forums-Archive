---
title: "In desperate need of statistics help... data reduction"
date: 2006-02-09
forum: Education &amp; Science
---

### Post by towsonu2003 on 2006-02-09
I am using SPSS and trying to write my thesis...

I did a factor analysis on some of my variables and I need to recode the factors into a new variable. The variables in the factors are 5-point likert scales. My teacher wanted me to just add each variable in a factor.

So, if factor1 consists of var1, var2, var3, and var4; according to the teacher, it would look like:
factor1=var1+var2+var3+var4
So the max for factor1 will be 20 (4 variables x 5th point in each Likert scaled var) and the minimum will be 4 (4 variables x 1st point in each Likert scaled var)

The question is: Is this the way to go? Shouldn't I add coefficients for each variable somehow? If so, how do you determine what those coefficients will be??

So, what I am thinking of is:
factor1=(coef1 x var1)+(coef2 x var2)+(coef3 x var3)+(coef4 x var4)

Thanks in advance for all help :)

---

### Post by towsonu2003 on 2006-02-10
sorry :( to bump this so early, but I'm really desperate (by tomorrow morning)... :cry:

---

### Post by towsonu2003 on 2006-02-12
factor analysis>save>use regression (new variable will appear at the end of the variable list), use primary component analysis option in factor analysis (factors now called components)

---

### Post by xequence on 2006-02-12
It's all greek to me.

---

### Post by towsonu2003 on 2006-02-12
[QUOTE=xequence]It's all greek to me.[/QUOTE]
same here...

I found a very nice book on this (thanks to "SPSS Wiki" clues): "advanced and multivariate statistical methods", which is kinda greek->english dictionary for this weird stuff.

---

### Post by xequence on 2006-02-12
[QUOTE=towsonu2003]same here...

I found a very nice book on this (thanks to "SPSS Wiki" clues): "advanced and multivariate statistical methods", which is kinda greek->english dictionary for this weird stuff.[/QUOTE]


Shouldent your teacher have thought you how to do this before making you do it? If not, theyre odd.

---

### Post by towsonu2003 on 2006-02-12
the teacher is my advisor... I jumped into this as my thesis, thinking that my undergrad statistics education would be enough (no good courses on statistics - quantitative in grad courseload though!), but it seems it wasn't. 

the solution was simple though: read more... I'm used to reading by now thanks to linux ;)

---

### Post by briancurtin on 2006-02-12
[QUOTE=towsonu2003]the solution was simple though: read more... I'm used to reading by now thanks to linux ;)[/QUOTE]
converting to all linux has helped me in this regard too. ive learned how to dig through documentation and how to search for what i need much, much better. i didnt really think about that until recently.

---

### Post by towsonu2003 on 2006-02-12
[QUOTE=briancurtin]converting to all linux has helped me in this regard too. ive learned how to dig through documentation and how to search for what i need much, much better. i didnt really think about that until recently.[/QUOTE]
we need a new policy: force students to learn linux regardless of graduate area of study ;) that'll teach them (us) how to work with literature reviews and other documentation...

---

### Post by WolfJay_83 on 2006-02-12
It's quite easy to use the compute function to create a new variable. Then you can simply click each variable and sum them up.  This will create a new variable with the above properties.

I cant remember where on the menu it is, as I'm on my ubuntu laptop right now.  I'm curious though, are you running spss on linux somehow?

---

### Post by towsonu2003 on 2006-02-12
[QUOTE=WolfJay_83]It's quite easy to use the compute function to create a new variable. Then you can simply click each variable and sum them up.  This will create a new variable with the above properties.[/quote]
It wasn't giving me the variable I wanted as I didn't know what coefficients to use... I could just add each variable to each other, but that didn't look right... the "save" option with regression under factor analysis did the trick. what it basicall does is create a new variable with mean=0 and stD=1, using some coefficients unknown to me, from the components it extracts. I still don't know how it gets the coefficients though...

I didn't get any feedback from my advisor, so I'm not sure whether this will be okay for her... we'll see... I may have to just add them up as she wanted initially, if she insists... it seems advisors are gods in the thesis world... 
[QUOTE=WolfJay_83]
I cant remember where on the menu it is, as I'm on my ubuntu laptop right now.[/quote] Transform>Compute  [QUOTE=WolfJay_83]I'm curious though, are you running spss on linux somehow?[/QUOTE]
nope... in Windows (department computer and own computer). but I end up reinstalling windows from time to time bc. for some reason, the version I use at home in spss craps itself out if I want it to do too much computing: make it come up with a couple of graphics and plots, u end up having to reinstall it. I wish my undergrad people thought me how to use R instead of SPSS!! why the hell do you teach ppl a proprietary thing for which they have to pay big bucks to use???? academics is weird! I'll learn R once this is over...

---

### Post by diafanos on 2007-06-18
> **xequence said:**
> It's all greek to me.

even though I am Greek...I can't help you either...:lol:

---

### Post by euler_fan on 2007-06-18
> **towsonu2003 said:**
>  . . . I wish my undergrad people thought me how to use R instead of SPSS!! why the hell do you teach ppl a proprietary thing for which they have to pay big bucks to use???? academics is weird! I'll learn R once this is over...

This might help in your quest to learn R coming from an SPSS background.

[R for SAS and SPSS Users]("http://oit.utk.edu/scc/RforSAS&SPSSusers.pdf")

---

