---
title: "IF conditions in R"
date: 2012-01-02
forum: Education &amp; Science
---

### Post by nischal_rd on 2012-01-02
Hey guys,

I am facing some basic issues in R .

i have 2 objects c1 , c2 and i am doing this:

IF(c1 < c2) { do something} - this is not working.

Am i doing something wrong?

I am new to R and i would be glad if someone could help me out.

Thanks in advance.

Cheers.

---

### Post by squaregoldfish on 2012-01-02
You have to be more specific than saying "it's not working". Please provide some sample code and any errors generated.

Steve.

---

### Post by nischal_rd on 2012-01-02
Hey Steve,

C1 and c2 are 2 vectors and sorry for not specifying the error,
I am getting a true/false not found error.

I am trying to convert the vectors into numeric by using as.numeric but i am still unable to compare c1 and c2.

---

### Post by gunksta on 2012-01-02
When you ask a programming question, it helps if you provide an example for others to work with. Asking a generic why is 'foo' not working is a difficult question because there are often many reasons something might fail to work and figuring out which one(s) apply to you is difficult without something more to work with.

But, in this case I think I can figure out the basic problem. You are using vectors, a fundamental data type in R, but you aren't vectorizing your logic. R doesn't do loops well (SLOW). In some cases this is an absolute curse, in other cases it is a semantic blessing. I often find myself working in other languages wishing I could use some of the clean syntax that is so easy in R. (Honestly, a merger between R and ANSI compatible SQL would be my dream language).

Anywho - you need to first figure out what you are trying to do. There are two reasonable ways to interpret what you appear to be trying to do. Are you trying to:


[LIST=1]
[*]Compare the vectors in their entirety. Thus, if ALL values of c1 are < ALL values of c2, then do something. OR
[*]Compare the individual elements to one another. Thus, if c1[i] < c2[i] then do something. This is a more classic loop.
[/LIST]
My confusion stems from the fact that your pseudo-code if-else statement appeared to handle the vectors in their entirety, but you wouldn't do that with if() in R. Thus, I'm not sure if you are making a semantic error or a fundamental error in implementing your goal.


Answering this question is critical regardless of what language you are working in because they are fundamentally different comparisons and without any context, I have no way of knowing which may be most appropriate for what you are trying to do. But, this is extra important in R because R handles vectors very differently compared to other languages. See ifelse

---

### Post by nischal_rd on 2012-01-02
hey,

Yes i realised the question i framed was wrong.

Sorry about that.

Will try to implement the suggestions you have given me .

Will let you know at the earliest about the results.

I am liking R . Its crisp and clean except sometimes some simple stuff like Looping and If is causing a little bit of problems.

Thanks a lot for the fast reply.

Kudos.

---

### Post by nischal_rd on 2012-01-02
hey,

This is the code i am working with which is showing errors.


checkHS<-function(HighValues,LowValues)
{
  counter<-1
  patternList<-c()
  
  while(counter < length(HighValues))
  {
     cmpValue1<- 0.15*HighValues[[counter]]
     cmpValue2<- HighValues[[counter+1]]
     if(cmpValue1<cmpValue2) 
     patternList<-c(patternList,counter)
     counter<-counter+1
    
  }
  return (patternList)
}


*Where HighValues is a list of numbers and LowValue is a list of numbers as well.


Is the comparison i am doing wrong?

---

### Post by squaregoldfish on 2012-01-03
The problem you have is that counter = -1 for the first iteration. Therefore, in the line

cmpValue1<- 0.15*HighValues[[counter]]

cmpValue1 will be NULL, because you're referencing HighValues[[-1]].

If if statement will throw an error because it can't compare a NULL value.

Steve.

---

### Post by gunksta on 2012-01-03
Hmmm. After looking at your example, I'm not sure there is an easy way to vectorize it. But, it was late last night, maybe something will occur to me today. But, in the meantime:

```

while(counter < length(HighValues))
{
    cmpValue1 <- 0.15 * HighValues[[counter]]
    cmpValue2 <- HighValues[[counter+1]]
    if( cmpValue1 < cmpValue2 ) { 
        patternList <- c(patternList,counter)
        counter <- counter+1
    }
    
  }

```this should work better. Because your 'then' statement is multiple lines, you need to show where it ends. You can omit the {} for single line quickies, like if a < b then c <- a + b but if you once you have multiple steps there, you need to use {} to mark it off.

---

### Post by gunksta on 2012-01-03
Here's a thought.

```

base_values <- HighValues * 0.15
next_values <- HighValues[-1]
less_than <- base_values == next_values

```

I was thinking about this on my drive in to work today and realized that it can be vectorized and quite easily. Apparently I don't do well answering questions after a day of skiing on icy slopes. The variable base_values is similar to your syntax, the rest is quite different. next_values should have a length that is exactly length(HighValues) - 1. This creates a second vector that basically drops the first value. Then, when we compare base_values to next_values we are comparing the same thing you are using the [i] == [i+1] notation, but we are operating on the vector as a single unit, which leverages R's awesome vector skills. Loops in R are slow, vectorized operations are, by comparison, fast. The variable less_than is a vector that will contain TRUE FALSE values. End result is similar to what you did with your loop, but it takes fewer lines of code and should run circles around your loop. This last part is only relevant if HighValues is long. If this vector contains a few hundred values the difference will probably not matter.

---

### Post by nischal_rd on 2012-01-04
@gunksta - Hey man thanks a lot , i eventually figured out how to do it , but ur method is slick as well. 

WIll definitely come in handy , will keep u posted on the different stuff i am doing too.

Thanks again.

Kudos. :)

---

