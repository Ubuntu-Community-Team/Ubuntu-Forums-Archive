---
title: "dealing with large data files in R"
date: 2011-10-11
forum: Education &amp; Science
---

### Post by avitua on 2011-10-11
Hello
I'm new using R and i'm trying to deal with a large dataset for give the data the format i require, till now i manage to read row by row what i need for don't store the entire data in a matrix or a data frame. The next step is to write in a file line by line the register with the data in the new format. Does anybody knows how to do it?
Thank you

Sergio

---

### Post by Johnb0y on 2011-10-11
can you give a little more detail please? thanks.

---

### Post by gunksta on 2011-10-11
Johnb0y is right. Folks here can throw out a few generic thoughts / ideas, but to really help you, we need to know more about what you are trying to do. Based on your first post, it seems that you are trying to import data from _?_ and store it as a data frame in R.

Knowing the dimensions of the data, the amount of RAM on your system, what else you are doing with your computer when running the import process, etc. will help us come up with better suggestions for you. Posting the code you are using to import the data could be useful as well. Everyone understands that you may not be able to post a sample of the actual data, but right now suggestions are just shots in the dark.

Others here may disagree, but for large / complex data management problems, I prefer to use a database to manage my data. R is a fantastic analytics tool, but it is only a mediocre data management tool. R can connect to any of the big, mainstream data base systems without a problem. I have successfully used SQL Server, MySQL, Postgres and SQLite for various projects. I'm going to assume that you are doing the data management and analysis on a single system. In that case, I have had very positive experiences integrating R and SQLite. This is a good start on how to do this:

