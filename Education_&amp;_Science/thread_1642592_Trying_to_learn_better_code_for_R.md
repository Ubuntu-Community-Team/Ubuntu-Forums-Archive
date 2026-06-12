---
title: "Trying to learn better code for R"
date: 2010-12-10
forum: Education &amp; Science
---

### Post by agm. on 2010-12-10
Hi,

I use R a lot, but there aren't many "experts" here anymore in my department (they all left for jobs at other schools).  The problem is that while my code works, it is inefficient and there isn't anyone here that I can have look over my code and critique it.  That is where (I hope) you all come in.  I am looking for different commands that would make this code more efficient or better.

The basic idea of the code is that I need to make a correlation matrix between all the different possible responses.  In my data (not used-- a runif() is used for simplicity), each column of the "scales" matrix represents a survey answer for each household and can take a value of 1, 2, 3, or 4.  As such, I have to make a 36x36 matrix to get all correlations.  I've got this to work using 3 loops, which I know more proficient coders cringe at.

Any comments would be awesome! I'd specifically like to learn how to not use "loop 2" that gets rid of the 4x4 block of correlations between the same question (which they can only answer once) and I'd like to learn if sapply()/tapply()/apply() could be used.

PS. Thanks again and I know this isn't an "R forum," but people here are much more tolerant than the R list-serv and quite knowledgeable (and I'm using R under Ubuntu)!

```


##Correlations between answers:

c2 <- rep(1:4, 9)
count <- 1
#Real data code
#scales <- matrix(c(data$SCALEA, data$SCALEB, data$SCALEC, data$SCALED, data$SCALEE, data$SCALEG, data$SCALEH, data$SCALEI), nrow=length(data$SCALEA), ncol=9)

#Example code:
scales <- matrix(round(runif(450, min=1, max=4)) , nrow=50, ncol=9)

cor.mat <- matrix(0 , nrow= 36, ncol=36)

#Loop 1
for(m in 1:36){
  for(i in 1:9){
      for(k in 0:8){
      cor.mat[count, (4*k +1)] <- cor(scales[ ,i]==c2[m],  scales[,(k+1)]==1)
      cor.mat[count, (4*k +2)] <- cor(scales[ ,i]==c2[m],  scales[,(k+1)]==2)
      cor.mat[count, (4*k +3)] <- cor(scales[ ,i]==c2[m],  scales[,(k+1)]==3)
      cor.mat[count, (4*k +4)] <- cor(scales[ ,i]==c2[m],  scales[,(k+1)]==4) 
      }
    }
count <- count + 1
}

#Loop 2
for(k in 1:9){
  cor.mat[(4*k-3) : (k*4), (4*k-3) : (k*4)] <- NA
}


```

---

### Post by spinoza666 on 2010-12-11
Hey,

I always find Burns R-inferno amusing and helpful for this type of question:

[http://lib.stat.cmu.edu/S/Spoetry/Tutor/R_inferno.pdf]("http://lib.stat.cmu.edu/S/Spoetry/Tutor/R_inferno.pdf")

I'm sure you'll find some good pointers in there, and have a laugh at the same time:)

---

### Post by gunksta on 2010-12-11
The people on the R mailing list are very friendly, when they're not being mean.  :D  You're right -- the RTFM mentality of the R mailing list can be  . . . challenging. Another good source of information is [Stack Overflow]("http://stackoverflow.com/questions/tagged/r?sort=newest&pagesize=15"). The link should take you to the newest questions on R. In contrast to the R mailing list, I think you will find the people who hang out there are much easier to get along with.

I may not understand your data structure, but how are you winding up with a 36x36 matrix? If you want to build a correlation matrix of 9 columns the correlation matrix should look something like:
```

  | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
----------------------------------------
1 | 1 | X | X | X | X | X | X | X | X |
2 | X | 1 | X | X | X | X | X | X | X |
3 | X | X | 1 | X | X | X | X | X | X |
4 | X | X | X | 1 | X | X | X | X | X |
5 | X | X | X | X | 1 | X | X | X | X |
6 | X | X | X | X | X | 1 | X | X | X |
7 | X | X | X | X | X | X | 1 | X | X |
8 | X | X | X | X | X | X | X | 1 | X |
9 | X | X | X | X | X | X | X | X | 1 |
 
```

Try:
```
cor(scales) 
```to calculate the correlation matrix automatically. Note: cor(scales) produces a 9x9 matrix.

---

### Post by gunksta on 2010-12-11
Two other quick comments:

Your "answers" are either '1', '2', '3', '4'. I am going to go out on a limb and assume these are categorical variables OR some sort of Likert scale. Testing for correlation using Pearson for categorical variables or Likert scales is not a good idea.

Pearons is a test of linear correlation for continuous variables. Using categorical data in this test is an absolute no-go and while some people will stubbornly persist in defending the practice, I think it is a bad idea to use this test against Likert scales as well. You know that '4' is 'greater' than '1', but you don't really know by how much. I suppose if your sample size is large enough you could argue that the natural variation should normalize this source of error, but if your data is highly skewed, you could get a really inadequate results.

Move your cor() to kendall's

---

### Post by agm. on 2010-12-11
Thanks so much for the responses!  I really appreciate the link gunksta.  Any alternatives to the R mailing list to learn is quite beneficial.

As for why I am looking at a 36 x 36 matrix.  My data is about 2000 households and I'm looking at correlation between answers to each question and the response to the next question.  So for example:  I'm checking the correlation between a household responding to Q1=1 and Q2 =1, but then I also want to check the correlation between Q1=1 and Q2=2 and so on... which adds up to a 36x36 matrix.

I will take what you said about the Likert scale data into account and look into Kendall's as an alternative to the simple correlation.  The purpose of these correlation is to see if we can identify any patterns in the data before real analysis, but if the simple correlations are incorrect it won't help!

Thanks again for the comments!

---

