---
title: "Compiling formulas in Latex"
date: 2008-05-26
forum: Education &amp; Science
---

### Post by linderox on 2008-05-26
I read a lot literature how to provide dividing of the formulas to new lines,but it's work just on a short one good like 1st one and doesn't on main (2nd one)
```

\begin{equation}\begin{split}
\Psi = & \cos kz + i\sin kz + {} \\
& {} + \frac{f(\theta)}{r}
(\cos kr + i\sin kr)
\end{split}\end{equation}

```

I try different ways used {split} but everything stoped on the 2nd "\\". Can anybody say me why?

```


\begin{equation}\begin{split}
U = U_0\cos[c_1 \cos(\omega t) + c_2 cos(\omega_1 t) + \phi] \\
=U_0 \cos\phi\left[|J_0(c_1)J_0(c_2)| + \sum_n |2J_0(c_2 )J_{2n}(c_1)|\cos 2n\omega t \\
+\sum_k|2J_0(c_1 )J_{2k}(c_2)|\cos 2k\omega_1 t + \sum_n\sum_k |2J_2n(c_1)J_{2k}(c_2)| \cos [2(k\omega_1 — n\omega)t] \\
+\sum_n \sum_k|2J_{2n}(c_1)J_{2k}(c_2)|\cos [2(k\omega_1 + n\omega)t] \\
+\sum_n \sum_k|J_{2n-1}(c_1)J_{2k-1}(c_2)|\cos[(2k —1)\omega_1—(2n — 1)\omega]t \\
+\sum_n \sum_k|J_{2n-1}(c_1)J_{2k-1}(c_2)|\cos[(2k —1)\omega_1+(2n — 1)\omega]t\right] \\
+U_0\sin\phi\left[\sum_n |2J_0(c_2)J_{2n-1}(c_1)|\cos[(2n—1)\omega t] \\
+\sum_k | 2J_0(c_1)J_{2k-1}(c_2)|\cos[(2k — 1)\omega_1 t] \\
+\sum_n \sum_k|2J_{2n-1}(c_1)J_{2k}(c_2)|\cos[2k\omega_1—(2n—1)\omega]t \\
+\sum_n \sum_k|2J_{2n-1}(c_1)J_{2k}(c_2)|\cos[2k\omega_1+(2n—1)\omega]t \\
+\sum_n \sum_k|J_{2n}(c_1)J_{2k-1}(c_2)|\cos [(2k—1)\omega_1—2n\omega]t \\
+\sum_n \sum_k|J_{2n}(c_1)J_{2k-1}(c_2)|\cos [(2k—1)\omega_1+2n\omega]t\right]
\end{split}\end{equation}


```

---

### Post by mulder82 on 2008-05-26
Hi 
the problem is you use \left[ ... \right] in several line, instead using it in a single line.

You have to put square brackets by yourself using

```
$\big(\Big(\bigg(\Bigg($\quad
$\big\}\Big\}\bigg\}\Bigg\}$\quad
$\big\|\Big\|\bigg\|\Bigg\|$

```

bye bye
Luca

---

### Post by linderox on 2008-05-26
Thank you
hm.... but why it does not work?
\be
\begin{split}
P(t)=cos\theta J_0(\alpha) + 2 \cos \theta \sum_{n=1}^\infty  J_{2n}(\alpha)\cos[2n f_0 t +l_0] \\
&&-2\sin\theta \sum_{n=1}^\infty J_{2n-1}(\alpha)cos[(2n-1) f_0 t +l_0]
\end{split}
\label{equ:P_t_bessel}
\ee

---

### Post by mulder82 on 2008-06-04
sorry, I'm late :KS

try it in this way:

```

\begin{equation}\label{equ:P_t_bessel}
\begin{split}
P(t)&=cos\theta J_0(\alpha) + 2 \cos \theta \sum_{n=1}^\infty J_{2n}(\alpha)\cos[2n f_0 t +l_0] \\
&-2\sin\theta \sum_{n=1}^\infty J_{2n-1}(\alpha)cos[(2n-1) f_0 t +l_0]
\end{split}
\end{equation}

```

bye bye
Luca

---

### Post by JudgeFudge on 2008-06-06
Not as flexible, but eqnarray handles this well, eg:

\begin{eqnarray*}
	e_\infty & = & R_2 F_f d^{-1}	\\
        r_\infty 	& = & G_1 F_f d^{-1}		\\
        f_\infty 	& = & R_2 J_1 d^{-1}		
\end{eqnarray*}

---

### Post by mulder82 on 2008-06-10
if you have to write a single equation in several lines, "split" looks better than "eqarray"
try these two cases:

\begin{eqnarray}
e_\infty & = & R_2 F_f d^{-1} \\
r_\infty & = & G_1 F_f d^{-1} \\
f_\infty & = & R_2 J_1 d^{-1}
\end{eqnarray}


\begin{equation}
\begin{split}
e_\infty = & R_2 F_f d^{-1} \\
r_\infty = & G_1 F_f d^{-1} \\
f_\infty = & R_2 J_1 d^{-1}
\end{split}
\end{equation}

it is not so easy handle the numbering in eqarray, and also the spacing near the " = " is not so good

---

