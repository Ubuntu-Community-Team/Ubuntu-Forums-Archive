---
title: "What Are The Mathematical Formulas to Calculate Sin, Cos, Tan"
date: 2009-02-22
forum: Education &amp; Science
---

### Post by transmition on 2009-02-22
Basically my question is this:

What are the formulas needed in order to calculate Sin, Cos and Tan.
For example: Tan 40 = 0.83909963
Cos 70 = 0.34202014
Sin 82 = 0.99026807

---

### Post by WatchingThePain on 2009-02-22
This is your lucky day 

 sin=opp/hyp

cos=adj/hyp

tan=opp/adj :-)

---

### Post by transmition on 2009-02-22
Errr... no, that was not what I was looking for. There is no way I can use SohCahToa to determine what the decimal value of Tan 38 is. I am asking how those values are computed.

---

### Post by stefangr1 on 2009-02-22
They are usually approximated by Taylor Series:

sin(x)=x-(x^3)/3!+(x^5)/5!-(x^7)/7!+ ...

[http://en.wikipedia.org/wiki/Taylor_series](http://en.wikipedia.org/wiki/Taylor_series)

---

### Post by boof1988 on 2009-02-23
> **stefangr1 said:**
> They are usually approximated by Taylor Series:

sin(x)=x-(x^3)/3!-(x^5)/5!-(x^7)/7!- ...

[http://en.wikipedia.org/wiki/Taylor_series](http://en.wikipedia.org/wiki/Taylor_series)

Note the following corrections (in red font).

sin(x)=x-(x^3)/3![COLOR="Red"]+[/COLOR](x^5)/5!-(x^7)/7![COLOR="Red"]+[/COLOR] ...

@Transmition,

Also make sure you are using proper "*units*" (Okay... radians may not be truly a "*written*" unit).  Degrees or Radians... depending on how you are approximating the decimal expansion.

IIRC... radians are needed to use the Taylor Series Expansion.  I welcome any corrections to this.

---

### Post by SuperSonic4 on 2009-02-23
> **boof1988 said:**
> Note the following corrections (in red font).

sin(x)=x-(x^3)/3![COLOR="Red"]+[/COLOR](x^5)/5!-(x^7)/7![COLOR="Red"]+[/COLOR] ...

@Transmition,

Also make sure you are using proper "*units*" (Okay... radians may not be truly a "*written*" unit).  Degrees or Radians... depending on how you are approximating the decimal expansion.

IIRC... radians are needed to use the Taylor Series Expansion.  I welcome any corrections to this.

Indeed you are correct, radians are necessary. Also

*pi* radians = 180 degrees

---

### Post by hubie on 2009-02-23
The infinite series mentioned above is not the [Taylor series]("http://mathworld.wolfram.com/TaylorSeries.html"), but a [MacLaurin series]("http://mathworld.wolfram.com/MaclaurinSeries.html").  The difference is subtle, where the Taylor series is an expansion of a function about a point, say x0 = a, while the MacLaurin series is an expansion of the function about zero (a = 0).  Because of this, the MacLaurin series look much friendlier and cleaner.

In terms of practical computation, these series converge rather slowly.  If you want to get into the nitty-gritty of it all, particularly with computing with them, you can check out [this paper]("http://www.math.ubc.ca/~fdezeeuw/math180/180-10-MaclaurinTaylor.pdf").

What is usually done in hardware, whether it be the old hand-held calculator or a specialty FPGA is to use the [CORDIC]("http://en.wikipedia.org/wiki/Cordic") algorithm.  You can look at how it is done in code [here]("http://www.dspguru.com/info/faqs/cordic.htm"), and if you really want to get hardcore and want to implement it in hardware, you can check it out [here]("http://www.google.com/url?sa=U&start=1&q=http://web.njit.edu/~hkj2/The%2520CORDIC%2520Algorithm-all%255B1%255D.ppt&ei=vceiSYvUNNKgtweFovyCDQ&usg=AFQjCNFMbutus04EeWSfgnsVvJXfyDX29Q").

---

### Post by sanskaras on 2009-02-23
The are actually defined as Maclaurin series, or tayler series centered at zero.  Hense they are only useful if you are finding a value of sin, cos, etc close to zero,  As soon as you try to estimate a value not close to the center the amount of error is larger.

Thus for any value you have to find the tayler series centered at the value you want to find.  

So for sin:

The definition of a tayler series - sorry I don't know how to write math notation on here, you can pm me, and I can latex something if it's confusion.

f(x) = f(a) + (f'(a)/1!)(x-a) + (f''(a)/2!)(x-a)^2 + (f'''(a)/3!)(x-a)^3) ... and so on.  X is the value your computer, and a is the center.

First find all the derivatives of sin:

f(x) = sinx
f'(x) = cosx
f''(x) = -sinx
f'''(x) = -cosx 
f''''(x) = sinx
etc..derivatives repeat in a cycle

It's best to equate a series with a center of a value close to the value your computing to reduce the amount of error, therefore reducing the the amount of terms needed.

Also, I'd recommend to only use the common values of sin, cos, etc for the center values.  Ex.  sin(0) = 0, sin(pi/6) = .5, sin(pi/4) = sq.rt.(2)/2, sin(pi/6) = sq.rt.(3)/2, etc (refer to a unit circle)
For example if you want the sin(3.15) use pi as the center so the equation for that would be:

f(pi) = 0
f'(pi) = -1
f''(pi) = 0
f'''(pi) = 1

f(x) = -(x-pi) + ((x-pi)^3)/3!

So f(x) of 3.15 is -.0084072474 from this equation.  (3rd degree tayler series)

To find the error use the absolute value of the next term which would be
(x-pi)^5/5!  --- the error is equal to 3.5e-13, good estimation.

Example of a value farther from the center:

Using the equation above just to the 3rd degree to esimate sin(3.50)

f(3.50) = -.3507340945

The error - (3.50 - pi)^5/5! = 4.92e-5  

So you can see the effect of estimating the value of sin farther from the center of the taylor series, which can easily be reduced by using more terms.  If your writing a program you can simply write an algorithm to find the error first then predict the amount of terms you need and/or the center. 


Hope that helps,
Nick

---

### Post by gareththomasnz on 2009-07-27
While we are on the subject - check this out 

[http://www.coyotegulch.com/products/unit_circle/](http://www.coyotegulch.com/products/unit_circle/)

---

### Post by finch127 on 2009-07-28
Well being that they are ratios, an easy way of doing the computation (though not so accurate) practically would be how they did in the old days:

Make a line of oh, about 10 cm and then draw an angle on the end of the line and extend that angle's line very very far. 

Then draw a straight line, 90 degrees to the other end of the original line and draw it out until it intersects the angle-line. you have just formed a right triangle and you now, knowing the base of the triangle can measure the other sides, and use the already known angle to compute the ratios between sides given the angles.

Basically, what this means is that, regardless of how big or small the lines in the triangle are, if the angles are the same, the ratio of the sides will always be the same. The decimal value is calculated from the ratios [or it used to be a longgggggg time ago].

---

