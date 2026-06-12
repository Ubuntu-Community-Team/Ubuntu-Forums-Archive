---
title: "Newbie questions about Ocatave"
date: 2008-02-20
forum: Education &amp; Science
---

### Post by octavenewbie on 2008-02-20
Hello all,

How do I make a symbolic expression and take partial derivatives of that function. For example, in Matlab I would do this:

syms  b c d e f % Alerts matlab that these variables have no set value to them

a = b*2+ (d^e+f*e/f^2) %my expression

da=diff(a,'e') %takes the derivative of a with respect to e

b=1 %values for the variables
c=2
d=3
e=4
f=5

z=eval(da) % this will plug in the values above and evaluate the expression da, which is the derivative of function a with respect to e.
--------

So far octave does not seem to be recognizing  'syms'. How do I make a program like this Octave compatible?

Also, if you have any tips on how do this on Scilab, feel free to contribute.

---

### Post by thisismalhotra on 2008-02-21
What version of Octave do you have 2.9 or 3.0, the newer 1 may support what you need, I use octave but I mostly write my own functions and rarely use bult-ins except for the standard ones....

Also, see if you have octave-forge installed or not, that add extra finctionality to octave

Correct place to ask this question would be ocatve mailing list or web based view of the same on nabble..

[http://www.gnu.org/software/octave/help.html](http://www.gnu.org/software/octave/help.html)

[http://www.nabble.com/Octave-f1895.html](http://www.nabble.com/Octave-f1895.html)

---

