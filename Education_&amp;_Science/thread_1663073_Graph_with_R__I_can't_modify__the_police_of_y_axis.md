---
title: "Graph with R : I can't modify  the police of y axis ?"
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
**bar.group(c, main="bar.group", cex.lab=0.5, cex.axis=0.5, las=1, ylab="pH", xlab="solubilité", col.lab="green", horiz=TRUE, density=4, col="blue",border="red", xlim=c(0,1.2)) # donne un graphique en barre avec les lettres marquent la différence statitistique entre les barres**
x11() # permet de faire afficher un graphique dans une seule fenêtre
bar.err(c, main="bar.err", cex.lab=0.5, cex.axis=0.5, las=1, ylab="pH", xlab="solubilité", col.lab="green", horiz=TRUE, density=4, col="blue",border="red", xlim=c(0,1)) # donne un graphique avec les barres d'erreurs
x11()
xyplot(ph ~ sol, data = a, main="xyplot", subscripts = TRUE, xlim = c(0, 1.2), scales = list(cex = 0.5, x = list(at = c(0, 1.2))), par.strip.text = list(cex = 1.2))
x11()
bwplot(ph ~ sol, data = a, main="bwplot", subscripts = TRUE, xlim = c(0, 1.2), scales = list(cex = 0.5, x = list(at = c(0, 1.2))), par.strip.text = list(cex = 1.2))
x11()
stripplot(ph ~ sol, data = a, main="stripplot", subscripts = TRUE, xlim = c(0, 1.2), scales = list(cex = 0.5, x = list(at = c(0, 1.2))), par.strip.text = list(cex = 1.2))
detach(a)


Could you please watch at the "bar.group" function. It is indicated "cex.axis=0.5". This modified only the police of the x axis but the police of y axis and the letters indicated on the bars are not modified

Please, could you help me as soon as possible to give me a solution ?

With best regards

---

### Post by demandeinfos on 2011-01-09
it's ok :

I must indicated  : par(cex=0.5) befor my graph

Best regards

---

