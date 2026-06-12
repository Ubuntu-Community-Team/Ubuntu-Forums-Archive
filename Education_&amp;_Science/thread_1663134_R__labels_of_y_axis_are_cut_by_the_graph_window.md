---
title: "R : labels of y axis are cut by the graph window ?"
date: 2011-01-09
forum: Education &amp; Science
---

### Post by demandeinfos on 2011-01-09
Good afternoon,

I you show the following script that I made for a Tukey HSD test :


library(agricolae) # library permet de charger un package dont on va utiliser les fonctions dans le script
library(lattice)
library(FactoMineR)
par(mfrow=c(2,2)) # permet d'afficher 2 graphiques par ligne et 1 par colonne dans une même fenêtre
a<-read.table("C:/Progra...3.txt", header=TRUE)
attach(a)
x11() # permet de faire afficher un graphique dans une seule fenêtre
boxplot(sol~ph, data=a, cex.lab=0.5, cex.axis=0.5, las=2)
bartlett.test(sol~ph, data=a)
b<-aov(sol~ph, data=a)
summary(b) # permet d'afficher les résultats de l'ANOVA
c<-HSD.test(a$sol, a$ph, 205, 0.000411, group=TRUE) # HSD.tests fonctionne si le package "agricolae" a été installé
x11() # permet de faire afficher un graphique dans une seule fenêtre
**bar.group(c, main="bar.group", cex.lab=0.5, cex.axis=0.5, las=1,  ylab="pH", xlab="solubilité", col.lab="green", horiz=TRUE, density=4,  col="blue",border="red", xlim=c(0,1.2)) # donne un graphique en barre  avec les lettres marquent la différence statitistique entre les barres**
x11() # permet de faire afficher un graphique dans une seule fenêtre
bar.err(c, main="bar.err", cex.lab=0.5, cex.axis=0.5, las=1, ylab="pH",  xlab="solubilité", col.lab="green", horiz=TRUE, density=4,  col="blue",border="red", xlim=c(0,1)) # donne un graphique avec les  barres d'erreurs
x11()
xyplot(ph ~ sol, data = a, main="xyplot", subscripts = TRUE, xlim = c(0,  1.2), scales = list(cex = 0.5, x = list(at = c(0, 1.2))),  par.strip.text = list(cex = 1.2))
x11()
bwplot(ph ~ sol, data = a, main="bwplot", subscripts = TRUE, xlim = c(0,  1.2), scales = list(cex = 0.5, x = list(at = c(0, 1.2))),  par.strip.text = list(cex = 1.2))
x11()
stripplot(ph ~ sol, data = a, main="stripplot", subscripts = TRUE, xlim =  c(0, 1.2), scales = list(cex = 0.5, x = list(at = c(0, 1.2))),  par.strip.text = list(cex = 1.2))
detach(a)

My problem is that the police of the y axis is cut by the windows. What is the solution, can I modify the size of the window or the size of the graph ?

Thanks a lot in advance for your answer

Best regards

---

### Post by hzambran_cl on 2011-01-12
Could you please give a reproducible example ?

We don't have access to the table: "C:/Progra...3.txt"

---

### Post by demandeinfos on 2011-01-14
Good morning,

Thanks for your answer, but I'm now able to modify my graphs thanks to helps found on the web.

Yet, I need others informations on statistical tests if you agree to answer (because I'm not statistician but I need statistics).

See just below a part of the results : 1 parameter (sol) was performed on differents compounds (a,b, ...) and all of these compounds were put in 3 conditions (ph6, ph7 and ph8), and measures were repeated.

ph               sol
apH6    0.97
apH6    0.99
apH6    0.97
apH6    0.96
apH7    0.96
apH7    0.97
apH7    1.01
apH7    0.98
apH8    0.93
apH8    0.94
apH8    0.96
apH8    0.93
bpH6    0.95
bpH6    0.93
bpH6    0.91
bpH6    0.93
bpH7    0.97
bpH7    0.93
bpH7    0.95
bpH7    0.96
bpH8    0.98
bpH8    0.92
bpH8    0.93
bpH8    0.96
cpH6    0.95
cpH6    0.93
cpH6    0.91
cpH6    0.93
cpH7    0.97
cpH7    0.93
cpH7    0.95
cpH7    0.96
cpH8    0.98
cpH8    0.92
cpH8    0.93
cpH8    0.96
(...)


To summarize what I want to know with R : if the "sol" of compounds were similar or different (and in this case which one) wathever the compounds and the pH.


Thanks a lot in advance for your answer.

---

### Post by sam81 on 2011-01-16
Hi, you can either increase the dimension of the window:
X11(width=8, height=7)

or you can change the size of the inner margins
par(mar=c(2,4,2,1))

or outer margins
par(mar=c(2,2,2,2))

when you change the size of the margins the first number referes to the bottom margin, the second to the left margin, and so on in a clockwise fashion. This document provides some info on setting margins etc... (see chapter 7.12) [http://xoomer.virgilio.it/sam_psy/soft/carcagno_R_guide.pdf]("http://xoomer.virgilio.it/sam_psy/soft/carcagno_R_guide.pdf")

---

