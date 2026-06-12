---
title: "Statistics"
date: 2010-02-18
forum: Education &amp; Science
---

### Post by ndmp on 2010-02-18
Hey guys

Does anyone know of an SPSS equivalent for ubuntu?

Thanks

---

### Post by earlycj5 on 2010-02-18
> **ndmp said:**
> Hey guys

Does anyone know of an SPSS equivalent for ubuntu?

Thanks

Quick search of this forum reveals discussions on PSPP...

---

### Post by Tibuda on 2010-02-18
> **ndmp said:**
> hey guys

does anyone know of an spss equivalent for ubuntu?

Thanks

spss.
[quote="http://www.spss.com/statistics"]
ibm spss statistics 18 for linux

    * operating system: Any linux os that meets the following requirements**:
          O 32 bit only
          o kernel 2.6.26.25
          o glibc 2.8
          o libstdc++6
          o xfree86-4.7
    * hardware:
          O processor: Intel or amd x86 processor running at 1ghz or higher
          o memory: 1gb ram or more recommended
          o minimum free drive space: 800mb***
          o dvd drive
          o super vga (800x600) or a higher-resolution monitor
    * web browser: Mozilla® firefox®

** note: Ibm spss statistics 18 was tested on and is supported only on red hat® enterprise linux 5 desktop and debian® 4.0[/quote]

---

### Post by anoop999 on 2010-02-19
Try R (package r-base in the Ubuntu repository). It takes a bit of time to learn but it is well worth it. It is very powerful and versatile and FREE, and is popular among applied statisticians.

---

### Post by earlycj5 on 2010-02-20
> **anoop999 said:**
> Try R (package r-base in the Ubuntu repository). It takes a bit of time to learn but it is well worth it. It is very powerful and versatile and FREE, and is popular among applied statisticians.

I certainly support using R since it's what I use for my work. However, the OP did ask for a SPSS equivalent for Ubuntu. R isn't much of an equivalent to SPSS I'm afraid. While they do the same thing, the interface of SPSS looks like this, [http://spss.en.softonic.com/images](http://spss.en.softonic.com/images) while R looks like this mostly.

```

>

```  ;)

I guess they do equivalent work, but if it were me asking and I asked for a Philips screwdriver and was handed a straight blade I would wonder.

---

### Post by tommers on 2010-02-21
You might also want to look at SOFA Statistics ([http://www.sofastatistics.com/home.php](http://www.sofastatistics.com/home.php)).  

SOFA (like PSPP) does not have the full functionality of SPSS, but it does provide a very friendly interface.

---

### Post by bryncoles on 2010-02-22
If you want something like SPSS (now PASW) for Linux, I give a big +1 for SPSS (since it runs on Linux - tested on Debian no less so should work on Ubuntu too). 

However, I give a bigger +1 to [R]("http://cran.r-project.org/"). I'd say add the repo's too, following the instructions from the CRAN website. 

It has a hellofa learning curve, which you might make easier by using a GUI (I like [Rcmdr]("http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/"), personally). 

After installing R, open a terminal and type 

```
R
```
(You have no idea how long it took em to figure that out the first time). Then if you're using Rcmdr, just type 

```
Rcmdr
```
Though be aware statistics people will shake their heads if you tell them you're using Rcmdr!

Finally, some tutorials in R might help. If you visit [www.rseek.org](www.rseek.org), it should see you right!

---

### Post by gunksta on 2010-02-22
[PSPP]("http://www.gnu.org/software/pspp/")

**- From the websites - **

PSPP is a program for statistical analysis of sampled data. It is a  Free replacement for the proprietary program SPSS, and appears very  similar to it with a few exceptions.

 PSPP can perform descriptive statistics, T-tests, linear regression and non-parametric tests. Its backend is designed to perform its analyses as fast as possible, regardless of the size of the input data. You can use PSPP with its graphical interface or the more traditional  syntax commands. 
    A brief list of some of the features of PSPP follows:
 
[LIST]
[*]Supports over 1 billion cases.
[*]Supports over 1 billion variables.
[*]Syntax and data files are compatible with SPSS.
[*]Choice of terminal or graphical user interface.
[*]Choice of text, postscript or html output formats.
[*]Inter-operates with      [Gnumeric]("http://www.gnome.org/projects/gnumeric/"),      [OpenOffice.Org]("http://openoffice.org/") and      other free software.
[*]Easy data import from spreadsheets, text files and database sources.
[*]Fast statistical procedures, even on very large data sets.
[*]No license fees.
[*]No expiration period.
[*]No unethical “end user license agreements”.
[*][Fully indexed]("http://www.gnu.org/software/pspp/manual/html_node/Concept-Index.html") user manual.
[*][Free Software]("http://www.gnu.org/philosophy/free-sw.html"); licensed under    [GPLv3]("http://www.gnu.org/licenses/gpl-3.0.html") or later.
[*]Cross platform; Runs on many different computers and many different operating systems.
[/LIST]
-------------------------------------------------------------------------

R is a good program, but it is hardly "equivalent" to R. PSPP is much closer, although it may or may not be be adequate, depending on what you are trying to do.

---

### Post by bryncoles on 2010-02-23
> **gunksta said:**
> [PSPP]("http://www.gnu.org/software/pspp/")

... 

R is a good program, but it is hardly "equivalent" to SPSS. PSPP is much closer, although it may or may not be be adequate, depending on what you are trying to do.

This is very true. PSPP will do less than SPSS (But it might do as much as you want). R will do infinitely more than you want it to do (but you might never figure out how to make it do it!)

---

### Post by gunksta on 2010-02-23
And depending on what the OP means by "equivalent" another option may be [SOFA Statistics]("http://www.sofastatistics.com/home.php"). SOFA is a SPSS-like program written in Python. Unlike PSPP it does not replicate the SPSS "syntax" language that many analysts are familiar with. Instead, it provides a python environment that has been specifically tooled for statistics. 

More importantly, SOFA provides a rich GUI and lots of helpful tips and information for analysts. SPSS is accessible because it provides a robust GUI. As much as I love R, it's not a realistic option for most of my co-workers. I work in the social sciences -- most of my colleagues aren't learning R this week. 

In fact, SOFA takes the strength of the GUI paradigm one step further by providing supplementary information and GRAPHS to help analysts develop meaningful insights into their data. 

And, because it is written in Python, it's accessible and easily extended. 

While it does not (and probably never will) have the insane wealth of additional tools, it doesn't need to for most students and many professional analysts. For users with little programming experience, this could become a really good alternative to SPSS.

There are two obvious caveats -- it is not file compatible (SOFA uses SQLite and other RDBMS systems for data storage) and the syntax is not compatible with SPSS, but it is still worth keeping an eye on, and it would not surprise me if SPSS data import/export could be added if requested. The developer appears to be very interested in getting feedback and feature requests from users.

---

