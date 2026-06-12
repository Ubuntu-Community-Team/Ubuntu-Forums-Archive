---
title: "Problem with packages on R-project"
date: 2011-12-22
forum: Education &amp; Science
---

### Post by RumilSH on 2011-12-22
Hello all,

I'm new here and following memilanuk's suggestion I have opened this threat to tell you my problem (I've written the same question in a 1 year old thread but it could be better write one new,isn't it?). First I have to tell I'm Spanish and not very good at English so maybe I'll write something meaningless. If you don't understand something, tell me and I'll try to explain it better.

After that I'll expose my doubt. I've installed R on my Ubuntu (11.10). It works but the trouble is I have to use some packages like BiodiversityR and I've to install it every time I want to use them. I've already started R as root but nothing changes.

Do you have any suggestion? Thanks a lot.

---

### Post by gunksta on 2011-12-22
Interesting.

1 - What version of Ubuntu are you using? (10.10, 11.04, 11.10, etc.)
2 - What folders can be found in '~/R' ```
ls ~
```
3 - What folders can be found in '/root/R'? ```
sudo ls /root/R
```
4 - Do you know which packages you have tried to install via the Ubuntu repos as opposed to install.packages()?

---

### Post by RumilSH on 2011-12-23
Hi, thanks for reply.

I use Ubuntu 11.10 (Oneiric Ocelot I guess, isn't it?).

With "ls ~/R" y found just one folder: x86_64-pc-linux-gnu-library.

I've entered into the folder and there are another folder called 2.14 (I guess it's the R version) and finally into this folder:  

```
ACCLMA    ade4       BiodiversityR  permute  tclust  xtermStyle
accuracy  ade4TkGUI  mclust         sn       texmex
acepack   bayesm     mnormt         tcltk2   vegan

```

About the third question, I haven't found any folder
```
ls: can not access / root / R: No such file or directory
```

I've installed all packages with "install.packages()". I edited the sourcers.list and added this one 
```
http://cran.r-project.org/bin/linux/ubuntu oneiric/
```

---

### Post by PGScooter on 2011-12-23
what happens when you open R and you run
library(BiodiversityR)
?

---

### Post by gunksta on 2011-12-26
I agree with PGScooter. It looks like you have successfully (and correctly) installed the necessary packages into your local user's profile. If you want to see what packages are recognized by R, you can use the command, 'library()'.

---

### Post by RumilSH on 2011-12-27
When y run "library(BiodiversityR)" this message appears:
```
> library(BiodiversityR)
Loading required package: vegan
Loading required package: permute
This is vegan 2.0-2

```
I've already installed these packages several times and it keep asking for they.
If I use the command "library()" I can see the next packages:
```
ACCLMA                  ACC & LMA Graph Plotting
accuracy                Tools for testing and improving accuracy of
                        statistical results.
acepack                 ace() and avas() for selecting regression
                        transformations
ade4                    Analysis of Ecological Data : Exploratory and
                        Euclidean methods in Environmental sciences
ade4TkGUI               ade4 Tcl/Tk Graphical User Interface
bayesm                  Bayesian Inference for
                        Marketing/Micro-econometrics
BiodiversityR           GUI for biodiversity and community ecology
                        analysis
mclust                  Model-Based Clustering / Normal Mixture
                        Modeling
mnormt                  The multivariate normal and t distributions
permute                 Functions for generating restricted
                        permutations of data
sn                      The skew-normal and skew-t distributions
tcltk2                  Tcl/Tk Additions
tclust                  Robust Trimmed Clustering
texmex                  Threshold exceedences and multivariate extremes

```

I thought I've to install all of them so, Why I can't install only these packages?

Thanks a lot.

---

### Post by gunksta on 2011-12-27
What are you expecting to happen? It looks like the BiodiversityR package is loading. I don't see any errors. I have never used this package, but most packages load their dependencies and then sit there waiting for instructions.

---

### Post by RumilSH on 2011-12-28
BiodiversityR keep loading but it never starts, and when I run Rmcdr I have to reinstall several packages that I've already installed before. For that reason if I don't have internet I can't run this packages.

---

### Post by gunksta on 2011-12-29
Hmmmm. Like I said before, I've never used this and I don't use RCMDR either, but I did some quick searching and found [this]("http://nbx4.nugo.org/bioinformatics/docs/BiodiversityR.html").

What happens if you:
```

library(BiodiversityR)
BiodiversityRGUI()  

```

This appears to be what you have to do to start RCMDR with the BiodiversityR menu items.

---

### Post by RumilSH on 2012-01-01
Happy New Year!

I've done what you said gunksta and this message appears
[IMG]http://img59.imageshack.us/img59/6273/msg1l.png[/IMG]

but I just have to click on yes and, in the next window, select the folder where the packages are installed.

[IMG]http://img576.imageshack.us/img576/6532/instalarpaquetes.png[/IMG]

Finally it Works!! Thanks a lot. I don't know why R don't search first the packages, anyway, I'm glad to have worked it out.

---

### Post by rewyllys on 2012-01-01
> **gunksta said:**
> Hmmmm. Like I said before, I've never used this and I don't use RCMDR either, but I did some quick searching and found [this]("http://nbx4.nugo.org/bioinformatics/docs/BiodiversityR.html").

What happens if you:
```

library(BiodiversityR)
BiodiversityRGUI()  

```

This appears to be what you have to do to start RCMDR with the BiodiversityR menu items.
@Gunsta, Thanks for finding this URL and reporting it here.  These statistics interest me also.

---

