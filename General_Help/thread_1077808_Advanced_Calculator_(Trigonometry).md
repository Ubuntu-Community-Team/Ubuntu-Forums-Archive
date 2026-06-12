---
title: "Advanced Calculator (Trigonometry)"
date: 2009-02-22
forum: General Help
---

### Post by igor. on 2009-02-22
Hi,

my first thread here...

I am looking for a calculator that can handle trigonometry. Perhaps I am blind but I was unable to find arc functions (arcsine, arccosine and arctangent) in gcalctool. And I couldn't find it in bc either.

Would be great if anyone could help me with this.

Thanks,

igor

---

### Post by Gizenshya on 2009-02-22
I'm not familiar with those programs... but arctan is just inverse tangent.  os, instead of arctan of whatever, just do tan-1 of whatever.  always remember to make sure that you're in radians if you're working in radians, and degrees if you're working in degrees... people forget that all the time.

---

### Post by ibuclaw on 2009-02-22
arcus tangent is available in bc, but you must run it with the '-l' argument.
This here prints pi: 4*atan(1)
```
echo "scale=10; 4*a(1)" | bc -l
```

As for a better calculator, I like genius, it is a very powerful maths tool/language.
```
sudo apt-get install genius
```
Alternately, you can get the front-end **gnome-genius**, which includes some extra features such as graph plotting, etc.
```
sudo apt-get install gnome-genius
```
and here is an example of what you want at work:
```

*genius>* atan(123)
= 1.56266642461
*genius>* asin(123)
= 1.57079632679-5.50531501097i
*genius>* acos(123)
= 5.50531501097i

```
Regards
Iain

---

### Post by mcduck on 2009-02-22
Gnome's default calculator can do them. Just change the mode from "basic" to"scientific", and then mark the "Inv"-checkbox for inverse trigonometric functions.

Anyway, if you need a really powerful desktop calculator, I recommend [Qalculate]("http://qalculate.sourceforge.net/"). You'll find it in repositories, with separate packages for both Gnome and KDE.

---

### Post by igor. on 2009-02-23
Thanks a lot for your answers. :)

---

### Post by geirha on 2009-02-23
If I need to calulate something, I usually just whip up a python shell. It's very handy if you know a little python.
```
$ python
Python 2.5.2 (r252:60911, Jul 31 2008, 17:28:52) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from math import *
>>> 4*atan(1)
3.1415926535897931
>>> x= 4*atan(1)
>>> x
3.1415926535897931
>>> x * x * 2
19.739208802178716
>>> 

```

---

### Post by joeoettinger on 2011-10-24
For arctan: In advanced mode, use tan-¹ by clicking tan or typing "tan" and then pressing Ctrl+i for the inversion symbol. The documentation says you can use "atan" but that apparently does not work. 

Be sure to select (in calculator > preferences) whether you want the argument to be in degrees or radians.

[By the way, in Google's calculator the default arguments of the trig functions are in radians. To get, eg tan of 45 degrees you have to enter tan(45 degrees).] 


Checking to see that it works, with angle units in degrees:
 
tan(45) = 1

tan-¹(1) = 45

tan(30) = 0.577350269

arctan(0.577350269) 30

---

### Post by Angelus-Michael on 2011-10-24
> **ibuclaw said:**
> arcus tangent is available in bc, but you must run it with the '-l' argument.
This here prints pi: 4*atan(1)
```
echo "scale=10; 4*a(1)" | bc -l
```As for a better calculator, I like genius, it is a very powerful maths tool/language.
```
sudo apt-get install genius
```Alternately, you can get the front-end **gnome-genius**, which includes some extra features such as graph plotting, etc.
```
sudo apt-get install gnome-genius
```and here is an example of what you want at work:
```

*genius>* atan(123)
= 1.56266642461
*genius>* asin(123)
= 1.57079632679-5.50531501097i
*genius>* acos(123)
= 5.50531501097i

```Regards
Iain
[COLOR=RoyalBlue]***Thanks a lot. I love genius***[/COLOR]

---

### Post by godfreezone on 2012-06-27
> **joeoettinger said:**
> For arctan: In advanced mode, use tan-¹ by clicking tan or typing "tan" and then pressing Ctrl+i for the inversion symbol. The documentation says you can use "atan" but that apparently does not work. 

Be sure to select (in calculator > preferences) whether you want the argument to be in degrees or radians.

[By the way, in Google's calculator the default arguments of the trig functions are in radians. To get, eg tan of 45 degrees you have to enter tan(45 degrees).] 


Checking to see that it works, with angle units in degrees:
 
tan(45) = 1

tan-¹(1) = 45

tan(30) = 0.577350269

arctan(0.577350269) 30

Do you know I have a Classpad330 Casio Graphics calc and it doesn't have a simple key way of obtaining arc-functions. You have to go through the laborious route of putting the desired function under a 1, ie: 1/tanx....crazy! when the cacl is sooooo good in so many ways
Godfree
I doubt, therefore I think.

---

### Post by 3Miro on 2012-06-27
> **godfreezone said:**
> Do you know I have a Classpad330 Casio Graphics calc and it doesn't have a simple key way of obtaining arc-functions. You have to go through the laborious route of putting the desired function under a 1, ie: 1/tanx....crazy! when the cacl is sooooo good in so many ways
Godfree
I doubt, therefore I think.

First of all, 1/tan(x) = cot(x) and tan^(-1)(x) = arctan(x). One over tan(x) is the inverse with respect to multiplication and 1/tan(x) is cot(x). On the other hand, tan^(-1)(x) is the inverse with respect to function composition and is called the arctan(x) function. If you want to learn trigonometry, you should learn the difference between the two.

Second, Galculator has most of those functions, look it up if you need a more advanced calculator.

Third, this thread has been dead for years and probably none of the people on it care anymore. Do not resurrect old threads like that, this is called necromancy and it is bad for the forum. Either ignore the thread or if you have a question, start a new one.

---

### Post by Alan.Brown on 2012-06-27
Try SpeedCrunch (use Synaptic Pakage Manager or apt-get).  It has the arc functions


Alan

---

### Post by ubudog on 2012-06-27
Old thread closed.

---

