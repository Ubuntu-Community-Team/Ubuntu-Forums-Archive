---
title: "HOWTO: Mathematica equations in Gnuplot and LaTeX"
date: 2007-05-29
forum: Education &amp; Science
---

### Post by Copter on 2007-05-29
Hi!

In this howto I will give some basic tips and tricks on using Wolfram Research Mathematica with Gnuplot and LaTeX. It is nothing new and special but it took me some time to dig it by myself. Here it goes:

**Gnuplot**

To use Mathematica's equations in Gnuplot we just need to use function CForm. For example
```

CForm[myEquation]

```
will produce
```

Sqrt(Power(y + x*y,2) + Power(2 + x*(2 + x) - Power(y,2),2)/4.)

```
Now to plot function myEquation in Gnuplot we need to copy and paste following code
```

Power(x,y)=x**y
Sqrt(x)=Power(x,0.5)
myEquation(x,y)=Sqrt(Power(y + x*y,2) + Power(2 + x*(2 + x) - Power(y,2),2)/4.)

```
We need to remeber to add (just like above) functions Power and Sqrt to our Gnuplot code.

**LaTeX**

This part is easy because all we need to do is to use TeXForm. For example
```

TeXForm[myEquation]

```
will produce
```

{\sqrt{{\left( y + x\,y \right) }^2 + \frac{{\left( 2 + x\,\left( 2 + x \right)  - y^2 \right) }^2}{4}}}

```
The code listed above is ready to use in LaTeX equation enviroment. Now the tricky part. If the equation is too wide, does not fit paper size and produces bad boxes we need to split it to several lines. But we can't split commands like "\left(" and "\right)" nor braces ("{", "}"), so first we need to get rid of them as much as possible. For example in the code above we see some redundant braces. Where possible we have to delete them or change to "\left(" and "\right)" (excluding things like \frac{}{}, \sqrt{} and some others). For example
```

\begin{equation}
myEqn(x,y) = \sqrt{\left( y + x\,y \right)^2 + \frac{\left( 2 + x\,\left( 2 + x \right)  - y^2 \right) ^2}{4}}
\end{equation}

```
Also "\," is not needed
```

\begin{equation}
myEqn(x,y) = \sqrt{\left( y + xy \right)^2 + \frac{\left( 2 + x\left( 2 + x \right)  - y^2 \right) ^2}{4}}
\end{equation}

```
If we want to split sqare root we need to change it to explicit power form
```

\begin{equation}
myEqn(x,y) = \left(\left( y + xy \right)^2 + \frac{\left( 2 + x\left( 2 + x \right)  - y^2 \right) ^2}{4}\right)^\frac{1}{2}
\end{equation}

```
Now we can split it using eqnarray form
```

\begin{eqnarray}
myEquation(x,y)&=&\left(\left( y + xy \right)^2  \right.\\ 
&+& \left. \frac{\left( 2 + x\left( 2 + x \right)  - y^2 \right) ^2}{4}\right)^\frac{1}{2}
\end{eqnarray}

```
We see that when we split "\left(" and "\right)" we need to remeber to virtually close them in each line using "\right." and  "\left." (yes, there **is** dot after left and right). If we have problems with getting the number of those commands we can use the following method: add only closing commands ("\right."), compile our document and check errors. If the equation is missing closing commands LaTeX will produce one type of error. If we find the exact number of them (using hit/miss technique) the error will change saying that we have not enough opening commands ("\left."). Than we add the same number of opening commands to the second line as we added closeings to the previous line.

I hope it is clear enough :)

btw. For LaTeX GUI I highly recommend Kile. It is in the standard repos.

good luck!
Copter :]

---

