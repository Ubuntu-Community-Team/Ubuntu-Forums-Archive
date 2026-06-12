---
title: "loops in R"
date: 2009-10-04
forum: Education &amp; Science
---

### Post by Mr_Pag on 2009-10-04
Hi all,

I'm doing a course in Statistical Modelling. I'm trying to convert a bit of SAS code to make a dataset with x points, my notes are in SAS and I'm hoping to do my work in R. I've been using R for about a week, but I've got nada programming experience so the following question about conditions and loops is a little confusing.

The SAS code looks like:

```


data sim;
do i=1 to 10000;
do x=1 to 10;
err = rannor(3921);
Y = 1+3*x+err;
output;
end;
end;


```

The code above has a loop within a loop, can anyone show me how to perform this task in the equivalent order in R. So far I've got (and quite proud of):

```

dataset <- matrix(ncol=4,nrow=10000)
dataset[,1]<- 1:10000
dataset[,2]<- 1:10
  for (i in 1:nrow(dataset)) {
      dataset[i,3]<- rnorm(1)
      dataset[i,4] <- 1+3*dataset[i,2]+dataset[i,3]
  }


```

I'd like to know how to put the generators for columns 1 and 2 inside the loop. I've tried all sorts of things - I'm sure this will come in useful later.

Thanks for your time folks,

Pag

---

### Post by whelanh on 2009-10-04
I don't know why you would want to put inside the loop (loops are generally much slower than using matrix and/or sapply type functions).  You should generally do your best to avoid loops if you can.  But.... If you want to do it:

dataset <- matrix(ncol=4,nrow=10000)
for (i in 1:nrow(dataset)) {
      dataset[i,1]<-i
      dataset[i,2]<- (i-1) %% 10 + 1
      dataset[i,3]<- rnorm(1)
      dataset[i,4] <- 1+3*dataset[i,2]+dataset[i,3]
  }


Best,
Hugh

---

### Post by Mr_Pag on 2009-10-05
Thanks for reply Hugh, thats great. Can I ask what the two %% in "dataset[i,2]<- (i-1) %% 10 + 1" do?

Best regards,

Alan

---

### Post by whelanh on 2009-10-05
%% is the modulus function...i.e., it gives you the remainder...so 11 %% 10 = 1.  Provides an easy way to repeat a cycle of numbers.

Best,
Hugh

---

### Post by hubie on 2009-10-05
For reference, I used your example to see how much longer it would take the looping to go vs. not looping.  I wrote the following script:
```
nr <- 1000000
dataset1 <- matrix(ncol=4,nrow=nr)
dataset2 <- matrix(ncol=4,nrow=nr)

t1_start <- Sys.time()
for (i in 1:nrow(dataset1)) {
   dataset1[i,1] <- i
   dataset1[i,2] <- (i-1) %% 10 + 1
   dataset1[i,3] <- rnorm(1)
   dataset1[i,4] <- 1 + 3*dataset1[i,2] + dataset1[i,3]
}
t1_stop <- Sys.time()
print(sprintf("The loop way took %6.2f seconds", t1_stop - t1_start))

t2_start <- Sys.time()
dataset2[,1] <- seq(1:nr)
dataset2[,2] <- rep(seq(1:10), nr/10)
dataset2[,3] <- rnorm(nr)
dataset2[,4] <- 1 + 3*dataset2[,2] + dataset2[,3]
t2_stop <- Sys.time()

print(sprintf("The better way took %6.2f seconds", t2_stop - t2_start))

t1 <- as.numeric(t1_stop - t1_start)
t2 <- as.numeric(t2_stop - t2_start)
print(sprintf("It took %6.2f times longer to do it with a loop!",t1/t2))
```

Note that I used a matrix with 1e6 entries so that I could get better numbers.  On my modest desktop it took 59.7 seconds to do the calculation with a loop, and 0.8 seconds to not use a loop, resulting in about a 77X improvement.

---

### Post by Mr_Pag on 2009-10-05
Guys,

This is some fantastic info. Thanks both! A 77X improvement in speed is a quite an achievement - I'll need to have a good think about structure when writing complicated scripts it would appear!!

Cheers,

Alan

P.S. Nice Sig Hubie

---

