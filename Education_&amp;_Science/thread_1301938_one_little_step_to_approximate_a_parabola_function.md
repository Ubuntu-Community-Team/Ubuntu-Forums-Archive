---
title: "one little step to approximate a parabola function, where is the mistake?"
date: 2009-10-26
forum: Education &amp; Science
---

### Post by awayguy on 2009-10-26
Halo ppl.

i need help, there is one little mistake when execute following commands:

Vte<- c(0,3,6,9,12,15,18,21,24,27,30)
Te<- c(20.585, 20.992, 21.250, 21.555, 21.842, 22.121, 22.384, 22.498, 22.471, 22.445, 22.420)



modell1 <-nls(Te~a+b*Vte+c*Vte^2, start=list(a=0, b=1, c=1), subset=which(Vte<20.0),control=list(maxiter=100))
modell2 <-nls(Te~a+b*Vte+c*Vte^2, start=list(a=0, b=1, c=1), subset=which(Vte>20.0),control=list(maxiter=100))


Vte1c <- seq(0,24,0.1)
Vte2c <- seq(18,34,0.1)

kurve1 <- predict(modell1, list(V=Vte1c))
kurve2 <- predict(modell2, list(V=Vte2c))

C <- coef(modell1) [1]-coef(modell2)[1]
B <- coef(modell1) [2]-coef(modell2)[2]
A <- coef(modell1) [3]-coef(modell2)[3]

xS <- (-B+sqrt(B*B-4*A*C))/(2*A)


plot(0,0,type="n", xlim=c(21.5, 24.0), ylim=c(21.5, 24.0),
    xlab="V(NaOH) / ml",
    ylab="T / Celsius")
lines(Vte1c,kurve1,lwd=2)
lines(Vte2c,kurve2,lwd=2)
points(V,T,pch=4,bg="white")
abline(v=xS,lty=2)
text(xS,min(T),sprintf("%.1f mL",xS),pos=4)


when i execute it there comes the following "error":
that I overstepped the iterationsteps in modell2 <-nls(Te~a+b*Vte+c*Vte^2.

but that happens to if i set the ...control=list(maxiter=100)) to control=list(maxiter=5000)).

isnt there a possibility not to aproximate the secound parabola that exactly.

just have so save my link somewhere [http://scsys.co.uk:8002/35421](http://scsys.co.uk:8002/35421)

---

### Post by awayguy on 2009-10-27
Vte<- c(0,3,6,9,12,15,18,21,24,27,30)
Te<- c(20.585, 20.992, 21.250, 21.555, 21.842, 22.121, 22.384, 22.498, 22.471, 22.445, 22.420)



modell1 <-lm(Te~I(Vte)+I(Vte^2), subset=which(Vte<20.0))
modell2 <-lm(Te~I(Vte)+I(Vte^2), subset=which(Vte>20.0))

Vte1c <- seq(0,24,0.1)
Vte2c <- seq(18,34,0.1)

kurve1 <- predict(modell1, list(Vte=Vte1c))
kurve2 <- predict(modell2, list(Vte=Vte2c))

C <- coef(modell1)[1]-coef(modell2)[1]
B <- coef(modell1)[2]-coef(modell2)[2]
A <- coef(modell1)[3]-coef(modell2)[3]

xS <- (-B+sqrt(B*B-4*A*C))/(2*A)


plot(0,0,type="n", xlim=c(0, 34.0), ylim=c(20.0, 24.0),
xlab="V(NaOH) / ml",
ylab="T / Celsius")
lines(Vte1c,kurve1,lwd=2)
lines(Vte2c,kurve2,lwd=2)
points(Vte,Te,pch=4,bg="white")
abline(v=xS,lty=2)
text(xS,min(Te),sprintf("%.1f mL",xS),pos=4)



with regards

---

