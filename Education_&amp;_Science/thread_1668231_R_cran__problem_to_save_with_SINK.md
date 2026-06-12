---
title: "R cran : problem to save with SINK"
date: 2011-01-16
forum: Education &amp; Science
---

### Post by demandeinfos on 2011-01-16
Good Morning,

I have a problem to save my results in a txt file with the function "SINK" with Opensource R cran project.

When I paste my script in R console all the results are saved in the txt file, it's ok. Yet, when I launch the script as a "SOURCE("/...), only the Duncan's tests and HSD are saved in the txt file, but AOV and all the normality (Levene, Bartlett, Shapiro) tests aren't.

Please, could you help me, and see below the script.

Thanks in advance for you answer.



SCRIPT
library(agricolae)
library(lattice)
library(FactoMineR)
library(GridR)
library(stats)
library(systemfit)
library(tseries)
library(laercio)
library(gplots)
sink("/Users/xxxxxx/TrtthsCs/solph3/solph3.txt")
a<-read.table("C:/Program Files/xxxxxxoluR2.txt", header=TRUE)
attach(a)
par(cex=0.5)
x11()
boxplot(sol~ph, data=a, cex.lab=0.5, cex.axis=0.5, las=2, main="Box", sub="Effet")
savePlot("/UsersxxxxxtthsCS/sol/boxplot.jpeg")
leveneTest(a$sol, a$ph, center=median)
bartlett.test(a)
shapiro.test(a$sol)
b<-aov(sol~ph, data=a)
summary(b) 
LDuncan(b, "ph", conf.level=0.95) 
d<-duncan.test(a$sol, a$ph, 23, 0.0002532, alpha=0.05, group=TRUE, main="ph vs sol")
x11()
par(cex=0.5)
par(mex=2)
bar.group(d, main="pH vs sol", sub="Résultats", cex.lab=1, cex.axis=1, las=1, ylab="pH", xlab="sol", col.lab="green", horiz=FALSE, density=0, col="blue",border="red", ylim=c(0,1.2))
savePlot("/UsersxxxxxxthsCS/duncan.jpeg")
x11()
par(cex=0.5)
par(mex=2)
bar.err(d, main="pH vs sol", sub="Barres d'erreur", cex.lab=1, cex.axis=1, las=1, ylab="pH", xlab="sol", col.lab="green", horiz=FALSE, density=0, col="blue",border="red", ylim=c(0,1.2))
savePlot("/UserxxxxxxrtthsCS/solph/ba.jpeg")
c<-HSD.test(a$sol, a$ph, 23, 0.0002532, alpha=0.05, group=TRUE)
x11()
par(cex=0.5)
par(mex=2)
bar.group(c, main="Effets", sub="Résultats", cex.lab=1, cex.axis=1, las=1, ylab="pH", xlab="sol", col.lab="green", horiz=FALSE, density=0, col="blue",border="red", ylim=c(0,1.2))
x11()
par(cex=0.5)
par(mex=2)
bar.err(c, main="Effets", sub="Bar", cex.lab=1, cex.axis=1, las=1, ylab="pH", xlab="sol", col.lab="green", horiz=FALSE, density=0, col="blue",border="red", ylim=c(0,1.2))
detach(a)") a

---

