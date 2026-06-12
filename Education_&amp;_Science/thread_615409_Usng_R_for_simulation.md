---
title: "Usng R for simulation"
date: 2007-11-17
forum: Education &amp; Science
---

### Post by hojjat on 2007-11-17
Hi all,

I'm relatively new to Linux, and have just downloaded R (to install it on my home machine). I want to use R for a simulation project, but I don't know if it is possible and how. Here is the description:

I want to give thousands of Means and Standard Deviations to the program, and get the returned p-value (and Confidence Interval if possible). The Mean, SD pairs are stored in a MySQL database (can be exported to a text file, if R works with them better) and I want to save the p-values in a separate table of the DB.

What I want to know is:

1) How to run t-test based on Mean and SD in R?

2) How to get the list of Mean and SDs from the DB/text file?

3) How to save the returned p-values to the DB/text file?

I would be grateful if you could help me with some of the above, or at least show me exactly where to find relevant information.

Btw, I have used SPSS in Windows for years, and have some experience with STATA, so don't bother yourself about the jargon.

Best,

Hojjat

---

### Post by akniss on 2007-11-17
[http://cran.r-project.org/src/contrib/Descriptions/RMySQL.html](http://cran.r-project.org/src/contrib/Descriptions/RMySQL.html)

```
R
?t.test
```

---

### Post by meatpan on 2007-11-17
1.  See previous post
2.  Use the 'mysql -e' command to extract data from the DB, into a text form.  The command will take a bit of research and practice.  Run '?read.table' in R, for instructions explaining how to import information from the filesystem into R
3.  Check out '?write.table' in R.

---

### Post by hojjat on 2007-11-17
Thanks for your replies. It'll take me some time to try to apply them. If I had a question, I'll come back.

---

