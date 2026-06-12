---
title: "Error when creating data set in R Commander (Rcmdr) by &quot;New Data Set&quot;"
date: 2009-08-15
forum: Education &amp; Science
---

### Post by youknowwhoian on 2009-08-15
I am new to Ubuntu as well as R.

When I was using the Rcmdr and want to enter data by "New Data Set", just after I had entered the name for the data set and clicked "OK", error message appear in my terminal as below:

> Error in if (eval(parse(text = paste("nrow(", dsnameValue, ")"))) == 0) { : 
  argument is of length zero

and in the R Commander Messages window as below:

[COLOR=Red]ERROR:  invalid device[/COLOR]

What's going on? Can anyone help?!~

Ubuntu 8.04 LTS
R version 2.6.2 (2008-02-08 )
Rcmdr Version 1.3-9

---

### Post by gunksta on 2009-08-16
What sort of data did you try to enter? (I'm grasping at straws here.)

---

### Post by ahmatti on 2009-08-18
Are you trying to enter and empty dataset? Or are you using illegal characters (like " " or $) in the variable name? If you give a bit more details I'm sure we can help you. 

You could also type in the data from the command line,  a small example on how to create a simple data.frame

```

numbers <- c(2,7,8,9)
labels <- c('label1','label2','label3','label2')
dataset <- data.frame(numbers,labels)

```

---

