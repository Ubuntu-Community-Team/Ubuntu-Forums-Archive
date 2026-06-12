---
title: "convert csv files to R script"
date: 2007-04-23
forum: Education &amp; Science
---

### Post by Lise on 2007-04-23
Hi,

Is it possible to convert a csv file, to an R script, so I can import it in RKward in a data file, so I can do easily analysis on it (so not in the command mode)


grtz
Annelies

---

### Post by Jussi Kukkonen on 2007-04-23
Kind of depends in the csv file you have and the R file you want, doesn't it? I don't think there's a general answer to that.

---

### Post by akniss on 2007-04-23
> **Lise said:**
> Hi,

Is it possible to convert a csv file, to an R script, so I can import it in RKward in a data file, so I can do easily analysis on it (so not in the command mode)


grtz
Annelies

I've never used RKward, but R has a command to read .csv files... it should be available from an RKward menu somewhere.  The R function is read.csv()
```
read.csv('filename.csv',header=T)
```

---

### Post by raja on 2007-04-23
At the current state of development of Rkward, it does seem easier to directly read the csv with read.csv and then attach it - you immediately have all the column names as variables.

---

### Post by Lise on 2007-04-24
> **raja said:**
> At the current state of development of Rkward, it does seem easier to directly read the csv with read.csv and then attach it - you immediately have all the column names as variables.
what do you mean with "then attach it"?

the first step is ok (in the command mode I can do read csv , I got output (in the script mode) , but I want it in a table (data mode)

---

### Post by raja on 2007-04-24
> **Lise said:**
> what do you mean with "then attach it"?

Well, I am not an expert in R, but this is the easiest way I have found to work with it.Suppose you have a csv file  called 'drugs.csv' with data as follows

drug1,   drug2,   drug3
1,           2,          3
2,           4,           5
4,          4,            3
3,          3,            1

What I would do is

```
data = read.csv('drugs.csv')
attach(data)
boxplot(data)
t.test(drug1,drug2)
detach()
```

Just reading in the csv file produces a table, but accessing the variables is not straightforward. Once you attach it, you can directly access the variable 'drug1'. Hope I am making myself  clear.

---

### Post by Lise on 2007-04-24
Thanks, it works really good 
Problem solved !!

---

### Post by sabica on 2011-10-07
Hi all,
Can anybody please guide me regarding this error in R. I have converted a csv data file into .RData format and trying to apply Bayesian pca on this in R. But this error msg appears

"Error: Data is not numeric
Error in kEstimate(heisenberg, method = "bpca", allVariables = TRUE, evalPcs = 1:10,  :Invalid data format! Use checkData(Matrix, verbose = TRUE) for details".

---

### Post by akniss on 2011-10-07
> **sabica said:**
> Hi all,
Can anybody please guide me regarding this error in R. I have converted a csv data file into .RData format and trying to apply Bayesian pca on this in R. But this error msg appears

"Error: Data is not numeric
Error in kEstimate(heisenberg, method = "bpca", allVariables = TRUE, evalPcs = 1:10,  :Invalid data format! Use checkData(Matrix, verbose = TRUE) for details".

Start a new thread for this question... it is not really relevant to the discussion in this thread.

---

### Post by overdrank on 2011-10-07
Hi and welcome, please start a new thread. Thread closed

---