[http://cran.r-project.org/web/packages/RSQLite/index.html](http://cran.r-project.org/web/packages/RSQLite/index.html)

Unfortunately, the package isn't in the Ubuntu repos, but install.packages() works well.

The end result is a two-part system. You store / structure the data in SQLite. SQL is such a powerful language that some transformations and such that may be memory intensive in R are comparatively trivial in a database system. From R, you can submit a query to the database and store the return as a data frame then perform your analysis.

If you think memory is an issue, upgrading the RAM in your system may be a cheap option, unless your motherboard is already maxed out.

---

### Post by avitua on 2011-10-12
Hi
Thanks for the answers, I will try with my sql but here are more details in case you have a suggestion

I have a file with 100,000 rows and 30001 cols from snp data. 
the structure is like this

Progeny Sire Dam Genotypes(paternal allele, maternal allele...)
1 0 0 1 2 1 1 2 1.......

I require to change the format of the data to obtain 2 rows for each individual, the first row containing the paternal alleles and the second containing the maternal alleles. From the example before will be like this
progeny Genotypes
1 1 1 2.....
1 2 1 1.....

I try this

no.reg <- nrow(read.table("1001_mrk_001.txt"))
reg.acti <- read.table("1001_mrk_001.txt", nrows=1)
no.snp <- (ncol(reg.acti)-3)/2
reg.temp <- matrix(0, 2, no.snp+1)
reg.mod <- matrix(0, 2, no.snp+1)
pntero=1
c=1
for (i in 1:no.reg){
  reg.temp[c,1]=as.numeric(reg.acti[1,1])
  reg.temp[(c+1),1]=as.numeric(reg.acti[1,1])
  j=4
  k=5
  for (n in 1:no.snp){
    reg.temp[c,(n+1)]=as.numeric(reg.acti[1,j])
    reg.temp[(c+1),(n+1)]=as.numeric(reg.acti[1,k])
    j=j+2
    k=k+2
    }
  if(pntero < no.reg){
    reg.acti <- read.table("1001_mrk_001.txt", nrows=1, skip=pntero)
    pntero=pntero+1
    reg.temp <- rbind(reg.temp, reg.mod)
    }
  c=c+2
  }
write.table(reg.temp, "genotypes.txt", sep=" ", col.names=FALSE, row.names=FALSE)

It works with small data, but when i deal with the entire data i received an error message saying that cannot allocate the vector.

What i was thinking was to simply add lines to a file increasing it size for don't allocate all the data in the array, but unfurtunatly i can't find the instruction for write one line at the end of a text file in R. I tried with writeLines but what i got is a file with the last register.

Thank you

---

### Post by gunksta on 2011-10-12
I'll take a closer look at your code this evening, but as a general rule, R works best if you avoid loops. Your code is very manual, which has the somewhat counter-intuitive side-affect of usually slowing things down in R.

If I understand you correctly, you have some data that basically breaks down to this (I may have the alleles backwards.):

Person 1,  Maternal Alleles, Paternal Alleles
Person 2,  Maternal Alleles, Paternal Alleles
Person 3,  Maternal Alleles, Paternal Alleles

Your function wants to read them in and the create an output that looks like:
Person 1, Maternal Alleles
Person 1, Paternal Alleles
Person 2, Maternal Alleles
Person 2, Paternal Alleles
Person 3, Maternal Alleles
Person 3, Paternal Alleles

Just off the top of my head, is it necessary to have the rows next to one another? I assume a computer will do most of the work. Example:
Person 1, Maternal Alleles
Person 2, Maternal Alleles
Person 3, Maternal Alleles
Person 1, Paternal Alleles
Person 2, Paternal Alleles
Person 3, Paternal Alleles

It makes it harder (impossible) to eyeball things, but it also makes it MUCH simpler to put it together the way you want. In most cases, I would recommend [Plyr]("http://cran.r-project.org/web/packages/plyr/index.html"), but you have a special case here because your data is quite wide. Plyr may not handle this well.

Look at my simplified examples of structure and tell me what you think.

---

### Post by avitua on 2011-10-13
Thank you for your answer

The data is similar as you say, the format in the files is as:

person, marker 1 paternal allele, marker 1 maternal allele.. maker n paternal allele, marker n maternal allele

And the format that I give to the data (and that you correctly describe) is specific for use it on a program made for a colleague

As I need to do this only one for me is not very important if it takes long time to do it. 

At the end I solve it with the next code in case somebody is interested. It takes long time to do it but as I said I will do it one time only.

fle <- file.choose()
fle1 <- file.choose()
ped <- read.table(fle, skip=3, header=TRUE)
names <- colnames(ped)
write.table(ped[,1:3], "ped.txt", sep=" ", eol="\n", col.names=FALSE, row.names=FALSE)
no.reg <- nrow(ped)
reg.acti <- read.table(fle1, nrows=1, skip=4)
no.snp <- (ncol(reg.acti)-3)/2
reg.temp <- matrix(0, 2, no.snp+1)
reg.mod <- matrix(0, 2, no.snp+1)
pntero=1
c=1

for (i in 1:no.reg){
  reg.temp[1,1]=as.numeric(reg.acti[1,1])
  reg.temp[2,1]=as.numeric(reg.acti[1,1])
  j=4
  k=5
  for (n in 1:no.snp){
    reg.temp[1,(n+1)]=as.numeric(reg.acti[1,j])
    reg.temp[2,(n+1)]=as.numeric(reg.acti[1,k])
    j=j+2
    k=k+2
    }
  if(i == 1){
    write.table(reg.temp, "genotypes.txt", sep=" ", eol="\n", col.names=FALSE, row.names=FALSE)
    }else{
      write.table(reg.temp, "genotypes.txt", sep=" ", append=TRUE, eol="\n", col.names=FALSE, row.names=FALSE)
      }
  if(pntero < no.reg){
    reg.acti <- read.table(fle1, nrows=1, skip=pntero+4)
    pntero=pntero+1
    reg.temp <- reg.mod
    }
  c=c+2
  }

Thank you very much to all for your help.
(note, the above code made 2 files, one with the pedigree and other with the genotypes)

---

